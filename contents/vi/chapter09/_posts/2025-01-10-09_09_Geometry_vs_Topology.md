---
layout: post
title: "Bài 09.09: Hình học và tô-pô"
lang: vi
lang-ref: lecture-09-09
chapter: 9
lecture: 9
order: 9
categories: [chapter09]
tags: [geometry, topology, so-sánh, khái-niệm-cơ-bản]
description: "Hình học đo độ dài và góc; tô-pô giữ những gì còn sau kéo–uốn. Không nhầm mặt đóng với có biên; vuông đặc ≠ đường tròn."
---

> **Câu chuyện mở đầu:** Cầm bản đồ tuyến tàu điện ngầm London (Tube Map) trên tay: các ga nằm thẳng tắp trên những đường ngang, dọc, chéo $$45^\circ$$ cách đều nhau — **sai hoàn toàn về khoảng cách và góc địa lý thực tế**, nhưng lại là tấm bản đồ hữu ích nhất thế giới cho hành khách! Bản đồ địa lý là **Hình học** (đo từng mét đường, từng góc cua); bản đồ tàu điện ngầm là **Tô-pô** (chỉ giữ lại thứ tự kết nối và trạm giao nhau). Hiểu rành mạch ranh giới giữa hai lăng kính này giúp bạn chọn đúng công cụ cho mọi bài toán toán học!

**Hình học** đo các đại lượng như độ dài, góc, diện tích và độ cong. **Tô-pô** nghiên cứu những tính chất vẫn được bảo toàn khi ta kéo giãn, nén hay uốn cong liên tục mà không cắt rời hay dán dính. Chẳng hạn, một chiếc ly có quai và một mặt xuyến (torus) khác nhau về mặt hình học nhưng lại đồng phôi về mặt tô-pô (xem [Bài 09.01]({{ site.baseurl }}/contents/vi/chapter09/09_01_Coffee_Donut/) và định nghĩa đồng phôi tại [Bài 01.03]({{ site.baseurl }}/contents/vi/chapter01/01_03_Continuous_Functions_Homeomorphisms/)).

![Ly biến thành torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)

*Ly có quai biến dạng liên tục thành mặt xuyến (torus). Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif).*

## 🗺️ Bản đồ kiến thức nền: Hình học và Tô-pô khác nhau ở đâu — và gặp nhau ở đâu?

### 1. Hai nhóm biến đổi đối xứng (Chương trình Erlangen của Felix Klein)
- **Hình học Euclid / Riemann:** Nghiên cứu các tính chất bất biến dưới **phép đẳng cự** (bảo toàn khoảng cách $$d(f(p), f(q)) = d(p, q)$$): độ dài, góc, diện tích, thể tích, đường trắc địa và độ cong $$K$$.
- **Tô-pô học:** Nghiên cứu các tính chất bất biến dưới **phép đồng phôi** (song ánh liên tục hai chiều): tính liên thông, tính compact, số chiều, sự tồn tại của biên, tính định hướng, đặc trưng Euler $$\chi$$ và nhóm cơ bản $$\pi_1$$.

### 2. Thứ bậc các mức độ tương đương (từ chặt đến lỏng)
$$
\text{Đẳng cự (Hình học)}
\;\Longrightarrow\;
\text{Vi phôi (Tô-pô vi phân)}
\;\Longrightarrow\;
\text{Đồng phôi (Tô-pô)}
\;\Longrightarrow\;
\text{Tương đương đồng luân (Tô-pô đại số)}.
$$
Chiều ngược lại nói chung **sai**!

### 3. Nơi Hình học và Tô-pô bắt tay nhau
- **Định lý Gauss–Bonnet:** Tích phân độ cong hình học $$\iint K\,dA$$ lại bằng đúng bất biến tô-pô $$2\pi\chi(M)$$!
- **Dòng Ricci (Perelman):** Dùng độ cong hình học để chứng minh phân loại tô-pô của đa tạp 3 chiều!

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc: Hai mặt cầu bán kính $$R_1 = 1$$ và $$R_2 = 3$$

Xét mặt cầu đơn vị $$S^2(1)$$ và mặt cầu bán kính $$3$$ là $$S^2(3)$$, nối với nhau bằng ánh xạ phóng đại $$f(x, y, z) = (3x, 3y, 3z)$$:

1. **Dưới lăng kính Hình học — KHÁC NHAU hoàn toàn:**
   - Khoảng cách giữa hai điểm nhân lên **3 lần**: $$d(f(p), f(q)) = 3\,d(p, q)$$.
   - Diện tích mặt cầu nhân lên **9 lần**: $$A_1 = 4\pi(1)^2 = 4\pi$$ vs. $$A_2 = 4\pi(3)^2 = 36\pi$$.
   - Độ cong Gauss giảm đi **9 lần**: $$K_1 = \frac{1}{1^2} = 1$$ vs. $$K_2 = \frac{1}{3^2} = \frac{1}{9}$$.
   $$\implies$$ **Không đẳng cự!**

2. **Dưới lăng kính Tô-pô — GIỐNG HỆT NHAU:**
   - $$f$$ là song ánh liên tục và $$f^{-1}(u, v, w) = \left(\tfrac{u}{3}, \tfrac{v}{3}, \tfrac{w}{3}\right)$$ cũng liên tục $$\implies S^2(1) \cong S^2(3)$$ (**đồng phôi**!).
   - Đặc trưng Euler đều bằng $$\chi = 2$$, nhóm cơ bản đều bằng $$\pi_1 = 0$$.
   - **Kiểm tra cầu nối Gauss–Bonnet:**
     $$
     \iint_{S^2(1)} K_1\,dA = 1 \cdot 4\pi = 4\pi,
     \qquad
     \iint_{S^2(3)} K_2\,dA = \frac{1}{9} \cdot 36\pi = 4\pi!
     $$
     Diện tích tăng 9 lần còn độ cong giảm 9 lần — chúng triệt tiêu nhau hoàn hảo để bảo toàn bất biến tô-pô $$2\pi\chi = 4\pi$$!

### Khung giải thích: 4 câu hỏi nhanh giúp phân biệt Hình học vs. Tô-pô (nên đọc chậm)

#### Bước 1: Hỏi "Có cần thước đo khoảng cách hay thước đo góc không?"
Nếu câu trả lời là CÓ (bán kính, diện tích, góc vuông, độ cong cục bộ, đường ngắn nhất) $$\to$$ đó là **Hình học**. Nếu KHÔNG $$\to$$ đó là **Tô-pô**.

#### Bước 2: Kiểm tra các "bẫy" thuật ngữ kinh điển
Phân biệt rạch ròi **mặt đóng** (compact + không biên, như $$S^2$$) với **tập đóng có biên** (như đĩa $$D^2$$); phân biệt **đường tròn $$S^1$$** (1 chiều) với **hình vuông đặc** (2 chiều, đồng phôi với $$D^2$$ chứ không phải $$S^1$$!).

#### Bước 3: Phân biệt Đồng phôi với Tương đương đồng luân
Hình trụ $$S^1 \times [0,1]$$ và đường tròn $$S^1$$ **không đồng phôi** (khác số chiều: 2D vs. 1D), nhưng **tương đương đồng luân** vì ta có thể co rút bề rộng hình trụ về đúng đường tròn giữa $$S^1$$!

#### Bước 4: Phối hợp cả hai lăng kính trong nghiên cứu hiện đại
Các bài toán lớn nhất (Gauss–Bonnet, Atiyah–Singer, Perelman, TDA) đều mạnh nhất khi ta đặt một cấu trúc hình học lên không gian tô-pô, dùng giải tích/độ cong để tính toán, rồi rút ra những bất biến tô-pô bất diệt!

---

## Cùng một vật thể, hai góc nhìn khác nhau

![Hình vuông](https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Square.svg/500px-Square.svg.png)

*Hình vuông: độ dài cạnh, góc vuông và diện tích là các thuộc tính hình học. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Square.svg).*

![Hình cầu](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Sphere_wireframe_10deg_6r.svg/500px-Sphere_wireframe_10deg_6r.svg.png)

*Hình cầu: bán kính và thể tích là các thuộc tính hình học. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Sphere_wireframe_10deg_6r.svg).*

Hai hình vuông đặc có cạnh 5 cm và 10 cm **khác nhau** về hình học (khác chu vi và diện tích), nhưng **đồng phôi** về tô-pô vì cả hai đều có cùng kiểu đĩa đóng hai chiều. Tương tự, hai mặt cầu có bán kính khác nhau khác nhau về hình học nhưng đồng phôi về tô-pô.

![Hình lập phương](https://upload.wikimedia.org/wikipedia/commons/thumb/0/02/Cube.svg/500px-Cube.svg.png)

*Bề mặt hình lập phương: các góc cạnh và chiều dài cạnh thuộc về hình học, còn tính đồng phôi với mặt cầu thuộc về tô-pô. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cube.svg).*

## Những cặp đối tượng dễ nhầm lẫn

| Cặp đối tượng | Khác biệt hình học | Quan hệ tô-pô |
|---|---|---|
| Hình vuông **đặc** và đĩa đóng | Khác về góc nhọn và độ dài cạnh | **Đồng phôi:** cả hai đều là 2-đĩa đóng |
| Đường tròn $$S^1$$ và đĩa đóng | Đường cong khép kín vs. miền phẳng | **Không** đồng phôi: đường tròn không có biên, đĩa đóng có biên |
| Mặt cầu $$S^2$$ và khối cầu đặc $$B^3$$ | Phần vỏ rỗng vs. khối đặc | **Không** đồng phôi: khác số chiều (2 chiều và 3 chiều) |
| Mặt cầu và mặt xuyến (torus) | Cả hai đều là mặt cong trơn | **Không** đồng phôi: khác số lỗ ($$g=0$$ và $$g=1$$) |

**Lưu ý thuật ngữ:** Trong tô-pô đa tạp, **mặt đóng** (closed surface) nghĩa là bề mặt compact **và không có biên**. Đĩa đóng là tập compact nhưng **có biên** (đường tròn bao quanh nó), nên đĩa đóng không phải là mặt đóng. Khi xét tính đồng phôi, cần phân biệt rõ *đường tròn* (1 chiều, không biên) với *đĩa đóng* (2 chiều, có biên).

## Khi nào dùng hình học, khi nào dùng tô-pô?

- Khi cần tính diện tích, góc, độ cong hay đường ngắn nhất: dùng **hình học** (hoặc hình học Riemann).
- Khi cần xét số lỗ, sự tồn tại của biên hay khả năng biến dạng liên tục từ không gian này sang không gian khác: dùng **tô-pô**.
- Hai không gian đồng phôi về tô-pô hoàn toàn có thể mang các metric (cách đo khoảng cách) rất khác nhau.

Ngoài ra, **tương đương đồng luân** là quan hệ yếu hơn đồng phôi: khối cầu đặc có thể co rút liên tục về một điểm (nên tương đương đồng luân với một điểm), còn mặt cầu rỗng thì không (xem thêm [Bài 09.01]({{ site.baseurl }}/contents/vi/chapter09/09_01_Coffee_Donut/)).

## Bài tập

1. Hình vuông đặc và đường tròn $$S^1$$ có đồng phôi với nhau không? Vì sao?

**Đáp án:** Không. Hình vuông đặc (đồng phôi với đĩa đóng 2 chiều) có biên, còn đường tròn $$S^1$$ (1 chiều) không có biên. Ta cũng có thể kiểm chứng bằng phép bỏ điểm: nếu bỏ đi hai điểm bất kỳ trên $$S^1$$, đường tròn bị tách thành hai mảnh rời nhau (mất tính liên thông đường), trong khi bỏ đi hai điểm bất kỳ trên hình vuông đặc thì phần còn lại vẫn liên thông đường.

2. Khái niệm "mặt đóng" có đồng nghĩa với "mặt compact" không?

**Đáp án:** Không. Mặt đóng phải vừa compact **vừa không có biên**. Đĩa đóng là tập compact nhưng có biên nên không phải mặt đóng.

3. Hai mặt cầu có bán kính khác nhau có đồng phôi không? Có đẳng cự không?

**Đáp án:** Có đồng phôi (cả hai đều có kiểu tô-pô của $$S^2$$), nhưng không đẳng cự (vì bán kính khác nhau nên không tồn tại ánh xạ bảo toàn khoảng cách — đây là tính chất hình học).

::: {style="margin-top: 20px; padding: 10px; background-color: #f8f9fa; border-left: 4px solid #007bff;"}
[← Quay lại đầu chương]({{ site.baseurl }}/contents/vi/chapter09/){style="text-decoration: none; color: #007bff; font-weight: bold;"}
:::
