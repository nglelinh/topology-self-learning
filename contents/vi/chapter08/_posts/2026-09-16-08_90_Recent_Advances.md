---
layout: post
title: "Lecture 08.90: Tiến bộ gần đây (2022–2026) — Topological deep learning và Morse tính toán"
lang: vi
lang-ref: lecture-08-90
chapter: 8
lecture: 90
order: 90
lesson_type: optional
categories: [chapter08]
tags: [optional, recent-advances, topological-deep-learning, morse, bundles]
description: "Bài tùy chọn: π_n, bundle, Morse, manifold gặp TDL và Morse rời rạc. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Các nội dung về nhóm đồng luân bậc cao, bó thớ, lý thuyết Morse, đa tạp và nút giữ nguyên; bài này xem cách chúng đi vào *kiến trúc học sâu* và *thuật toán rút gọn* giai đoạn gần đây.

---

## 📖 Tổng quan

**Học sâu tô-pô** (Topological Deep Learning — TDL) xử lý dữ liệu xác định trên phức đơn hình, phức tế bào và siêu đồ thị — chính những miền tô-pô đã giới thiệu ở Chương 08. Hajij và cộng sự (2022/23) đặt khung khái niệm ban đầu; Papillon và cộng sự (2023/24) phân loại các kiến trúc truyền thông điệp (message-passing); Papamarkou và cộng sự (bài quan điểm tại ICML 2024) định vị TDL như một hướng mở rộng của học biểu diễn quan hệ. Song song đó, lý thuyết Morse rời rạc trở thành công cụ thực tế để tính đồng điều bền vững trên các tập dữ liệu kích thước lớn.

![Phức simplicial](https://upload.wikimedia.org/wikipedia/commons/5/50/Simplicial_complex_example.svg)
*Miền dữ liệu của TDL: không chỉ dừng ở đồ thị mà mở rộng sang các đơn hình ở mọi chiều. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

![Klein bottle](https://upload.wikimedia.org/wikipedia/commons/4/46/KleinBottle-01.png)
*Một đa tạp không nhúng được vào $\mathbb{R}^3$: minh họa rằng khái niệm đa tạp ở Chương 08 rộng hơn các mặt thông thường trong không gian Euclid. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:KleinBottle-01.png)*

---

## 🎯 Trực giác

Một mạng nơ-ron đồ thị (GNN) chỉ trao đổi thông tin dọc theo các cạnh ($1$-đơn hình). Ngược lại, một mạng đơn hình (simplicial neural network) có thể trao đổi thông tin trên các tam giác ($2$-mặt), cho phép mô hình nắm bắt trực tiếp quan hệ bậc cao giữa ba nút cùng thuộc một $2$-đơn hình — đây là cách chuyển cấu trúc phức CW và Morse của bài 08.02–08.03 thành tầng mạng học sâu. Tương tự, cấu trúc bó thớ xuất hiện khi các vectơ đặc trưng nằm trên từng thớ biến đổi theo phép chuẩn (gauge) khi di chuyển trên không gian cơ sở, tương tự ngôn ngữ vật lý nhưng được cài đặt dưới dạng tầng học được.

---

## 📐 Bốn tiến bộ cụ thể

### 1. TDL mở rộng vượt ra ngoài dữ liệu đồ thị

Hajij, Zamzmi, Papamarkou, Miolane, Dey, Birdal và các đồng tác giả (2022/23) hệ thống hóa TDL như bài toán học trên các miền tô-pô tổng quát (phức đơn hình, phức tế bào, phức tổ hợp), kết nối trực tiếp nội dung của Chương 08 với học sâu hình học (geometric deep learning).

- Mustafa Hajij et al., *Topological Deep Learning: Going Beyond Graph Data*, arXiv:2206.00606 (2022).

### 2. Khảo sát kiến trúc và bài quan điểm tại ICML 2024

Papillon, Sanborn, Hajij và Miolane (2023/24) phân loại các mạng nơ-ron tô-pô theo cơ chế truyền thông điệp trên các khung (skeleton) của phức. Papamarkou, Birdal, Bronstein, Carlsson, Curry cùng hơn 20 đồng tác giả (2024) công bố bài quan điểm tại ICML 2024 khẳng định TDL bổ sung chứ không thay thế học biểu diễn đồ thị, đồng thời chỉ ra các khoảng trống còn tồn tại về biểu diễn, hiệu năng tính toán và bộ tiêu chuẩn đánh giá (benchmark).

- Mathilde Papillon, Sophia Sanborn, Mustafa Hajij, Nina Miolane, *Architectures of Topological Deep Learning: A Survey of Message-Passing Topological Neural Networks*, arXiv:2304.10031 (2023).
- Theodore Papamarkou et al., *Position: Topological Deep Learning is the New Frontier for Relational Learning*, ICML 2024, arXiv:2402.08871.

### 3. Lý thuyết Morse rời rạc như công cụ tính toán cho bài 08.02

Bauer–Roll (2022) kết nối đồng điều bền vững với lý thuyết Morse rời rạc thông qua khái niệm "wrapping cycles". Guillou–Vidal–Tierny (2022) và Le Guillou–Fortin–Tierny (2025) phát triển *Discrete Morse Sandwich* thành quy trình xử lý phân tán. Ahuja–Iyer (2026) đưa các bất biến đồng luân đơn giản vào đồng điều bền vững nhờ Morse rời rạc. Như vậy, lý thuyết Morse không chỉ là định lý về cấu trúc tế bào mà còn đóng vai trò bước tiền xử lý rút gọn phức hiệu quả.

- Ulrich Bauer, Fabian Roll, *Wrapping Cycles in Delaunay Complexes: Bridging Persistent Homology and Discrete Morse Theory*, arXiv:2212.02345 (2022).
- Eve Le Guillou, Pierre Fortin, Julien Tierny, *Distributed Discrete Morse Sandwich*, arXiv:2505.21266 (2025).

### 4. Ứng dụng TDL trong vật liệu, protein và công cụ chẩn đoán

Wang, Jamasb, Hajij và cộng sự (2025) áp dụng TDL vào học biểu diễn protein (Topotein). Papillon và cộng sự (2026) xây dựng phương pháp chẩn đoán "look before you lift" cho các mô hình TDL. Yadav, Er, Goto và Xia (2026) sử dụng TDL tuần hoàn cho vật liệu polymer. Các khái niệm đa tạp và bó thớ của Chương 08 trở thành thiên kiến quy nạp (inductive bias) trực tiếp trong thiết kế mô hình.

- Zhiyu Wang, Arian Jamasb, Mustafa Hajij et al., *Topotein: Topological Deep Learning for Protein Representation Learning*, arXiv:2509.03885 (2025).
- Mathilde Papillon et al., *Look Before You Lift: Visual and Quantitative Diagnostics for Topological Deep Learning*, arXiv:2608.15388 (2026).

---

## 🧠 Tài liệu

- Hatcher, *Algebraic Topology*, Ch. 4 (nhóm đồng luân bậc cao).
- Milnor, *Morse Theory*.
- Các bài báo arXiv và ICML nêu trên.

## 🔗 Ứng dụng

Trong bài toán dự đoán tính chất polymer khi các đơn vị lặp nằm trên một phức tuần hoàn, TDL khai thác trực tiếp tính đối xứng được mô tả bởi bó thớ và tác động nhóm (Chương 05–08).

## Video tham khảo

- **xem trước** [Introduction to Topological Deep Learning](https://www.youtube.com/watch?v=N67GABKImZA) — Mathilde Papillon, tiếng Anh. Giới thiệu học sâu tô-pô vượt ra ngoài dữ liệu đồ thị, đúng mạch khảo sát của bài.
- [Nicholas Scoville: Discrete Morse Theory as an Introduction to Topology](https://www.youtube.com/watch?v=p7bzaDrNHrQ) — Kaleidoscope Circles, tiếng Anh. Lý thuyết Morse rời rạc của Nicholas Scoville, phiên bản tính toán được của lý thuyết Morse trong bài.

## 🧩 Bài tập

1. Hãy nêu một ví dụ về quan hệ 3 điểm mà mạng GNN thông thường không nắm bắt được nhưng mạng đơn hình có thể biểu diễn.
2. Liên hệ giữa chỉ số Morse (Morse index) và thời điểm "sinh/tử" của một vạch trong biểu đồ barcode.
3. Đọc phần tóm tắt (abstract) của bài báo Papamarkou et al. (2024) và liệt kê hai khoảng trống của TDL mà các tác giả nêu ra.
