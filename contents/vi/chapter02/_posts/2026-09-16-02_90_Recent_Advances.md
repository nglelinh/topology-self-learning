---
layout: post
title: "Lecture 02.90: Tiến bộ gần đây (2022–2026) — Liên thông, compact, và thành phần của dữ liệu"
lang: vi
lang-ref: lecture-02-90
chapter: 2
lecture: 90
order: 90
lesson_type: optional
categories: [chapter02]
tags: [optional, recent-advances, connectedness, compactness, mode-connectivity]
description: "Bài tùy chọn: connectedness/compactness gặp clustering, persistence 0-chiều, và mode connectivity. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Các định nghĩa về tính liên thông, liên thông đường và tính compact của Chương 02 vẫn giữ nguyên. Bài này giới thiệu cách những khái niệm đó được vận dụng trong phân tích dữ liệu và nghiên cứu không gian tham số của mạng nơ-ron.

---

## 📖 Tổng quan

Khi huấn luyện cùng một mạng nơ-ron sâu từ hai bộ trọng số khởi tạo ngẫu nhiên khác nhau, thuật toán tối ưu hội tụ về hai nghiệm $$w_A$$ và $$w_B$$ cách nhau rất xa trong không gian hàng triệu tham số. Nếu lấy trung bình cộng trực tiếp $$\frac{1}{2}(w_A + w_B)$$, độ chính xác thường tụt thảm hại — khiến người ta từng tin rằng các cực tiểu nằm trong những "thung lũng cô lập" ngăn cách bởi những bức tường mất mát khổng lồ. Thế nhưng một khám phá gây chấn động của học sâu giai đoạn gần đây cho thấy: **hai cực tiểu đó thực ra vẫn nối được với nhau bằng một đường cong liên tục nằm hoàn toàn dưới đáy thung lũng mất mát thấp** (*Mode Connectivity*)!

Hai tính chất trọng tâm của Chương 02 — **tính liên thông** (không thể phân tách) và **tính compact** (mọi phủ mở đều có phủ con hữu hạn) — đang trở thành ngôn ngữ nền tảng để giải mã cả cấu trúc cụm của dữ liệu lẫn địa hình tối ưu của trí tuệ nhân tạo hiện đại.

![Cà phê và torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)
*Liên thông đường trong không gian hình dạng: một đường biến dạng liên tục qua các phép đồng phôi. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif)*

**Mạch bài học:** Bản đồ kiến thức nền (liên thông đường trong cảnh quan mất mát, liên thông tuyến tính sau hoán vị & vai trò tính compact trong ổn định TDA) → Khung giải thích chậm: cầm tay tính rào chắn mất mát trên đoạn thẳng vs. đường cong nối hai cực tiểu của một hàm mất mát 2 biến → Trực giác & 4 tiến bộ 2022–2026 → Bài tập.

---

## Bản đồ kiến thức nền: Tính Liên thông và Compact xuất hiện ở đâu trong Học máy 2022–2026?

### 1. Homology bền vững $$H_0$$ — lý thuyết thành phần liên thông đa tỉ lệ

Thay vì hỏi dữ liệu có liên thông tại một ngưỡng cố định hay không, $$H_0$$ theo dõi cách các thành phần liên thông hợp nhất dọc theo toàn bộ thang tỉ lệ, liên kết chặt chẽ với cây phân cấp (dendrogram) và phân cụm mật độ.

### 2. Mode Connectivity & Linear Mode Connectivity (LMC)

Trong không gian tham số $$\mathbb{R}^P$$ của mạng nơ-ron, tập siêu mức dưới $$S_\varepsilon = \{w \in \mathbb{R}^P : L(w) \le \varepsilon\}$$ là một không gian con. **Mode Connectivity** nói rằng các nghiệm tối ưu nằm trong cùng một **thành phần liên thông đường** của $$S_\varepsilon$$. Thậm chí **Linear Mode Connectivity** (sau khi căn chỉnh đối xứng hoán vị nơ-ron, như thuật toán Git Re-Basin năm 2022–2023) cho thấy ngay cả *đoạn thẳng* nối hai mô hình cũng giữ nguyên mức mất mát thấp — mở đường cho kỹ thuật **trộn mô hình (model merging)**!

### 3. Tính compact đảm bảo định lý tồn tại và ổn định trong TDA

Khi dữ liệu nằm trong một miền compact của $$\mathbb{R}^d$$, các phủ mở và tập mức của hàm khoảng cách đều kiểm soát được bằng hữu hạn bước — nhờ đó ta chứng minh được các định lý ổn định (nhiễu nhỏ trong dữ liệu kéo theo dịch chuyển nhỏ trong mã vạch).

---

### Khung giải thích (nên đọc chậm): Cầm tay kiểm chứng Mode Connectivity trên hàm mất mát 2 tham số

Để thấy trực tiếp sự khác biệt giữa **nội suy thẳng** (gặp núi cao) và **liên thông đường** (đi men theo thung lũng mất mát 0), hãy xét hàm mất mát đơn giản trên mặt phẳng tham số $$(w_1, w_2) \in \mathbb{R}^2$$:
$$
L(w_1, w_2) = (w_1^2 + w_2^2 - 1)^2.
$$
Tập các cực tiểu toàn cục ($$L = 0$$) chính là đường tròn đơn vị $$S^1$$. Chọn hai nghiệm tối ưu nằm ở hai vị trí khác nhau: $$A = (1, 0)$$ và $$B = (0, 1)$$ (dễ kiểm tra $$L(A) = L(B) = 0$$):

1. **Thử nối thẳng bằng đoạn thẳng (nội suy tuyến tính):**
   $$
   \ell(t) = (1 - t)A + tB = (1 - t,\; t), \qquad t \in [0, 1].
   $$
   Tại đúng trung điểm $$t = \frac{1}{2}$$, ta được $$M = (0.5,\; 0.5)$$. Tính hàm mất mát tại $$M$$:
   $$
   L(0.5,\; 0.5) = (0.5^2 + 0.5^2 - 1)^2 = (0.25 + 0.25 - 1)^2 = (-0.5)^2 = \mathbf{0.25} > 0!
   $$
   Nếu chỉ nhìn dọc đoạn thẳng, ta tưởng hai cực tiểu $$A, B$$ bị ngăn cách bởi một "ngọn núi" cao $$0.25$$!
2. **Thử nối bằng một đường cong liên tục (Mode Connectivity):**
   Chọn cung tròn $$\gamma(t) = \left(\cos\frac{\pi t}{2},\; \sin\frac{\pi t}{2}\right)$$ với $$t \in [0, 1]$$ ($$\gamma(0) = A,\; \gamma(1) = B$$). Tính hàm mất mát dọc toàn bộ đường đi:
   $$
   L(\gamma(t)) = \left(\cos^2\frac{\pi t}{2} + \sin^2\frac{\pi t}{2} - 1\right)^2 = (1 - 1)^2 = \mathbf{0} \quad \forall t \in [0, 1]!
   $$
   Hai cực tiểu $$A$$ và $$B$$ hoàn toàn **liên thông đường** ở mức mất mát 0 — minh họa thu nhỏ cực kỳ trong sáng cho hiện tượng Mode Connectivity trong không gian hàng tỉ tham số của mạng nơ-ron!

---

## 🎯 Trực giác

Một không gian liên thông không thể viết thành $X = U \cup V$ với $U, V$ mở, khác rỗng và rời nhau. Trong phân cụm, đó là mô tả tự nhiên của "một cụm" ở một tỉ lệ cố định. Homology bền vững bậc $0$ ($H_0$) tinh chỉnh ý tưởng này theo nhiều tỉ lệ: hai điểm thuộc cùng một thành phần ở bán kính $\varepsilon$ khi có một chuỗi điểm trung gian nối giữa chúng với mỗi bước dài không vượt quá $\varepsilon$. Về phía tính compact, câu hỏi về tính ổn định của biểu đồ bền vững (*persistence diagram*) gắn liền với tính đầy đủ và tính compact địa phương của không gian các biểu đồ hữu hạn dưới mê-tric nút cổ chai (*bottleneck metric*).

---

## 📐 Bốn tiến bộ cụ thể

### 1. Homology bền vững $H_0$ như lý thuyết thành phần đa tỉ lệ

Bot, McInnes và Aerts (2025) cùng dòng thuật toán ToMATo 2025–2026 (xem Bài 01.90) mở rộng khái niệm thành phần liên thông thành một **đối tượng đa tỉ lệ**. Nếu
$$
X_{\varepsilon}=\bigsqcup_{\alpha} C_{\alpha}(\varepsilon)
$$
là phân hoạch thành các thành phần liên thông đường của phức ở tỉ lệ $\varepsilon$, thì mỗi thời điểm kết thúc ("cái chết") của một thanh trong barcode $H_0$ tương ứng với lúc hai thành phần $C_\alpha$ hợp nhất với nhau.

- Daniël Bot, Leland McInnes, Jan Aerts, *Persistent Multiscale Density-based Clustering*, arXiv:2512.16558 (2025).

### 2. Tính liên thông giữa các cực tiểu (*Mode connectivity*) trong cảnh quan mất mát

Với một mạng nơ-ron có tham số $w \in \mathbb{R}^N$ và hàm mất mát $L$, xét tập dưới mức (*sublevel set*):
$$
S_c=\{w:L(w)\le c\}.
$$
Bài toán **mode connectivity** đặt câu hỏi liệu $S_c$ có liên thông đường khi $c$ đủ gần mức tối ưu hay không. Các công trình giai đoạn 2025–2026 mở rộng câu hỏi này vượt ra ngoài mô hình phân loại cổ điển: Yao, Zhang và Tian (2026) khảo sát đường nối cực tiểu ở các mô hình sinh và học tương phản; Cheng và Amiri (2026) phân tích bài toán *machine unlearning* qua góc nhìn liên thông đường.

- Chengzheyi Yao, Yongzhao Zhang, Yongding Tian, *Mode Connectivity Beyond Classifiers: Evidence from Generative and Contrastive Models*, arXiv:2608.30366 (2026).
- Jiali Cheng, Hadi Amiri, *Understanding Machine Unlearning Through the Lens of Mode Connectivity*, arXiv:2607.23970 (2026).

### 3. Liên thông tuyến tính giữa các cực tiểu (*Linear mode connectivity*) ở quy mô lớn

*Linear mode connectivity* đòi hỏi đường nối giữa hai cực tiểu $w_0, w_1$ là chính đoạn thẳng $(1 - t)w_0 + t w_1$ nằm trọn trong $S_c$ — một điều kiện mạnh hơn nhiều so với liên thông đường tổng quát:
$$
\gamma(t)=(1-t)w_0+tw_1,\qquad t\in[0,1],\qquad L(\gamma(t))\le c.
$$
Li và Shen (2026) khảo sát tính chất này trên các mô hình Transformer cỡ hàng tỷ tham số; Tran et al. (2026) phân tích tính tương đương hàm của cơ chế chú ý (*attention*) như một cơ chế giải thích khả năng nối tuyến tính giữa các nghiệm.

- Tianyi Li, Zhiqiang Shen, *Scaling Linear Mode Connectivity and Merging to Billion Parameter Pretrained Transformers*, arXiv:2606.23607 (2026).
- Viet-Hoang Tran et al., *Functional Equivalence in Attention: A Comprehensive Study with Applications to Linear Mode Connectivity*, arXiv:2606.17830 (2026).

### 4. Vai trò của tính compact trong kiểm soát ổn định của TDA

Định lý ổn định kinh điển (Cohen–Steiner, Edelsbrunner và Harer) chỉ ra ánh xạ từ không gian mê-tric compact sang không gian biểu đồ bền vững có tính Lipschitz theo mê-tric nút cổ chai. Các nghiên cứu gần đây về vector hóa biểu đồ bền vững (Loiseaux et al. 2023; Bravetti, Mijangos và Padilla 2024) tiếp tục xây dựng các phép nhúng Lipschitz để đưa barcode vào mạng nơ-ron mà vẫn giữ được tính ổn định.

- David Loiseaux, Luis Scoccola, Mathieu Carrière, Magnus Bakke Botnan, *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Alessandro Bravetti, Martín Mijangos, Pablo Padilla, *New divergence measures between persistence diagrams and stability of vectorizations*, arXiv:2410.03910 (2024).

---

## 🧠 Tài liệu tham khảo

- Munkres, *Topology*, Ch. 3 (tính liên thông, tính compact).
- Morris, *Topology without Tears*, Ch. 12–13.
- Các bài báo arXiv trích dẫn ở trên.

## 🔗 Ứng dụng

Khi hai điểm kiểm tra (*checkpoint*) của cùng một mô hình ngôn ngữ lớn có thể nối với nhau bằng một đoạn thẳng có hàm mất mát thấp, ta có thể trộn trực tiếp trọng số (*model merging*) thay vì phải chạy đồng thời nhiều mô hình — đây là ứng dụng thực tế trực tiếp của tính liên thông đường tuyến tính.

## Video tham khảo

- **xem trước** [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, tiếng Anh. H_0 bền vững như lý thuyết các thành phần liên thông của một mẫu dữ liệu.
- [[NeurIPS 2018] Loss Surfaces, Mode Connectivity, and Fast Ensembling of DNNs](https://www.youtube.com/watch?v=UwKdNzb_Q6U) — Timur Garipov, tiếng Anh. Mode connectivity: cảnh quan mất mát liên thông đường giữa các cực tiểu, đúng mục 2 của bài.

## 🧩 Bài tập

1. Phác họa tập dưới mức $S_c$ cho hàm $L(x, y) = (x^2 - 1)^2 + y^2$. Với những giá trị nào của $c$ thì $S_c$ liên thông?
2. Thảo luận sự khác biệt giữa liên thông và liên thông đường khi quan sát một đám mây điểm hữu hạn lấy mẫu từ đường cong sin của nhà tô-pô.
3. Giải thích trực quan vì sao tập các barcode có vô hạn vạch dài không mang tính "hữu hạn ẩn" như tập compact trong Định lý Heine–Borel.
