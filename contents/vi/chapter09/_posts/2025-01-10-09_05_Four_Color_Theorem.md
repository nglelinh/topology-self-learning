---
layout: post
title: "Bài 09.05: Bốn Màu Đủ Để Tô Bản Đồ"
lang: vi
lang-ref: lecture-09-05
chapter: 9
lecture: 5
categories: [chapter09]
tags: [four-color-theorem, bản-đồ, topology, graph-theory]
description: "Khám phá định lý bốn màu - một trong những định lý nổi tiếng nhất trong toán học, và cách nó liên quan đến topology và graph theory"
---

**Định lý tô màu bản đồ và vai trò của đồ thị phẳng**

---

## 📖 Tổng quan

Khi tô màu một bản đồ hành chính, chỉ cần tối đa bốn màu là đủ để không có hai vùng nào có chung đường biên giới lại trùng màu nhau. Phát biểu nghe rất giản dị, nhưng đây lại là một trong những bài toán tồn tại lâu năm và khó chứng minh nhất trong lịch sử toán học.

**Định lý Bốn màu** (Four Color Theorem) khẳng định: *Mọi bản đồ trên mặt phẳng (hoặc trên mặt cầu) đều có thể được tô bằng tối đa bốn màu sao cho hai vùng có chung một đoạn biên giới luôn khác màu nhau.*

Bài toán được Francis Guthrie nêu ra năm 1852 nhưng phải đến năm 1976 — hơn 120 năm sau — mới được chứng minh hoàn chỉnh. Đáng chú ý, đây là định lý lớn đầu tiên có phần chứng minh phụ thuộc vào kiểm tra bằng máy tính trên hàng nghìn cấu hình, làm dấy lên cuộc thảo luận kéo dài về tiêu chuẩn của một chứng minh toán học.

Trong bài học này, chúng ta sẽ tìm hiểu phát biểu chính xác của định lý Bốn màu, lịch sử chứng minh, mối liên hệ với tô-pô đồ thị phẳng và các ứng dụng thực tế của bài toán tô màu đồ thị.

![Four color map](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4a/4-colour_problem.png/500px-4-colour_problem.png)  
*Bản đồ được tô bằng bốn màu - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:4-colour_problem.png)*

**Vì sao kiến thức này quan trọng?** Định lý Bốn màu gắn kết chặt chẽ tô-pô của mặt phẳng với lý thuyết đồ thị, đồng thời mở ra hướng ứng dụng rộng rãi của bài toán tô màu đồ thị trong lập lịch, phân bổ tài nguyên và thiết kế trình biên dịch.

---

## 🗺️ Bài toán tô màu bản đồ

### Câu hỏi khởi nguồn

Năm 1852, khi đang tô màu bản đồ các hạt của nước Anh, Francis Guthrie nhận thấy bốn màu là đủ để các hạt tiếp giáp nhau không bị trùng màu. Ông đặt câu hỏi liệu điều này có đúng với mọi bản đồ hay không và nhờ em trai hỏi giáo sư Augustus De Morgan. De Morgan gửi bài toán cho William Rowan Hamilton, và từ đó giả thuyết bốn màu lan rộng trong giới toán học.

### Phát biểu chính xác

**Định lý Bốn màu:** Mọi bản đồ vẽ trên mặt phẳng (với mỗi vùng là một miền liên thông) đều có thể được tô bằng không quá bốn màu sao cho không có hai vùng nào có chung một đoạn biên giới lại mang cùng một màu.

**Các điều kiện cần lưu ý:**

1. **Bản đồ trên mặt phẳng (hoặc mặt cầu):** Nhờ phép chiếu nổi, bản đồ trên mặt cầu tương đương tô-pô với bản đồ trên mặt phẳng nên định lý cũng đúng trên mặt cầu. Tuy nhiên, trên các bề mặt có lỗ như mặt xuyến (torus), bốn màu không đủ (cần tối đa 7 màu).
2. **Chung đoạn biên giới:** Hai vùng chỉ bị ràng buộc khác màu nếu chúng chia sẻ một đoạn biên giới có độ dài dương; nếu chỉ chạm nhau tại một điểm đơn lẻ (như bốn ô ở ngã tư bàn cờ), chúng được phép cùng màu.
3. **Tối đa bốn màu:** Có bản đồ chỉ cần hai hoặc ba màu, nhưng không bao giờ cần quá bốn màu.

### Vì sao ba màu là chưa đủ?

Có những bản đồ phẳng bắt buộc cần đúng bốn màu. Xét bản đồ gồm bốn vùng A, B, C, D sao cho mỗi vùng đều có chung đoạn biên giới với cả ba vùng còn lại (đồ thị đối ngẫu là đồ thị đầy đủ $K_4$):

```
    A
   /|\
  / | \
 B--+--C
  \ | /
   \|/
    D
```

Vì bốn vùng đôi một tiếp giáp nhau, bốn vùng này bắt buộc phải nhận bốn màu khác nhau. Do đó ba màu không đủ.

![Graph requiring four colors](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4a/4-colour_problem.png/500px-4-colour_problem.png)  
*Đồ thị đòi hỏi bốn màu - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:4-colour_problem.png)*

### Vì sao không cần đến năm màu?

Trong suốt nhiều thập kỷ, các nhà toán học chứng minh được rằng **năm màu luôn đủ** (Định lý Năm màu, 1890), nhưng việc hạ cận trên từ 5 xuống 4 lại khó khăn hơn nhiều và phải chờ đến năm 1976 mới hoàn tất.

---

## 🔍 Lịch sử và hành trình chứng minh

### Những nỗ lực ban đầu

- **1879 — Alfred Kempe:** Công bố một lời giải cho giả thuyết Bốn màu; chứng minh này được giới toán học công nhận suốt 11 năm.
- **1890 — Percy Heawood:** Phát hiện ra một lỗ hổng trong lập luận của Kempe, nhưng tận dụng chính kỹ thuật dây chuyền Kempe (Kempe chain) để chứng minh chặt chẽ **Định lý Năm màu**.
- **Nửa đầu thế kỷ 20:** Nhiều nhà toán học tiếp tục phát triển phương pháp rút gọn cấu hình nhưng chưa thể hoàn tất chứng minh cho 4 màu.

### Chứng minh bằng máy tính (1976)

Năm 1976, Kenneth Appel và Wolfgang Haken (Đại học Illinois) công bố chứng minh hoàn chỉnh đầu tiên cho Định lý Bốn màu dựa trên hai bước:

1. **Tập cấu hình không thể tránh khỏi (unavoidable set):** Chứng minh rằng mọi bản đồ phẳng tối tiểu đều phải chứa ít nhất một trong 1.936 cấu hình địa phương.
2. **Tính rút gọn (reducibility):** Chứng minh rằng nếu một bản đồ chứa bất kỳ cấu hình nào trong số này thì việc tô 4 màu cho nó có thể quy về tô 4 màu cho một bản đồ nhỏ hơn.

Vì số lượng cấu hình quá lớn để kiểm tra thủ công, Appel và Haken đã lập trình kiểm tra toàn bộ 1.936 cấu hình bằng máy tính, tiêu tốn hơn 1.200 giờ tính toán.

Chứng minh này tạo ra hai luồng quan điểm trong giới toán học: một phía cho rằng phép kiểm tra bằng máy tính hoàn toàn hợp lệ miễn thuật toán đúng; phía còn lại băn khoăn vì con người không thể tự tay kiểm tra từng bước để nắm bắt toàn bộ lý do trực giác đằng sau định lý.

### Các chứng minh cải tiến (1996–2005)

- **1996:** Neil Robertson, Daniel Sanders, Paul Seymour và Robin Thomas công bố một chứng minh gọn hơn, giảm số cấu hình cần kiểm tra từ 1.936 xuống còn 633.
- **2005:** Georges Gonthier sử dụng hệ thống hỗ trợ chứng minh hình thức (proof assistant) để kiểm chứng tự động toàn bộ định lý từ các tiên đề cơ bản, giúp củng cố độ tin cậy tuyệt đối của kết quả.

---

## 🧮 Liên hệ với tô-pô và lý thuyết đồ thị

### Chuyển bản đồ thành đồ thị

Ta có thể chuyển mọi bài toán tô màu bản đồ sang ngôn ngữ **lý thuyết đồ thị** (đồ thị đối ngẫu):
- Mỗi quốc gia (vùng) tương ứng với một **đỉnh** (vertex).
- Hai đỉnh được nối với nhau bằng một **cạnh** (edge) nếu hai vùng tương ứng có chung đoạn biên giới.

Khi đó, **Định lý Bốn màu** được phát biểu lại thành: *Mọi đồ thị phẳng đơn (simple planar graph) đều có thể tô đỉnh bằng không quá bốn màu sao cho hai đỉnh kề nhau luôn khác màu.*

### Vai trò của tô-pô mặt phẳng

Một đồ thị gọi là **đồ thị phẳng** (planar graph) nếu có thể vẽ nó trên mặt phẳng sao cho không có hai cạnh nào cắt nhau ngoài các đỉnh chung.

Với mọi đồ thị phẳng liên thông, công thức Euler $V - E + F = 2$ vẫn đúng. Từ công thức Euler, ta chứng minh được một tính chất cốt lõi: **mọi đồ thị phẳng đơn đều có ít nhất một đỉnh có bậc nhỏ hơn hoặc bằng 5**. Tính chất này là nền tảng cho phép chứng minh quy nạp của Định lý Năm màu (và là điểm xuất phát cho kỹ thuật xả/rút gọn trong Định lý Bốn màu).

### Định lý Năm màu

**Định lý Năm màu:** Mọi đồ thị phẳng đơn đều có thể tô đỉnh bằng tối đa năm màu.

<div class="textbook-proof" markdown="1">
**Chứng minh (phác thảo quy nạp theo số đỉnh):**

1. Từ công thức Euler, mọi đồ thị phẳng đơn đều tồn tại ít nhất một đỉnh $v$ có bậc $\le 5$.
2. Loại bỏ đỉnh $v$ cùng các cạnh kề nó; theo giả thiết quy nạp, đồ thị phẳng còn lại tô được bằng 5 màu.
3. Khôi phục đỉnh $v$:
   - Nếu các đỉnh kề của $v$ dùng tối đa 4 màu (luôn đúng khi $\deg(v) \le 4$), luôn còn ít nhất 1 màu trong 5 màu để tô cho $v$.
   - Nếu $\deg(v) = 5$ và cả 5 đỉnh kề $v_1, v_2, v_3, v_4, v_5$ (theo thứ tự quanh $v$) mang 5 màu khác nhau, ta dùng lập luận **dây chuyền Kempe**: xét đồ thị con sinh bởi hai màu của $v_1$ và $v_3$. Nếu $v_1$ và $v_3$ nằm ở hai thành phần liên thông khác nhau, đổi hai màu trong thành phần chứa $v_1$ để giải phóng một màu cho $v$. Nếu chúng nối nhau tạo thành một đường ngăn cách $v_2$ với $v_4$, thì $v_2$ và $v_4$ không thể nối với nhau bằng dây chuyền hai màu của chúng (do tính phẳng của đồ thị), nên ta đổi màu ở thành phần chứa $v_2$ để giải phóng một màu cho $v$.
</div>

**Vì sao lập luận đơn giản này không kéo xuống 4 màu được?** Khi chỉ có 4 màu, một đỉnh bậc 5 có thể tiếp giáp với cả 4 màu theo nhiều cấu hình phức tạp khiến việc hoán đổi một dây chuyền Kempe làm hỏng dây chuyền khác (chính là lỗ hổng trong chứng minh năm 1879 của Kempe).

---

## 🔗 Ứng dụng trong thực tế và khoa học máy tính

- **Xuất bản bản đồ:** Tô màu bản đồ địa lý và bản đồ hành chính rõ ràng, dễ phân biệt các khu vực giáp ranh.
- **Lập lịch thi và thời khóa biểu:** Biểu diễn mỗi môn học (hoặc sự kiện) là một đỉnh, nối cạnh giữa hai sự kiện không thể diễn ra cùng lúc (trùng phòng học hoặc trùng sinh viên); mỗi màu tương ứng với một khung giờ.
- **Phân bổ tần số:** Gán tần số phát sóng cho các trạm radio, truyền hình hoặc trạm di động sao cho hai trạm có vùng phủ giao nhau không dùng chung tần số gây nhiễu.
- **Phân bổ thanh ghi (Register allocation):** Trong thiết kế trình biên dịch (compiler), hai biến cùng tồn tại tại một thời điểm không thể dùng chung một thanh ghi CPU — bài toán này được mô hình hóa trực tiếp thành tô màu đồ thị.
- **Lý thuyết độ phức tạp:** Với đồ thị tổng quát, bài toán quyết định xem đồ thị có tô được bằng $k$ màu hay không (với $k \ge 3$) là bài toán NP-đầy đủ (NP-complete).

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Francis Guthrie** - *Letter to De Morgan* (1852)  
   *Câu hỏi ban đầu về tô màu bản đồ*

2. **Alfred Kempe** - *"On the Geographical Problem of the Four Colours"* (1879)  
   *Chứng minh sai nhưng có các kỹ thuật quan trọng*

3. **Percy Heawood** - *"Map-Colour Theorem"* (1890)  
   *Chứng minh định lý Năm Màu và phát hiện lỗi trong chứng minh của Kempe*

4. **Kenneth Appel & Wolfgang Haken** - *"Every Planar Map is Four Colorable"* (1976)  
   *Chứng minh đầu tiên của định lý Bốn Màu bằng máy tính*

5. **Neil Robertson, Daniel Sanders, Paul Seymour, Robin Thomas** - *"The Four-Colour Theorem"* (1996)  
   *Chứng minh cải tiến với ít cấu hình hơn*

### Textbooks

- **Reinhard Diestel** - *Graph Theory*, 4th Ed., Ch. 5  
  *Graph coloring và định lý Bốn Màu*

- **Robin Wilson** - *"Four Colors Suffice"* (2002)  
  *Lịch sử và chứng minh của định lý Bốn Màu*

---

## Video tham khảo

- **xem trước** [The Four Color Map Theorem - Numberphile](https://www.youtube.com/watch?v=NgbK43jB4rQ) — Numberphile, tiếng Anh. Định lý bốn màu từ bản đồ tới đồ thị phẳng, đúng lối bài đang đi.
- [The 4 Colour Theorem Explained](https://www.youtube.com/watch?v=siFuRrhb-cU) — The Science Biome, tiếng Anh. Một lần kể lại ngắn, nếu muốn nghe phát biểu trước chi tiết lịch sử.

## 🧩 Bài tập và suy ngẫm

### Câu hỏi suy ngẫm

1. **Thực hành vẽ bản đồ:** Vẽ một bản đồ đơn giản gồm 6–8 vùng và thử tô nó bằng tối đa bốn màu.
2. **Phân biệt số màu:** Vì sao có những bản đồ chỉ cần hai hoặc ba màu, trong khi một số bản đồ bắt buộc phải dùng bốn màu?
3. **So sánh hai định lý:** Giải thích sự khác biệt về độ khó chứng minh giữa Định lý Năm màu và Định lý Bốn màu.
4. **Liên hệ thực tế:** Chọn một bài toán lập lịch quen thuộc và mô tả cách chuyển nó thành bài toán tô màu đồ thị.
5. **Thử thách:** Thiết kế một bản đồ phẳng ít vùng nhất có thể sao cho không thể tô bằng ba màu.

### Thử nghiệm thực tế

1. In một bản đồ hành chính (như bản đồ các tỉnh hoặc các nước châu Âu) và tự tô màu bằng bốn màu.
2. Chuyển một bản đồ đơn giản sang đồ thị đối ngẫu của nó rồi tô màu các đỉnh.
3. Mô hình hóa lịch thi của 5–6 môn học có sinh viên trùng nhau thành đồ thị xung đột và tìm số ca thi tối thiểu.

---

## 📚 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu:

- **Định lý Bốn màu:** Mọi bản đồ phẳng (hay đồ thị phẳng đơn) đều tô được bằng tối đa bốn màu.
- **Lịch sử chứng minh:** Xuất phát từ câu hỏi năm 1852 của Guthrie, hoàn tất năm 1976 bởi Appel và Haken với sự hỗ trợ của máy tính, sau đó được rút gọn năm 1996 và kiểm chứng hình thức năm 2005.
- **Liên hệ tô-pô và đồ thị:** Bản đồ phẳng chuyển về đồ thị phẳng; công thức Euler bảo đảm tồn tại đỉnh bậc $\le 5$.
- **Ứng dụng:** Tô màu bản đồ, lập lịch, phân bổ tần số và phân bổ thanh ghi trong trình biên dịch.
