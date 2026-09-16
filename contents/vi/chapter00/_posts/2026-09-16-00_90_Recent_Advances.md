---
layout: post
title: "Lecture 00.90: Tiến bộ gần đây (2022–2026) — Dữ liệu hữu hạn và hình dạng của đám mây điểm"
lang: vi
lang-ref: lecture-00-90
chapter: 0
lecture: 90
order: 90
lesson_type: optional
categories: [chapter00]
tags: [optional, recent-advances, tda, finite-spaces, point-clouds]
description: "Bài tùy chọn: các tiến bộ 2022–2026 nối nền tảng tập hợp/Euclid với TDA trên dữ liệu hữu hạn. Không thay thế lý thuyết."
---

**Bài tùy chọn.** Lý thuyết của Chapter 00 không đổi. Bài này chỉ chỉ ra *chỗ* các tiên đề tập hợp, hàm, và không gian Euclid đang sống trong khoa học dữ liệu gần đây.

---

## 📖 Tổng quan

Chapter 00 dạy rằng mọi không gian tô-pô bắt đầu từ một **tập** $X$ và một họ tập con. Trong thực hành hiện đại, $X$ hầu như luôn hữu hạn: một đám mây điểm $\{x_1,\ldots,x_N\}\subset\mathbb{R}^d$, một bảng số, hoặc một đồ thị. Câu hỏi không còn là “$\mathbb{R}$ có đầy đủ không?” mà là “từ một tập hữu hạn, làm sao khôi phục hình dạng của không gian liên tục mà nó lấy mẫu?”

Đó chính là cầu nối từ lý thuyết tập hợp sang **Topological Data Analysis (TDA)**. Ba–bốn tiến bộ dưới đây cho thấy nền tảng Chapter 00 không “chỉ để chuẩn bị”: chúng đang được viết lại thành thuật toán.

![Đám mây điểm trên torus](https://upload.wikimedia.org/wikipedia/commons/4/4c/Point_cloud_torus.gif)
*Một torus được lấy mẫu hữu hạn — đúng loại đối tượng mà TDA cố gắng đọc lại. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Point_cloud_torus.gif)*

---

## 🎯 Trực giác

Hãy tưởng tượng bạn không được nhìn chiếc bánh donut, chỉ được một túi hạt muối rắc lên bề mặt nó. Bạn vẫn “thấy” một lỗ nếu, khi nối các hạt gần nhau thành cạnh rồi tam giác, lỗ đó **sống đủ lâu** khi bán kính nối tăng. Tập hợp hữu hạn cộng quan hệ “gần” đã đủ để nói về lỗ — không cần công thức khoảng cách đầy đủ trên toàn $\mathbb{R}^n$ ngay từ đầu.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Homology bền vững qua không gian tô-pô hữu hạn

Kayacan (2025) chỉ ra rằng persistent homology có thể được diễn đạt hoàn toàn trên **không gian tô-pô hữu hạn** (Alexandroff): mỗi giai đoạn lọc là một tập hữu hạn với topology xác định bởi một thứ tự. Điều này đưa Chapter 00 — tập, quan hệ, hàm — sát với pipeline tính toán: dữ liệu không cần được nhúng sẵn vào $\mathbb{R}^d$ mới có homology.

**Định nghĩa (nhắc lại, không thay lý thuyết):** một không gian Alexandroff hữu hạn có basis các lân cận tối thiểu $U_x$. Filtration hữu hạn là một dãy đơn điệu
$$
X_0\subseteq X_1\subseteq\cdots\subseteq X_m
$$
và persistent homology đọc các lớp $[z]\in H_n(X_i)$ còn sống ở $X_j$.

- Selçuk Kayacan, *Persistent Homology via Finite Topological Spaces*, arXiv:2512.23348 (2025).

### 2. TDA như hình học của mẫu Euclid — khung cho nhà khoa học dữ liệu

Khảo sát chuẩn của Chazal–Michel (vẫn là cửa vào 2022–2026) nhấn mạnh: một điểm dữ liệu là một phần tử của tập hữu hạn, và “hình dạng” là bất biến của các phức được xây từ khoảng cách Euclid. Su, Liu, Bou Hamdan, Maroulas, Wu, Carlsson và Wei (2025) cập nhật bức tranh: TDA không còn chỉ là persistent homology trên $\mathbb{R}^d$, mà là một họ bất biến (homotopy, sheaf, phức tế bào) xuất phát từ cùng một ý tưởng tập-và-quan-hệ.

- Frédéric Chazal, Bertrand Michel, *An introduction to Topological Data Analysis: fundamental and practical aspects for data scientists*, *Frontiers in Artificial Intelligence* (2021), arXiv:1710.04019.
- Zhe Su et al., *Topological Data Analysis and Topological Deep Learning Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

### 3. Ổn định Gromov–Hausdorff cho tập có nhãn

Fu, Lagoda, Li, Needham và Ver Hoef (2025) chứng minh một dạng ổn định Gromov–Hausdorff cho persistent homology của **tập có nhãn**. Đây là định lý kiểu Chapter 00+04: nếu hai tập hữu hạn gần nhau theo khoảng cách giữa các metric space, barcode không thể nhảy xa. Nền tảng “tập + ánh xạ + khoảng cách Euclid” trở thành định lý ổn định cho học máy.

- Yaoying Fu, Evgeniya Lagoda, Shiying Li, Tom Needham, Lander Ver Hoef, *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 4. TDA/TDL trong khoa học phân tử: dữ liệu là tập nguyên tử

Wee và Jiang (2025) tổng kết cách các tập hữu hạn nguyên tử — đúng nghĩa tập hợp, không phải đa tạp trơn — được biến thành đặc trưng tô-pô cho AI hóa học. Chapter 00 cho phép đọc các bài này mà không sợ “thiếu giải tích”: đối tượng ban đầu là tập và hàm.

- JunJie Wee, Jian Jiang, *A review of topological data analysis and topological deep learning in molecular sciences*, arXiv:2509.16877 (2025).

---

## 🧠 Tài liệu nền và bài báo

- James R. Munkres, *Topology*, 2nd ed., Ch. 1 (tập, hàm, tích).
- Sidney A. Morris, *Topology without Tears*, Ch. 1–2.
- Các arXiv nêu trên (2021–2025).

## 🔗 Ứng dụng

Trong hóa tin, một phân tử là một tập hữu hạn nguyên tử với quan hệ liên kết. Persistent homology đọc “lỗ” của tập đó qua nhiều tỉ lệ — cùng ngôn ngữ tập/hàm của bài 00.00–00.03.

## 🧩 Bài tập

1. Lấy 8 điểm trên một vòng tròn. Mô tả, không tính máy, khi nào phức “gần nhau” xuất hiện một $1$-cycle.
2. Vì sao một không gian Alexandroff hữu hạn luôn $T_0$ nhưng hiếm khi Hausdorff? Liên hệ bài 00.00 với Chapter 03.
3. Giải thích bằng lời: ổn định Gromov–Hausdorff nói gì về việc *thêm một điểm nhiễu* vào đám mây.
