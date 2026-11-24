---
layout: post
title: "Bài 09.04: Euler Characteristic - Công Thức $V - E + F$"
lang: vi
lang-ref: lecture-09-04
chapter: 9
lecture: 4
categories: [chapter09]
tags: [euler-characteristic, bất-biến, polyhedra, topology-cơ-bản]
description: "Khám phá Euler Characteristic - một bất biến toán học quan trọng được tính bằng công thức $V - E + F$, và tại sao nó lại quan trọng trong topology"
---

**Bất biến toán học cơ bản để phân loại bề mặt**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Cầm bất kỳ khối hộp nào trên bàn — một viên xúc xắc 6 mặt, một kim tự tháp 4 mặt, hay thậm chí một quả bóng đá khâu từ 32 miếng da ngũ giác và lục giác — rồi thử đếm số đỉnh $$V$$, trừ đi số cạnh $$E$$, cộng với số mặt $$F$$. Kỳ lạ thay, dù bạn chia nhỏ mặt thêm hàng nghìn tam giác hay bóp méo khối hộp thành hình củ khoai tây, con số $$V - E + F$$ vẫn cứng đầu đứng yên tại đúng **$$2$$**! Nhưng chỉ cần đục một lỗ xuyên qua tâm biến nó thành chiếc bánh donut, con số ấy lập tức tụt xuống **$$0$$**! **Đặc trưng Euler $$\chi = V - E + F$$** chính là bất biến tô-pô quyền năng và thân thiện nhất trong toàn bộ lịch sử toán học!

Với mọi khối đa diện lồi (như hình lập phương, hình tứ diện hay hình bát diện), nếu lấy số đỉnh ($V$) trừ số cạnh ($E$) rồi cộng số mặt ($F$), ta luôn thu được cùng một giá trị:

- **Hình lập phương:** $V = 8$, $E = 12$, $F = 6$ → $V - E + F = 8 - 12 + 6 = 2$.
- **Hình tứ diện:** $V = 4$, $E = 6$, $F = 4$ → $V - E + F = 4 - 6 + 4 = 2$.
- **Hình bát diện:** $V = 6$, $E = 12$, $F = 8$ → $V - E + F = 6 - 12 + 8 = 2$.

Kết quả luôn bằng **2**. Đây không phải sự trùng hợp ngẫu nhiên mà là một định lý nổi tiếng do nhà toán học **Leonhard Euler** (1707–1783) công bố năm 1750.

Đại lượng **$V - E + F$** được gọi là **đặc trưng Euler** (Euler characteristic), một trong những bất biến quan trọng nhất của tô-pô. Công thức này không chỉ đúng cho các khối đa diện mà còn mở rộng cho mọi bề mặt có thể phân chia thành các đa giác.

Trong bài học này, chúng ta sẽ tìm hiểu định nghĩa công thức $V - E + F$, vì sao nó là một bất biến tô-pô, vai trò của nó trong định lý phân loại bề mặt và mối liên hệ với các số Betti trong tô-pô đại số.

![Euler's polyhedron formula](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Euler%27s_formula.svg/500px-Euler%27s_formula.svg.png)  
*Công thức Euler cho polyhedra - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Euler%27s_formula.svg)*

**Vì sao kiến thức này quan trọng?** Đặc trưng Euler là cây cầu nối giữa hình học tổ hợp (đếm đỉnh, cạnh, mặt) với tô-pô đại số, cho phép phân loại trực tiếp các bề mặt đóng, định hướng được.

---

## 🗺️ Bản đồ kiến thức nền: Đặc trưng Euler là gì và nối những lĩnh vực nào?

### 1. Tô-pô Tổ hợp: Đếm đỉnh–cạnh–mặt mà không phụ thuộc cách chia lưới
- **Bản chất:** Chia một mặt thành lưới đa giác (hay tổng quát hơn là một phức CW chiều $$n$$) rồi tính tổng đan dấu $$\chi(X) = \sum_{k=0}^n (-1)^k c_k$$ (số tế bào chiều chẵn trừ số tế bào chiều lẻ). Điều kỳ diệu là dù bạn thay đổi cách chia lưới tùy ý, tổng đan dấu này **không hề đổi**!

### 2. Tô-pô Đại số: Công thức Euler–Poincaré qua các số Betti
- **Bản chất:** Đặc trưng Euler trùng khít với tổng đan dấu của các **số Betti** (hạng các nhóm đồng điều $$H_k$$):
  $$
  \chi(X) = \beta_0 - \beta_1 + \beta_2 - \cdots
  $$
  Với mặt đóng định hướng được có $$g$$ lỗ ($$\beta_0 = 1,\; \beta_1 = 2g,\; \beta_2 = 1$$), công thức lập tức cho **$$\chi(\Sigma_g) = 2 - 2g$$**!

### 3. Hình học Vi phân: Định lý Gauss–Bonnet
- **Bản chất:** Một trong những đỉnh cao đẹp nhất của toán học: tích phân toàn bộ độ cong Gauss $$K$$ trên một mặt đóng trơn $$M$$ luôn bằng đúng $$2\pi \chi(M)$$!
  $$
  \iint_M K\,dA = 2\pi \chi(M).
  $$
  Bạn uốn cong một chỗ nhô lên (tăng $$K$$), chỗ khác bắt buộc phải lõm xuống (giảm $$K$$) để giữ nguyên tổng diện tích độ cong bằng $$2\pi(2 - 2g)$$!

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc

### Ví dụ 1: Chứng minh bằng tay vì sao CHỈ CÓ ĐÚNG 5 khối đa diện đều Platonic
Giả sử một khối đa diện đều lồi có mọi mặt là đa giác đều $$p$$ cạnh ($$p \ge 3$$) và tại mọi đỉnh có đúng $$q$$ mặt gặp nhau ($$q \ge 3$$).
1. Mỗi mặt có $$p$$ cạnh và mỗi cạnh kẹp giữa 2 mặt $$\implies pF = 2E \implies F = \frac{2E}{p}$$.
2. Mỗi đỉnh có $$q$$ cạnh tỏa ra và mỗi cạnh nối 2 đỉnh $$\implies qV = 2E \implies V = \frac{2E}{q}$$.
3. Thay thẳng vào công thức Euler $$V - E + F = 2$$ rồi chia hai vế cho $$2E$$:
   $$
   \frac{2E}{q} - E + \frac{2E}{p} = 2
   \quad\Longrightarrow\quad
   \frac{1}{p} + \frac{1}{q} = \frac{1}{2} + \frac{1}{E} > \frac{1}{2}!
   $$
4. Liệt kê **mọi** cặp số nguyên $$(p, q) \ge 3$$ thỏa $$\frac{1}{p} + \frac{1}{q} > \frac{1}{2}$$:
   - Nếu $$p = 3$$: $$\frac{1}{q} > \frac{1}{6} \implies q \in \{3, 4, 5\}$$ (Tứ diện $$E=6$$, Bát diện $$E=12$$, Nhị thập diện $$E=30$$).
   - Nếu $$p = 4$$: $$\frac{1}{q} > \frac{1}{4} \implies q = 3$$ (Lập phương $$E=12$$).
   - Nếu $$p = 5$$: $$\frac{1}{q} > \frac{3}{10} \implies q = 3$$ (Thập nhị diện $$E=30$$).
   - Nếu $$p \ge 6$$: $$\frac{1}{p} + \frac{1}{q} \le \frac{1}{6} + \frac{1}{3} = \frac{1}{2}$$ (vô nghiệm!).

Chỉ trong 4 bước đại số sơ cấp từ $$V - E + F = 2$$, ta đã chứng minh chặt chẽ rằng trong vũ trụ 3D **chỉ tồn tại đúng 5 khối đa diện đều**!

### Ví dụ 2: Kiểm tra quả bóng đá cổ điển (Nhị thập diện cụt)
Một quả bóng đá chuẩn gồm $$12$$ miếng ngũ giác đen và $$20$$ miếng lục giác trắng:
- Tổng số mặt: $$F = 12 + 20 = 32$$.
- Tổng số cạnh (mỗi cạnh thuộc chung 2 miếng da): $$E = \frac{12\cdot 5 + 20\cdot 6}{2} = \frac{60 + 120}{2} = 90$$.
- Tổng số đỉnh (tại mỗi mũi khâu có đúng 3 đường chỉ gặp nhau): $$V = \frac{2E}{3} = \frac{180}{3} = 60$$.
- Kiểm tra công thức Euler: $$V - E + F = 60 - 90 + 32 = 2$$! (Và cũng là lý do bạn **không bao giờ** may được một quả bóng chỉ toàn miếng lục giác: nếu toàn lục giác thì $$\chi = 0$$ — đó phải là một chiếc bánh donut chứ không phải quả cầu!)

### Khung giải thích: Tại sao chia nhỏ lưới thế nào thì $$V - E + F$$ vẫn không đổi? (nên đọc chậm)

#### Bước 1: Thêm 1 đường chéo chia đôi một mặt
Kẻ thêm 1 cạnh nối hai đỉnh có sẵn của một mặt đa giác: $$V$$ giữ nguyên, $$E \to E+1$$, $$F \to F+1$$. Tổng $$V - (E+1) + (F+1) = V - E + F$$ **bất biến**!

#### Bước 2: Chấm thêm 1 đỉnh mới nằm giữa một cạnh
Chấm 1 điểm chia đôi một cạnh: $$V \to V+1$$, $$E \to E+1$$, $$F$$ giữ nguyên. Tổng $$(V+1) - (E+1) + F = V - E + F$$ **bất biến**!

#### Bước 3: Kết nối với việc đục thêm một "quai cầm" (tăng giống $$g$$ thêm 1)
Muốn biến mặt cầu thành mặt xuyến, ta khoét bỏ 2 mặt ($$F \to F-2$$) rồi gắn một ống hình trụ nối hai lỗ biên đó lại (hình trụ có $$\chi = 0$$ nên đóng góp $$0$$ vào tổng). Kết quả: $$\chi$$ giảm đi đúng **$$2$$** mỗi khi thêm một lỗ $$\implies \chi(\Sigma_g) = 2 - 2g$$!

#### Bước 4: Bước lên đại số và hình học
Chính tính bất biến khi chia nhỏ lưới khiến $$\chi$$ trở thành một bất biến tô-pô đích thực, nối trực tiếp tổ hợp ($$V-E+F$$) với đại số ($$\sum (-1)^k \beta_k$$) và hình học vi phân (Gauss–Bonnet $$\iint K\,dA = 2\pi\chi$$).

$$
V - E + F
\;\xlongequal{\;\text{Chia lưới bất biến}\;}\;
\beta_0 - \beta_1 + \beta_2
\;\xlongequal{\;\text{Mặt đóng }\Sigma_g\;}\;
2 - 2g
\;\xlongequal{\;\text{Gauss–Bonnet}\;}\;
\frac{1}{2\pi}\iint_{\Sigma_g} K\,dA.
$$

---

## 🎯 Công thức cơ bản: $V - E + F$

### Định nghĩa

**Đặc trưng Euler** của một đa diện (hoặc một bề mặt được chia thành các đa giác) được định nghĩa là:

$$
\chi = V - E + F
$$

trong đó $V$ là số đỉnh (vertices), $E$ là số cạnh (edges) và $F$ là số mặt (faces).

### Ví dụ: Hình lập phương

Hình lập phương có $V = 8$ đỉnh, $E = 12$ cạnh và $F = 6$ mặt vuông, do đó:

$$
\chi = V - E + F = 8 - 12 + 6 = 2
$$

![Cube](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/Cube.svg/500px-Cube.svg.png)  
*Hình lập phương với 8 đỉnh, 12 cạnh, 6 mặt - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cube.svg)*

### Ví dụ: Hình tứ diện

Hình tứ diện (tetrahedron) có $V = 4$ đỉnh, $E = 6$ cạnh và $F = 4$ mặt tam giác, do đó:

$$
\chi = V - E + F = 4 - 6 + 4 = 2
$$

![Tetrahedron](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d1/Regular_tetrahedron.svg/500px-Regular_tetrahedron.svg.png)  
*Hình tứ diện với 4 đỉnh, 6 cạnh, 4 mặt - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Regular_tetrahedron.svg)*

### Định lý Euler cho đa diện lồi

**Định lý Euler (1750):** Đối với mọi khối đa diện lồi (convex polyhedron), ta luôn có:

$$
V - E + F = 2
$$

### Vì sao kết quả luôn bằng 2?

Ta có thể hình dung cách xây dựng một mặt cầu từ cấu trúc tế bào đơn giản nhất (phức CW):

1. **Bắt đầu với một đỉnh:** $V = 1, E = 0, F = 0 \Rightarrow \chi = 1$.
2. **Gắn một cạnh khép kín (vòng lặp) vào đỉnh đó để tạo thành đường tròn xích đạo:** $V = 1, E = 1, F = 0 \Rightarrow \chi = 1 - 1 + 0 = 0$.
3. **Gắn mặt thứ nhất (bán cầu bắc) dọc theo đường tròn:** $V = 1, E = 1, F = 1 \Rightarrow \chi = 1 - 1 + 1 = 1$.
4. **Gắn mặt thứ hai (bán cầu nam) để khép kín mặt cầu:** $V = 1, E = 1, F = 2 \Rightarrow \chi = 1 - 1 + 2 = 2$.

Giá trị $\chi = 2$ phản ánh bản chất tô-pô của mặt cầu: một bề mặt đóng (không có biên), liên thông, định hướng được và không có lỗ (genus $g = 0$). Dù bạn chia mặt cầu thành tam giác, tứ giác hay bất kỳ lưới đa giác hợp lệ nào khác, tổng $V - E + F$ vẫn luôn giữ nguyên bằng 2.

---

## 🔍 Đặc trưng Euler như một bất biến tô-pô

### Bất biến tô-pô là gì?

Một **bất biến tô-pô** (topological invariant) là đại lượng không thay đổi khi ta biến đổi liên tục không gian qua các phép đồng phôi (kéo giãn, nén, uốn mà không cắt hay dán). Đặc trưng Euler chỉ phụ thuộc vào cấu trúc tô-pô của bề mặt chứ không phụ thuộc vào hình dáng cụ thể hay cách chia lưới.

### Ví dụ: Mặt cầu và bề mặt hình lập phương

Vì mặt cầu và bề mặt hình lập phương đồng phôi với nhau, chúng bắt buộc có cùng đặc trưng Euler:
- Hình lập phương có $V = 8, E = 12, F = 6 \Rightarrow \chi = 2$.
- Mọi phép chia tam giác của mặt cầu cũng đều cho $\chi = 2$.

### Công thức tổng quát cho các bề mặt đóng, định hướng được

Đối với một bề mặt đóng, liên thông, định hướng được có giống (số lỗ) bằng $g$, đặc trưng Euler được cho bởi công thức:

$$
\chi = 2 - 2g
$$

Trong công thức này, số $2$ ứng với đặc trưng Euler của mặt cầu ($g = 0$), còn mỗi lỗ (tay cầm) được thêm vào làm giảm đặc trưng Euler đi đúng $2$ đơn vị:

- **Mặt cầu ($g = 0$):** $\chi = 2 - 2(0) = 2$.
- **Mặt xuyến / torus ($g = 1$):** $\chi = 2 - 2(1) = 0$.
- **Bề mặt 2 lỗ ($g = 2$):** $\chi = 2 - 2(2) = -2$.
- **Bề mặt 3 lỗ ($g = 3$):** $\chi = 2 - 2(3) = -4$.

Đặc trưng Euler hoàn toàn có thể nhận giá trị âm khi bề mặt có từ 2 lỗ trở lên.

### Tính đặc trưng Euler của mặt xuyến (Torus)

Xét một cấu trúc tế bào (phức CW) tối giản của mặt xuyến (thu được bằng cách dán các cạnh đối diện của một hình vuông):
- $V = 1$ đỉnh (4 góc hình vuông dán thành 1 điểm).
- $E = 2$ cạnh (2 cặp cạnh đối diện dán thành 2 vòng tròn).
- $F = 1$ mặt (phần trong của hình vuông).

Khi đó:
$$
\chi = V - E + F = 1 - 2 + 1 = 0
$$
Kết quả khớp hoàn toàn với công thức $\chi = 2 - 2g$ tại $g = 1$.

![Torus](https://upload.wikimedia.org/wikipedia/commons/thumb/4/43/Torus.png/500px-Torus.png)  
*Torus (bánh donut) với Euler Characteristic $= 0$ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus.png)*

---

## 🧮 Các hướng chứng minh định lý Euler

### 1. Hướng quy nạp toán học
- **Bước cơ sở:** Kiểm tra trực tiếp trên hình tứ diện ($V = 4, E = 6, F = 4 \Rightarrow \chi = 2$).
- **Bước quy nạp:** Chứng minh rằng khi chia nhỏ hoặc bổ sung thêm mặt bằng các phép biến đổi sơ cấp trên đồ thị phẳng, số lượng đỉnh, cạnh và mặt thay đổi bù trừ nhau sao cho $V - E + F$ không đổi.

### 2. Hướng tô-pô
1. Bề mặt của mọi khối đa diện lồi đều đồng phôi với mặt cầu $S^2$.
2. Đặc trưng Euler của mặt cầu bằng $2$.
3. Vì đặc trưng Euler là một bất biến tô-pô nên mọi khối đa diện lồi đều có $V - E + F = 2$.

### 3. Hướng trải phẳng (phép chiếu lên mặt phẳng)
1. Bỏ đi một mặt của đa diện lồi và trải phẳng phần còn lại lên mặt phẳng thành một đồ thị phẳng liên thông (mặt vừa bỏ tương ứng với miền vô hạn bên ngoài).
2. Trên mặt phẳng, tổng $V - E + F_{\text{trong}} = 1$ (có thể kiểm chứng bằng cách rút dần về một cây khung gồm $V$ đỉnh và $V - 1$ cạnh).
3. Cộng thêm mặt ngoài đã loại bỏ, ta thu được $V - E + F = 2$.

---

## 🎨 Các ví dụ và ứng dụng

### Ba khối đa diện đều còn lại

- **Hình bát diện đều (octahedron):** $V = 6$, $E = 12$, $F = 8$ (mặt tam giác).
$$
\chi = 6 - 12 + 8 = 2
$$

![Octahedron](https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/Octahedron.svg/500px-Octahedron.svg.png)  
*Hình bát diện - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Octahedron.svg)*

- **Hình thập nhị diện đều (dodecahedron):** $V = 20$, $E = 30$, $F = 12$ (mặt ngũ giác).
$$
\chi = 20 - 30 + 12 = 2
$$

- **Hình nhị thập diện đều (icosahedron):** $V = 12$, $E = 30$, $F = 20$ (mặt tam giác).
$$
\chi = 12 - 30 + 20 = 2
$$

### Ứng dụng trong phân loại bề mặt

Một câu hỏi trung tâm của tô-pô bề mặt là: làm thế nào nhận biết hai bề mặt đóng có đồng phôi với nhau hay không?

#### Lược sử định lý phân loại bề mặt
- **1858–1861 (Möbius và Listing):** Phát hiện dải Möbius, mở ra khái niệm tính định hướng của bề mặt.
- **Thập niên 1870 (Felix Klein):** Hệ thống hóa nghiên cứu về các bề mặt không định hướng được.
- **Thập niên 1880–1890 (Henri Poincaré):** Xây dựng các công cụ nền tảng của tô-pô hiện đại.
- **1907 (Max Dehn và Poul Heegaard):** Công bố một trong những chứng minh tổ hợp đầu tiên cho định lý phân loại bề mặt.
- **Giữa thế kỷ 20:** Định lý được hoàn thiện chặt chẽ bằng ngôn ngữ tô-pô đại số (đồng điều, nhóm cơ bản) và trở thành kết quả cơ sở trong mọi giáo trình tô-pô.

#### Định lý phân loại bề mặt (trường hợp định hướng được)

**Định lý:** Mọi bề mặt đóng, liên thông và định hướng được đều được xác định duy nhất (sai khác phép đồng phôi) bởi đặc trưng Euler $\chi$ của nó (hay tương đương, bởi giống $g$ với $\chi = 2 - 2g$).

Nói cách khác, với lớp bề mặt đóng, liên thông và định hướng được, đặc trưng Euler là một **bất biến đầy đủ**:
- Hai bề mặt có cùng $\chi$ thì đồng phôi (ví dụ mọi bề mặt có $\chi = 2$ đều đồng phôi với mặt cầu; mọi bề mặt có $\chi = 0$ đều đồng phôi với mặt xuyến; mọi bề mặt có $\chi = -2$ đều đồng phôi với mặt 2 lỗ).
- Hai bề mặt có $\chi$ khác nhau thì không thể đồng phôi.

#### Quy trình thực hành phân loại một bề mặt đóng định hướng được

1. Kiểm tra bề mặt là đóng (không có biên), liên thông và định hướng được.
2. Chia bề mặt thành các đa giác hợp lệ, đếm $V$, $E$, $F$ và tính $\chi = V - E + F$.
3. Suy ra giống $g$ từ công thức $\chi = 2 - 2g$.

**Ví dụ minh họa:** Giả sử bạn chia một bề mặt đóng, liên thông, định hướng được thành các tứ giác và đếm được $V = 10$, $E = 24$, $F = 12$ (thỏa mãn $4F = 2E = 48$). Khi đó:
- $\chi = 10 - 24 + 12 = -2$.
- Từ $-2 = 2 - 2g$, ta suy ra $g = 2$.
- Vậy bề mặt đó đồng phôi với mặt xuyến 2 lỗ.

### Liên hệ với đồng điều (Homology) và số Betti

Trong tô-pô đại số, đặc trưng Euler được biểu diễn tổng quát qua các nhóm đồng điều $H_n$:

$$
\chi = \sum_{n=0}^{\infty} (-1)^n \beta_n
$$

trong đó $\beta_n = \mathrm{rank}(H_n)$ là các **số Betti**:
- **$\beta_0$:** Số thành phần liên thông (với mặt cầu hay mặt xuyến liên thông, $\beta_0 = 1$).
- **$\beta_1$:** Số lỗ một chiều độc lập (ví dụ đường tròn $S^1$ có $\beta_1 = 1$; mặt xuyến $T^2$ có $\beta_1 = 2$ tương ứng với vòng kinh tuyến và vòng vĩ tuyến).
- **$\beta_2$:** Số khoang trống hai chiều (với mặt cầu đóng hoặc mặt xuyến đóng, $\beta_2 = 1$).
- **$\beta_n$ ($n > 2$):** Số lỗ ở chiều cao hơn.

Dấu đan xen $(-1)^n$ cộng các số Betti bậc chẵn và trừ các số Betti bậc lẻ:
- **Mặt cầu $S^2$:** $\beta_0 = 1, \beta_1 = 0, \beta_2 = 1 \Rightarrow \chi = 1 - 0 + 1 = 2$.
- **Mặt xuyến $T^2$:** $\beta_0 = 1, \beta_1 = 2, \beta_2 = 1 \Rightarrow \chi = 1 - 2 + 1 = 0$.

---

## 🔗 Ứng dụng trong toán học, khoa học và công nghệ

- **Toán học:** Phân loại đa tạp và bề mặt, liên kết hình học đa diện với tô-pô đại số.
- **Vật lý:** Nghiên cứu các không gian compact hóa trong lý thuyết dây, cấu trúc không-thời gian và các pha tô-pô của vật chất.
- **Sinh học:** Mô tả hình thái tế bào, mô và cấu trúc phân tử DNA, protein.
- **Khoa học máy tính và đồ họa 3D:** Kiểm tra tính toàn vẹn lưới đa giác (mesh), phân loại bề mặt 3D và tối ưu hóa thuật toán dựng hình (rendering).
- **Kỹ thuật và kiến trúc:** Phân tích kết cấu không gian, độ ổn định hình học của mạng lưới giàn khung.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Leonhard Euler** - *"Elementa doctrinae solidorum"* (1750)  
   *Bài báo gốc của Euler về công thức $V - E + F = 2$*

2. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Euler Characteristic trong topology hiện đại*

3. **James W. Alexander** - *"Combinatorial Analysis Situs"* (1926)  
   *Euler Characteristic và homology*

### Textbooks

- **James R. Munkres** - *Topology*, 2nd Ed., Ch. 2  
  *Euler Characteristic và các bất biến topology*

- **Sidney A. Morris** - *Topology without Tears*, Ch. 3  
  *Giải thích trực quan về Euler Characteristic*

- **Allen Hatcher** - *Algebraic Topology*, §2.2  
  *Euler Characteristic và homology*

---

## Video tham khảo

- **xem trước** [Euler's Formula and Graph Duality](https://www.youtube.com/watch?v=-9OUyo8NFZg) — 3Blue1Brown, tiếng Anh. Công thức Euler và đối ngẫu đồ thị, để thấy V − E + F không phụ thuộc cách chia.
- [Euler Characteristic (some extra footage)](https://www.youtube.com/watch?v=QwfPTE7lEbE) — Numberphile2, tiếng Anh. Numberphile nói thêm về đặc trưng Euler sau các ví dụ phẳng.
- [Euler's Characteristic - The Incredible Geometry Formula](https://www.youtube.com/watch?v=a9u1agKEjl4) — vinteachesmath, tiếng Anh. Tính V − E + F trên vài khối đa diện, trước khi bài nâng nó thành bất biến.

## 🧩 Bài tập và suy ngẫm

### Câu hỏi suy ngẫm

1. **Tính toán trên đa diện:** Tính $V - E + F$ cho một số hình lăng trụ ($n$-giác) và hình chóp ($n$-giác). Nhận xét về kết quả thu được.
2. **So sánh:** Giải thích vì sao mặt cầu có $\chi = 2$ còn mặt xuyến có $\chi = 0$ theo cả công thức $\chi = 2 - 2g$ lẫn công thức số Betti.
3. **Kiểm chứng bất biến:** Chia một mặt của hình lập phương thành hai tam giác bằng đường chéo; đếm lại $V$, $E$, $F$ và kiểm tra xem $\chi$ có thay đổi không.
4. **Liên hệ ứng dụng:** Nêu một ví dụ mà đặc trưng Euler hữu ích trong đồ họa máy tính, kỹ thuật hoặc vật lý.
5. **Thử thách:** Tính đặc trưng Euler của một bề mặt đóng, định hướng được có 4 lỗ.

### Thử nghiệm thực tế

1. Lấy hoặc gấp bằng giấy một vài khối đa diện lồi (tứ diện, lập phương, lăng trụ tam giác), đếm trực tiếp $V, E, F$ và kiểm chứng $V - E + F = 2$.
2. Vẽ một mạng lưới tam giác trên quả bóng nhựa bằng bút xóa được, đếm $V, E, F$ và tính $\chi$.
3. Dựng mô hình mặt xuyến từ một hình lập phương bị khoét thủng một lỗ vuông xuyên tâm, đếm $V, E, F$ và kiểm tra $\chi = 0$.

---

## 📚 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu:

- **Công thức Euler cho đa diện lồi:** $V - E + F = 2$.
- **Đặc trưng Euler:** Một bất biến tô-pô không phụ thuộc vào cách phân chia đa giác.
- **Phân loại bề mặt đóng, liên thông, định hướng được:** Công thức $\chi = 2 - 2g$ xác định duy nhất lớp đồng phôi của bề mặt.
- **Liên hệ đại số:** $\chi = \sum_{n=0}^{\infty} (-1)^n \beta_n$, nối phép đếm hình học với các số Betti.
