---
layout: post
title: "Bài 09.06: Topology của DNA - Xoắn và Nút"
lang: vi
lang-ref: lecture-09-06
chapter: 9
lecture: 6
categories: [chapter09]
tags: [knot-theory, DNA, sinh-học, topology-ứng-dụng]
description: "Khám phá cách các nhà khoa học sử dụng topology và knot theory để nghiên cứu cấu trúc của DNA và các phân tử sinh học"
---

**Lý thuyết nút và ứng dụng trong sinh học phân tử**

---

## 📖 Tổng quan

DNA — phân tử mang thông tin di truyền của sinh vật — không chỉ tồn tại dưới dạng chuỗi xoắn kép thẳng đơn giản. Trong tế bào, sợi DNA rất dài và thường khép vòng hoặc bị cố định từng đoạn, nên nó có thể bị siêu xoắn, lồng vòng và tạo thành các nút thắt phức tạp. Để phân tích những cấu trúc này, các nhà sinh học phân tử sử dụng **lý thuyết nút** (knot theory) — một nhánh của tô-pô.

Lý thuyết nút nghiên cứu các đường cong khép kín nhúng trong không gian ba chiều. Trong bài học này, chúng ta sẽ tìm hiểu cấu trúc xoắn kép và siêu xoắn của DNA, cách DNA tạo nút thắt, cơ chế tháo gỡ nút của enzyme topoisomerase, công thức số liên kết ($Lk = Tw + Wr$) và ứng dụng trong y học cũng như công nghệ sinh học.

![DNA double helix](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4c/DNA_Structure%2BKey%2BLabelled.pn_NoBB.png/500px-DNA_Structure%2BKey%2BLabelled.pn_NoBB.png)  
*Cấu trúc xoắn kép của DNA - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:DNA_Structure%2BKey%2BLabelled.pn_NoBB.png)*

**Vì sao kiến thức này quan trọng?** Việc kiểm soát trạng thái xoắn và nút thắt của DNA là điều kiện sống còn cho quá trình sao chép và phiên mã. Hiểu rõ tô-pô của DNA giúp phát triển nhiều nhóm thuốc điều trị ung thư, giải thích một số rối loạn di truyền và thúc đẩy các kỹ thuật công nghệ sinh học mới.

---

## 🧬 Cấu trúc cơ bản của DNA

### Cấu trúc xoắn kép (Double Helix)

Cấu trúc xoắn kép của DNA do James Watson và Francis Crick đề xuất năm 1953 có các đặc điểm chính:
- **Hai mạch đơn:** Gồm hai chuỗi polynucleotide xoắn quanh một trục chung.
- **Xoắn phải (right-handed):** Dạng phổ biến trong tự nhiên (B-DNA) xoắn theo chiều phải.
- **Bước xoắn:** Mỗi vòng xoắn gồm khoảng 10–11 cặp base.
- **Khoảng cách giữa các cặp base:** Khoảng 0,34 nanomet.

Cấu trúc này giúp phân tử DNA bền vững về mặt hóa học, thuận lợi cho cơ chế tự sao chép bán bảo toàn và có thể đóng gói gọn gàng trong nhân tế bào.

### Siêu xoắn (Supercoiling)

Khi một phân tử DNA xoắn kép khép vòng (hoặc bị cố định hai đầu) tiếp tục bị xoắn quanh trục của chính nó, nó tạo thành cấu trúc **siêu xoắn** (supercoil) — tương tự hiện tượng sợi dây điện thoại xoắn chồng lên nhau thành nhiều vòng cuộn.

![DNA supercoiling](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/DNA_supercoiling.svg/500px-DNA_supercoiling.svg.png)  
*Supercoiling của DNA - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:DNA_supercoiling.svg)*

**Hai dạng siêu xoắn:**
1. **Siêu xoắn dương (positive supercoiling):** Xoắn tăng cường cùng chiều với xoắn kép tự nhiên, làm mạch DNA căng hơn và khó tách hai mạch đơn.
2. **Siêu xoắn âm (negative supercoiling):** Xoắn ngược chiều với xoắn kép tự nhiên (phổ biến trong tế bào), giúp hai mạch đơn dễ tách nhau ra hơn khi sao chép và phiên mã.

Trạng thái siêu xoắn ảnh hưởng trực tiếp đến tốc độ sao chép, phiên mã và mức độ đóng gói DNA trong nhân tế bào. Với một vòng DNA khép kín, trạng thái tô-pô tổng thể của nó không thể thay đổi nếu không cắt mạch.

---

## 🔗 Lý thuyết nút và DNA

### Nút trong toán học

Trong tô-pô, một **nút** (knot) là một đường cong khép kín đơn nhúng trong không gian ba chiều. Hai nút được coi là tương đương nếu có thể biến dạng liên tục nút này thành nút kia trong không gian mà không cắt hay cho dây tự xuyên qua chính nó.

**Một vài nút cơ bản:**
- **Nút tầm thường / nút không (unknot):** Đường cong khép kín có thể biến dạng liên tục thành một vòng tròn phẳng đơn giản không tự cắt.
- **Nút ba lá (trefoil knot):** Nút không tầm thường đơn giản nhất, có số giao điểm tối thiểu bằng 3.
- **Nút số tám (figure-eight knot):** Nút có số giao điểm tối thiểu bằng 4.

![Mathematical knots](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Knot_table.svg/500px-Knot_table.svg.png)  
*Các loại nút toán học cơ bản - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Knot_table.svg)*

### Sự hình thành nút thắt trên DNA

Trong các quá trình như sao chép, tái tổ hợp di truyền hoặc đóng gói chặt trong nhiễm sắc thể, sợi DNA có thể tự thắt nút hoặc lồng vòng vào nhau. Nếu không được xử lý, các nút thắt này sẽ cản trở bộ máy sao chép và phiên mã, thậm chí làm đứt gãy mạch và gây đột biến.

### Enzyme Topoisomerase

Tế bào giải quyết vấn đề nút thắt và siêu xoắn nhờ nhóm enzyme **topoisomerase**:

1. **Cắt mạch:** Enzyme cắt tạm thời một mạch đơn hoặc cả hai mạch của DNA.
2. **Thay đổi cấu trúc tô-pô:** Cho phép mạch DNA xoay giảm ứng suất xoắn hoặc cho một đoạn xoắn kép khác đi xuyên qua khe cắt để tháo nút.
3. **Nối lại:** Hàn kín lại mạch DNA mà không làm thay đổi trình tự cặp base.

![Topoisomerase mechanism](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8a/Topoisomerase_I_mechanism.svg/500px-Topoisomerase_I_mechanism.svg.png)  
*Cơ chế hoạt động của Topoisomerase - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Topoisomerase_I_mechanism.svg)*

**Hai nhóm chính:**
- **Topoisomerase loại I:** Cắt một mạch đơn của DNA để giải tỏa ứng suất siêu xoắn rồi nối lại.
- **Topoisomerase loại II:** Cắt đồng thời cả hai mạch của một đoạn DNA, cho một đoạn xoắn kép khác đi qua để tháo nút hoặc tách hai vòng DNA lồng nhau, sau đó nối kín lại.

Về bản chất, topoisomerase thực hiện các phép biến đổi tô-pô trên phân tử DNA mà vẫn bảo toàn nguyên vẹn thông tin di truyền.

---

## 🧮 Các đại lượng tô-pô của DNA

### Số liên kết (Linking Number)

Đối với một phân tử DNA xoắn kép khép vòng, **số liên kết** (linking number, ký hiệu $Lk$) là một số nguyên đo số lần một mạch đơn quấn quanh mạch đơn kia. Đại lượng này liên hệ với hình học không gian của phân tử qua định lý White–Fuller:

$$
Lk = Tw + Wr
$$

trong đó:
- **$Lk$ (Linking number):** Số liên kết — là một **bất biến tô-pô**, không đổi khi DNA bị uốn cong hay kéo giãn mà không bị cắt mạch.
- **$Tw$ (Twist):** Số vòng xoắn cục bộ của hai mạch quanh trục xoắn kép.
- **$Wr$ (Writhe):** Độ quấn (siêu xoắn) của bản thân trục xoắn kép trong không gian ba chiều.

Vì $Lk$ không đổi khi không có enzyme cắt mạch, mọi thay đổi của $Tw$ (chẳng hạn khi tách cục bộ hai mạch DNA) đều kéo theo sự thay đổi bù trừ tương ứng ở $Wr$. Muốn thay đổi $Lk$, tế bào bắt buộc phải nhờ đến enzyme topoisomerase.

### Một số bất biến tô-pô khác

- **Loại nút (knot type):** Phân loại vòng DNA theo dạng nút (unknot, trefoil, figure-eight, ...).
- **Sự lồng vòng (catenation):** Mô tả trạng thái hai hay nhiều vòng DNA móc nối vào nhau như các mắt xích (thường xuất hiện ngay sau khi DNA vòng hoàn tất sao chép).
- **Mật độ siêu xoắn (supercoiling density):** Đo mức độ chênh lệch của số liên kết so với trạng thái thư giãn trên một đơn vị chiều dài DNA.

---

## 🔬 Ứng dụng trong y học và công nghệ sinh học

### Thuốc điều trị ung thư

Nhiều thuốc hóa trị hoạt động theo cơ chế **ức chế topoisomerase** (topoisomerase inhibitors): chúng khóa chặt phức hợp enzyme–DNA ở giai đoạn cắt mạch hoặc ngăn enzyme tháo nút và giảm siêu xoắn. Khi tế bào ung thư phân chia nhanh không thể hoàn tất quá trình sao chép DNA, các đứt gãy tích tụ khiến tế bào chết theo chương trình.

**Hai ví dụ tiêu biểu:**
- **Camptothecin** (và các dẫn xuất): ức chế topoisomerase I.
- **Etoposide:** ức chế topoisomerase II.

### Nghiên cứu bệnh lý và đột biến

Các đột biến ở gen mã hóa topoisomerase hoặc sai lỗi trong cơ chế giải tỏa nút thắt có thể gây mất ổn định bộ gen, đứt gãy nhiễm sắc thể và liên quan đến nhiều rối loạn di truyền.

### Công nghệ nano và tính toán DNA

- **DNA origami:** Khai thác khả năng bắt cặp bổ sung và thiết kế tô-pô mạch để gấp DNA thành các cấu trúc nano hai chiều và ba chiều có hình dạng xác định.
- **Tính toán DNA (DNA computing):** Dùng phản ứng sinh hóa và cấu trúc mạch DNA để mã hóa và giải một số bài toán tổ hợp.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **James Watson & Francis Crick** - *"Molecular Structure of Nucleic Acids"* (1953)  
   *Phát hiện cấu trúc xoắn kép của DNA*

2. **James White** - *"Self-Linking and the Gauss Integral in Higher Dimensions"* (1969)  
   *Linking number và topology của DNA*

3. **Nicholas Cozzarelli** - *"DNA Topology and Its Biological Effects"* (1980)  
   *Topology của DNA và các ứng dụng sinh học*

### Textbooks

- **Dale Rolfsen** - *Knots and Links* (1976)  
  *Knot theory cơ bản*

- **Colin Adams** - *The Knot Book* (1994)  
  *Giới thiệu về knot theory*

- **Nicholas Cozzarelli & James Wang** - *DNA Topology and Its Biological Effects* (2006)  
  *Topology của DNA và ứng dụng*

---

## Video tham khảo

- **xem trước** [What are...knots and DNA?](https://www.youtube.com/watch?v=WFBWtpXTE5Q) — VisualMath, tiếng Anh. Nút thắt gặp DNA, đúng cầu nối của bài.
- [DNA Topology || Linking number || Twist || Writhe](https://www.youtube.com/watch?v=DxREU4puGyc) — Rethink Biology, tiếng Anh. Linking number, twist và writhe, ba số mà bài dùng để nói topo của DNA.

## 🧩 Bài tập và suy ngẫm

### Câu hỏi suy ngẫm

1. **Phân biệt nút:** Với một sợi dây được nối kín hai đầu, làm thế nào phân biệt một nút không (unknot) với một nút ba lá (trefoil)?
2. **Quan hệ $Lk = Tw + Wr$:** Nếu một phân tử DNA khép vòng không bị cắt mạch và số vòng xoắn $Tw$ giảm đi 2 vòng, đại lượng $Wr$ sẽ thay đổi như thế nào?
3. **So sánh enzyme:** Phân biệt vai trò và cơ chế cắt mạch của topoisomerase loại I và loại II.
4. **Liên hệ y học:** Giải thích vì sao thuốc ức chế topoisomerase lại có tác động mạnh lên các tế bào ung thư đang phân chia nhanh.

### Thử nghiệm thực tế

1. Dùng một sợi dây mềm, tạo thử nút ba lá và nút số tám rồi nối tạm hai đầu lại; kiểm tra xem có thể kéo giãn chúng thành vòng tròn phẳng mà không tháo mối nối hay không.
2. Cầm hai sợi dây xoắn chặt vào nhau giống dây thừng rồi đưa hai đầu lại gần nhau để quan sát trực tiếp hiện tượng siêu xoắn (writhe).

---

## 📚 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu:

- **Cấu trúc tô-pô của DNA:** Xoắn kép, siêu xoắn dương và siêu xoắn âm.
- **Lý thuyết nút và topoisomerase:** Cách DNA hình thành nút thắt/lồng vòng và cách enzyme topoisomerase loại I, II cắt – tháo – nối mạch.
- **Bất biến số liên kết:** Hệ thức $Lk = Tw + Wr$ liên kết bất biến tô-pô $Lk$ với hình học xoắn $Tw$ và siêu xoắn $Wr$.
- **Ứng dụng:** Thuốc ức chế topoisomerase trong điều trị ung thư, nghiên cứu cơ chế ổn định bộ gen và công nghệ DNA origami.
