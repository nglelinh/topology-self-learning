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

**Bài tùy chọn.** Phần lý thuyết cốt lõi của Chương 00 không thay đổi; bài này chỉ giới thiệu nơi các khái niệm tập hợp, ánh xạ và không gian Euclid được vận dụng trực tiếp trong khoa học dữ liệu gần đây.

---

## 📖 Tổng quan

Chương 00 cho thấy mọi không gian tô-pô đều bắt đầu từ một **tập hợp** $X$ cùng một họ tập con. Trong thực hành khoa học dữ liệu hiện đại, $X$ hầu như luôn là tập hữu hạn: một đám mây điểm $\{x_1,\ldots,x_N\}\subset\mathbb{R}^d$, một bảng dữ liệu, hoặc một đồ thị. Câu hỏi trọng tâm khi đó không còn là "$\mathbb{R}$ có đầy đủ không?" mà là "từ một tập điểm hữu hạn, làm thế nào khôi phục hình dạng của không gian liên tục mà nó lấy mẫu?"

Đó chính là cầu nối từ lý thuyết tập hợp sang **Phân tích dữ liệu tô-pô** (*Topological Data Analysis* — TDA). Bốn hướng nghiên cứu gần đây dưới đây cho thấy nền tảng của Chương 00 không chỉ là bước chuẩn bị lý thuyết, mà đang được chuyển hóa trực tiếp thành các công cụ thuật toán.

![Đám mây điểm trên torus](https://upload.wikimedia.org/wikipedia/commons/4/4c/Point_cloud_torus.gif)
*Một hình xuyến được lấy mẫu hữu hạn — đúng loại đối tượng mà TDA tìm cách nhận diện hình dạng. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Point_cloud_torus.gif)*

---

## 🎯 Trực giác

Hãy tưởng tượng bạn không nhìn thấy chiếc bánh donut, mà chỉ có một tập các hạt muối rắc trên bề mặt nó. Dù vậy, bạn vẫn có thể phát hiện ra "lỗ" ở giữa nếu nối các hạt nằm gần nhau thành cạnh và tam giác rồi tăng dần bán kính nối: một lỗ thực sự sẽ **tồn tại bền vững** qua một khoảng bán kính đủ rộng. Một tập hợp hữu hạn kèm quan hệ "gần nhau" đã đủ để mô tả đặc trưng lỗ mà chưa cần đến toàn bộ cấu trúc giải tích trên $\mathbb{R}^n$.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Homology bền vững qua không gian tô-pô hữu hạn

Kayacan (2025) chỉ ra rằng homology bền vững (*persistent homology*) có thể được diễn đạt hoàn toàn trên **không gian tô-pô hữu hạn** (không gian Alexandroff): mỗi bước lọc là một tập hữu hạn với tô-pô xác định bởi một quan hệ thứ tự. Cách tiếp cận này nối trực tiếp các khái niệm tập hợp, quan hệ và ánh xạ của Chương 00 với quy trình tính toán: dữ liệu không nhất thiết phải nhúng sẵn vào $\mathbb{R}^d$ mới xác định được homology.

<div class="textbook-definition" markdown="1">
**Định nghĩa (nhắc lại, không thay thế lý thuyết):** Một không gian Alexandroff hữu hạn có cơ sở gồm các lân cận tối thiểu $U_x$. Một phép lọc (*filtration*) hữu hạn là một dãy đơn điệu
$$
X_0\subseteq X_1\subseteq\cdots\subseteq X_m
$$
và homology bền vững theo dõi các lớp $[z]\in H_n(X_i)$ còn tồn tại khi chuyển sang $X_j$.
</div>

- Selçuk Kayacan, *Persistent Homology via Finite Topological Spaces*, arXiv:2512.23348 (2025).

### 2. TDA như hình học của mẫu Euclid — khung làm việc cho khoa học dữ liệu

Bài khảo sát của Chazal–Michel (vẫn là tài liệu nhập môn phổ biến trong giai đoạn 2022–2026) nhấn mạnh rằng mỗi điểm dữ liệu là một phần tử của tập hữu hạn, còn "hình dạng" được nắm bắt qua các bất biến của phức đơn hình xây từ khoảng cách Euclid. Su, Liu, Bou Hamdan, Maroulas, Wu, Carlsson và Wei (2025) cập nhật bức tranh rộng hơn: TDA hiện nay không chỉ dừng ở homology bền vững trên $\mathbb{R}^d$, mà mở rộng sang cả một họ bất biến (đồng luân, bó, phức tế bào) phát triển từ cùng nền tảng tập hợp và quan hệ.

- Frédéric Chazal, Bertrand Michel, *An introduction to Topological Data Analysis: fundamental and practical aspects for data scientists*, *Frontiers in Artificial Intelligence* (2021), arXiv:1710.04019.
- Zhe Su et al., *Topological Data Analysis and Topological Deep Learning Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

### 3. Ổn định Gromov–Hausdorff cho tập dữ liệu có nhãn

Fu, Lagoda, Li, Needham và Ver Hoef (2025) chứng minh một định lý ổn định kiểu Gromov–Hausdorff cho homology bền vững của **tập dữ liệu có nhãn**. Nếu hai tập hữu hạn gần nhau theo khoảng cách giữa các không gian mê-tric, thì biểu đồ thanh (*barcode*) của chúng cũng không thay đổi đột ngột. Nền tảng tập hợp, ánh xạ và khoảng cách Euclid từ đó trở thành cơ sở cho các định lý ổn định trong học máy.

- Yaoying Fu, Evgeniya Lagoda, Shiying Li, Tom Needham, Lander Ver Hoef, *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 4. TDA và học sâu tô-pô trong khoa học phân tử: dữ liệu là tập nguyên tử

Wee và Jiang (2025) tổng kết cách các tập hữu hạn nguyên tử — xét trực tiếp như các tập hợp rời rạc thay vì đa tạp trơn — được chuyển hóa thành đặc trưng tô-pô cho trí tuệ nhân tạo trong hóa học. Nền tảng của Chương 00 giúp người học tiếp cận các công trình này dễ dàng hơn vì đối tượng khởi đầu chính là tập hợp và ánh xạ.

- JunJie Wee, Jian Jiang, *A review of topological data analysis and topological deep learning in molecular sciences*, arXiv:2509.16877 (2025).

---

## 🧠 Tài liệu nền và bài báo

- James R. Munkres, *Topology*, 2nd ed., Ch. 1 (tập hợp, ánh xạ, tích Đề-các).
- Sidney A. Morris, *Topology without Tears*, Ch. 1–2.
- Các bài báo arXiv trích dẫn ở trên (2021–2025).

## 🔗 Ứng dụng

Trong hóa tin học, một phân tử được biểu diễn như một tập hữu hạn các nguyên tử kèm quan hệ liên kết. Homology bền vững đo các cấu trúc "lỗ" và khoang rỗng của tập đó qua nhiều tỉ lệ — sử dụng đúng ngôn ngữ tập hợp và ánh xạ đã học ở các bài 00.00–00.03.

## Video tham khảo

- **xem trước** [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, tiếng Anh. Homology bền vững trên một mẫu hữu hạn: hình của đám mây điểm thay đổi theo tỉ lệ.
- [Finite Topology [Shelley Kandola]](https://www.youtube.com/watch?v=zTiHx3z59N8) — Applied Algebraic Topology Network, tiếng Anh. Không gian tô-pô hữu hạn như mô hình tính toán của dữ liệu rời rạc trong bài.
- [Henry Adams: An Introduction to Applied Topology](https://www.youtube.com/watch?v=Xv4IoKVdGKA) — Kaleidoscope Circles, tiếng Anh. Bản đồ ứng dụng rộng hơn, để bốn mục của bài có chỗ đứng trong TDA.

## 🧩 Bài tập

1. Lấy $8$ điểm phân bố đều trên một vòng tròn. Mô tả bằng lời (không dùng máy tính) khi nào phức xây từ quan hệ "gần nhau" xuất hiện một chu trình $1$-chiều ($1$-cycle).
2. Vì sao một không gian Alexandroff hữu hạn xác định bởi một thứ tự bộ phận luôn thỏa mãn tiên đề $T_0$ nhưng hiếm khi Hausdorff (chỉ Hausdorff khi là không gian rời rạc)? Liên hệ Bài 00.00 với Chương 03.
3. Giải thích bằng lời: tính ổn định Gromov–Hausdorff nói lên điều gì khi ta *thêm một điểm nhiễu* vào đám mây điểm?
