---
layout: post
title: "Lecture 01.90: Tiến bộ gần đây (2022–2026) — Tô-pô của dữ liệu và phân cụm"
lang: vi
lang-ref: lecture-01-90
chapter: 1
lecture: 90
order: 90
lesson_type: optional
categories: [chapter01]
tags: [optional, recent-advances, clustering, topology-of-data, tda]
description: "Bài tùy chọn: point-set topology gặp clustering và TDA (2022–2026). Không viết lại lý thuyết."
---

**Bài tùy chọn.** Các định nghĩa về tập mở, cơ sở, bao đóng và ánh xạ liên tục của Chương 01 vẫn giữ nguyên. Bài này chỉ trình bày cách các khái niệm đó xuất hiện trong bài toán phân cụm và phân tích dữ liệu khi $X$ là một đám mây điểm.

---

## 📖 Tổng quan

Khi một nhà khoa học dữ liệu chạy thuật toán phân cụm trên tập khách hàng hay tế bào sinh học, câu hỏi đầu tiên luôn làm họ đau đầu là: *"dữ liệu này thực sự có 2 cụm, 3 cụm hay 5 cụm — và làm sao biết đó không phải do ta chọn sai ngưỡng khoảng cách?"* Hóa ra, câu hỏi thực tế ấy chính là phiên bản rời rạc của một câu hỏi kinh điển trong Chương 01: **làm thế nào định nghĩa cấu trúc "lân cận" và "tách cụm" trên một tập $$X$$ mà không bị lệ thuộc vào một thước đo cố định?**

Một tô-pô trên $$X$$ mô tả cấu trúc lân cận mà không cần cố định mê-tric; tương tự, giai đoạn 2022–2026 chứng kiến sự trưởng thành mạnh mẽ của **phân cụm tô-pô đa tỉ lệ** (như ToMATo và phân cụm dựa trên homology bền vững $$H_0$$), nơi các thuật toán đi kèm định lý ổn định toán học chặt chẽ.

![Phân cụm](https://upload.wikimedia.org/wikipedia/commons/c/c8/Cluster-2.svg)
*Hai cụm trong mặt phẳng: phiên bản rời rạc của tính không liên thông. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cluster-2.svg)*

**Mạch bài học:** Bản đồ kiến thức nền (phân cụm liên kết đơn & $$H_0$$ persistence, lọc theo mật độ ToMATo & giảm chiều bảo toàn lân cận) → Khung giải thích chậm: cầm tay chạy phân cụm đa tỉ lệ trên 4 điểm trên trục số và đọc số cụm thật → Trực giác & 4 tiến bộ 2022–2026 → Bài tập.

---

## Bản đồ kiến thức nền: Tô-pô của Dữ liệu và Phân cụm Tô-pô nghiên cứu những gì?

### 1. Phân cụm liên kết đơn (Single-Linkage) chính là $$H_0$$ bền vững

Nếu ta nối cạnh giữa hai điểm dữ liệu bất kỳ cách nhau $$\le r$$ rồi cho $$r$$ tăng dần từ $$0 \to \infty$$, số thành phần liên thông giảm dần từ $$N$$ xuống $$1$$. Mỗi lần hai cụm nhập làm một, cụm "non hơn" kết thúc vòng đời. Tập hợp các khoảng sống $$[0, r_{\text{death}})$$ chính là **biểu đồ bền vững bậc 0** — giúp nhận ra số cụm tự nhiên mà không cần đoán trước $$K$$ như K-means!

### 2. Phân cụm theo mật độ (ToMATo) và tính ổn định trước nhiễu

Liên kết đơn dễ bị "hiệu ứng cầu nối" (chỉ vài điểm nhiễu nằm giữa hai cụm cũng nối chúng thành một). Các thuật toán tô-pô hiện đại như **ToMATo** khắc phục bằng cách lọc theo **hàm ước lượng mật độ $$\hat{f}(x)$$** (siêu mức $$\{x : \hat{f}(x) \ge \lambda\}$$) rồi chỉ giữ lại những "đỉnh mật độ" có độ bền (prominence) vượt ngưỡng — vừa giữ cấu trúc tô-pô vừa miễn nhiễm với nhiễu thưa.

### 3. Giảm chiều (UMAP / t-SNE) dưới lăng kính ánh xạ liên tục và phép đồng phôi

Các phương pháp trực quan hóa dữ liệu nhiều chiều xuống 2D thực chất đang cố tìm một ánh xạ $$f: X \subset \mathbb{R}^D \to \mathbb{R}^2$$ bảo toàn lân cận cục bộ tốt nhất có thể — tức mô phỏng một phép nhúng tô-pô. Hiểu rõ ánh xạ liên tục và phép đồng phôi ở Chương 01 giúp ta nhận biết khi nào hình vẽ 2D đã **xé rách** hoặc **dán nhầm** các cụm trong dữ liệu gốc.

---

### Khung giải thích (nên đọc chậm): Cầm tay chạy phân cụm đa tỉ lệ $$H_0$$ trên 4 điểm trục số

Xét 4 điểm dữ liệu nằm trên đường thẳng thực:
$$
x_1 = 0,\qquad x_2 = 1,\qquad x_3 = 5,\qquad x_4 = 6.5.
$$
Khoảng cách giữa các cặp điểm kề nhau lần lượt là $$d(x_1, x_2) = 1$$, $$d(x_3, x_4) = 1.5$$, và khoảng trống giữa hai nhóm là $$d(x_2, x_3) = 4$$. Hãy tăng ngưỡng bán kính nối cạnh $$r$$ từ $$0$$ trở đi:

1. **Tại $$r = 0$$:** Có **4 cụm** cô lập: $$\{x_1\}, \{x_2\}, \{x_3\}, \{x_4\}$$ ($$\beta_0 = 4$$).
2. **Tại $$r = 1$$:** Cạnh $$(x_1, x_2)$$ xuất hiện → $$\{x_1, x_2\}$$ gộp thành 1 cụm. Số cụm giảm còn **3** (1 thanh $$H_0$$ chết tại $$r = 1$$).
3. **Tại $$r = 1.5$$:** Cạnh $$(x_3, x_4)$$ xuất hiện → $$\{x_3, x_4\}$$ gộp thành 1 cụm. Số cụm giảm còn **2**: $$\{x_1, x_2\}$$ và $$\{x_3, x_4\}$$ (1 thanh $$H_0$$ chết tại $$r = 1.5$$).
4. **Trong cả dải dài $$1.5 \le r < 4$$:** Cấu trúc **2 cụm đứng yên bất biến** suốt độ dài $$\Delta r = 4 - 1.5 = 2.5$$!
5. **Tại $$r = 4$$:** Cạnh cầu nối $$(x_2, x_3)$$ xuất hiện → mọi điểm hợp thành **1 cụm duy nhất** (thanh sống dài thứ hai chết tại $$r = 4$$; thanh cuối cùng sống tới $$\infty$$).

**Kết luận đọc từ mã vạch:** Bốn khoảng đời của $$H_0$$ là $$[0, 1),\; [0, 1.5),\; [0, 4),\; [0, \infty)$$. Khoảng nhảy lớn giữa $$1.5$$ và $$4$$ là dấu hiệu toán học định lượng khẳng định dữ liệu này tự nhiên chia thành **2 cụm**!

---

## 🎯 Trực giác

Theo định nghĩa tập mở, nếu $x \in U$ thì cả một vùng lân cận quanh $x$ cũng nằm trong $U$. Với dữ liệu thực tế, lân cận quanh $x$ thường được xấp xỉ bởi $k$ láng giềng gần nhất hoặc hình cầu bán kính $\varepsilon$. Khi $\varepsilon$ rất nhỏ, mỗi điểm tách thành một cụm riêng; khi $\varepsilon$ đủ lớn, toàn bộ dữ liệu gộp làm một. **Phân cụm bền vững** (*persistent clustering*) theo dõi sự xuất hiện và hợp nhất của các cụm khi thay đổi $\varepsilon$ — tương ứng trực tiếp với việc so sánh các tô-pô thô hơn và mịn hơn ở Bài 01.01.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Phân cụm mật độ đa tỉ lệ bền vững

Bot, McInnes và Aerts (2025) đề xuất *Persistent Multiscale Density-based Clustering*: thay vì chọn cố định một ngưỡng mật độ duy nhất, thuật toán theo dõi các thành phần liên thông của các tập siêu mức mật độ theo một phép lọc. Cách tiếp cận này chuyển trực tiếp khái niệm Chương 01 thành thuật toán: họ tập mở $\{x : \rho(x) > \lambda\}$ biến thiên theo $\lambda$ với sự thay đổi cấu trúc tô-pô được kiểm soát.

- Daniël Bot, Leland McInnes, Jan Aerts, *Persistent Multiscale Density-based Clustering*, arXiv:2512.16558 (2025).

### 2. ToMATo và phân cụm tô-pô đa tham số

Dòng thuật toán ToMATo (*Topological Mode Analysis Tool*) kết hợp các cực đại mật độ với homology bền vững $0$-chiều. Martineau, Pouzat và Geffray (2025) mở rộng ToMATo cho dữ liệu chiều cao (như phân loại tín hiệu thần kinh *spike sorting*). Andrianirina và Carrière (2026) tiếp tục phát triển thành ToMAToMP — thuật toán phân cụm đa tham số có tính ổn định. Về mặt hình học, mỗi "mode" tương ứng với đỉnh của hàm mật độ, còn các "thung lũng" là biên ngăn cách giữa các cụm — đúng với trực giác bao đóng và biên của tô-pô đại cương.

- Louise Martineau, Christophe Pouzat, Ségolen Geffray, *ToMATo: an efficient and robust clustering algorithm for high dimensional datasets*, arXiv:2509.17499 (2025).
- Ludo Andrianirina, Mathieu Carrière, *ToMAToMP: Robust and Multi-Parameter Topological Clustering*, arXiv:2605.14824 (2026).

### 3. Ánh xạ liên tục và phép đồng phôi trong giảm chiều

Thuật toán UMAP hướng tới việc bảo toàn cấu trúc tô-pô địa phương khi giảm chiều dữ liệu. Dalmia và Sia (2021, có ảnh hưởng kéo dài trong giai đoạn 2022–2026) chỉ ra rằng **tính liên thông** của đồ thị láng giềng quyết định trực tiếp chất lượng phân cụm sau khi chạy UMAP: mất cạnh nối có thể làm đứt thành phần liên thông. Đây là minh họa thực nghiệm cho Bài 01.03: một ánh xạ chỉ "gần liên tục" có thể phá vỡ tính đồng phôi và làm gộp hoặc tách nhầm các cụm.

- Ayush Dalmia, Suzanna Sia, *Clustering with UMAP: Why and How Connectivity Matters*, arXiv:2108.05525 (2021).

### 4. Tô-pô của mạng nơ-ron như không gian dữ liệu

Ballester, Casacuberta và Escalera (2023) khảo sát việc ứng dụng TDA để phân tích mạng nơ-ron: không gian trọng số, không gian kích hoạt và tập dữ liệu đều được xem như các không gian tô-pô, còn quá trình lan truyền tiến (*forward pass*) đóng vai trò ánh xạ liên tục giữa chúng — đúng theo khung lý thuyết của Chương 01 nhưng ở quy mô hàng triệu điểm.

- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *Topological Data Analysis for Neural Network Analysis: A Comprehensive Survey*, arXiv:2312.05840 (2023).

**Nhắc lại định nghĩa:** Nếu $f: X \to Y$ liên tục và $U \subset Y$ mở thì $f^{-1}(U)$ mở trong $X$. Trong một bộ mã hóa (*encoder*), tập mở thường được xấp xỉ bởi các hình cầu trong không gian tiềm ẩn; khi bộ mã hóa vi phạm tính liên tục theo nghĩa này, các cụm dữ liệu có thể bị xé rách.

---

## 🧠 Tài liệu tham khảo

- Munkres, *Topology*, Ch. 2 (tô-pô, cơ sở, tính liên tục).
- Adams & Franzosa, *Introduction to Topology: Pure and Applied*, Ch. 1.
- Các bài báo arXiv trích dẫn ở trên.

## 🔗 Ứng dụng

Phân nhóm dữ liệu tế bào đơn (*single-cell*) thường kết hợp giảm chiều UMAP với phân cụm dựa trên mật độ. Các khái niệm của Chương 01 giúp người học theo dõi trực tiếp các công trình nghiên cứu giai đoạn 2025–2026 trong lĩnh vực này.

## Video tham khảo

- **xem trước** [UMAP Dimension Reduction, Main Ideas!!!](https://www.youtube.com/watch?v=eN0wFzBA4Sc) — StatQuest with Josh Starmer, tiếng Anh. UMAP được giới thiệu như một phép giảm chiều. Bài này sẽ nói vì sao đó chưa phải là đồng phôi.
- [Henry Adams (5/3/22): Topology in Machine Learning](https://www.youtube.com/watch?v=kwYiQNa_pTc) — Applied Algebraic Topology Network, tiếng Anh. Tô-pô dùng như đặc trưng của dữ liệu và của phân cụm, sát các mục TDA của bài.
- [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, tiếng Anh. Thành phần liên thông và lỗ xuất hiện theo tỉ lệ, thứ mà thuật toán phân cụm đang cố thấy.

## 🧩 Bài tập

1. Xây dựng hai tô-pô trên cùng một tập gồm $5$ điểm: một tô-pô tách tập thành $2$ cụm mở rời nhau, tô-pô kia giữ cả $5$ điểm liên thông thành $1$ cụm. Trong hai tô-pô đó, tô-pô nào mịn hơn?
2. Giải thích vì sao việc tăng tham số $k$ trong đồ thị $k$-láng giềng gần nhất ($k$-NN) có tác dụng tương tự việc chuyển sang một cấu trúc thô hơn.
3. Xét một hàm mật độ $\rho$ trên $\mathbb{R}^2$ có hai đỉnh cực đại khác độ cao. Phác họa sự thay đổi của các tập siêu mức $\{\rho > \lambda\}$ khi $\lambda$ giảm dần.
