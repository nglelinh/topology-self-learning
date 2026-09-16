---
layout: post
title: "Bài 09.90: Tiến bộ gần đây (2022–2026) — Vật liệu, thần kinh, đồ thị, và TDA đại chúng"
lang: vi
lang-ref: lecture-09-90
chapter: 9
lecture: 90
order: 90
lesson_type: optional
categories: [chapter09]
tags: [optional, recent-advances, materials, neuroscience, graph-tda, applications]
description: "Bài tùy chọn: topology đại chúng gặp ứng dụng TDA 2022–2026 (vật liệu, não, đồ thị, NLP). Không viết lại các câu chuyện lý thuyết."
---

**Bài tùy chọn.** Các câu chuyện cà phê–donut, Königsberg, Möbius, Euler, bốn màu, DNA, vật lý, Poincaré giữ nguyên. Ta chỉ thêm *chỗ* chúng đang chạy trong các paper ứng dụng gần đây.

---

## 📖 Tổng quan

Chapter 09 dạy topology bằng hình ảnh. Các nhóm 2022–2026 làm điều đối xứng: lấy hình ảnh đó — lỗ, nút, mạng, mặt — và đo trên vật liệu xốp, mạng nơ-ron sinh học, đồ thị xã hội, và ngôn ngữ. Bài này là bản đồ đọc, không phải bài vật lý hay sinh học mới.

![Mạng não](https://upload.wikimedia.org/wikipedia/commons/0/0e/Brain_network.png)
*Một mạng não: đồ thị mà TDA đọc lỗ và tỉ lệ. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Brain_network.png)*

![Đồ thị](https://upload.wikimedia.org/wikipedia/commons/3/3d/Undirected_graph.svg)
*Đồ thị vô hướng: hậu duệ trực tiếp của bảy cầu Königsberg. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Undirected_graph.svg)*

---

## 🎯 Trực giác

Công thức Euler $V-E+F$ đếm “lỗ” của đa diện. Persistent homology đếm lỗ của một đồ thị hoặc một đám mây nguyên tử *qua nhiều tỉ lệ*. Không cần công thức mới: cần một filtration. Đó là lý do Chapter 09 và Chapter 07 gặp nhau ở phòng thí nghiệm.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Vật liệu và phân tử: lỗ là đặc trưng vật lý

Wee và Jiang (2025) tổng kết TDA/TDL trong khoa học phân tử — đúng chỗ bài DNA-nút (09.06) gặp hóa học tính toán. Topolnicki, Bogdan, Malinowski, Naskręcki và Harańczyk (2026) dùng mô tả tử tô-pô có hướng để dự đoán tensor độ cứng của vật liệu xốp: “lỗ” không còn ẩn dụ, mà là đầu vào của mô hình đàn hồi.

- JunJie Wee, Jian Jiang, *A review of topological data analysis and topological deep learning in molecular sciences*, arXiv:2509.16877 (2025).
- Rafał Topolnicki et al., *Direction-aware topological descriptors for elastic stiffness tensor prediction in porous materials*, arXiv:2604.08105 (2026).

### 2. Thần kinh học: mạng, tỉ lệ, và tín hiệu

Gisolf, Santos và Wierstra (2023/24) dùng persistent homology để tách “tín hiệu / nhiễu” khỏi tính bất biến tỉ lệ trong mạng thần kinh và mạng tài chính. Connectome là một đồ thị khổng lồ — Königsberg viết lại. Ballester–Casacuberta–Escalera (2023) bổ sung cách TDA đọc *mạng nhân tạo*, tạo cặp so sánh não / máy.

- Roel Gisolf, Fernando A. N. Santos, Felix Wierstra, *Beyond Signal and Noise: Unraveling Scale Invariance in Neuroscience and Financial Networks with TDA*, arXiv:2311.17912 (2023).
- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *TDA for Neural Network Analysis*, arXiv:2312.05840 (2023).

### 3. TDA trên đồ thị và trên ngôn ngữ

Uchendu và Le (2024/26) khảo sát TDA trong NLP: câu và corpus được xem như đồ thị hoặc đám mây điểm ngữ nghĩa, rồi đo $H_0,H_1$. Grelier, Kaufmann và Pfau (2026) vẽ Games Mapper — Mapper trên thể loại Steam — một ứng dụng đại chúng đúng tinh thần Chapter 09.

- Adaku Uchendu, Thai Le, *Topological Data Analysis Applications in Natural Language Processing: A Survey*, arXiv:2411.10298 (2024).
- Nicolas Grelier, Stéphane Kaufmann, Johannes Pfau, *Games Mapper: Topological Data Analysis of Steam Genres*, arXiv:2606.14376 (2026).

### 4. Vị trí của TDL: từ câu chuyện đến kiến trúc

Papamarkou et al. (2024) và Su et al. (2025) đặt các ứng dụng trên vào một chương trình: học trên phức, không chỉ trên đồ thị. Với độc giả Chapter 09, thông điệp là đơn giản — cái tách cà phê và cái donut giờ là *inductive bias* của một layer.

- Theodore Papamarkou et al., *Position: Topological Deep Learning is the New Frontier for Relational Learning*, ICML 2024, arXiv:2402.08871.
- Zhe Su et al., *TDA and TDL Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

---

## 🧠 Tài liệu

- Adams & Franzosa, *Introduction to Topology: Pure and Applied* (các chương ứng dụng).
- Poincaré, *Analysis Situs* (1895) — nguồn gốc câu chuyện lỗ.
- Các arXiv trên.

## 🔗 Ứng dụng

Một lab vật liệu xốp có thể thay “nhìn ảnh SEM và đoán độ cứng” bằng barcode hướng của phần rỗng — Euler characteristic theo từng hướng. Đó là bài 09.04 đang chạy trên tensor đàn hồi.

## 🧩 Bài tập

1. Giải thích bằng một câu vì sao connectome cần $H_1$ chứ không chỉ số nút/cạnh (Königsberg).
2. Lấy một câu 6 từ, vẽ một đồ thị đồng xuất hiện, và đoán $H_0$.
3. Tìm trong Wee–Jiang (2025) một ví dụ TDA trên protein và viết nó lại bằng ngôn ngữ “cà phê / donut / lỗ”.
