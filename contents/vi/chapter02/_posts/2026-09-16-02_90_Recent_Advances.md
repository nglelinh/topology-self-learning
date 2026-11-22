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

Hai tính chất trọng tâm của tô-pô đại cương — **tính liên thông** (không thể phân tách) và **tính compact** (mọi phủ mở đều có phủ con hữu hạn) — gắn trực tiếp với hai câu hỏi trung tâm trong học máy hiện đại: (1) một tập dữ liệu gồm bao nhiêu cụm tự nhiên? (2) hai bộ trọng số tối ưu của một mạng nơ-ron có thể nối với nhau bằng một đường đi liên tục mà không phải vượt qua vùng mất mát cao hay không?

![Cà phê và torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)
*Liên thông đường trong không gian hình dạng: một đường biến dạng liên tục qua các phép đồng phôi. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif)*

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
