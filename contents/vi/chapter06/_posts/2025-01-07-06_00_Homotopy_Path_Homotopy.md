---
layout: post
title: "Lecture 06.00: Homotopy and Path Homotopy"
lang: vi
lang-ref: lecture-06-00
chapter: 6
lecture: 0
categories: [chapter06]
tags: [homotopy, path-homotopy, homotopy-equivalence, contractible]
description: "Homotopy: continuous deformation, path homotopy, homotopy equivalence, và contractible spaces"
---

**Homotopy and Path Homotopy**

---

## 📖 Tổng quan

Lý thuyết homotopy là trái tim của tô-pô học đại số. Ý tưởng cốt lõi là:

> **Hai đối tượng được coi là "giống nhau" nếu một đối tượng có thể biến dạng liên tục thành đối tượng kia.**

Homotopy chính là sự biến dạng liên tục này. Nó cho phép chúng ta phân loại các không gian "theo homotopy" (một quan hệ yếu hơn homeomorphism), định nghĩa fundamental group $\pi_1$ (các vòng lặp theo homotopy), và chứng minh các định lý mạnh mẽ như định lý điểm cố định Brouwer và định lý quả bóng có lông.

![Homotopy visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4a/Homotopy_Illustration.svg/500px-Homotopy_Illustration.svg.png)  
*Sự biến dạng liên tục (homotopy) - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Homotopy_Illustration.svg)*

Trong bài học này, chúng ta sẽ khám phá các khái niệm cơ bản của homotopy theory. Chúng ta bắt đầu với homotopy của các ánh xạ—một ánh xạ liên tục $F: X \times I \to Y$ kết nối hai ánh xạ $f$ và $g$ một cách liên tục. Chúng ta sẽ nghiên cứu homotopy equivalence—một quan hệ yếu hơn homeomorphism nhưng vẫn bảo toàn nhiều tính chất đại số quan trọng. Chúng ta sẽ khám phá path homotopy—sự biến dạng của các đường đi với các điểm đầu và cuối cố định, đây là nền tảng cho fundamental group. Chúng ta sẽ nghiên cứu các không gian contractible—các không gian đồng luân tương đương với một điểm, và các ví dụ quan trọng như hình tròn, hình cầu, và torus.

Các bài học tiếp theo sẽ khám phá $\pi_1$, covering spaces, và định lý van Kampen—đây là nơi tô-pô học đại số thực sự nở rộ!

---

## 🔄 Homotopy of Maps

### 1. Definition

**Định nghĩa (Homotopy):**  
Cho $f, g: X \to Y$ là các ánh xạ liên tục. **Homotopy** từ $f$ đến $g$ là một ánh xạ liên tục:

$$
F: X \times [0,1] \to Y
$$

sao cho $F(x, 0) = f(x)$ và $F(x, 1) = g(x)$ cho mọi $x \in X$.

**Ký hiệu:** $F: f \simeq g$ (hay $f \sim g$).

Trực giác hình học đằng sau định nghĩa này là chúng ta tưởng tượng một "bộ phim" của sự biến dạng liên tục từ ánh xạ $f$ đến ánh xạ $g$. Tham số $t \in [0,1]$ đóng vai trò như "thời gian" trong bộ phim này—tại thời điểm $t=0$, chúng ta có ánh xạ $f$, và tại thời điểm $t=1$, chúng ta có ánh xạ $g$. Với mỗi giá trị trung gian $t \in (0,1)$, $F(x, t)$ cho chúng ta một ánh xạ trung gian—một "khung hình" trong bộ phim biến dạng. Tính liên tục của $F$ đảm bảo rằng sự biến dạng này diễn ra một cách mượt mà, không có "nhảy vọt" đột ngột. Đây chính là ý tưởng cốt lõi của homotopy: chúng ta có thể biến dạng một ánh xạ thành ánh xạ khác một cách liên tục, giống như cách chúng ta có thể kéo giãn và uốn cong một tấm cao su mà không làm rách nó.

---

**Homotopic:** $f$, $g$ **homotopic** nếu $\exists$ homotopy $F: f \simeq g$.

---

**Định lý:** $\sim$ là quan hệ tương đương.

**Chứng minh:** Chúng ta cần kiểm tra ba tính chất của quan hệ tương đương. Tính phản xạ được thỏa mãn một cách tầm thường—mỗi ánh xạ đồng luân với chính nó thông qua constant homotopy $F(x,t) = f(x)$, nghĩa là chúng ta không thay đổi ánh xạ trong suốt quá trình biến dạng. Tính đối xứng được thiết lập bằng cách đảo ngược thời gian—nếu $F: f \simeq g$ là một homotopy từ $f$ đến $g$, thì $G(x,t) = F(x, 1-t)$ là một homotopy từ $g$ đến $f$, đơn giản là chạy bộ phim ngược lại. Tính bắc cầu được chứng minh bằng cách nối các homotopies—nếu chúng ta có $F: f \simeq g$ và $G: g \simeq h$, chúng ta có thể tạo ra một homotopy từ $f$ đến $h$ bằng cách chạy $F$ trong nửa đầu của khoảng thời gian và $G$ trong nửa sau, với một reparametrization thích hợp để đảm bảo tính liên tục tại điểm nối.

---

### 2. Examples

**Ví dụ 1: Ánh xạ đồng nhất đồng luân với chính nó**

Ví dụ đơn giản nhất của homotopy là trường hợp một ánh xạ đồng luân với chính nó. Cho $f = \text{id}_X$ là ánh xạ đồng nhất trên $X$. Chúng ta có thể định nghĩa một homotopy tầm thường bằng cách đặt $F(x,t) = x$ cho mọi $t \in [0,1]$. Điều này có nghĩa là chúng ta không thay đổi ánh xạ trong suốt quá trình biến dạng—mỗi điểm được ánh xạ đến chính nó tại mọi thời điểm. Đây là một ví dụ quan trọng vì nó cho thấy rằng mỗi ánh xạ đều đồng luân với chính nó, đảm bảo tính phản xạ của quan hệ homotopy.

**Ví dụ 2: Các ánh xạ hằng đồng luân**

Một ví dụ thú vị hơn là trường hợp các ánh xạ hằng. Giả sử $X$ là một không gian liên thông và $f, g: X \to Y$ là các ánh xạ hằng, nghĩa là $f(x) = y_0$ và $g(x) = y_1$ cho mọi $x \in X$, trong đó $y_0$ và $y_1$ là hai điểm cố định trong $Y$. Nếu $Y$ là path-connected, thì tồn tại một đường đi liên tục $\alpha: [0,1] \to Y$ từ $y_0$ đến $y_1$. Chúng ta có thể định nghĩa một homotopy $F: X \times [0,1] \to Y$ bằng cách đặt $F(x,t) = \alpha(t)$ cho mọi $x \in X$. Điều này có nghĩa là tại mỗi thời điểm $t$, tất cả các điểm của $X$ đều được ánh xạ đến cùng một điểm $\alpha(t)$ trên đường đi từ $y_0$ đến $y_1$. Kết quả là $f \simeq g$, cho thấy rằng trong một không gian path-connected, tất cả các ánh xạ hằng đều đồng luân với nhau.

**Ví dụ 3: Ánh xạ đối cực trên $S^1$**

Một ví dụ quan trọng về hai ánh xạ không đồng luân là ánh xạ đối cực trên hình tròn. Cho $f: S^1 \to S^1$ được định nghĩa bởi $f(z) = -z$, đây là ánh xạ ánh xạ mỗi điểm trên hình tròn đến điểm đối diện của nó. Cho $\text{id}: S^1 \to S^1$ là ánh xạ đồng nhất. Mặc dù cả hai ánh xạ đều liên tục, nhưng chúng không đồng luân với nhau. Lý do sâu xa là ánh xạ đối cực "quấn" hình tròn một cách khác với ánh xạ đồng nhất—nó có winding number khác nhau. Nếu chúng ta cố gắng biến dạng liên tục ánh xạ đồng nhất thành ánh xạ đối cực, chúng ta sẽ phải "xé" hình tròn tại một số điểm, điều này vi phạm tính liên tục. Một cách chính thức hơn, nếu $f \simeq \text{id}$, thì chúng sẽ cảm ứng cùng một đồng cấu trên fundamental group $\pi_1(S^1) \cong \mathbb{Z}$, nhưng ánh xạ đối cực cảm ứng phép nhân với $-1$, trong khi ánh xạ đồng nhất cảm ứng phép nhân với $1$. Điều này cho thấy rằng homotopy không chỉ là một khái niệm hình học mà còn có ý nghĩa đại số sâu sắc.

---

## 🏠 Homotopy Equivalence

### 1. Definition

**Định nghĩa (Homotopy Equivalence):**  
Cho $f: X \to Y$ là một ánh xạ liên tục. $f$ là **homotopy equivalence** nếu $\exists g: Y \to X$:
- $g \circ f \simeq \text{id}_X$
- $f \circ g \simeq \text{id}_Y$

**$g$ được gọi là homotopy inverse của $f$.**

**Các không gian $X$, $Y$ được gọi là **homotopy equivalent:** $X \simeq Y$.

---

**Định lý:** $\simeq$ là quan hệ tương đương trên các không gian.

---

### 2. Examples

**Ví dụ 1: Các không gian Contractible**

**Định nghĩa:** Một không gian $X$ được gọi là **contractible** nếu $X \simeq \{pt\}$, nghĩa là $X$ đồng luân tương đương với một điểm.

Điều này tương đương với việc ánh xạ đồng nhất $\text{id}_X$ đồng luân với một ánh xạ hằng. Trực giác hình học là chúng ta có thể "co" toàn bộ không gian về một điểm một cách liên tục, giống như cách một con sứa co lại khi bị chạm vào. Đây là một tính chất hình học mạnh mẽ—một không gian contractible không có "lỗ" hoặc "vòng lặp" nào mà không thể co lại được.

Các ví dụ quan trọng của không gian contractible bao gồm $\mathbb{R}^n$—chúng ta có thể co toàn bộ không gian Euclid về gốc tọa độ bằng cách nhân mỗi điểm với một hệ số $(1-t)$ khi $t$ chạy từ $0$ đến $1$. Tương tự, đĩa đóng $D^n$ là contractible vì chúng ta có thể co nó về tâm của nó. Cone $CX$ của một không gian $X$ cũng là contractible—cone về bản chất là một cách xây dựng một không gian contractible từ một không gian bất kỳ. Các tập star-shaped (các tập có một điểm sao cho mọi điểm khác đều có thể được nối với điểm đó bằng một đoạn thẳng nằm trong tập) cũng là contractible vì chúng ta có thể co chúng về điểm sao.

Ngược lại, các không gian như $S^1$ (hình tròn), $S^n$ (hình cầu), và $T^2$ (torus) không phải là contractible. Lý do là chúng có "lỗ" hoặc "vòng lặp" không thể co lại được. Ví dụ, trên hình tròn $S^1$, bất kỳ vòng lặp nào đi một vòng quanh hình tròn đều không thể co lại về một điểm mà không "xé" hình tròn. Điều này được phản ánh trong fundamental group không tầm thường của chúng—$\pi_1(S^1) \cong \mathbb{Z}$ và $\pi_1(T^2) \cong \mathbb{Z}^2$.

---

**Ví dụ 2: $D^2 \simeq \{pt\}$**

Một ví dụ cụ thể và trực quan của không gian contractible là đĩa đóng $D^2$. Chúng ta có thể chứng minh rằng $D^2$ đồng luân tương đương với một điểm bằng cách xây dựng một homotopy rõ ràng. Đặt $F: D^2 \times I \to D^2$ được định nghĩa bởi $F(x,t) = (1-t)x$. Tại thời điểm $t=0$, chúng ta có $F(x,0) = x$, nghĩa là ánh xạ đồng nhất. Tại thời điểm $t=1$, chúng ta có $F(x,1) = 0$, nghĩa là ánh xạ hằng ánh xạ mọi điểm đến gốc tọa độ. Quá trình này có thể được hình dung như việc "thu nhỏ" đĩa về tâm của nó một cách liên tục—mỗi điểm di chuyển dọc theo đường thẳng từ vị trí ban đầu của nó đến gốc tọa độ với tốc độ tỷ lệ với khoảng cách của nó đến gốc. Đây là một ví dụ đẹp về cách một không gian có thể được co lại về một điểm mà không làm thay đổi topology cơ bản của nó.

**Ví dụ 3: $\mathbb{R}^n \setminus \{0\} \simeq S^{n-1}$**

Một ví dụ quan trọng khác là mối quan hệ giữa không gian $\mathbb{R}^n \setminus \{0\}$ (không gian Euclid trừ đi gốc tọa độ) và hình cầu $S^{n-1}$. Mặc dù hai không gian này không homeomorphic (một không gian là không compact và một không gian là compact), chúng đồng luân tương đương với nhau. Cách xây dựng homotopy equivalence này thông qua khái niệm deformation retract. Chúng ta định nghĩa một retraction $r: \mathbb{R}^n \setminus \{0\} \to S^{n-1}$ bằng cách đặt $r(x) = x/||x||$, nghĩa là chúng ta chiếu mỗi điểm về hình cầu đơn vị bằng cách chuẩn hóa vector của nó. Cho $i: S^{n-1} \to \mathbb{R}^n \setminus \{0\}$ là ánh xạ bao hàm. Khi đó hợp thành $r \circ i$ là ánh xạ đồng nhất trên $S^{n-1}$, và hợp thành $i \circ r$ đồng luân với ánh xạ đồng nhất trên $\mathbb{R}^n \setminus \{0\}$ thông qua homotopy $F(x,t) = (1-t)x + t(x/||x||)$, nghĩa là chúng ta di chuyển mỗi điểm từ vị trí ban đầu của nó đến hình chiếu của nó trên hình cầu. Trực giác hình học là chúng ta có thể "kéo" tất cả các điểm trong $\mathbb{R}^n \setminus \{0\}$ về hình cầu đơn vị một cách liên tục mà không làm thay đổi topology cơ bản của không gian.

---

### 3. Homotopy Invariants

**Homotopy invariant:** Một tính chất được gọi là **homotopy invariant** nếu nó được bảo toàn bởi homotopy equivalence. Điều này có nghĩa là nếu hai không gian đồng luân tương đương, thì chúng phải có cùng tính chất đó. Đây là một khái niệm quan trọng vì nó cho phép chúng ta phân loại các không gian theo homotopy type thay vì chỉ theo homeomorphism type.

Các ví dụ quan trọng của homotopy invariants bao gồm fundamental group $\pi_1(X)$—nhóm các lớp đồng luân của các vòng lặp, homology groups $H_n(X)$—các nhóm đo lường "lỗ" trong các chiều khác nhau, cohomology groups $H^n(X)$—các nhóm đối ngẫu của homology groups, và homotopy groups $\pi_n(X)$—các nhóm tổng quát hóa của fundamental group cho các chiều cao hơn. Tất cả các bất biến này đều được bảo toàn bởi homotopy equivalence, nghĩa là nếu $X \simeq Y$, thì $\pi_1(X) \cong \pi_1(Y)$, $H_n(X) \cong H_n(Y)$, và tương tự cho các bất biến khác. Đây là lý do tại sao homotopy theory lại mạnh mẽ đến vậy—nó cho phép chúng ta nghiên cứu các không gian thông qua các bất biến đại số mà không cần biết chi tiết về cấu trúc hình học của chúng.

Tuy nhiên, không phải tất cả các tính chất đều là homotopy invariants. Ví dụ, compactness không phải là homotopy invariant—$\mathbb{R}^n \simeq \{pt\}$ (một điểm là compact), nhưng $\mathbb{R}^n$ không compact. Tính chất Hausdorff cũng không phải là homotopy invariant. Connectedness thường được bảo toàn bởi homotopy equivalence, nhưng có những sắc thái phức tạp khi làm việc với các không gian không path-connected. Điều này cho thấy rằng homotopy equivalence là một quan hệ yếu hơn homeomorphism—nó bảo toàn các tính chất đại số nhưng không nhất thiết bảo toàn các tính chất tô-pô như compactness.

---

## 🛤️ Paths và Loops

### 1. Paths

**Định nghĩa (Path):**  
Một **path** trong không gian $X$ từ điểm $x_0$ đến điểm $x_1$ là một ánh xạ liên tục:

$$
\gamma: [0,1] \to X
$$

thỏa mãn $\gamma(0) = x_0$ và $\gamma(1) = x_1$. Trực giác hình học là một path là một "đường đi liên tục" từ điểm này đến điểm khác trong không gian—chúng ta có thể tưởng tượng một con kiến đi từ $x_0$ đến $x_1$ dọc theo đường đi $\gamma$. Tham số $t \in [0,1]$ đại diện cho "thời gian" trong hành trình này—tại thời điểm $t=0$, con kiến ở điểm xuất phát $x_0$, và tại thời điểm $t=1$, con kiến đến điểm đích $x_1$.

Một **loop** (hay **based loop**) là một path đặc biệt trong đó điểm xuất phát và điểm đích trùng nhau, nghĩa là $\gamma(0) = \gamma(1) = x_0$ cho một điểm cố định $x_0$ được gọi là **basepoint**. Trực giác hình học là một loop là một đường đi khép kín—con kiến bắt đầu tại $x_0$, đi vòng quanh không gian, và quay lại điểm xuất phát. Các loops là đối tượng cơ bản trong nghiên cứu fundamental group vì chúng nắm bắt cách không gian có thể được "quấn" hoặc "vòng lặp" xung quanh các điểm cố định.

---

**Concatenation:**  
Khi chúng ta có hai paths $\gamma$ và $\delta$ với điểm cuối của $\gamma$ trùng với điểm đầu của $\delta$, nghĩa là $\gamma(1) = \delta(0)$, chúng ta có thể "nối" chúng lại với nhau để tạo thành một path mới. **Product path** $\gamma \cdot \delta$ được định nghĩa bằng cách đi qua $\gamma$ với tốc độ gấp đôi trong nửa đầu của khoảng thời gian, sau đó đi qua $\delta$ với tốc độ gấp đôi trong nửa sau:

$$
(\gamma \cdot \delta)(t) = \begin{cases}
\gamma(2t) & 0 \leq t \leq 1/2 \\
\delta(2t-1) & 1/2 \leq t \leq 1
\end{cases}
$$

Trực giác hình học là chúng ta đi qua $\gamma$ rồi tiếp tục đi qua $\delta$—giống như cách chúng ta đi từ điểm A đến điểm B, rồi từ điểm B đến điểm C. Reparametrization (thay đổi tốc độ) là cần thiết để đảm bảo rằng path mới vẫn được định nghĩa trên khoảng $[0,1]$. Điều này cho phép chúng ta định nghĩa một phép toán trên các paths, và khi chúng ta xét các lớp đồng luân của các loops, phép toán này sẽ trở thành phép nhóm trong fundamental group.

**Inverse path:** Cho một path $\gamma$ từ $x_0$ đến $x_1$, chúng ta có thể định nghĩa **inverse path** $\gamma^{-1}$ bằng cách đảo ngược hướng: $\gamma^{-1}(t) = \gamma(1-t)$. Điều này có nghĩa là chúng ta đi ngược lại đường đi ban đầu—nếu $\gamma$ đi từ $x_0$ đến $x_1$, thì $\gamma^{-1}$ đi từ $x_1$ đến $x_0$ dọc theo cùng một đường đi nhưng theo hướng ngược lại. Trực giác hình học là chúng ta quay lại con đường mà chúng ta đã đi. Khi chúng ta xét các lớp đồng luân của các loops, inverse path sẽ trở thành phần tử nghịch đảo trong fundamental group.

---

### 2. Path Homotopy

**Định nghĩa (Path Homotopy):**  
Cho $\gamma$, $\delta$: $[0,1] \to X$ là các paths với cùng các điểm đầu và cuối, nghĩa là $\gamma(0) = \delta(0) = x_0$ và $\gamma(1) = \delta(1) = x_1$. Một **path homotopy** $F: \gamma \simeq \delta$ (rel endpoints) là một ánh xạ liên tục:

$$
F: [0,1] \times [0,1] \to X
$$

thỏa mãn $F(s,0) = \gamma(s)$ và $F(s,1) = \delta(s)$ cho mọi $s \in [0,1]$, và quan trọng là $F(0,t) = x_0$ và $F(1,t) = x_1$ cho mọi $t \in [0,1]$, nghĩa là các điểm đầu và cuối được giữ cố định trong suốt quá trình biến dạng.

**Ký hiệu:** $\gamma \simeq_p \delta$ (path homotopic).

Trực giác hình học đằng sau path homotopy là chúng ta có thể biến dạng liên tục đường đi $\gamma$ thành đường đi $\delta$ trong khi giữ các điểm đầu và cuối được "dán chặt" tại vị trí của chúng. Hãy tưởng tượng một sợi dây được căng giữa hai điểm cố định—chúng ta có thể uốn cong và kéo giãn sợi dây này một cách liên tục, nhưng chúng ta không thể di chuyển hai đầu của nó. Điều kiện giữ các điểm đầu và cuối cố định là rất quan trọng vì nó đảm bảo rằng khi chúng ta xét các lớp đồng luân của các loops, chúng ta có thể định nghĩa một phép toán nhóm một cách nhất quán. Nếu chúng ta cho phép các điểm đầu và cuối di chuyển, thì phép toán concatenation sẽ không được định nghĩa tốt.

![Path homotopy](https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Path_homotopy.svg/400px-Path_homotopy.svg.png)  
*Path homotopy with fixed endpoints - Nguồn concept*

---

**Định lý:** $\simeq_p$ là quan hệ tương đương.

---

### 3. Homotopy Classes

**$[\gamma]$ = homotopy class của path $\gamma$.**

**Tập các based loops tại $x_0$:**

$$
\Omega(X, x_0) = \{\text{loops } \gamma: [0,1] \to X, \gamma(0)=\gamma(1)=x_0\}
$$

**Quotient:** $\Omega(X,x_0) / \simeq_p$ = các homotopy classes.

**Đây sẽ trở thành fundamental group $\pi_1(X, x_0)$!** (Bài học tiếp theo.)

---

## 🎯 Key Theorems

### 1. Homotopy Extension Property (HEP)

**Định lý:**  
Cho $(X, A)$ là một cặp "nice" (ví dụ, CW pair). Cho trước:
- $f: X \to Y$
- $F: A \times I \to Y$ là homotopy bắt đầu tại $f|_A$

Khi đó $\exists$ extension $\tilde{F}: X \times I \to Y$ mở rộng $F$.

**Application:** Construct homotopies.

---

### 2. Deformation Retract

**Định nghĩa (Deformation Retract):**  
Cho $A \subseteq X$. $A$ là **deformation retract** của $X$ nếu $\exists r: X \to A$:
- $r|_A = \text{id}_A$ (retraction)
- $ir \simeq \text{id}_X$ ($i: A \to X$ là inclusion, homotopy rel $A$)

**Ví dụ:** $S^{n-1}$ là deformation retract của $\mathbb{R}^n \setminus \{0\}$. ✓

---

**Định lý:** Nếu $A$ là deformation retract của $X$, thì $A \simeq X$.

---

### 3. Contractibility

**Định lý:**  
Nếu $X$ contractible, thì $X$ path-connected, $\pi_1(X) = \{e\}$, $H_n(X) = 0$ ($n \geq 1$).

**Điều ngược lại sai:** (Whitehead manifold counterexample—nâng cao.)

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Founded algebraic topology, introduced notion of continuous deformation*

2. **L.E.J. Brouwer** - *"Über Abbildung von Mannigfaltigkeiten"* (1911)  
   *Fixed point theorem using homotopy theory*

3. **Heinz Hopf** - *"Über die Abbildungen der dreidimensionalen Sphäre"* (1931)  
   *Hopf fibration, foundational homotopy theory*

4. **Witold Hurewicz** - *"Beiträge zur Topologie der Deformationen"* (1935-36)  
   *Systematized homotopy theory*

### Textbooks

5. **James R. Munkres** - *Topology*, 2nd Ed., **§51-52: Homotopy**

6. **Allen Hatcher** - *Algebraic Topology*, **§0-1: Homotopy and Fundamental Group**  
   *Modern comprehensive treatment với geometric intuition*

7. **Edwin Spanier** - *Algebraic Topology*, **Chapter 1: Homotopy Theory**

8. **Glen E. Bredon** - *Topology and Geometry*, **Chapter I**

9. **Tammo tom Dieck** - *Algebraic Topology*, **Chapter 2**

---

## 🔗 Applications and Connections

### Topology - Classification

Homotopy type là một cách phân loại các không gian tô-pô dựa trên homotopy equivalence thay vì homeomorphism. Đây là một quan hệ yếu hơn homeomorphism nhưng lại nắm bắt được các tính chất đại số quan trọng của không gian. Ví dụ, $\mathbb{R}^n$ đồng luân tương đương với một điểm mặc dù chúng không homeomorphic—điều này cho thấy rằng từ quan điểm của homotopy theory, không gian Euclid không có "lỗ" hoặc "vòng lặp" nào. Ngược lại, $S^1$ không đồng luân tương đương với một điểm vì nó có một vòng lặp không thể co lại được, được phản ánh trong fundamental group không tầm thường $\pi_1(S^1) \cong \mathbb{Z}$.

### Analysis - Fixed Point Theorems

Định lý điểm cố định Brouwer là một trong những ứng dụng nổi tiếng nhất của homotopy theory trong giải tích. Định lý phát biểu rằng mọi ánh xạ liên tục $f: D^n \to D^n$ từ đĩa đóng $n$-chiều vào chính nó đều có ít nhất một điểm cố định. Chứng minh của định lý này sử dụng homotopy theory một cách tinh tế—nếu $f$ không có điểm cố định, thì chúng ta có thể xây dựng một retraction từ $S^{n-1}$ (biên của đĩa) vào $D^n$, điều này mâu thuẫn với một kết quả cơ bản trong homotopy theory rằng không thể có một retraction như vậy. Đây là một ví dụ tuyệt vời về cách homotopy theory cung cấp các công cụ mạnh mẽ để chứng minh các định lý trong các lĩnh vực khác của toán học.

### Complex Analysis - Winding Numbers

Trong giải tích phức, tích phân đường $\int_\gamma f(z)dz$ của một hàm holomorphic $f$ chỉ phụ thuộc vào homotopy class của đường đi $\gamma$, không phụ thuộc vào đường đi cụ thể. Điều này có nghĩa là nếu chúng ta biến dạng liên tục đường đi $\gamma$ thành đường đi $\delta$ (với các điểm đầu và cuối cố định), thì tích phân sẽ không thay đổi. Đây là một kết quả sâu sắc kết nối giải tích phức với topology—winding number của một đường đi quanh một điểm là một bất biến homotopy, và nó đóng vai trò quan trọng trong định lý thặng dư Cauchy.

### Robotics - Configuration Spaces

Trong robotics, không gian cấu hình của một robot là không gian của tất cả các vị trí và hướng có thể của robot. Mỗi điểm trong không gian cấu hình đại diện cho một "trạng thái" của robot. Khi robot cần di chuyển từ một cấu hình này sang cấu hình khác trong khi tránh các chướng ngại vật, các đường đi hợp lệ tương ứng với các homotopy classes của paths trong không gian cấu hình. Các homotopy classes khác nhau đại diện cho các cách "về mặt tô-pô khác nhau" để robot có thể di chuyển—ví dụ, đi bên trái hoặc bên phải của một chướng ngại vật là hai homotopy classes khác nhau. Hiểu được cấu trúc homotopy của không gian cấu hình giúp các nhà robotics thiết kế các thuật toán lập kế hoạch đường đi hiệu quả.

### Physics - Gauge Theory

Trong vật lý, gauge theory là một khung lý thuyết quan trọng để mô tả các tương tác cơ bản trong tự nhiên. Các gauge transformations là các phép biến đổi của các connections trên principal bundles, và chúng có thể được hiểu như các homotopy equivalences. Các instantons—các nghiệm của phương trình Yang-Mills—tương ứng với các homotopy classes của gauge fields. Điều này cho thấy rằng topology đóng vai trò quan trọng trong việc phân loại các trạng thái vật lý, và homotopy theory cung cấp các công cụ để nghiên cứu các cấu trúc này.

### Data Science - Topological Data Analysis

Topological Data Analysis (TDA) là một lĩnh vực mới nổi sử dụng các công cụ từ topology để phân tích dữ liệu. Persistent homology là một kỹ thuật quan trọng trong TDA—nó nghiên cứu "hình dạng" của dữ liệu thông qua các homology groups, là các homotopy invariants. Các homotopy types khác nhau tương ứng với các cấu trúc dữ liệu khác nhau—ví dụ, một tập dữ liệu có thể có các "lỗ" hoặc "vòng lặp" mà persistent homology có thể phát hiện. Điều này cho phép chúng ta phân loại và so sánh các tập dữ liệu dựa trên cấu trúc tô-pô của chúng, không chỉ dựa trên các tính chất metric hoặc thống kê.

---

## 🧩 Exercises

### Homotopy Definition

1. **Verify Equivalence Relation:**  
   Prove carefully that homotopy ~ is equivalence relation: reflexive, symmetric, transitive.

2. **Constant Homotopy:**  
   f: X → Y. Show F(x,t) = f(x) is homotopy f ≃ f.

3. **Explicit Homotopy:**  
   ℝ² contractible. Write explicit F: [0,1] × ℝ² → ℝ² với F₀ = id, F₁ = const.

### Homotopy Equivalence

4. **Verify Homotopy Equivalence:**  
   D² và {pt} homotopy equivalent. Write explicit maps f, g và homotopies.

5. **ℝⁿ \ {0} ≃ S^(n-1):**  
   Construct explicit homotopy equivalence. Verify r ∘ i = id và i ∘ r ≃ id.

6. **Cylinder:**  
   S¹ × [0,1] homotopy equivalent với S¹. Find explicit homotopy equivalence.

### Contractible Spaces

7. **Star-Shaped:**  
   X ⊆ ℝⁿ star-shaped (∃x₀: line segment [x₀,x] ⊆ X ∀x) ⇒ X contractible. Prove.

8. **Cone:**  
   Cone CX = (X × [0,1])/(X × {0}) contractible. Prove.

9. **KHÔNG Contractible:**  
   $S^1$ không contractible. Lập luận trực quan (chứng minh chính thức yêu cầu $\pi_1(S^1) \cong \mathbb{Z}$).

### Path Homotopy

10. **Path Concatenation:**  
    Cho $\gamma$, $\delta$ là các paths. Xác minh $(\gamma \cdot \delta)(t)$ well-defined và continuous.

11. **Inverse Path:**  
    Cho $\gamma$ là path từ $x_0$ đến $x_1$. Chứng minh $\gamma \cdot \gamma^{-1} \simeq_p$ constant path tại $x_0$.

12. **Associativity:**  
    Chứng minh $(\gamma \cdot \delta) \cdot \varepsilon \simeq_p \gamma \cdot (\delta \cdot \varepsilon)$ (associative up to homotopy).

### Deformation Retracts

13. **$S^{n-1} \subseteq \mathbb{R}^n \setminus \{0\}$:**  
    Chứng minh $S^{n-1}$ là deformation retract của $\mathbb{R}^n \setminus \{0\}$. Retraction rõ ràng $r(x) = x/||x||$.

14. **Properties:**  
    Cho $A$ là deformation retract của $X$. Chứng minh:  
    a) $A \simeq X$  
    b) $i_*: \pi_1(A) \to \pi_1(X)$ là isomorphism (sẽ chứng minh sau)

15. **Strong Deformation Retract:**  
    $r: X \to A$ là strong deformation retract nếu homotopy $F: \text{id}_X \simeq ir$ cố định $A$ từng điểm. Ví dụ: $S^1 \subseteq \mathbb{R}^2 \setminus \{0\}$.

### Homotopy Extension

16. **HEP Example:**  
    $(D^2, S^1)$ có HEP. Cho trước $f: D^2 \to Y$, $F: S^1 \times I \to Y$. Xây dựng $\tilde{F}: D^2 \times I \to Y$ mở rộng $F$.

17. **Applications:**  
    Why HEP important cho proving theorems về homotopy?

### Advanced

18. **Homotopy Equivalence KHÔNG phải Homeomorphism:**  
    Tìm $X$, $Y$: $X \simeq Y$ nhưng $X \not\cong Y$ (không homeomorphic).  
    Gợi ý: $\mathbb{R} \simeq$ điểm nhưng $\mathbb{R}$ không compact.

19. **Whitehead Theorem Preview:**  
    Cho $f: X \to Y$ là ánh xạ giữa các CW complexes. Nếu $f$ cảm ứng isomorphism $\pi_n$ $\forall n$, thì $f$ là homotopy equivalence.  
    Nghiên cứu phát biểu này.

20. **Applications:**  
    Give three examples applications của homotopy theory trong different fields (physics, CS, data science).

### Reflection

21. **Homotopy vs Homeomorphism:**  
    So sánh: homeomorphism preserves gì? Homotopy equivalence preserves gì?  
    Which coarser?

22. **Intuition:**  
    Explain homotopy concept đến người không học topology. Use rubber sheet / deformation analogy.

23. **Why Path Homotopy?:**  
    Tại sao fix endpoints khi define path homotopy? Ý nghĩa cho fundamental group?

---

## 📚 Further Reading

- **Hatcher, Algebraic Topology:** §0-1 (Geometric intuition excellent)
- **Munkres, Topology:** §51-52 (Rigorous treatment)
- **Spanier, Algebraic Topology:** Chapter 1 (Comprehensive)
- **Bredon, Topology and Geometry:** Chapter I (Modern perspective)
- **May, Concise Course:** Homotopy theory foundations

---

## 🎓 Summary

Trong bài học này, chúng ta đã khám phá các nền tảng của **homotopy theory**—một trong những công cụ mạnh mẽ nhất trong tô-pô học đại số. Homotopy là một ánh xạ liên tục $F: X \times I \to Y$ kết nối hai ánh xạ $f$ và $g$ một cách liên tục—nó cho phép chúng ta biến dạng một ánh xạ thành ánh xạ khác. Homotopy equivalence là một quan hệ giữa các không gian—một ánh xạ $f: X \to Y$ là homotopy equivalence nếu tồn tại một ánh xạ ngược $g: Y \to X$ sao cho các hợp thành là đồng luân với ánh xạ đồng nhất. Một không gian contractible là một không gian đồng luân tương đương với một điểm—$X \simeq \{pt\}$, tương đương với việc ánh xạ đồng nhất đồng luân với một ánh xạ hằng. Path homotopy là sự biến dạng của các đường đi với các điểm đầu và cuối cố định—đây là nền tảng cho fundamental group. Deformation retract là một không gian con $A \subseteq X$ mà $X$ có thể co lại về $A$ thông qua một homotopy—đây là một cách tự nhiên để xây dựng các homotopy equivalences. Các ví dụ quan trọng bao gồm: $\mathbb{R}^n$ là contractible, $\mathbb{R}^n \setminus \{0\} \simeq S^{n-1}$, và $D^2 \simeq$ điểm.

Điểm chính của bài học là homotopy là sự biến dạng liên tục—một quan hệ yếu hơn homeomorphism nhưng vẫn bảo toàn nhiều tính chất đại số quan trọng. Homotopy equivalence bảo toàn các bất biến đại số như $\pi_1$ và $H_n$—đây là lý do tại sao homotopy theory lại mạnh mẽ đến vậy. Path homotopy là nền tảng cho fundamental group—các lớp đồng luân của các đường đi tạo thành các phần tử của fundamental group. Các không gian contractible là đơn giản nhất về mặt đại số—chúng có fundamental group tầm thường và homology groups bằng không. Deformation retracts bảo toàn homotopy type—nếu $A$ là deformation retract của $X$, thì $A \simeq X$.

Trực giác hình học đằng sau homotopy là hãy tưởng tượng sự biến dạng của một tấm cao su—chúng ta có thể kéo giãn, uốn cong, và biến dạng không gian một cách liên tục. Homotopy giống như một bộ phim từ $f$ đến $g$—mỗi khung hình là một ánh xạ trung gian. Path homotopy là biến dạng đường đi trong khi giữ các điểm đầu và cuối được dán chặt—điều này đảm bảo rằng các đường đi vẫn có cùng điểm đầu và cuối. Contractible có nghĩa là chúng ta có thể co không gian về một điểm—đây là một tính chất hình học mạnh mẽ.

Trong thực tế, chúng ta kiểm tra homotopy equivalence bằng cách tìm các ánh xạ rõ ràng và các homotopies—chúng ta cần chứng minh rằng các hợp thành là đồng luân với ánh xạ đồng nhất. Deformation retracts đơn giản hóa các tính toán—nếu chúng ta có thể tìm thấy một deformation retract đơn giản hơn, chúng ta có thể tính toán các bất biến đại số dễ dàng hơn. Các lớp path homotopy là các phần tử của $\pi_1$—chúng ta sẽ thấy điều này trong bài học tiếp theo. Các bất biến homotopy phân biệt các không gian—nếu hai không gian có các bất biến homotopy khác nhau, chúng không thể đồng luân tương đương.

**Tiếp theo:** Lecture 06.01 về **Fundamental Group $\pi_1(X, x_0)$**—bất biến đại số đầu tiên từ homotopy theory! Chúng ta sẽ gán một nhóm cho mỗi không gian có điểm cơ sở, nắm bắt các vòng lặp và các "lỗ".

---

*"Homotopy is the art of continuous deformation."* — Algebraic topologist's motto

🎯 **Master homotopy! It's the gateway to algebraic topology.** 🎯

---

**Previous Chapter:** [Chapter 05: Quotient Spaces](/contents/vi/topology-chapter05/)  
**Next:** [Lecture 06.01: Fundamental Group](/contents/vi/topology-chapter06/06_01_Fundamental_Group/)

