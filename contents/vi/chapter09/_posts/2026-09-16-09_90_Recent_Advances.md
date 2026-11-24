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

**Bài đọc thêm (tùy chọn):** Các chủ đề nền tảng của Chương 09 — từ ly cà phê và bánh donut, bảy cầu Königsberg, dải Möbius, đặc trưng Euler, định lý bốn màu đến DNA, vật lý và giả thuyết Poincaré — vẫn giữ nguyên giá trị. Bài này chỉ điểm qua những nơi các ý tưởng đó đang được đưa vào nghiên cứu ứng dụng giai đoạn 2022–2026.

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu bạn từng tự hỏi *"Học đặc trưng Euler $$V - E + F$$, đồ thị Königsberg hay lỗ bánh donut thì dùng làm gì ngoài phòng thi?"*, thì giai đoạn 2022–2026 chính là câu trả lời sống động nhất! Từ việc dự đoán **độ cứng cơ học của vật liệu xốp** bằng đường cong đặc trưng Euler, phát hiện **vòng lặp tín hiệu trong mạng kết nối não bộ**, cho đến việc lập **bản đồ thể loại game Steam** bằng thuật toán Mapper — những ý tưởng trực quan nhất của Chương 09 nay đã trở thành công cụ phân tích dữ liệu chuẩn mực trong phòng thí nghiệm hiện đại!

Trong khi các bài trước của Chương 09 dùng hình ảnh trực quan (lỗ, nút, đồ thị, bề mặt) để giải thích tô-pô, nhiều nhóm nghiên cứu giai đoạn 2022–2026 đi theo chiều ngược lại: dùng chính những đặc trưng tô-pô đó để đo đạc và phân tích vật liệu xốp, mạng nơ-ron sinh học, đồ thị xã hội và dữ liệu ngôn ngữ. Bài viết này đóng vai trò bản đồ dẫn đọc các công trình tiêu biểu, không nhằm thay thế giáo trình vật lý hay sinh học chuyên sâu.

![Mạng não](https://upload.wikimedia.org/wikipedia/commons/0/0e/Brain_network.png)
*Một mạng não: cấu trúc đồ thị mà phân tích dữ liệu tô-pô (TDA) khai thác để đo lỗ và cấu trúc đa tỉ lệ. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Brain_network.png)*

![Đồ thị](https://upload.wikimedia.org/wikipedia/commons/3/3d/Undirected_graph.svg)
*Đồ thị vô hướng: mô hình kế thừa trực tiếp từ bài toán bảy cây cầu ở Königsberg. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Undirected_graph.svg)*

---

## 🎯 Trực giác kết nối

Công thức Euler $V-E+F$ giúp đo cấu trúc "lỗ" của một khối đa diện hay bề mặt cố định. **Đồng điều bền vững** (persistent homology) mở rộng ý tưởng đó sang dữ liệu thực: nó theo dõi các lỗ của một đồ thị hoặc đám mây nguyên tử *xuyên suốt nhiều thang tỉ lệ* thông qua một dãy lọc (filtration). Chính ở đây, trực giác của Chương 09 gặp công cụ đồng điều của Chương 07 trong thực tế phòng thí nghiệm.

---

## 🗺️ Bản đồ kiến thức nền: Tô-pô đại chúng bước vào Khoa học Dữ liệu (TDA) như thế nào?

### 1. Đường cong Đặc trưng Euler (ECC) & Vật liệu Xốp
- **Bản chất:** Với một ảnh chụp CT 3D của đá xốp, xương hoặc vật liệu tổng hợp, mỗi điểm ảnh (voxel) có một cường độ $$f(x)$$. Quét ngưỡng $$t$$ từ thấp lên cao và ghi lại $$\chi(\{x : f(x) \le t\})$$ tạo thành **Đường cong Đặc trưng Euler** — một chữ ký tô-pô cực nhanh giúp dự đoán độ bền cơ học và độ thấm chất lỏng!

### 2. Đồng điều bền vững trên Mạng Thần kinh & Ngôn ngữ (NLP)
- **Bản chất:** Biến mạng kết nối nơ-ron (connectome) hoặc đồ thị đồng xuất hiện từ ngữ thành phức đơn hình có trọng số (phức cờ — flag complex). Các lớp $$H_0$$ đo các cụm rời rạc, còn $$H_1$$ đo các **vòng phản hồi (feedback loops)** và cấu trúc ngữ nghĩa lặp — điều mà đếm bậc đỉnh kiểu Königsberg đơn thuần không thể thấy!

### 3. Thuật toán Mapper & Trực quan hóa Dữ liệu Cao chiều
- **Bản chất:** Thuật toán **Mapper** chiếu đám mây dữ liệu cao chiều qua một hàm lọc (lens), chia thành các dải chồng lấn, gom cụm từng dải rồi nối cạnh giữa các cụm giao nhau — biến hàng trăm chiều dữ liệu (bệnh án, hồ sơ gen, kho game Steam) thành một **đồ thị tô-pô trực quan** giữ nguyên nhánh và vòng lặp cốt lõi!

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc

### Ví dụ 1: Tính tay Đường cong Đặc trưng Euler (ECC) trên lưới vật liệu $$3\times 3$$
Xét một lát cắt ảnh vật liệu xốp $$3\times 3$$ ô vuông (pixel) có giá trị độ rỗng như sau (ô có giá trị $$\le t$$ được tô đen là vật chất):
- 8 ô viền xung quanh đều có giá trị $$1$$ (tạo thành một vòng khung vuông rỗng).
- Đúng 1 ô ở chính giữa có giá trị $$2$$ (lỗ rỗng trung tâm!).

Tính $$\chi(t) = V - E + F$$ (hoặc $$\beta_0 - \beta_1$$) theo từng ngưỡng $$t$$:
- **Khi $$t < 1$$:** Chưa có ô nào $$\implies \chi(t) = 0$$.
- **Khi $$1 \le t < 2$$:** Cả 8 ô viền xuất hiện tạo thành một vòng khung khép kín có đúng 1 lỗ ở giữa ($$\beta_0 = 1,\; \beta_1 = 1$$) $$\implies \chi(t) = 1 - 1 = 0$$!
- **Khi $$t \ge 2$$:** Ô trung tâm được lấp đầy thành hình vuông đặc $$3\times 3$$ ($$\beta_0 = 1,\; \beta_1 = 0$$) $$\implies \chi(t) = 1 - 0 = +1$$!

Đường cong bậc thang $$\chi(t): 0 \to 0 \to 1$$ ghi nhận ngay dấu vết của lỗ rỗng ở ngưỡng $$t \in [1, 2)$$ — nhanh hơn hàng chục lần so với chạy mô phỏng phần tử hữu hạn!

### Ví dụ 2: Đồ thị đồng xuất hiện câu 6 từ trong NLP
Lấy một câu 6 từ khác nhau đôi một $$w_1 - w_2 - w_3 - w_4 - w_5 - w_6$$ (nối mỗi từ với từ liền kề):
- Ta có $$V = 6$$ đỉnh và $$E = 5$$ cạnh (một đường thẳng cây) $$\implies \beta_0 = 1,\; \beta_1 = E - V + \beta_0 = 5 - 6 + 1 = 0$$ (không có vòng lặp ngữ nghĩa).
- Nếu từ cuối lặp lại chủ đề đầu (nối thêm cạnh $$w_6 - w_1$$), ta có $$E = 6 \implies \beta_1 = 6 - 6 + 1 = 1$$ — lập tức sinh ra một lớp $$H_1$$ phản ánh cấu trúc vòng hồi quy của đoạn văn!

### Khung giải thích: Quy trình 4 bước đưa Tô-pô vào phòng thí nghiệm hiện đại (nên đọc chậm)

#### Bước 1: Mã hóa dữ liệu thực thành không gian tô-pô có lọc
Ảnh CT vật liệu thành phức hình hộp (cubical complex); mạng não thành phức cờ có trọng số; văn bản NLP thành đám mây vectơ nhúng (embedding cloud).

#### Bước 2: Trích xuất chữ ký tô-pô đa tỉ lệ
Tính Đường cong Đặc trưng Euler (ECC), Barcode đồng điều bền vững ($$H_0, H_1, H_2$$), hoặc đồ thị Mapper — giữ lại những đặc trưng hình dáng bền vững trước nhiễu đo đạc.

#### Bước 3: Kiểm chứng ý nghĩa vật lý / sinh học / ngữ nghĩa
Liên kết từng thanh barcode dài với đối tượng thật: kích thước khe rỗng quyết định độ cứng vật liệu, vòng lặp $$H_1$$ tương ứng mạch phản hồi thần kinh, nhánh Mapper tương ứng phân nhóm bệnh nhân hoặc thể loại trò chơi.

#### Bước 4: Đưa thẳng vào kiến trúc Học sâu Tô-pô (TDL)
Thay vì chỉ trích xuất đặc trưng tĩnh ở bước tiền xử lý, thế hệ mô hình 2024–2026 (TDL) tích hợp trực tiếp cấu trúc đơn hình, phức tế bào và lớp tô-pô vào bên trong mạng nơ-ron học đầu-cuối!

$$
\text{Dữ liệu thực (Vật liệu / Não / NLP)}
\;\xrightarrow{\;\text{Phép lọc / Mapper}\;}\;
\text{ECC \& Barcode }(H_0, H_1, H_2)
\;\xrightarrow{\;\text{Học máy / TDL}\;}\;
\text{Dự đoán cơ học, sinh học \& ngữ nghĩa}.
$$

---

## 📐 Bốn hướng tiến bộ tiêu biểu

### 1. Khoa học vật liệu và phân tử: lỗ trở thành đặc trưng vật lý

Wee và Jiang (2025) tổng quan các ứng dụng của phân tích dữ liệu tô-pô (TDA) và học sâu tô-pô (TDL) trong khoa học phân tử — điểm giao giữa bài toán nút DNA (Bài 09.06) với hóa học tính toán. Topolnicki, Bogdan, Malinowski, Naskręcki và Harańczyk (2026) sử dụng các bộ mô tả tô-pô có hướng để dự đoán tensor độ cứng đàn hồi của vật liệu xốp: ở đây, khái niệm "lỗ" không còn là ví dụ minh họa trừu tượng mà trở thành đặc trưng đầu vào trực tiếp cho mô hình cơ học.

- JunJie Wee, Jian Jiang, *A review of topological data analysis and topological deep learning in molecular sciences*, arXiv:2509.16877 (2025).
- Rafał Topolnicki et al., *Direction-aware topological descriptors for elastic stiffness tensor prediction in porous materials*, arXiv:2604.08105 (2026).

### 2. Khoa học thần kinh: mạng lưới, tính bất biến tỉ lệ và tín hiệu

Gisolf, Santos và Wierstra (2023) áp dụng đồng điều bền vững để phân tách tín hiệu, nhiễu và tính bất biến tỉ lệ trong mạng thần kinh sinh học cũng như mạng tài chính — nơi đồ thị kết nối (connectome) là phiên bản quy mô lớn của bài toán đồ thị Königsberg. Ở hướng song song, Ballester, Casacuberta và Escalera (2023) khảo sát cách TDA phân tích *mạng nơ-ron nhân tạo*, tạo cầu nối so sánh giữa mạng sinh học và mô hình máy học.

- Roel Gisolf, Fernando A. N. Santos, Felix Wierstra, *Beyond Signal and Noise: Unraveling Scale Invariance in Neuroscience and Financial Networks with TDA*, arXiv:2311.17912 (2023).
- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *TDA for Neural Network Analysis*, arXiv:2312.05840 (2023).

### 3. TDA trên đồ thị và ngôn ngữ tự nhiên

Uchendu và Le (2024) khảo sát ứng dụng TDA trong xử lý ngôn ngữ tự nhiên (NLP): các câu văn và kho ngữ liệu được biểu diễn dưới dạng đồ thị hoặc đám mây điểm ngữ nghĩa, sau đó trích xuất các đặc trưng đồng điều $H_0,H_1$. Trong khi đó, Grelier, Kaufmann và Pfau (2026) giới thiệu *Games Mapper* — áp dụng thuật toán Mapper lên dữ liệu thể loại trò chơi trên Steam, mang lại một ví dụ ứng dụng gần gũi đúng tinh thần tô-pô đại chúng của Chương 09.

- Adaku Uchendu, Thai Le, *Topological Data Analysis Applications in Natural Language Processing: A Survey*, arXiv:2411.10298 (2024).
- Nicolas Grelier, Stéphane Kaufmann, Johannes Pfau, *Games Mapper: Topological Data Analysis of Steam Genres*, arXiv:2606.14376 (2026).

### 4. Học sâu tô-pô (TDL): từ trực giác đến kiến trúc mạng

Papamarkou và cộng sự (2024) cùng Su và cộng sự (2025) hệ thống hóa các hướng ứng dụng trên thành một chương trình nghiên cứu thống nhất: học biểu diễn trên các cấu trúc bậc cao (phức đơn hình, phức tế bào) thay vì chỉ dừng ở đồ thị cạnh đôi. Với người đọc Chương 09, thông điệp cốt lõi khá rõ ràng: cấu trúc tô-pô giờ đây đóng vai trò *thiên kiến quy nạp* (inductive bias) ngay bên trong các tầng tính toán của mô hình học máy.

- Theodore Papamarkou et al., *Position: Topological Deep Learning is the New Frontier for Relational Learning*, ICML 2024, arXiv:2402.08871.
- Zhe Su et al., *TDA and TDL Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

---

## 🧠 Tài liệu tham khảo

- Adams & Franzosa, *Introduction to Topology: Pure and Applied* (các chương ứng dụng).
- Poincaré, *Analysis Situs* (1895) — nguồn gốc lý thuyết của các bất biến về lỗ.
- Các bài báo arXiv liệt kê trong bốn mục trên.

## 🔗 Minh họa ứng dụng

Trong nghiên cứu vật liệu xốp, thay vì ước lượng độ cứng một cách định tính từ ảnh hiển vi điện tử quét (SEM), phòng thí nghiệm có thể trích xuất biểu đồ vạch (barcode) có hướng hoặc đặc trưng Euler theo từng hướng của hệ thống lỗ rỗng để dự đoán tensor đàn hồi — một ứng dụng trực tiếp của ý tưởng Bài 09.04 vào cơ học vật liệu.

## Video tham khảo

- **xem trước** [Henry Adams: An Introduction to Applied Topology](https://www.youtube.com/watch?v=Xv4IoKVdGKA) — Kaleidoscope Circles, tiếng Anh. Henry Adams dẫn vào tô-pô ứng dụng, khung chung cho vật liệu, tín hiệu và dữ liệu trong bài.
- [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, tiếng Anh. Homology bền vững: lỗ trở thành đặc trưng đo được, đúng ý mục vật liệu và tín hiệu.
- [Introduction to Topological Deep Learning](https://www.youtube.com/watch?v=N67GABKImZA) — Mathilde Papillon, tiếng Anh. Từ câu chuyện TDA tới một kiến trúc học được, đúng mục topological deep learning.

## 🧩 Bài tập

1. Giải thích ngắn gọn trong một câu vì sao phân tích mạng kết nối não (connectome) cần đến thông tin đồng điều $H_1$ (chu trình, vòng lặp) chứ không chỉ dừng ở số đỉnh và số cạnh như trong bài toán Königsberg.
2. Lấy một câu tiếng Việt gồm 6 từ, dựng đồ thị đồng xuất hiện đơn giản giữa các từ liền kề và dự đoán bậc của $H_0$ (số thành phần liên thông).
3. Chọn một ví dụ ứng dụng TDA trên cấu trúc protein trong tổng quan của Wee–Jiang (2025) và diễn giải lại ý tưởng chính bằng ngôn ngữ trực quan "lỗ và bề mặt" của Chương 09.
