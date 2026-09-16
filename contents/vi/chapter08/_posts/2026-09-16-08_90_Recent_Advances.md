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

**Bài tùy chọn.** Nhóm homotopy cao, fiber bundle, Morse, manifold, knot giữ nguyên. Ta xem chúng trở thành *kiến trúc học* và *thuật toán rút gọn*.

---

## 📖 Tổng quan

Topological deep learning (TDL) lấy dữ liệu sống trên phức simplicial, phức tế bào, siêu đồ thị — những domain mà Chapter 08 vừa đặt tên. Hajij et al. (2022/23) đặt nền; Papillon et al. (2023/24) phân loại kiến trúc message-passing; Papamarkou et al. (ICML 2024 position) tuyên bố TDL là biên của relational learning. Song song, Morse rời rạc trở thành công cụ tính persistence trên dữ liệu khổng lồ.

![Phức simplicial](https://upload.wikimedia.org/wikipedia/commons/5/50/Simplicial_complex_example.svg)
*Domain của TDL: không chỉ đồ thị, mà các simplex mọi chiều. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

![Klein bottle](https://upload.wikimedia.org/wikipedia/commons/4/46/KleinBottle-01.png)
*Một đa tạp không nhúng được trong $\mathbb{R}^3$: nhắc rằng “manifold” của Chapter 08 rộng hơn mặt trong không gian Euclid. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:KleinBottle-01.png)*

---

## 🎯 Trực giác

Một GNN chỉ nói chuyện theo cạnh ($1$-simplex). Một mạng simplicial nói chuyện theo tam giác: ba nút đã “biết” chúng cùng một $2$-face. Đó là Morse và CW của bài 08.02–08.03 viết thành layer. Fiber bundle xuất hiện khi feature sống trên các fiber thay đổi khi đi quanh base — đúng ngôn ngữ gauge mà vật lý đã dùng, giờ là layer học được.

---

## 📐 Bốn tiến bộ cụ thể

### 1. TDL vượt dữ liệu đồ thị

Hajij, Zamzmi, Papamarkou, Miolane, Dey, Birdal và nhiều đồng tác giả (2022/23) định nghĩa TDL: học trên domain tô-pô (simplicial, cell, combinatorial complex). Đây là bản tuyên ngôn nối Chapter 08 với geometric deep learning.

- Mustafa Hajij et al., *Topological Deep Learning: Going Beyond Graph Data*, arXiv:2206.00606 (2022).

### 2. Khảo sát kiến trúc và position ICML 2024

Papillon, Sanborn, Hajij và Miolane (2023/24) phân loại các topological neural network theo cách message đi trên skeleton. Papamarkou, Birdal, Bronstein, Carlsson, Curry và hơn 20 đồng tác giả (2024) viết position paper: TDL bổ sung — không thay — graph representation learning, và liệt kê các lỗ hổng (biểu diễn, tính toán, benchmark).

- Mathilde Papillon, Sophia Sanborn, Mustafa Hajij, Nina Miolane, *Architectures of Topological Deep Learning: A Survey of Message-Passing Topological Neural Networks*, arXiv:2304.10031 (2023).
- Theodore Papamarkou et al., *Position: Topological Deep Learning is the New Frontier for Relational Learning*, ICML 2024, arXiv:2402.08871.

### 3. Morse rời rạc như máy tính của Chapter 08.02

Bauer–Roll (2022) bắc cầu persistent homology và discrete Morse qua “wrapping cycles”. Guillou–Vidal–Tierny (2022) và Le Guillou–Fortin–Tierny (2025) biến Morse sandwich thành pipeline phân tán. Ahuja–Iyer (2026) đưa simple-homotopy invariants vào persistence qua Morse rời rạc. Morse không còn chỉ là định lý tế bào: nó là preprocessor.

- Ulrich Bauer, Fabian Roll, *Wrapping Cycles in Delaunay Complexes: Bridging Persistent Homology and Discrete Morse Theory*, arXiv:2212.02345 (2022).
- Eve Le Guillou, Pierre Fortin, Julien Tierny, *Distributed Discrete Morse Sandwich*, arXiv:2505.21266 (2025).

### 4. TDL trong vật liệu / protein, và chẩn đoán

Wang, Jamasb, Hajij et al. (2025) đưa TDL vào biểu diễn protein (Topotein). Papillon et al. (2026) xây chẩn đoán “look before you lift” cho TDL. Yadav, Er, Goto và Xia (2026) dùng TDL tuần hoàn cho polymer. Các đa tạp và bundle của Chapter 08 trở thành inductive bias.

- Zhiyu Wang, Arian Jamasb, Mustafa Hajij et al., *Topotein: Topological Deep Learning for Protein Representation Learning*, arXiv:2509.03885 (2025).
- Mathilde Papillon et al., *Look Before You Lift: Visual and Quantitative Diagnostics for Topological Deep Learning*, arXiv:2608.15388 (2026).

---

## 🧠 Tài liệu

- Hatcher, *Algebraic Topology*, Ch. 4 (higher homotopy).
- Milnor, *Morse Theory*.
- Các arXiv/ICML trên.

## 🔗 Ứng dụng

Dự đoán tính chất polymer khi đơn vị lặp lại sống trên một phức tuần hoàn: TDL dùng đúng symmetry mà bundle và group action (Chapter 05–08) đã mô tả.

## 🧩 Bài tập

1. Nêu một quan hệ 3-điểm mà GNN không thấy nhưng mạng simplicial thấy.
2. Liên hệ Morse index với “sinh/tử” của một vạch trong barcode.
3. Đọc abstract Papamarkou et al. (2024) và liệt kê hai lỗ hổng TDL mà họ nêu.
