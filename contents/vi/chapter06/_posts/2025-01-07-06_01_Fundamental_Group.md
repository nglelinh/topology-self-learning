---
layout: post
title: "Lecture 06.01: The Fundamental Group"
lang: vi
lang-ref: lecture-06-01
chapter: 6
lecture: 1
categories: [chapter06]
tags: [fundamental-group, π1, group-structure, basepoint, path-connected]
description: "Fundamental group π₁(X,x₀): định nghĩa, group structure, invariance, và ý nghĩa hình học"
---

**π₁(X, x₀) - First Algebraic Invariant**

---

## 📖 Tổng quan

Trong lecture trước, chúng ta học về **homotopy**—continuous deformation. Giờ đây, chúng ta sẽ sử dụng homotopy để construct **first algebraic invariant** trong topology: **fundamental group**.

**Ý tưởng cốt lõi:**

> **Gán một NHÓM cho mỗi không gian có điểm cơ sở $(X, x_0)$.**  
> **Các phần tử của nhóm = các lớp đồng luân của các vòng lặp tại $x_0$.**

Đây là một bước cách mạng trong toán học, thay đổi cách chúng ta nghĩ về các không gian. **Từ hình học đến đại số**: chúng ta gán một đối tượng đại số (nhóm) cho một đối tượng hình học (không gian), cho phép chúng ta suy luận đại số về các vấn đề hình học. **Khả năng tính toán**: không giống như trực giác hình học mơ hồ, $\pi_1$ thường có thể tính toán được thông qua các thuật toán—chúng ta thực sự có thể tính toán nó! **Sức mạnh**: fundamental group phân biệt các không gian tô-pô khác nhau và chứng minh các định lý sâu sắc (định lý điểm cố định Brouwer, định lý đường cong Jordan). **Tính phổ quát**: các ứng dụng trải dài từ tô-pô học thuần túy qua vật lý (gauge theory, instantons) đến robotics (lập kế hoạch chuyển động, không gian cấu hình).

![Fundamental group visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Fundamental_group.svg/500px-Fundamental_group.svg.png)  
*Loops trong space và group structure - Nguồn concept*

**Tại sao đây là một bước cách mạng?**

Trước Poincaré (1895), tô-pô học chủ yếu dựa vào trực giác hình học và lập luận trực quan—mạnh mẽ nhưng thường không chính xác. **Việc Poincaré giới thiệu fundamental group** đã thay đổi mọi thứ, cung cấp công cụ đại số thực sự đầu tiên trong tô-pô học. Đột phá này **mở ra cánh cửa cho tô-pô học đại số**—một lĩnh vực hoàn chỉnh được xây dựng trên ý tưởng nghiên cứu các không gian thông qua các bất biến đại số. Nó **cho phép các chứng minh chặt chẽ** thay thế các hình ảnh mơ hồ bằng các lập luận chính xác. Fundamental group **kết nối tô-pô học với lý thuyết nhóm**, cho phép chúng ta sử dụng các công cụ đại số mạnh mẽ. Quan trọng nhất, nó **dẫn đến một loạt các tổng quát hóa**: homology groups, cohomology rings, higher homotopy groups $\pi_n$, K-theory—toàn bộ kho vũ khí của tô-pô học đại số hiện đại đều bắt nguồn từ ý tưởng đơn lẻ này.

Trong bài học này, chúng ta xây dựng lý thuyết một cách có hệ thống từ đầu. **Định nghĩa $\pi_1(X, x_0)$** bắt đầu với các vòng lặp theo homotopy—một quan hệ tương đương trên các đường đi liên tục. **Cấu trúc nhóm** xuất hiện tự nhiên từ phép toán concatenation—"thực hiện vòng lặp $f$, sau đó vòng lặp $g$". **Xác minh** chứng minh tất cả các tiên đề nhóm: phần tử đơn vị (vòng lặp hằng), phần tử nghịch đảo (đường đi ngược), và quan trọng là tính kết hợp (thứ tự hợp thành không quan trọng). **Độc lập với điểm cơ sở** cho thấy $\pi_1(X, x_0) \cong \pi_1(X, x_1)$ đối với $X$ path-connected—nhóm về cơ bản độc lập với việc chọn điểm cơ sở. **Các ví dụ đầu tiên** bao gồm $\mathbb{R}^n$ (nhóm tầm thường—contractible), $S^1$ (số nguyên $\mathbb{Z}$—winding number), các hình cầu cao hơn $S^n$ (tầm thường cho $n \geq 2$), và torus $T^2$ ($\mathbb{Z} \times \mathbb{Z}$—hai vòng lặp độc lập). **Các tính chất** như functoriality và homotopy invariance thiết lập $\pi_1$ như một bất biến tô-pô thực sự.

**Tại sao đây là kiến thức cần thiết?** $\pi_1$ là **bất biến đại số đầu tiên** mà hầu hết sinh viên gặp phải—một giới thiệu hoàn hảo về mặt sư phạm cho sức mạnh của tô-pô học đại số. Nó **tương đối có thể tính toán được** so với các higher homotopy groups $\pi_n$ vốn nổi tiếng là khó tính toán. **Các ứng dụng** rất rộng rãi: phân loại covering spaces, chứng minh các định lý điểm cố định, nghiên cứu lý thuyết nút nơi fundamental groups của các phần bù nút phân biệt các nút. Quan trọng nhất, $\pi_1$ phục vụ như một **cánh cửa** truyền cảm hứng cho toàn bộ hành trình tô-pô học đại số—một khi bạn thấy điều này hoạt động, bạn sẽ muốn nhiều hơn!

---

## 🔄 Construction của Fundamental Group

### 1. Loops và Path Homotopy (Nhắc lại)

**Định nghĩa (Loop):**  
Một **loop** based tại $x_0 \in X$ là một ánh xạ liên tục:

$$
\gamma: [0,1] \to X, \quad \gamma(0) = \gamma(1) = x_0
$$

**Tập tất cả các loops tại $x_0$:**

$$
\Omega(X, x_0) = \{\gamma: [0,1] \to X : \gamma(0) = \gamma(1) = x_0\}
$$

Trực giác hình học là một loop là một đường đi khép kín—chúng ta bắt đầu tại điểm cơ sở $x_0$, đi vòng quanh không gian, và quay lại điểm xuất phát. Hãy tưởng tượng một con kiến bắt đầu tại $x_0$, đi vòng quanh không gian theo một đường đi liên tục, và quay lại đúng điểm xuất phát. Các loops là đối tượng cơ bản trong nghiên cứu fundamental group vì chúng nắm bắt cách không gian có thể được "quấn" hoặc "vòng lặp" xung quanh điểm cơ sở.

---

**Path Homotopy (rel endpoints):**  
Cho các loops $\gamma$, $\delta$ tại $x_0$. Chúng được gọi là **path homotopic** ($\gamma \simeq_p \delta$) nếu tồn tại một ánh xạ liên tục $F: [0,1] \times [0,1] \to X$ thỏa mãn $F(s, 0) = \gamma(s)$ và $F(s, 1) = \delta(s)$ cho mọi $s \in [0,1]$, và quan trọng là $F(0, t) = F(1, t) = x_0$ cho mọi $t \in [0,1]$ (basepoint được giữ cố định).

Trực giác hình học là chúng ta có thể biến dạng liên tục loop $\gamma$ thành loop $\delta$ trong khi giữ điểm cơ sở $x_0$ được "dán chặt" tại vị trí của nó. Hãy tưởng tượng một sợi dây được căng giữa điểm cơ sở và chính nó tạo thành một vòng lặp—chúng ta có thể uốn cong và kéo giãn sợi dây này một cách liên tục, nhưng chúng ta không thể di chuyển điểm cơ sở. Điều kiện giữ điểm cơ sở cố định là rất quan trọng vì nó đảm bảo rằng khi chúng ta xét các lớp đồng luân của các loops, chúng ta có thể định nghĩa một phép toán nhóm một cách nhất quán.

![Path homotopy loops](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Homotopy_of_loops.svg/400px-Homotopy_of_loops.svg.png)  
*Path homotopy giữa hai loops - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Homotopy_of_loops.svg)*

---

**Homotopy Class:**  
**$[\gamma]$** = homotopy class của loop $\gamma$ = tập tất cả các loops path homotopic với $\gamma$.

**Quotient:**

$$
\pi_1(X, x_0) = \Omega(X, x_0) / {\sim_p}
$$

Đây là tập các homotopy classes của các loops tại $x_0$. Trực giác là chúng ta đồng nhất các loops có thể biến dạng liên tục thành nhau—từ quan điểm của fundamental group, các loops đồng luân được coi là "giống nhau". Điều này cho phép chúng ta nghiên cứu các loops không phải từng cái một mà theo các lớp đồng luân của chúng, làm giảm đáng kể độ phức tạp của vấn đề.

---

### 2. Group Operation: Path Concatenation

**Định nghĩa (Concatenation):**  
Cho các loops $\gamma$, $\delta$ tại $x_0$. **Product loop** $\gamma \cdot \delta$ được định nghĩa bằng cách đi qua $\gamma$ với tốc độ gấp đôi trong nửa đầu của khoảng thời gian, sau đó đi qua $\delta$ với tốc độ gấp đôi trong nửa sau:

$$
(\gamma \cdot \delta)(t) = \begin{cases}
\gamma(2t) & 0 \leq t \leq 1/2 \\
\delta(2t - 1) & 1/2 \leq t \leq 1
\end{cases}
$$

Trực giác hình học là chúng ta đi qua $\gamma$ trước (với tốc độ gấp đôi, hoàn thành tại $t=1/2$), sau đó đi qua $\delta$ (với tốc độ gấp đôi, hoàn thành tại $t=1$). Reparametrization (thay đổi tốc độ) là cần thiết để đảm bảo rằng loop mới vẫn được định nghĩa trên khoảng $[0,1]$. Điều này cho phép chúng ta định nghĩa một phép toán trên các loops, và khi chúng ta xét các lớp đồng luân, phép toán này sẽ trở thành phép nhóm trong fundamental group.

---

**Well-defined trên homotopy classes:**

**Định lý:** Nếu $\gamma \simeq_p \gamma'$ và $\delta \simeq_p \delta'$, thì $\gamma \cdot \delta \simeq_p \gamma' \cdot \delta'$.

**Chứng minh:** Giả sử chúng ta có các homotopies $F_\gamma: \gamma \simeq \gamma'$ và $F_\delta: \delta \simeq \delta'$. Chúng ta có thể định nghĩa một homotopy $F_{\gamma \cdot \delta}$ từ $\gamma \cdot \delta$ đến $\gamma' \cdot \delta'$ bằng cách nối các homotopies $F_\gamma$ và $F_\delta$ lại với nhau—chúng ta biến dạng $\gamma$ thành $\gamma'$ trong nửa đầu của khoảng thời gian, và biến dạng $\delta$ thành $\delta'$ trong nửa sau. Các chi tiết kỹ thuật xác minh tính liên tục của homotopy này. ✓

**Hệ quả:** Phép nhân được định nghĩa tốt trên các lớp đồng luân:

$$
[\gamma] \cdot [\delta] = [\gamma \cdot \delta]
$$

Điều này có nghĩa là phép toán concatenation không phụ thuộc vào việc chọn đại diện cụ thể của mỗi lớp đồng luân—nếu chúng ta thay thế $\gamma$ bằng một loop đồng luân với nó, kết quả sẽ không thay đổi.

---

### 3. Group Axioms Verification

**Theorem:** (π₁(X, x₀), ·) is a group.

**Proof:** Verify identity, inverses, associativity.

---

**Identity Element:**

**Constant loop:** Định nghĩa $e_{x_0}(t) = x_0$ cho mọi $t \in [0,1]$. Đây là loop "không làm gì cả"—nó chỉ đứng yên tại điểm cơ sở.

**Khẳng định:** $[e_{x_0}]$ là phần tử đơn vị trong $\pi_1(X, x_0)$.

**Chứng minh:** Chúng ta cần chứng minh rằng $[\gamma] \cdot [e] = [\gamma]$ và $[e] \cdot [\gamma] = [\gamma]$ cho mọi loop $\gamma$.

**Homotopy $\gamma \cdot e \simeq_p \gamma$:**

Trực giác hình học là khi chúng ta nối một loop với constant loop, chúng ta có thể "co" phần constant lại để chỉ còn lại loop ban đầu. Chúng ta định nghĩa một homotopy $F(s,t)$ bằng cách thu nhỏ phần constant: tại $t=0$, chúng ta có $\gamma \cdot e$ với tốc độ bằng nhau; tại $t=1$, $\gamma$ chiếm toàn bộ khoảng $[0,1]$.

**Rõ ràng:**
$$
F(s,t) = \begin{cases}
\gamma(2s/(1+t)) & 0 \leq s \leq (1+t)/2 \\
x_0 & (1+t)/2 \leq s \leq 1
\end{cases}
$$

Tại $t=0$: $\gamma \cdot e$. Tại $t=1$: $\gamma$ (reparametrized). ✓

Tương tự, chúng ta có thể chứng minh $[e \cdot \gamma] = [\gamma]$ bằng cách co phần constant ở đầu. ✓

---

**Inverses:**

**Inverse loop:** Cho một loop $\gamma$, chúng ta định nghĩa **inverse loop** $\gamma^{-1}$ bằng cách đảo ngược hướng: $\gamma^{-1}(t) = \gamma(1-t)$. Điều này có nghĩa là chúng ta đi ngược lại đường đi ban đầu.

**Khẳng định:** $[\gamma] \cdot [\gamma^{-1}] = [e]$.

**Chứng minh:** Loop $\gamma \cdot \gamma^{-1}$ đi qua $\gamma$ theo hướng thuận rồi đi ngược lại theo hướng ngược. Trực giác hình học là chúng ta có thể "co" loop này về constant loop bằng cách thu nhỏ nó liên tục từ các điểm đầu và cuối. Hãy tưởng tượng một sợi dây được căng giữa hai điểm—nếu chúng ta đi qua sợi dây theo cả hai hướng, chúng ta có thể thu nhỏ nó về một điểm bằng cách kéo từ cả hai đầu.

**Homotopy $F(s,t)$:**
- Tại $t=0$: $\gamma \cdot \gamma^{-1}(s)$
- Thu nhỏ dần dần
- Tại $t=1$: $e_{x_0}$

**Rõ ràng:** Kỹ thuật nhưng có thể hình dung—collapse loop từ các điểm đầu và cuối. ✓

Tương tự, chúng ta có $[\gamma^{-1}] \cdot [\gamma] = [e]$. ✓

---

**Associativity:**

**Khẳng định:** $([\gamma] \cdot [\delta]) \cdot [\varepsilon] = [\gamma] \cdot ([\delta] \cdot [\varepsilon])$.

**Chứng minh:** Cả hai vế đều bằng $[\gamma \cdot \delta \cdot \varepsilon]$ (đi qua cả ba loops). Sự khác biệt chỉ là cách reparametrization—cách chúng ta phân chia khoảng thời gian $[0,1]$ giữa ba loops. Ở vế trái, $\gamma$ chiếm $[0, 1/4]$, $\delta$ chiếm $[1/4, 1/2]$, và $\varepsilon$ chiếm $[1/2, 1]$. Ở vế phải, $\gamma$ chiếm $[0, 1/2]$, $\delta$ chiếm $[1/2, 3/4]$, và $\varepsilon$ chiếm $[3/4, 1]$. Chúng ta có thể xây dựng một homotopy $F$ reparametrizes một cách mượt mà giữa hai cách phân chia này, chứng minh rằng hai vế là đồng luân. ✓

**Kết luận:** $\pi_1(X, x_0)$ thỏa mãn tất cả các tiên đề nhóm! ✓ **QED**

---

## 📊 First Examples

### 1. $\pi_1(\mathbb{R}^n) = 0$ (Nhóm Tầm thường)

**Định lý:** $\mathbb{R}^n$ là simply connected: $\pi_1(\mathbb{R}^n, x_0) = \{[e]\}$.

**Chứng minh:**  
$\mathbb{R}^n$ là contractible—chúng ta có thể co toàn bộ không gian về một điểm. Bất kỳ loop $\gamma$ nào đều đồng luân với constant loop thông qua straight-line homotopy:

$$
F(s,t) = (1-t)\gamma(s) + t x_0
$$

Đây là một homotopy "đường thẳng"—tại mỗi thời điểm $t$, chúng ta di chuyển mỗi điểm trên loop $\gamma$ dọc theo đường thẳng từ vị trí ban đầu của nó đến điểm cơ sở $x_0$. Tính chất convex của $\mathbb{R}^n$ đảm bảo rằng đường thẳng này nằm hoàn toàn trong không gian. ✓

**Hệ quả:** $\mathbb{R}^n$ không có "lỗ" về mặt đại số—mọi loop đều có thể co lại về một điểm, phản ánh trong fundamental group tầm thường.

---

### 2. $\pi_1(S^1) \cong \mathbb{Z}$ (Số Nguyên!)

**Định lý:** $\pi_1(S^1, 1) \cong \mathbb{Z}$.

Trực giác hình học là các loops trên hình tròn được phân loại bởi **winding number** $n \in \mathbb{Z}$—số lần chúng ta quấn quanh hình tròn. Hãy tưởng tượng một sợi dây được quấn quanh một cái cột—số lần quấn là một số nguyên, và đây chính là winding number. Một loop quấn một lần theo chiều ngược chiều kim đồng hồ có winding number $+1$, một loop quấn một lần theo chiều kim đồng hồ có winding number $-1$, và một loop không quấn quanh cột có winding number $0$.

**Chứng minh outline:**
Chứng minh này sử dụng khái niệm covering space, mà chúng ta sẽ nghiên cứu chi tiết trong các bài học sau. Ý tưởng cơ bản là chúng ta có một covering map $p: \mathbb{R} \to S^1$ được định nghĩa bởi $p(t) = e^{2\pi it}$, ánh xạ đường thẳng thực lên hình tròn. Một loop $\gamma: [0,1] \to S^1$ có thể được "lift" lên một đường đi $\tilde{\gamma}: [0,1] \to \mathbb{R}$ trên đường thẳng thực. Sự khác biệt $\tilde{\gamma}(1) - \tilde{\gamma}(0)$ là một số nguyên, và đây chính là winding number của loop $\gamma$. Mỗi homotopy class $[\gamma]$ tương ứng với một số nguyên $n$, và phép toán concatenation tương ứng với phép cộng trong $\mathbb{Z}$.

**Kết quả:** $\pi_1(S^1) \cong \mathbb{Z}$! ✓

**Generator:** Loop $\gamma_1(t) = e^{2\pi it}$ (quấn một lần theo chiều ngược chiều kim đồng hồ) là một generator của nhóm—mọi loop khác đều có thể được biểu diễn như một bội số nguyên của loop này.

**Ý nghĩa hình học:** Hình tròn có "một lỗ"—được phản ánh trong $\pi_1 \cong \mathbb{Z}$. Đây là một trong những ví dụ quan trọng nhất trong tô-pô học đại số vì nó cho thấy cách fundamental group nắm bắt cấu trúc tô-pô của không gian.

![S1 fundamental group](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Winding_number.svg/400px-Winding_number.svg.png)  
*Winding number around circle - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Winding_number.svg)*

---

### 3. $\pi_1(S^n) = 0$ cho $n \geq 2$

**Định lý:** Các hình cầu cao hơn là simply connected.

**Chứng minh sketch:**  
Cho một loop $\gamma: S^1 \to S^n$. Ảnh $\gamma(S^1)$ của loop này là một tập compact một chiều trong không gian $n$-chiều, và do đó nó phải bỏ qua ít nhất một điểm $p$ (đây là một kết quả về dimension—một tập một chiều không thể phủ toàn bộ không gian $n$-chiều với $n \geq 2$). Không gian $S^n \setminus \{p\}$ đồng luân tương đương với $\mathbb{R}^n$, là contractible. Do đó, loop $\gamma$ có thể được factor qua một không gian contractible, nghĩa là $\gamma \simeq$ constant. ✓

**Trực giác hình học:** Các hình cầu cao hơn "quá lớn" về mặt chiều—mọi loop đều có thể được co lại về một điểm vì có đủ không gian để "tránh" các điểm. Điều này tương phản mạnh mẽ với trường hợp $S^1$, nơi các loops có thể bị "mắc kẹt" quanh hình tròn.

**Sự tương phản:** $S^1$ có $\pi_1 = \mathbb{Z}$, nhưng $S^2$ có $\pi_1 = 0$! Đây là một ví dụ tuyệt vời về cách topology phân biệt các chiều—fundamental group có thể phân biệt giữa các không gian có chiều khác nhau.

---

### 4. $\pi_1(T^2) \cong \mathbb{Z} \times \mathbb{Z}$ (Torus)

**Định lý:** $\pi_1(T^2) \cong \mathbb{Z} \times \mathbb{Z}$.

Trực giác hình học là torus $T^2 = S^1 \times S^1$ có hai hướng độc lập để tạo thành loops: meridian (vòng quanh theo một hướng) và longitude (vòng quanh theo hướng khác, đi qua lỗ). Hãy tưởng tượng một torus như một chiếc bánh donut—chúng ta có thể quấn một sợi dây quanh "lỗ" của donut (meridian), hoặc quanh "thân" của donut (longitude), hoặc cả hai theo các tổ hợp khác nhau.

**Generators:**
- $\alpha$: Loop quanh meridian (một hướng)
- $\beta$: Loop quanh longitude (hướng khác)

**Relations:** $\alpha$ và $\beta$ giao hoán với nhau (chúng ta có thể đi qua chúng theo bất kỳ thứ tự nào)—điều này phản ánh tính chất tích của torus $T^2 = S^1 \times S^1$.

**Kết quả:** $\pi_1(T^2) = \langle \alpha, \beta | \alpha\beta = \beta\alpha \rangle \cong \mathbb{Z} \times \mathbb{Z}$. ✓

**Xác minh:** Chúng ta sẽ chứng minh kết quả này một cách chính thức bằng cách sử dụng định lý Seifert-van Kampen trong các bài học tiếp theo, nhưng trực giác hình học đã cho chúng ta một hiểu biết sâu sắc về cấu trúc của fundamental group của torus.

---

## 🔗 Basepoint Independence

### 1. Basepoint Change Isomorphism

**Setup:** Cho $X$ là path-connected. Cho $x_0$, $x_1 \in X$. Chọn một path $\alpha: [0,1] \to X$ với $\alpha(0) = x_0$ và $\alpha(1) = x_1$.

**Định nghĩa ánh xạ $\beta_\alpha: \pi_1(X, x_0) \to \pi_1(X, x_1)$:**

$$
\beta_\alpha([\gamma]) = [\alpha^{-1} \cdot \gamma \cdot \alpha]
$$

Đây là **conjugation bởi $\alpha$**. Trực giác hình học là chúng ta bắt đầu tại $x_1$, đi theo $\alpha^{-1}$ (đường đi ngược của $\alpha$) để đến $x_0$, đi qua loop $\gamma$ tại $x_0$, sau đó quay lại $x_1$ qua $\alpha$. Kết quả là một loop based tại $x_1$!

---

**Định lý:** $\beta_\alpha$ là một group isomorphism.

**Chứng minh:** Chúng ta cần kiểm tra hai điều. Thứ nhất, $\beta_\alpha$ là một homomorphism—$\beta_\alpha([\gamma][\delta]) = \beta_\alpha([\gamma])\beta_\alpha([\delta])$, điều này có thể được kiểm tra bằng cách sử dụng tính chất của concatenation. Thứ hai, $\beta_\alpha$ là song ánh—nghịch đảo của nó là $\beta_{\alpha^{-1}}$, ánh xạ từ $\pi_1(X, x_1)$ về $\pi_1(X, x_0)$. ✓

**Hệ quả:** $\pi_1(X, x_0) \cong \pi_1(X, x_1)$ cho mọi $x_0$, $x_1$ (trong cùng một thành phần liên thông).

---

**Cảnh báo:** Isomorphism phụ thuộc vào việc chọn path $\alpha$!

Các paths khác nhau $\alpha$, $\alpha'$ cho các isomorphisms khác nhau (chúng khác nhau bởi một inner automorphism). Điều này có nghĩa là mặc dù các nhóm là isomorphic, cách chúng ta xác định isomorphism phụ thuộc vào đường đi mà chúng ta chọn để kết nối hai điểm cơ sở.

**Ký hiệu:** Khi $X$ path-connected, chúng ta thường viết **$\pi_1(X)$** (bỏ qua basepoint).

**Lưu ý:** Đây là "up to isomorphism"—cấu trúc nhóm thực tế phụ thuộc vào basepoint và cách chọn path. Tuy nhiên, đối với các mục đích thực tế, chúng ta thường chỉ quan tâm đến isomorphism type của fundamental group, không phải cấu trúc nhóm cụ thể.

---

### 2. Các không gian không Path-Connected

**Nếu $X$ không path-connected:**

$\pi_1(X, x_0)$ phụ thuộc hoàn toàn vào thành phần path-connected chứa $x_0$. Điều này có nghĩa là nếu chúng ta chọn các điểm cơ sở từ các thành phần liên thông khác nhau, chúng ta sẽ nhận được các fundamental groups khác nhau.

**Định lý:** $\pi_1(X, x_0) = \pi_1(C, x_0)$, trong đó $C$ là thành phần path-connected của $x_0$.

**Hệ quả:** Chúng ta phải nghiên cứu $\pi_1$ riêng biệt cho mỗi thành phần liên thông. Điều này có nghĩa là để hiểu đầy đủ fundamental group của một không gian không path-connected, chúng ta cần tính toán fundamental group của từng thành phần liên thông và sau đó kết hợp thông tin này lại với nhau.

---

## 🎯 Functoriality

### 1. Induced Homomorphism

**Setup:** Cho $f: (X, x_0) \to (Y, y_0)$ là một ánh xạ liên tục (basepoint-preserving, nghĩa là $f(x_0) = y_0$).

**Định nghĩa $f_*: \pi_1(X, x_0) \to \pi_1(Y, y_0)$:**

$$
f_*([\gamma]) = [f \circ \gamma]
$$

Trực giác hình học là chúng ta ánh xạ loop $\gamma$ trong $X$ thành loop $f \circ \gamma$ trong $Y$ bằng cách áp dụng ánh xạ $f$ lên mỗi điểm trên loop. Điều này có nghĩa là nếu chúng ta có một loop trong $X$, chúng ta có thể "đẩy" nó về $Y$ thông qua ánh xạ $f$, và kết quả là một loop trong $Y$.

---

**Định lý:** $f_*$ là một group homomorphism được định nghĩa tốt.

**Chứng minh:** Chúng ta cần kiểm tra hai điều. Thứ nhất, $f_*$ được định nghĩa tốt—nếu $\gamma \simeq_p \delta$, thì $f \circ \gamma \simeq_p f \circ \delta$ vì $f$ liên tục và do đó bảo toàn homotopy. Cụ thể, nếu chúng ta có một homotopy $F$ giữa $\gamma$ và $\delta$, thì $f \circ F$ là một homotopy giữa $f \circ \gamma$ và $f \circ \delta$. Thứ hai, $f_*$ là một homomorphism—$f_*([\gamma][\delta]) = [f \circ (\gamma \cdot \delta)] = [f \circ \gamma \cdot f \circ \delta] = f_*([\gamma])f_*([\delta])$, điều này có thể được kiểm tra bằng cách sử dụng tính chất của concatenation và composition. ✓

---

**Các tính chất:**

**Tính chất (1) - Identity:** $(id_X)_* = id_{\pi_1(X,x_0)}$. Điều này có nghĩa là ánh xạ đồng nhất cảm ứng ánh xạ đồng nhất trên fundamental group—một kết quả tự nhiên và mong đợi.

**Tính chất (2) - Composition:** $(g \circ f)_* = g_* \circ f_*$. Điều này có nghĩa là composition của các ánh xạ cảm ứng composition của các homomorphisms—một tính chất quan trọng đảm bảo rằng fundamental group "tôn trọng" cấu trúc của các ánh xạ.

**Hệ quả:** $\pi_1$ là một **functor** từ phạm trù các pointed spaces với các basepoint-preserving maps đến phạm trù các groups với các homomorphisms. Đây là một khái niệm quan trọng trong category theory—fundamental group không chỉ là một cách gán một nhóm cho mỗi không gian, mà còn là một cách "tôn trọng" cấu trúc của các ánh xạ giữa các không gian.

---

### 2. Homotopy Invariance

**Định lý:** Nếu $f, g: (X, x_0) \to (Y, y_0)$ đồng luân (relative to basepoint), thì $f_* = g_*$.

**Chứng minh:** Giả sử chúng ta có một homotopy $F: X \times I \to Y$ kết nối $f$ và $g$. Homotopy này cảm ứng một homotopy giữa $f \circ \gamma$ và $g \circ \gamma$ cho mỗi loop $\gamma$—cụ thể, $F(\gamma(s), t)$ là một homotopy từ $f \circ \gamma$ đến $g \circ \gamma$. Do đó $[f \circ \gamma] = [g \circ \gamma]$ cho mọi loop $\gamma$, nghĩa là $f_* = g_*$. ✓

---

**Hệ quả (Homotopy Invariance chính):**  
Nếu $X \simeq Y$ đồng luân tương đương, thì $\pi_1(X) \cong \pi_1(Y)$.

**Chứng minh:** Giả sử chúng ta có một homotopy equivalence $f: X \to Y$ với homotopy inverse $g: Y \to X$ sao cho $g \circ f \simeq id_X$ và $f \circ g \simeq id_Y$. Khi đó $g_* \circ f_* = (g \circ f)_* = id_* = id$ và $f_* \circ g_* = id$, nghĩa là $f_*$ và $g_*$ là nghịch đảo của nhau, và do đó là các isomorphisms. ✓

**Sức mạnh:** $\pi_1$ là **homotopy invariant**—nó chỉ phụ thuộc vào homotopy type của không gian, không phụ thuộc vào chi tiết cụ thể của cấu trúc tô-pô! Đây là một tính chất cực kỳ mạnh mẽ cho phép chúng ta tính toán fundamental group bằng cách sử dụng homotopy equivalence để đơn giản hóa không gian.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Introduced fundamental group, revolutionized topology*

2. **Henri Poincaré** - *"Cinquième complément à l'Analysis Situs"* (1904)  
   *Further developed fundamental group theory*

3. **Max Dehn** - *"Über die Topologie des dreidimensionalen Raumes"* (1910)  
   *Applications to 3-manifolds*

4. **Emmy Noether** - Group theory applications to topology (1920s)  
   *Algebraic foundations*

### Textbooks

5. **James R. Munkres** - *Topology*, 2nd Ed., **§52: Fundamental Group**

6. **Allen Hatcher** - *Algebraic Topology*, **§1.1: Basic Constructions**  
   *Best modern treatment, geometric intuition*

7. **William S. Massey** - *A Basic Course in Algebraic Topology*, **Chapters 2-3**

8. **Glen E. Bredon** - *Topology and Geometry*, **Chapter I-II**

9. **Joseph J. Rotman** - *An Introduction to Algebraic Topology*, **Chapter 7**

10. **Marvin J. Greenberg & John R. Harper** - *Algebraic Topology: A First Course*, **Chapter 3**

---

## 🔗 Applications and Connections

### Topology - Distinguishing Spaces

Fundamental group là một công cụ mạnh mẽ để phân biệt các không gian tô-pô. Ví dụ, $\pi_1(S^1) \cong \mathbb{Z} \neq 0 = \pi_1(S^2)$ chứng minh rằng $S^1 \not\cong S^2$—không tồn tại homeomorphism giữa hình tròn và hình cầu mặc dù cả hai đều compact và connected. Đây là một ví dụ tuyệt vời về cách fundamental group có thể phân biệt các không gian mà các tính chất tô-pô cơ bản không thể phân biệt được.

### Fixed Point Theorems - Brouwer

Định lý điểm cố định Brouwer phát biểu rằng mọi ánh xạ liên tục $f: D^2 \to D^2$ đều có ít nhất một điểm cố định. Chứng minh của định lý này sử dụng $\pi_1(S^1) \cong \mathbb{Z}$ một cách tinh tế—nếu $f$ không có điểm cố định, thì chúng ta có thể xây dựng một retraction $r: D^2 \to S^1$, điều này dẫn đến mâu thuẫn vì $\pi_1(D^2) = 0$ trong khi $\pi_1(S^1) = \mathbb{Z}$. Đây là một ứng dụng cổ điển của fundamental group trong giải tích.

### Covering Space Theory

Covering spaces của một không gian $X$ được phân loại bởi các nhóm con của $\pi_1(X)$. Universal cover $\tilde{X}$ thỏa mãn $\pi_1(\tilde{X}) = 0$ và $X = \tilde{X}/\pi_1(X)$, nghĩa là không gian ban đầu có thể được xây dựng như một quotient của universal cover bởi fundamental group. Đây là một kết nối sâu sắc giữa fundamental group và covering spaces, và chúng ta sẽ nghiên cứu chi tiết trong các bài học sau.

### Complex Analysis - Monodromy

Trong giải tích phức, các hàm đa trị như $\sqrt{z}$ và $\log z$ trở thành đơn trị trên universal cover của miền xác định của chúng. Monodromy là hành động của $\pi_1$ trên các giá trị hàm—khi chúng ta đi vòng quanh một điểm kỳ dị, giá trị của hàm có thể thay đổi, và cách thay đổi này được mã hóa bởi fundamental group. Đây là một ví dụ tuyệt vời về cách topology xuất hiện tự nhiên trong giải tích phức.

### Robotics - Configuration Spaces

Trong robotics, không gian cấu hình của robot là không gian của tất cả các vị trí và hướng có thể của robot. Các paths trong không gian cấu hình tương ứng với các chuyển động của robot. Các homotopy classes tương ứng với các chiến lược về mặt tô-pô khác nhau—ví dụ, đi bên trái hoặc bên phải của một chướng ngại vật là hai homotopy classes khác nhau. $\pi_1(X)$ đại diện cho các chướng ngại vật cơ bản đối với chuyển động—nếu fundamental group không tầm thường, có những cách "về mặt tô-pô khác nhau" để robot có thể di chuyển.

### Physics - Aharonov-Bohm Effect

Trong cơ học lượng tử, hiệu ứng Aharonov-Bohm cho thấy rằng sự dịch chuyển pha của electron phụ thuộc vào $\pi_1$ của không gian cấu hình (loại trừ từ thông từ tính). Nếu $\pi_1$ không tầm thường, có thể có các hiệu ứng lượng tử quan sát được ngay cả khi đường đi cổ điển tránh trường. Đây là một ví dụ về cách topology xuất hiện trong vật lý lượng tử và cho thấy rằng fundamental group không chỉ là một khái niệm toán học trừu tượng mà còn có ý nghĩa vật lý sâu sắc.

---

## 🧩 Exercises

### Definition và Basic Properties

1. **Verify Loop Concatenation:**  
   γ, δ loops at x₀. Verify γ · δ well-defined loop (continuous, based at x₀).

2. **Constant Loop Identity:**  
   Write explicit homotopy F: γ · e ≃_p γ. Verify F continuous và fixes basepoint.

3. **Inverse Loop:**  
   Prove [γ] · [γ⁻¹] = [e] by constructing explicit homotopy collapsing γ · γ⁻¹ to constant.

4. **Associativity Homotopy:**  
   Sketch homotopy showing (γ · δ) · ε ≃_p γ · (δ · ε). Describe reparametrization.

### Computing π₁

5. **ℝⁿ Simply Connected:**  
   Prove any loop trong ℝⁿ homotopic to constant using straight-line homotopy F(s,t) = (1-t)γ(s) + tx₀.

6. **Disk D²:**  
   π₁(D²) = 0. Why? (Same proof as ℝ²—D² convex.)

7. **Annulus:**  
   A = {z ∈ ℂ : 1 ≤ |z| ≤ 2}. Compute π₁(A). (Answer: ≅ ℤ, same as S¹.)

8. **ℝ² \ {0}:**  
   ℝ² \ {0} ≃ S¹ ⇒ π₁(ℝ² \ {0}) ≅ ℤ. Geometric intuition.

9. **ℝ² \ {two points}:**  
   Intuitive argument: π₁(ℝ² \ {p,q}) ≅ ℤ * ℤ (free product). Will prove với Van Kampen.

### Basepoint Independence

10. **Basepoint Change:**  
    Path α from x₀ to x₁. Define β_α([γ]) = [α⁻¹ · γ · α]. Verify β_α homomorphism.

11. **Inverse Isomorphism:**  
    Prove β_{α⁻¹} is inverse của β_α, establishing isomorphism.

12. **Path Dependence:**  
    α, α' two paths from x₀ to x₁. How do β_α và β_{α'} differ? (Differ by inner automorphism induced by loop α' · α⁻¹.)

### Functoriality

13. **Induced Homomorphism:**  
    f: S¹ → S¹, f(z) = z². Compute f_*: π₁(S¹) → π₁(S¹). (Answer: f_*(n) = 2n, multiplication by 2.)

14. **Composition:**  
    f: X → Y, g: Y → Z. Verify (g∘f)_* = g_* ∘ f_* carefully.

15. **Identity:**  
    Verify (id_X)_* = id_{π₁(X)}.

### Homotopy Invariance

16. **Retraction:**  
    r: X → A retraction (r|_A = id). Show r_*: π₁(X) → π₁(A) surjective.

17. **Deformation Retract:**  
    A deformation retract của X. Prove i_*: π₁(A) → π₁(X) isomorphism (i = inclusion).

18. **Homotopy Equivalence:**  
    X ≃ Y. Prove π₁(X) ≅ π₁(Y) using functoriality.

### Advanced

19. **Non-Abelian:**  
    π₁ generally non-abelian. Research example: π₁(figure-eight) = ℤ * ℤ (free product, non-abelian).

20. **Abelianization:**  
    π₁^{ab}(X) = π₁(X)/[π₁(X), π₁(X)] (abelianization). Relate to H₁(X) (will see: π₁^{ab} ≅ H₁).

21. **Higher Homotopy Groups:**  
    π_n(X) = [S^n, X] (homotopy classes của maps Sⁿ → X). π_n abelian for n ≥ 2. Research brief overview.

### Reflection

22. **Why Basepoint?:**  
    Tại sao cần basepoint x₀? (Concatenation requires common starting point. Basepoint provides group structure.)

23. **Geometric Intuition:**  
    Explain π₁(S¹) ≅ ℤ đến non-mathematician. Use winding number / wrapping string analogy.

24. **Applications:**  
    List three applications của π₁ trong different fields. Explain briefly.

25. **History:**  
    Research Poincaré's motivation introducing π₁. Why revolutionary?

---

## 📚 Further Reading

- **Hatcher, Algebraic Topology:** §1.1 (Outstanding geometric treatment)
- **Munkres, Topology:** §52 (Rigorous, clear)
- **Massey, Basic Course:** Chapters 2-3 (Comprehensive)
- **Armstrong, Basic Topology:** Chapter 5 (Accessible)
- **Stillwell, Classical Topology:** Historical perspective

---

## 🎓 Summary

Trong bài học này, chúng ta đã xây dựng **fundamental group $\pi_1(X, x_0)$**—bất biến đại số đầu tiên trong tô-pô học. Định nghĩa của $\pi_1(X, x_0)$ là tập các lớp đồng luân của các vòng lặp tại $x_0$—mỗi phần tử của nhóm đại diện cho một cách "đi vòng quanh" không gian và quay lại điểm xuất phát. Phép toán nhóm được định nghĩa bằng concatenation—$[\gamma] \cdot [\delta] = [\gamma \cdot \delta]$, nghĩa là "thực hiện vòng lặp $\gamma$, sau đó vòng lặp $\delta$". Tất cả các tiên đề nhóm đều được xác minh: phần tử đơn vị là lớp của vòng lặp hằng $[e]$, phần tử nghịch đảo là $[\gamma^{-1}]$ (đường đi ngược), và quan trọng là tính kết hợp được thỏa mãn. Các ví dụ quan trọng bao gồm: $\pi_1(\mathbb{R}^n) = 0$ (nhóm tầm thường vì contractible), $\pi_1(S^1) \cong \mathbb{Z}$ (số nguyên tương ứng với winding number), $\pi_1(S^n) = 0$ cho $n \geq 2$ (simply connected), và $\pi_1(T^2) \cong \mathbb{Z}^2$ (hai vòng lặp độc lập). Tính độc lập với điểm cơ sở cho thấy $\pi_1(X, x_0) \cong \pi_1(X, x_1)$ đối với không gian path-connected—nhóm về cơ bản độc lập với việc chọn điểm cơ sở, thông qua conjugation. Functoriality cho phép mỗi ánh xạ liên tục $f: X \to Y$ cảm ứng một đồng cấu nhóm $f_*: \pi_1(X) \to \pi_1(Y)$. Homotopy invariance đảm bảo rằng nếu $X \simeq Y$, thì $\pi_1(X) \cong \pi_1(Y)$—đây là một tính chất quan trọng cho phép chúng ta tính toán fundamental group bằng cách sử dụng homotopy equivalence.

Điểm chính của bài học là $\pi_1$ là một bất biến đại số được xây dựng từ dữ liệu hình học—chúng ta chuyển đổi các vòng lặp hình học thành các phần tử của một nhóm đại số. Nó có thể tính toán được cho nhiều không gian chuẩn—chúng ta có các kỹ thuật để tính toán fundamental group của các không gian phổ biến. Nó phân biệt các không gian—ví dụ, $S^1 \neq S^2$ vì $\pi_1(S^1) \cong \mathbb{Z}$ trong khi $\pi_1(S^2) = 0$. Nó là functorial và homotopy invariant—hai tính chất quan trọng đảm bảo rằng $\pi_1$ là một bất biến tô-pô thực sự. Nó tạo thành nền tảng cho lý thuyết covering spaces—fundamental group và covering spaces có mối quan hệ sâu sắc.

Trực giác hình học đằng sau $\pi_1$ là các vòng lặp là các cách đi qua không gian—chúng ta bắt đầu tại điểm cơ sở, đi vòng quanh không gian, và quay lại điểm xuất phát. Homotopy là sự biến dạng bảo toàn điểm cơ sở—chúng ta có thể biến dạng một vòng lặp thành vòng lặp khác trong khi giữ điểm cơ sở cố định. Trực giác về winding number cho $S^1$ là chúng ta có thể quấn một vòng dây quanh hình tròn một số lần—số lần quấn này tương ứng với một số nguyên trong $\mathbb{Z}$. Các chiều cao hơn dẫn đến $\pi_1$ đơn giản hơn—$S^n$ là simply connected cho $n \geq 2$, nghĩa là mọi vòng lặp đều có thể co lại về một điểm.

Trong thực tế, chúng ta kiểm tra tính path-connected để đảm bảo tính độc lập với điểm cơ sở—nếu không gian không path-connected, fundamental group có thể phụ thuộc vào thành phần liên thông mà điểm cơ sở nằm trong đó. Chúng ta sử dụng homotopy equivalence để đơn giản hóa các tính toán—nếu chúng ta có thể tìm thấy một không gian đồng luân tương đương đơn giản hơn, chúng ta có thể tính toán fundamental group dễ dàng hơn. Functoriality cho phép so sánh giữa các không gian—mỗi ánh xạ liên tục cảm ứng một đồng cấu nhóm, cho phép chúng ta nghiên cứu mối quan hệ giữa các không gian. $\pi_1$ được bảo toàn bởi deformation retracts—nếu $A$ là deformation retract của $X$, thì $\pi_1(A) \cong \pi_1(X)$.

**Tiếp theo:** Lecture 06.02 về **Computing $\pi_1$**—các kỹ thuật và ví dụ (chứng minh cho $S^1$, surfaces, các ứng dụng)!

---

*"The fundamental group is where algebra meets geometry."* — Poincaré's legacy

🎯 **Master π₁! It's the first step into algebraic topology.** 🎯

---

**Previous:** [Lecture 06.00: Homotopy](/contents/vi/topology-chapter06/06_00_Homotopy_Path_Homotopy/)  
**Next:** [Lecture 06.02: Computing π₁](/contents/vi/topology-chapter06/06_02_Computing_Fundamental_Group/)
