---
layout: post
title: "Lecture 03.90: Tiến bộ gần đây (2022–2026) — Phân ly, nhúng, và ổn định hình dạng"
lang: vi
lang-ref: lecture-03-90
chapter: 3
lecture: 90
order: 90
lesson_type: optional
categories: [chapter03]
tags: [optional, recent-advances, hausdorff, embedding, stability]
description: "Bài tùy chọn: tiên đề phân ly và metrization gặp ổn định TDA và phê bình UMAP. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Các tiên đề tách $T_0$–$T_4$, Bổ đề Urysohn và định lý mê-tric hóa của Chương 03 vẫn giữ nguyên. Bài này đặt câu hỏi: trong khoa học dữ liệu hiện đại, các dữ liệu và bất biến TDA "tách điểm" theo nghĩa nào?

---

## 📖 Tổng quan

Khi mở một biểu đồ UMAP hay t-SNE 2 chiều của hàng chục nghìn bức ảnh hay tế bào đơn lẻ, người dùng thường có cảm giác yên tâm rằng: *"hai chấm tách xa nhau trên hình thì chắc chắn chúng khác nhau trong dữ liệu gốc, còn hai chấm dính sát nhau thì là hàng xóm."* Nhưng trong khoa học dữ liệu giai đoạn 2022–2026, nhiều công trình phê bình sâu sắc đã chỉ ra rằng các phép giảm chiều phổ biến **không thực sự là phép nhúng tô-pô** — chúng có thể bóp méo khoảng cách toàn cục, thậm chí làm mất tính tách biệt của dữ liệu gốc.

Ngược lại, tính chất **Hausdorff** và **mê-tric hóa** của Chương 03 lại đóng vai trò nền móng cho **không gian các biểu đồ bền vững** trong TDA, nơi ta đo khoảng cách giữa hai "hình dạng dữ liệu" một cách chặt chẽ và có định lý ổn định Lipschitz bảo chứng.

![Khoảng cách Hausdorff](https://upload.wikimedia.org/wikipedia/commons/2/21/Hausdorff_distance_sample.svg)
*Khoảng cách Hausdorff giữa hai tập hợp: phiên bản định lượng gắn với tư duy tách điểm. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_distance_sample.svg)*

**Mạch bài học:** Kiến thức cần nhớ (khoảng cách Hausdorff & nút cổ chai trên biểu đồ bền vững, phê bình phép nhúng UMAP & điều kiện Lipschitz) → Giải thích: cầm tay tính khoảng cách Hausdorff $$d_H(A, B)$$ trên hai tập điểm hữu hạn để thấy độ nhạy với điểm nhiễu → Trực giác & 4 tiến bộ 2022–2026 → Bài tập.

---

## Kiến thức cần nhớ: Phân ly, Phép nhúng và Ổn định Hình dạng trong Dữ liệu 2022–2026 nghiên cứu những gì?

### 1. Không gian các biểu đồ bền vững là không gian mê-tric (Hausdorff)

Mỗi đám mây điểm sinh ra một biểu đồ bền vững (tập các cặp $$(b_i, d_i)$$). Để so sánh hai tập dữ liệu, TDA trang bị cho không gian các biểu đồ bền vững **khoảng cách nút cổ chai (bottleneck distance)** và **khoảng cách Wasserstein** — biến nó thành một không gian mê-tric thực thụ (nên tự động là không gian Hausdorff $$T_2$$ và chuẩn tắc $$T_4$$!).

### 2. Phép nhúng tô-pô vs. Giảm chiều trực quan (UMAP / t-SNE)

Một **phép nhúng tô-pô** (như phép nhúng vào $$[0, 1]^\omega$$ trong Định lý Urysohn) phải là đồng phôi lên ảnh của nó — không bao giờ được dán hai điểm xa nhau thành một hay xé rách lân cận. Trong khi đó, các thuật toán giảm chiều xuống 2D tối ưu hàm mất mát cục bộ nên dễ tạo ra cụm giả hoặc nén các cụm cách xa nhau lại sát nhau.

### 3. Từ liên tục thuần túy sang ổn định định lượng (Lipschitz)

Tính liên tục chỉ nói *"nhiễu đủ nhỏ thì đầu ra đổi nhỏ"*, chưa nói rõ đổi bao nhiêu. Trong học máy tô-pô hiện đại, ta cần **tính ổn định Lipschitz** ($$d(\Phi(X), \Phi(Y)) \le C \cdot d(X, Y)$$) để bảo đảm vector đặc trưng tô-pô đưa vào mô hình AI không bị rung lắc hỗn loạn trước nhiễu đo.

---

### Giải thích: Cầm tay tính khoảng cách Hausdorff $$d_H(A, B)$$ và thấy rõ độ nhạy với nhiễu

Cho hai tập con compact khác rỗng $$A, B$$ của không gian mê-tric $$(X, d)$$, **khoảng cách Hausdorff** được định nghĩa là giá trị lớn hơn giữa hai khoảng cách có hướng:
$$
d_H(A, B) = \max\!\Bigl(\,\sup_{a \in A} d(a, B),\;\; \sup_{b \in B} d(b, A)\,\Bigr).
$$
Hãy tự tay tính $$d_H(A, B)$$ trên trục số $$\mathbb{R}$$ cho hai tập điểm đơn giản:
$$
A = \{0,\; 2\}, \qquad B = \{0,\; 1,\; 5\}.
$$
1. **Tính khoảng cách có hướng từ $$A$$ sang $$B$$** (từ mỗi điểm của $$A$$, tìm điểm gần nhất trong $$B$$, rồi lấy lớn nhất):
   - $$d(0, B) = \min(\lvert 0-0\rvert, \lvert 0-1\rvert, \lvert 0-5\rvert) = \mathbf{0}$$.
   - $$d(2, B) = \min(\lvert 2-0\rvert, \lvert 2-1\rvert, \lvert 2-5\rvert) = \mathbf{1}$$.
   → $$\max_{a \in A} d(a, B) = \max(0, 1) = \mathbf{1}$$.
2. **Tính khoảng cách có hướng từ $$B$$ sang $$A$$:**
   - $$d(0, A) = \mathbf{0}$$; $$d(1, A) = \min(1, 1) = \mathbf{1}$$;
   - $$d(5, A) = \min(\lvert 5-0\rvert, \lvert 5-2\rvert) = \mathbf{3}$$.
   → $$\max_{b \in B} d(b, A) = \max(0, 1, 3) = \mathbf{3}$$!
3. **Lấy cực đại hai chiều:** $$d_H(A, B) = \max(1, 3) = \mathbf{3}$$!

**Bài học trực quan cho khoa học dữ liệu:** Hai tập $$A = \{0, 2\}$$ và $$\{0, 1\}$$ ban đầu chỉ cách nhau $$1$$, nhưng chỉ cần **một điểm nhiễu ngoại lai duy nhất** là $$5$$ lọt vào $$B$$ đã kéo vọt khoảng cách Hausdorff lên $$3$$! Chính vì thế, các bài toán dữ liệu thực tế năm 2022–2026 thường kết hợp khoảng cách Hausdorff với khoảng cách Wasserstein hoặc lọc theo mật độ để chống ngoại lai.

---

## 🎯 Trực giác

Bổ đề Urysohn khẳng định trong không gian chuẩn tắc, hai tập đóng rời nhau có thể tách bằng một hàm liên tục nhận giá trị trên $[0, 1]$. Các thuật toán như Mapper hay UMAP có thể nhìn như nỗ lực xấp xỉ các ánh xạ tách cấu trúc trên dữ liệu thực. Ngược lại, khi không gian nền không Hausdorff — chẳng hạn không gian Alexandroff hữu hạn trong công trình của Kayacan (Bài 00.90) — khả năng tách điểm bị giới hạn và các thuật toán nhúng dễ tạo ra khoảng cách giả tạo.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Không gian biểu đồ bền vững là không gian mê-tric (Hausdorff)

Mê-tric nút cổ chai (*bottleneck metric*) $d_B$ trên không gian các biểu đồ bền vững thỏa mãn bất đẳng thức ổn định:
$$
d_B(\mathrm{Dgm}(X),\mathrm{Dgm}(Y))\le d_{GH}(X,Y)
$$
(dưới các giả thiết compact thích hợp). Vì $(\mathrm{Dgm}, d_B)$ là không gian mê-tric nên nó là không gian Hausdorff ($T_2$): hai biểu đồ khác nhau luôn tách được bởi các hình cầu mở rời nhau. Fu et al. (2025) mở rộng định lý ổn định Gromov–Hausdorff cho tập dữ liệu có nhãn, củng cố việc xem mỗi barcode như một điểm tách biệt trong không gian mê-tric.

- Yaoying Fu et al., *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 2. Phê bình UMAP: không phải mọi phép giảm chiều đều là phép nhúng tô-pô

Yang (2026) chứng minh rằng UMAP, ở dạng thông dụng, thực chất hoạt động như **phân cụm phổ (*spectral clustering*) trên đồ thị láng giềng mờ** chứ không phải một phép nhúng tô-pô đúng nghĩa của đa tạp ẩn. Li và Zhang (2026) bổ sung các ràng buộc tiên nghiệm hình học và tô-pô (thuật toán JORC-UMAP) để khắc phục những điểm mà UMAP làm sai lệch cấu trúc tách cục bộ. Thông điệp từ Chương 03 rất rõ ràng: "biểu diễn được lên $\mathbb{R}^2$" không đồng nghĩa với "tồn tại một phép nhúng tô-pô".

- Yang Yang, *UMAP Is Spectral Clustering on the Fuzzy Nearest-Neighbor Graph*, arXiv:2602.11662 (2026).
- Xiaobin Li, Run Zhang, *Understanding and Improving UMAP with Geometric and Topological Priors: The JORC-UMAP Algorithm*, arXiv:2601.16552 (2026).

### 3. Không gian hữu hạn $T_0$ như tầng tính toán trung gian

Kayacan (2025) xây dựng homology bền vững trực tiếp trên không gian tô-pô hữu hạn $T_0$ (không Hausdorff). Điều này cho thấy trong thực hành TDA rời rạc, quy trình tính toán có thể đi qua các không gian trung gian không-$T_2$ trước khi xuất ra biểu đồ bền vững nằm trong không gian mê-tric Hausdorff.

- Selçuk Kayacan, *Persistent Homology via Finite Topological Spaces*, arXiv:2512.23348 (2025).

### 4. Vector hóa ổn định: điều kiện Lipschitz thay cho chỉ liên tục

Trong học máy, một ánh xạ chỉ liên tục trên không gian biểu đồ bền vững là chưa đủ vì nhiễu nhỏ ở đầu vào vẫn có thể khuếch đại mạnh ở đặc trưng đầu ra; ta cần tính liên tục Lipschitz. Loiseaux et al. (2023) và Bravetti, Mijangos và Padilla (2024) xây dựng các phương pháp vector hóa (kể cả cho homology bền vững đa tham số) kèm chứng minh ổn định định lượng.

- David Loiseaux et al., *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Alessandro Bravetti, Martín Mijangos, Pablo Padilla, *New divergence measures between persistence diagrams and stability of vectorizations*, arXiv:2410.03910 (2024).

---

## 🧠 Tài liệu tham khảo

- Munkres, *Topology*, Ch. 4–5 (tiên đề tách, Urysohn, mê-tric hóa).
- Willard, *General Topology*, Ch. 13–23.
- Các bài báo arXiv trích dẫn ở trên.

## 🔗 Ứng dụng

Khi một biểu đồ trực quan hóa UMAP tách hai nhóm bệnh nhân thành hai cụm riêng biệt, góc nhìn của Chương 03 nhắc ta kiểm tra xem đó là sự tách biệt thực sự trong dữ liệu gốc hay chỉ là hệ quả giả tạo của phân cụm phổ.

## Video tham khảo

- **xem trước** [UMAP Dimension Reduction, Main Ideas!!!](https://www.youtube.com/watch?v=eN0wFzBA4Sc) — StatQuest with Josh Starmer, tiếng Anh. UMAP được gọi là một embedding. Bài này tách từ đó khỏi embedding theo nghĩa tách và metric hóa.
- [Henry Adams (5/3/22): Topology in Machine Learning](https://www.youtube.com/watch?v=kwYiQNa_pTc) — Applied Algebraic Topology Network, tiếng Anh. Tô-pô trong học máy, nơi tính ổn định và điều kiện Lipschitz của bài thực sự được dùng.

## 🧩 Bài tập

1. Xây dựng một không gian tô-pô $3$ điểm thỏa $T_0$ nhưng không thỏa $T_1$. Không gian này có thể xuất hiện làm tầng trung gian của một phép lọc hữu hạn không?
2. Giải thích vì sao mê-tric nút cổ chai biến không gian biểu đồ bền vững thành không gian Hausdorff.
3. Đọc phần tóm tắt (*abstract*) bài báo của Yang (2026) và tóm gọn trong một câu: UMAP bảo toàn tính chất nào và không bảo toàn tính chất nào?
