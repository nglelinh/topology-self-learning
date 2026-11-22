---
layout: post
title: "Bài 09.02: Bảy Cây Cầu ở Königsberg - Bài Toán Mở Đầu của Topology"
lang: vi
lang-ref: lecture-09-02
chapter: 9
lecture: 2
categories: [chapter09]
tags: [graph-theory, euler-path, liên-thông, topology-cơ-bản]
description: "Khám phá bài toán cổ điển về bảy cây cầu ở Königsberg và cách nó mở đầu cho topology và graph theory hiện đại"
---

**Bài toán cổ điển mở đầu cho tô-pô và lý thuyết đồ thị**

---

## 📖 Tổng quan

Vào thế kỷ 18, tại thành phố Königsberg (nay là Kaliningrad, Nga), sông Pregel chia thành phố thành bốn vùng đất nối với nhau bằng bảy cây cầu. Người dân thành phố thường đặt ra một câu đố: **Có thể đi dạo qua tất cả bảy cây cầu, mỗi cây cầu đúng một lần, rồi quay về điểm xuất phát hay không?**

Nhiều người đã thử tìm lộ trình bằng cách mò mẫm nhưng đều thất bại. Năm 1736, nhà toán học **Leonhard Euler** (1707–1783) chứng minh rằng lộ trình như vậy **không tồn tại**. Quan trọng hơn, cách tiếp cận trừu tượng của Euler đã đặt nền móng cho **lý thuyết đồ thị** (graph theory) và được xem là một trong những khởi điểm sớm nhất của tô-pô hiện đại.

Trong bài học này, chúng ta sẽ phân tích bài toán bảy cây cầu ở Königsberg, tìm hiểu chứng minh của Euler, phân biệt **đường đi Euler** với **chu trình Euler**, và thấy cách bài toán này gắn với tính liên thông trong tô-pô.

![Seven Bridges of Königsberg](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/7_bridges.svg/500px-7_bridges.svg.png)  
*Bảy cây cầu ở Königsberg - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:7_bridges.svg)*

**Vì sao bài toán này quan trọng?** Nó minh họa sức mạnh của việc gạt bỏ các chi tiết hình học không cần thiết (độ dài cầu, diện tích bờ sông) để giữ lại duy nhất cấu trúc kết nối — tinh thần cốt lõi của lý thuyết đồ thị và tô-pô.

---

## 🗺️ Bài toán bảy cây cầu

### Bối cảnh lịch sử

Vào thế kỷ 18, Königsberg thuộc Đông Phổ (nay là Kaliningrad, Nga). Sông Pregel chia thành phố thành bốn vùng đất chính:

- **Vùng A:** Đảo Kneiphof ở giữa sông.
- **Vùng B:** Bờ bắc của sông.
- **Vùng C:** Bờ nam của sông.
- **Vùng D:** Vùng đất phía đông nằm giữa hai nhánh sông.

Bảy cây cầu kết nối bốn vùng đất này như sau:
- Cầu 1 và Cầu 2: Nối A với B (2 cây cầu).
- Cầu 3 và Cầu 4: Nối A với C (2 cây cầu).
- Cầu 5: Nối A với D (1 cây cầu).
- Cầu 6: Nối B với D (1 cây cầu).
- Cầu 7: Nối C với D (1 cây cầu).

### Câu hỏi đặt ra

**Liệu có tồn tại một lộ trình đi qua cả bảy cây cầu, mỗi cây cầu đúng một lần, rồi quay lại điểm xuất phát (hoặc thậm chí chỉ cần đi qua cả bảy cây cầu mà không cần quay lại điểm xuất phát) hay không?**

Dù thử xuất phát từ bất kỳ vùng đất nào, người đi bộ luôn gặp tình huống còn sót ít nhất một cây cầu hoặc buộc phải đi lặp lại một cây cầu đã qua.

---

## 🧮 Lời giải của Euler

### Cách tiếp cận của Euler

Thay vì liệt kê từng lộ trình cụ thể, Euler nhận ra ba điểm mấu chốt:

1. **Hình dạng và kích thước không quan trọng:** Chiều dài cây cầu hay diện tích từng vùng đất không ảnh hưởng đến đáp án; chỉ có quan hệ kết nối giữa các vùng đất mới quyết định.
2. **Điểm xuất phát của một chu trình khép kín không quan trọng:** Nếu tồn tại một vòng đi khép kín qua tất cả các cầu, ta có thể bắt đầu từ bất kỳ vùng nào trên vòng đó.
3. **Số cây cầu nối với mỗi vùng đất là yếu tố then chốt.**

### Phân tích theo số lần vào – ra

Giả sử có một lộ trình đi qua mọi cây cầu đúng một lần và quay trở lại điểm xuất phát:

- Mỗi khi đi vào một vùng đất qua một cây cầu, bạn phải rời khỏi vùng đó qua một cây cầu khác chưa từng đi qua.
- Ngay cả tại vùng xuất phát, lần rời đi đầu tiên cũng ghép cặp với lần quay trở về cuối cùng.
- Do đó, các cây cầu nối với mỗi vùng đất phải được ghép thành từng cặp (một cầu đi vào, một cầu đi ra), nghĩa là **số cây cầu nối với mỗi vùng đất phải là số chẵn**.

Nếu một vùng đất có số lẻ cây cầu nối tới, đến một lúc nào đó bạn sẽ đi vào vùng đó mà không còn cây cầu chưa đi nào để thoát ra.

**Kiểm tra trực tiếp trên bản đồ Königsberg:**

Đếm số cây cầu nối với từng vùng đất:
- **Vùng A:** 5 cây cầu (cầu 1, 2, 3, 4, 5) → **Số lẻ** ❌
- **Vùng B:** 3 cây cầu (cầu 1, 2, 6) → **Số lẻ** ❌
- **Vùng C:** 3 cây cầu (cầu 3, 4, 7) → **Số lẻ** ❌
- **Vùng D:** 3 cây cầu (cầu 5, 6, 7) → **Số lẻ** ❌

Cả bốn vùng đất đều có số lẻ cây cầu, nên **không tồn tại** chu trình khép kín đi qua mỗi cầu đúng một lần (và như ta sẽ thấy bên dưới, ngay cả đường đi không khép kín cũng không tồn tại).

### Định lý Euler về chu trình Euler

Euler đã khái quát hóa phân tích trên thành một điều kiện đầy đủ cho đồ thị:

<div class="textbook-theorem" markdown="1">
**Định lý:** Một đồ thị hữu hạn có **chu trình Euler** (đường đi khép kín qua tất cả các cạnh, mỗi cạnh đúng một lần) nếu và chỉ nếu:
1. Đồ thị là **liên thông** (bỏ qua các đỉnh cô lập, có thể đi từ mọi đỉnh đến mọi đỉnh khác).
2. Mọi đỉnh của đồ thị đều có **bậc chẵn** (số cạnh liên thuộc với mỗi đỉnh là số chẵn).
</div>

Ở Königsberg, điều kiện thứ hai bị vi phạm hoàn toàn vì cả bốn đỉnh đều có bậc lẻ.

---

## 🔗 Lý thuyết đồ thị và tô-pô

### Đồ thị là gì?

Từ bài toán này, khái niệm **đồ thị** (graph) ra đời để mô hình hóa các quan hệ kết nối. Một đồ thị gồm:
- **Đỉnh (vertices):** Các nút biểu diễn đối tượng.
- **Cạnh (edges):** Các đoạn nối biểu diễn liên kết giữa các đỉnh.

Với bài toán Königsberg:
- **Đỉnh:** Bốn vùng đất A, B, C, D.
- **Cạnh:** Bảy cây cầu nối giữa chúng.

![Graph representation of Königsberg bridges](https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Konigsberg_bridges.png/500px-Konigsberg_bridges.png)  
*Biểu diễn đồ thị của bài toán bảy cây cầu - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Konigsberg_bridges.png)*

### Mối liên hệ với tô-pô

Bài toán bảy cây cầu thường được coi là mốc mở đầu của tư duy tô-pô vì ba lý do:

1. **Bỏ qua hình học đo đạc:** Hình dáng bờ sông hay độ cong của cây cầu không làm thay đổi lời giải; chỉ cấu trúc liên kết mới có ý nghĩa.
2. **Tính liên thông:** Khả năng di chuyển từ vùng này sang vùng khác là biểu hiện trực tiếp của tính liên thông trong tô-pô.
3. **Bất biến cấu trúc:** Bậc của mỗi đỉnh không đổi khi ta kéo giãn hay bóp méo sơ đồ thành phố.

---

## 🎯 Đường đi Euler và chu trình Euler

### Đường đi Euler

Một **đường đi Euler** (Euler path) là đường đi qua tất cả các cạnh của đồ thị, mỗi cạnh đúng một lần, không bắt buộc phải quay lại điểm xuất phát.

<div class="textbook-theorem" markdown="1">
**Định lý:** Một đồ thị liên thông có đường đi Euler nếu và chỉ nếu số đỉnh có **bậc lẻ** bằng **0** hoặc **2**. (Cụ thể, để có đường đi Euler *không khép kín*, đồ thị phải có đúng **hai đỉnh bậc lẻ**, và đó chính là đỉnh đầu và đỉnh cuối của đường đi.)
</div>

**Giải thích điều kiện:**
- **Tính liên thông:** Nếu đồ thị bị tách thành các mảnh rời nhau đều có cạnh, không một đường đi duy nhất nào có thể đi qua tất cả các cạnh.
- **Số đỉnh bậc lẻ bằng 2 (trường hợp không khép kín):** Tại đỉnh xuất phát, số lần đi ra nhiều hơn số lần đi vào đúng 1 nên đỉnh đó có bậc lẻ; tại đỉnh kết thúc, số lần đi vào nhiều hơn số lần đi ra đúng 1 nên đỉnh đó cũng có bậc lẻ; mọi đỉnh trung gian đều có số lần vào bằng số lần ra nên có bậc chẵn.

Trong đồ thị Königsberg có tới 4 đỉnh bậc lẻ (A, B, C, D), vượt quá giới hạn 0 hoặc 2 đỉnh bậc lẻ, nên thành phố này **không có cả đường đi Euler lẫn chu trình Euler**.

### Chu trình Euler

Một **chu trình Euler** (Euler circuit) là đường đi Euler khép kín, quay về đúng đỉnh xuất phát.

<div class="textbook-theorem" markdown="1">
**Định lý:** Một đồ thị liên thông có chu trình Euler nếu và chỉ nếu mọi đỉnh đều có **bậc chẵn**.
</div>

Khi lộ trình khép kín, ngay cả đỉnh xuất phát cũng có số lần đi ra bằng số lần đi vào, nên không được phép còn đỉnh bậc lẻ nào.

Với bài toán Königsberg (gồm 4 đỉnh bậc lẻ là 5, 3, 3, 3):
- Nếu xây thêm **1 cây cầu** nối hai vùng đất bất kỳ, bậc của hai vùng đó chuyển từ lẻ sang chẵn, còn lại đúng 2 đỉnh bậc lẻ → thành phố sẽ có **đường đi Euler** (nhưng vẫn chưa có chu trình Euler).
- Để có **chu trình Euler** (cả 4 đỉnh đều bậc chẵn), cần xây thêm ít nhất **2 cây cầu** nối hai cặp vùng đất riêng biệt.

### Ví dụ: Phân tích một đồ thị đơn giản

Xét đồ thị bốn đỉnh dưới đây:

```
    A
   / \
  B---C
   \ /
    D
```

![Simple graph example](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/6n-graph.svg/300px-6n-graph.svg.png)  
*Ví dụ về một đồ thị đơn giản - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:6n-graph.svg)*

**Bậc của từng đỉnh:**
- **Đỉnh A:** Bậc 2 (chẵn) ✓ — nối với B và C.
- **Đỉnh B:** Bậc 3 (lẻ) ✗ — nối với A, C và D.
- **Đỉnh C:** Bậc 3 (lẻ) ✗ — nối với A, B và D.
- **Đỉnh D:** Bậc 2 (chẵn) ✓ — nối với B và C.

**Kết luận:** Đồ thị liên thông và có đúng **hai đỉnh bậc lẻ** (B và C), nên nó có **đường đi Euler** bắt đầu tại B và kết thúc tại C (ví dụ: `B → A → C → B → D → C`, đi qua đủ 5 cạnh mỗi cạnh một lần), nhưng **không có chu trình Euler** vì vẫn còn đỉnh bậc lẻ.

---

## 🔗 Ứng dụng và kết nối

### Trong đời sống và kỹ thuật
- **Giao thông và vận tải:** Lập kế hoạch tuyến đường tối ưu (như thu gom rác, tuần tra hoặc giao hàng) và thiết kế mạng lưới đô thị.
- **Mạch điện:** Phân tích sơ đồ kết nối và dòng điện trong mạch.
- **Mạng máy tính và internet:** Định tuyến dữ liệu, đánh giá độ tin cậy và tối ưu hóa hạ tầng mạng.

### Trong toán học và khoa học
- **Toán học:** Mở đường cho lý thuyết đồ thị, tô-pô và toán học tổ hợp.
- **Khoa học máy tính:** Nền tảng cho nhiều thuật toán tìm đường, cấu trúc dữ liệu đồ thị và mô hình học máy trên đồ thị.
- **Khoa học xã hội và sinh học:** Phân tích mạng xã hội, mạng lưới thương mại và các mạng tương tác sinh học.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Leonhard Euler** - *"Solutio problematis ad geometriam situs pertinentis"* (1736)  
   *Bài báo gốc của Euler về bài toán bảy cây cầu—khởi đầu của graph theory và topology*

2. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Nền tảng của topology hiện đại*

### Textbooks

- **James R. Munkres** - *Topology*, 2nd Ed., Ch. 1  
  *Tính liên thông trong topology*

- **Sidney A. Morris** - *Topology without Tears*, Ch. 3  
  *Giải thích trực quan về tính liên thông*

- **Reinhard Diestel** - *Graph Theory*, 4th Ed., Ch. 1  
  *Graph theory và đường đi Euler*

---

## Video tham khảo

- **xem trước** [The Seven Bridges of Königsberg - Numberphile](https://www.youtube.com/watch?v=W18FDEA1jRQ) — Numberphile, tiếng Anh. Bảy cây cầu Königsberg và cách Euler bỏ độ dài, chỉ giữ cách nối.
- [How the Königsberg bridge problem changed mathematics - Dan Van der Vieren](https://www.youtube.com/watch?v=nZwSo4vfw6c) — TED-Ed, tiếng Anh. Cùng bài toán, kể ngắn, nếu muốn nghe lại lịch sử trước phần đồ thị.
- [Euler Paths & the 7 Bridges of Konigsberg | Graph Theory](https://www.youtube.com/watch?v=dSK5jTEe-AM) — Dr. Trefor Bazett, tiếng Anh. Đường đi Euler và chu trình Euler, đúng tiêu chuẩn bậc chẵn mà bài chứng minh.

## 🧩 Bài tập và suy ngẫm

### Câu hỏi suy ngẫm

1. **Tự thiết kế bản đồ:** Vẽ một sơ đồ gồm các vùng đất và cây cầu rồi kiểm tra xem nó có đường đi Euler hoặc chu trình Euler hay không.
2. **Giải thích:** Vì sao ở Königsberg ngay cả một đường đi Euler không khép kín cũng không tồn tại?
3. **Liên hệ thực tế:** Nêu một tình huống trong đời sống có thể mô hình hóa bằng đồ thị và bài toán tìm đường đi qua mọi cạnh.
4. **Chỉnh sửa bài toán:** Nếu được phép phá bỏ hoặc xây thêm cây cầu ở Königsberg, cần ít nhất bao nhiêu cây cầu để xuất hiện (a) một đường đi Euler, và (b) một chu trình Euler?

### Thử nghiệm thực tế

1. **Vẽ lại đồ thị Königsberg:** Biểu diễn 4 vùng đất thành 4 đỉnh, 7 cây cầu thành 7 cạnh và tự kiểm tra bậc của từng đỉnh.
2. **Tìm đường đi một nét:** Thử vẽ các hình đơn giản (như hình phong bì thư) bằng một nét liền không nhấc bút và đối chiếu với tiêu chuẩn bậc đỉnh.
3. **Mô hình hóa khu phố:** Vẽ sơ đồ một vài tuyến đường gần nơi bạn sống và kiểm tra xem có thể đi qua mỗi đoạn đường đúng một lần hay không.

---

## 📚 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu:

- **Bài toán bảy cây cầu ở Königsberg:** Câu đố cổ điển dẫn tới lời giải tổng quát của Leonhard Euler năm 1736.
- **Tiêu chuẩn Euler:** Đồ thị liên thông có chu trình Euler khi và chỉ khi mọi đỉnh đều có bậc chẵn; có đường đi Euler khi và chỉ khi số đỉnh bậc lẻ là 0 hoặc 2.
- **Tư duy lý thuyết đồ thị và tô-pô:** Bỏ qua các thông số đo đạc hình học để tập trung vào tính liên thông và cấu trúc kết nối.
- **Ứng dụng:** Lập tuyến giao thông, phân tích mạch điện, mạng máy tính và mạng xã hội.
