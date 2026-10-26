---
layout: post
title: "Lecture 06.02: Computing π₁ - Examples and Techniques"
lang: vi
lang-ref: lecture-06-02
chapter: 6
lecture: 2
categories: [chapter06]
tags: [π1-computations, circle, sphere, torus, simply-connected]
description: "Computing fundamental groups: S¹, S^n, T², surfaces, techniques và detailed proofs"
---

**Examples, Techniques, and Detailed Computations**

---

## 📖 Tổng quan

Trong bài học trước, chúng ta đã định nghĩa fundamental group $\pi_1(X, x_0)$. Giờ đây, câu hỏi tự nhiên nảy sinh:

> **Làm sao TÍNH TOÁN $\pi_1(X)$ cho các không gian cụ thể?**

Đây không phải là một câu hỏi tầm thường! Việc tính toán $\pi_1$ yêu cầu sự kết hợp của trực giác hình học để hình dung các loops, các kỹ thuật đại số từ lý thuyết nhóm, các định lý mạnh mẽ như covering spaces và Van Kampen, và các chứng minh cẩn thận để xác minh các homotopies.

Trong bài học này, chúng ta sẽ khám phá các ví dụ cụ thể và các kỹ thuật tính toán fundamental group. Chúng ta sẽ nghiên cứu chi tiết chứng minh rằng $\pi_1(S^1) = \mathbb{Z}$ thông qua covering space—đây là một trong những ví dụ quan trọng nhất trong tô-pô học đại số. Chúng ta sẽ chứng minh rằng $\pi_1(S^n) = 0$ cho $n \geq 2$—các hình cầu cao hơn là simply connected. Chúng ta sẽ tính toán $\pi_1(T^2) = \mathbb{Z}^2$ bằng cách sử dụng product theorem. Chúng ta sẽ khám phá fundamental groups của các surfaces với genus $g$. Chúng ta sẽ học các kỹ thuật như covering spaces, homotopy equivalence, và một preview của định lý Van Kampen. Cuối cùng, chúng ta sẽ xem xét các ứng dụng như $\mathbb{R}^n \setminus \{\text{points}\}$ và projective spaces.

![Fundamental group computations](https://upload.wikimedia.org/wikipedia/commons/thumb/9/97/Torus_cycles.svg/400px-Torus_cycles.svg.png)  
*Các generators của fundamental group trên torus - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus_cycles.svg)*

Tại sao những ví dụ và kỹ thuật này lại quan trọng đến vậy? Thứ nhất, chúng là các ví dụ chuẩn—các building blocks cho sự hiểu biết của chúng ta về fundamental group. Thứ hai, các kỹ thuật có thể chuyển giao—các phương pháp này hoạt động rộng rãi cho nhiều loại không gian khác nhau. Thứ ba, chúng phân biệt các không gian—chúng ta có thể chứng minh các không gian không homeomorphic bằng cách tính toán fundamental groups của chúng. Cuối cùng, các ứng dụng rộng rãi trong robotics, vật lý, và giải tích phức.

---

## 🔵 π₁(S¹) = ℤ: The Circle

### 1. Statement và Intuition

**Theorem:** π₁(S¹, 1) ≅ ℤ.

Trực giác hình học là các loops trên hình tròn được phân loại bởi **winding number**—số lần chúng ta quấn quanh hình tròn. Một loop không quấn quanh hình tròn có winding number $0$. Một loop quấn một lần theo chiều ngược chiều kim đồng hồ có winding number $1$. Một loop quấn hai lần có winding number $2$. Một loop quấn một lần theo chiều kim đồng hồ có winding number $-1$. Và cứ thế tiếp tục.

Điều quan trọng là **winding number $n \in \mathbb{Z}$ hoàn toàn xác định homotopy class!** Điều này có nghĩa là nếu hai loops có cùng winding number, chúng đồng luân với nhau, và nếu chúng có winding numbers khác nhau, chúng không đồng luân với nhau. Đây là một kết quả sâu sắc cho thấy rằng fundamental group của hình tròn là $\mathbb{Z}$.

**Phép toán nhóm:** Concatenate loops tương ứng với cộng winding numbers. Nếu chúng ta có một loop với winding number $n$ và một loop với winding number $m$, thì loop được tạo ra bằng cách nối chúng lại với nhau có winding number $n + m$. Điều này chính xác là cách phép cộng hoạt động trong $\mathbb{Z}$, và đây là lý do tại sao $\pi_1(S^1) \cong \mathbb{Z}$.

![Winding number illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Winding_number.svg/500px-Winding_number.svg.png)  
*Loops với different winding numbers - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Winding_number.svg)*

---

### 2. Proof via Covering Space

**Setup:** Chúng ta sử dụng covering space $p: \mathbb{R} \to S^1$ được định nghĩa bởi $p(t) = e^{2\pi it}$. Đây là một ánh xạ ánh xạ đường thẳng thực lên hình tròn bằng cách "quấn" đường thẳng quanh hình tròn.

**Các tính chất quan trọng:**
- $p$ liên tục và surjective—mọi điểm trên hình tròn đều có ít nhất một preimage trên đường thẳng.
- $p^{-1}(e^{i\theta}) = \{\theta/(2\pi) + n : n \in \mathbb{Z}\}$—mỗi điểm trên hình tròn có vô số preimages, cách nhau một khoảng nguyên.
- $p$ locally homeomorphic—về mặt địa phương, $p$ là một homeomorphism, nghĩa là mỗi điểm trên hình tròn có một lân cận được ánh xạ homeomorphically từ một lân cận trên đường thẳng.

---

**Step 1: Lifting Loops**

**Bổ đề (Path Lifting):** Cho một loop $\gamma: [0,1] \to S^1$ với $\gamma(0) = 1$. Tồn tại duy nhất một lift $\tilde{\gamma}: [0,1] \to \mathbb{R}$ với $\tilde{\gamma}(0) = 0$ và $p \circ \tilde{\gamma} = \gamma$.

**Chứng minh:** Đây là một kết quả cơ bản trong lý thuyết covering space mà chúng ta sẽ nghiên cứu chi tiết trong bài học tiếp theo. Ý tưởng cơ bản là vì $p$ là locally homeomorphic, chúng ta có thể "lift" một cách duy nhất mỗi đoạn nhỏ của loop lên đường thẳng thực, và sau đó nối các lifts này lại với nhau để tạo thành một lift toàn cục. ✓

**Quan sát quan trọng:** $\tilde{\gamma}(1) \in \mathbb{Z}$ vì $\gamma$ là một loop nên $\gamma(1) = 1$, và do đó $\tilde{\gamma}(1) \in p^{-1}(1) = \mathbb{Z}$. Điều này có nghĩa là điểm cuối của lift là một số nguyên, và đây chính là winding number của loop $\gamma$.

---

**Step 2: Winding Number Map**

**Định nghĩa $\phi: \pi_1(S^1, 1) \to \mathbb{Z}$:**

$$
\phi([\gamma]) = \tilde{\gamma}(1)
$$

trong đó $\tilde{\gamma}$ là unique lift với $\tilde{\gamma}(0) = 0$.

**Well-defined:** Các loops đồng luân có các lifts với cùng điểm cuối (đây là một kết quả trong lý thuyết covering space—nếu hai loops đồng luân, thì các lifts của chúng cũng đồng luân và do đó có cùng điểm cuối). ✓

---

**Step 3: Verify Homomorphism**

**Khẳng định:** $\phi([\gamma][\delta]) = \phi([\gamma]) + \phi([\delta])$.

**Chứng minh:**  
Khi chúng ta lift loop $\gamma \cdot \delta$, chúng ta có thể làm điều này bằng cách lift từng phần một. Trong nửa đầu, lift của $\gamma$ kết thúc tại $\tilde{\gamma}(1) = n$. Trong nửa sau, lift của $\delta$ bắt đầu tại $n$ (để đảm bảo tính liên tục) và kết thúc tại $n + \tilde{\delta}(1) = n + m$. Tổng cộng, điểm cuối của lift của $\gamma \cdot \delta$ là $n + m = \phi([\gamma]) + \phi([\delta])$. ✓

**$\phi$ là một homomorphism!** Điều này có nghĩa là phép toán concatenation trên các loops tương ứng với phép cộng trên các số nguyên, và đây chính là lý do tại sao $\pi_1(S^1) \cong \mathbb{Z}$.

---

**Step 4: Verify Bijection**

**Injective:** Nếu $\phi([\gamma]) = 0$, thì $\tilde{\gamma}(1) = 0$. Điều này có nghĩa là $\tilde{\gamma}$ là một lift của $\gamma$ từ $0$ đến $0$—một đường đi từ $0$ đến $0$ trong $\mathbb{R}$. Vì $\mathbb{R}$ là contractible, đường đi này đồng luân với constant path, và do đó $\gamma$ đồng luân với constant loop, nghĩa là $[\gamma] = [e]$. ✓

**Surjective:** Cho mọi $n \in \mathbb{Z}$, chúng ta có thể xây dựng một loop $\gamma_n(t) = e^{2\pi int}$. Lift của loop này là $\tilde{\gamma}_n(t) = nt$, và do đó $\tilde{\gamma}_n(1) = n$. Điều này có nghĩa là $\phi([\gamma_n]) = n$, và do đó $\phi$ là surjective. ✓

**Kết luận:** $\phi: \pi_1(S^1, 1) \to \mathbb{Z}$ là một isomorphism! ✓ **QED**

---

**Generator:** $[\gamma_1]$ trong đó $\gamma_1(t) = e^{2\pi it}$ (quấn một lần theo chiều ngược chiều kim đồng hồ) là một generator của nhóm. Mọi phần tử đều có thể được biểu diễn như $[\gamma_1]^n$ cho một số $n \in \mathbb{Z}$—điều này có nghĩa là mọi loop đều có thể được biểu diễn như một bội số nguyên của loop cơ bản này.

---

### 3. Geometric Significance

**$\pi_1(S^1) = \mathbb{Z}$ phản ánh:** Hình tròn có "một lỗ"—một tính chất tô-pô cơ bản được phản ánh trong fundamental group không tầm thường. Chúng ta có thể quấn quanh hình tròn nhiều lần—đây là một tính chất hình học quan trọng cho phép chúng ta phân loại các loops theo số lần quấn. Winding là một tính chất tô-pô cơ bản—nó không thể bị loại bỏ bằng cách biến dạng liên tục. Các loops được phân loại bởi một bất biến nguyên—winding number là một số nguyên hoàn toàn xác định homotopy class của một loop.

**Các ứng dụng:** Trong giải tích phức, tích phân $\int_\gamma dz/z = 2\pi i \cdot (\text{winding number})$—đây là một kết quả cổ điển cho thấy cách winding number xuất hiện trong giải tích phức. Trong vật lý, magnetic flux quantization sử dụng winding number để giải thích tại sao từ thông bị lượng tử hóa. Trong robotics, cable winding around obstacle là một ví dụ về cách fundamental group xuất hiện trong các ứng dụng thực tế.

---

## 🌐 π₁(S^n) = 0 for n ≥ 2

### 1. Statement

**Định lý:** $S^n$ là simply connected cho $n \geq 2$:

$$
\pi_1(S^n, *) = \{e\} \quad \forall n \geq 2
$$

**Mọi loop trong $S^n$ đều contractible!** Đây là một kết quả đáng ngạc nhiên—mặc dù hình cầu có vẻ "phức tạp" hơn hình tròn, nhưng fundamental group của nó lại tầm thường. Điều này phản ánh một sự khác biệt cơ bản giữa các chiều—trong các chiều cao hơn, có đủ không gian để "tránh" các điểm và co các loops lại.

---

### 2. Proof

**Ý tưởng chính:** Lập luận về chiều—loop tránh các điểm.

**Chứng minh:**  
Cho $\gamma: S^1 \to S^n$ là một loop.

**Bước 1:** Ảnh $\gamma(S^1) \subseteq S^n$ là compact và có chiều $1$.

**Bước 2:** $S^n$ có chiều $n \geq 2$.

**Đếm chiều:** Một ảnh một chiều trong không gian $n$-chiều (với $n \geq 2$) không thể phủ toàn bộ không gian. Do đó tồn tại một điểm $p \in S^n \setminus \gamma(S^1)$. ✓

**Bước 3:** $S^n \setminus \{p\}$ homeomorphic với $\mathbb{R}^n$ (stereographic projection)—chúng ta có thể chiếu hình cầu lên không gian Euclid bằng cách loại bỏ một điểm.

**Bước 4:** Loop $\gamma$ factors qua $S^1 \to S^n \setminus \{p\} \simeq \mathbb{R}^n$.

**Bước 5:** Vì $\mathbb{R}^n$ contractible, loop $\gamma$ đồng luân với constant loop. ✓

**Kết luận:** Mọi loop đều contractible, do đó $\pi_1(S^n) = 0$. ✓ **QED**

---

### 3. Contrast with S¹

**Sự tương phản giữa $S^1$ và $S^2$:**
- $\pi_1(S^1) = \mathbb{Z}$ (không tầm thường)
- $\pi_1(S^2) = 0$ (tầm thường)

**Topology phân biệt các chiều!** Đây là một khám phá sâu sắc—các không gian có chiều khác nhau có các tính chất tô-pô khác nhau một cách cơ bản, và fundamental group là một công cụ mạnh mẽ để phân biệt chúng.

**Trực giác hình học:** Trong $S^1$, mọi loop đều "quấn quanh" một cách không thể tránh được—không có cách nào để một loop tránh được việc quấn quanh hình tròn. Trong $S^2$, mọi loop đều có thể "trượt ra" qua đỉnh hoặc đáy—có đủ không gian để co loop về một điểm mà không gặp chướng ngại vật nào.

**Higher $\pi_n$:** Thú vị là $\pi_3(S^2) = \mathbb{Z}$ (Hopf fibration)—các higher homotopy groups không tầm thường! Điều này cho thấy rằng mặc dù fundamental group của hình cầu là tầm thường, các higher homotopy groups lại không tầm thường, và đây là một khám phá quan trọng trong topology.

---

## 🍩 π₁(T²) = ℤ × ℤ: The Torus

### 1. Product Theorem

**Định lý (Product của Fundamental Groups):**  
Cho $(X, x_0)$, $(Y, y_0)$ là các pointed spaces. Khi đó:

$$
\pi_1(X \times Y, (x_0, y_0)) \cong \pi_1(X, x_0) \times \pi_1(Y, y_0)
$$

**Chứng minh sketch:**  
Một loop $\gamma: [0,1] \to X \times Y$ có thể được phân tích thành các thành phần: $\gamma(t) = (\gamma_1(t), \gamma_2(t))$, trong đó $\gamma_1$ là một loop trong $X$ và $\gamma_2$ là một loop trong $Y$. Homotopy class $[\gamma]$ tương ứng với cặp $([\gamma_1], [\gamma_2])$. Phép toán concatenation hoạt động theo từng thành phần—khi chúng ta nối hai loops lại với nhau, chúng ta nối các thành phần tương ứng của chúng. Isomorphism $\phi([\gamma]) = ([\gamma_1], [\gamma_2])$ cho thấy rằng fundamental group của tích là tích của các fundamental groups. ✓

---

### 2. Application to Torus

**$T^2 = S^1 \times S^1$** (torus = tích của các hình tròn).

**Áp dụng product theorem:**

$$
\pi_1(T^2) = \pi_1(S^1 \times S^1) \cong \pi_1(S^1) \times \pi_1(S^1) \cong \mathbb{Z} \times \mathbb{Z}
$$

**Generators:**
- **$\alpha$:** Loop quanh "meridian" (hình tròn ngắn, vòng quanh theo một hướng)
- **$\beta$:** Loop quanh "longitude" (hình tròn dài, đi qua lỗ theo hướng khác)

**Relation:** $\alpha$ và $\beta$ giao hoán với nhau (nhóm abelian). Điều này phản ánh tính chất tích của torus—chúng ta có thể đi qua các loops theo bất kỳ thứ tự nào mà không thay đổi homotopy class.

**Mọi loop đều có thể được biểu diễn như $\alpha^m \beta^n$** cho một số $m, n \in \mathbb{Z}$. Điều này có nghĩa là mọi loop trên torus đều có thể được hiểu như một tổ hợp của các loops cơ bản theo hai hướng độc lập.

---

### 3. Geometric Visualization

Torus có hai "hướng độc lập" để tạo thành loops: một là vòng quanh ống (meridian), và một là đi qua lỗ (longitude). Hai hướng này tạo ra toàn bộ $\pi_1(T^2) \cong \mathbb{Z}^2$. Trực giác hình học là chúng ta có thể quấn một sợi dây quanh torus theo hai cách độc lập—quanh ống hoặc qua lỗ—và mọi cách quấn khác đều có thể được biểu diễn như một tổ hợp của hai cách cơ bản này.

**Sự tương phản với $S^1$:**
- $S^1$: một hướng ($\mathbb{Z}$)
- $T^2$: hai hướng ($\mathbb{Z}^2$)

Điều này cho thấy cách fundamental group phản ánh cấu trúc hình học của không gian—số lượng các hướng độc lập để tạo thành loops tương ứng với số lượng các generators của fundamental group.

**Higher tori:** $T^n = (S^1)^n$ có $\pi_1(T^n) \cong \mathbb{Z}^n$—mỗi thành phần $S^1$ đóng góp một generator $\mathbb{Z}$ vào fundamental group.

---

## 🎭 π₁ of Surfaces

### 1. Orientable Surfaces (Genus g)

**$\Sigma_g$ = compact orientable surface với genus $g$.**

**Các ví dụ:**
- $g = 0$: $S^2$ (hình cầu)
- $g = 1$: $T^2$ (torus)
- $g = 2$: "pretzel" (torus hai lỗ)

**Định lý:**

$$
\pi_1(\Sigma_g) = \langle a_1, b_1, \ldots, a_g, b_g \mid [a_1,b_1] \cdots [a_g,b_g] = 1 \rangle
$$

**Nhóm:** $2g$ generators với một relation. Mỗi "lỗ" trong surface đóng góp hai generators—một cho mỗi hướng độc lập quanh lỗ đó. Relation $[a_1,b_1] \cdots [a_g,b_g] = 1$ phản ánh cách các loops quanh các lỗ khác nhau tương tác với nhau.

**Cho $g=1$ (torus):**  
$\pi_1(T^2) = \langle a, b | aba^{-1}b^{-1} = 1 \rangle = \langle a, b | ab = ba \rangle \cong \mathbb{Z}^2$. Đây là nhóm abelian—hai generators giao hoán với nhau.

**Cho $g \geq 2$:** Nhóm không abelian! Đây là một khám phá quan trọng—các surfaces với nhiều lỗ hơn có fundamental groups phức tạp hơn nhiều, và chúng không abelian. Điều này phản ánh cách các loops quanh các lỗ khác nhau không thể giao hoán với nhau một cách tự do.

---

### 2. Non-Orientable Surfaces

**ℝP² (Projective Plane):**

**Định lý:** $\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$.

**Chứng minh sketch:** $\mathbb{R}P^2 = S^2/(x \sim -x)$—projective plane được xây dựng bằng cách đồng nhất mỗi điểm trên hình cầu với điểm đối cực của nó. Chúng ta có một covering $p: S^2 \to \mathbb{R}P^2$ (2-fold covering—mỗi điểm trên projective plane có hai preimages trên hình cầu). Vì $\pi_1(S^2) = 0$, lý thuyết covering space cho chúng ta biết rằng $\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$. ✓

**Generator:** Loop từ một điểm đến điểm đối cực của nó và quay lại. Điều này tương ứng với phần tử không tầm thường trong $\mathbb{Z}/2\mathbb{Z}$—nếu chúng ta đi qua loop này hai lần, chúng ta có thể co nó về constant loop, phản ánh tính chất $2 = 0$ trong $\mathbb{Z}/2\mathbb{Z}$.

---

**Klein Bottle K:**

**Định lý:** $\pi_1(K) = \langle a, b | aba^{-1}b = 1 \rangle$.

**Không abelian:** Đây là một sự khác biệt quan trọng so với torus, nơi relation là $aba^{-1}b^{-1} = 1$ (tương đương với $ab = ba$). Relation $aba^{-1}b = 1$ cho thấy rằng $a$ và $b$ không giao hoán với nhau theo cách đơn giản như trong torus. Điều này phản ánh tính chất không định hướng được của Klein bottle—nó không thể được định hướng như torus.

---

## 🛠️ Techniques for Computing π₁

### 1. Covering Space Method

**Nguyên lý:** Sử dụng covering $p: \tilde{X} \to X$. Ý tưởng cơ bản là chúng ta có thể "lift" các loops từ không gian ban đầu lên covering space, và các tính chất của covering space cho phép chúng ta tính toán fundamental group.

**Lifting:** Các loops được lift thành các paths trên covering space, và các điểm cuối của các lifts này xác định homotopy class. Đây là phương pháp chúng ta đã sử dụng để chứng minh $\pi_1(S^1) \cong \mathbb{Z}$.

**Ví dụ:** $\mathbb{R} \to S^1$ (đã sử dụng ở trên). Covering space này cho phép chúng ta "mở ra" hình tròn thành đường thẳng thực, và winding number xuất hiện tự nhiên như sự khác biệt giữa các điểm cuối của lift.

**Mạnh mẽ cho:** Các không gian có universal covers đẹp. Universal cover là covering space đơn giản nhất—nó có fundamental group tầm thường và có thể được sử dụng để tính toán fundamental group của không gian ban đầu.

---

### 2. Homotopy Equivalence

**Nguyên lý:** Nếu $X \simeq Y$ đồng luân tương đương, thì $\pi_1(X) \cong \pi_1(Y)$. Đây là một công cụ mạnh mẽ cho phép chúng ta tính toán fundamental group bằng cách tìm một không gian đồng luân tương đương đơn giản hơn.

**Ví dụ:** $\mathbb{R}^n \setminus \{0\} \simeq S^{n-1}$ (chúng ta đã thấy điều này trong bài học trước thông qua deformation retract). Do đó $\pi_1(\mathbb{R}^n \setminus \{0\}) \cong \pi_1(S^{n-1})$.

**Các ứng dụng:**
- $\mathbb{R}^2 \setminus \{0\} \simeq S^1$ ⇒ $\pi_1(\mathbb{R}^2 \setminus \{0\}) \cong \mathbb{Z}$—mặt phẳng trừ đi một điểm có fundamental group giống như hình tròn.
- $\mathbb{R}^3 \setminus \{0\} \simeq S^2$ ⇒ $\pi_1(\mathbb{R}^3 \setminus \{0\}) = 0$—không gian ba chiều trừ đi một điểm có fundamental group tầm thường vì hình cầu hai chiều là simply connected.

Đây là một phương pháp rất hữu ích vì nó cho phép chúng ta đơn giản hóa không gian trước khi tính toán fundamental group.

---

### 3. Van Kampen's Theorem (Preview)

**Nguyên lý:** Phân tích $X = A \cup B$, tính toán $\pi_1(X)$ từ $\pi_1(A)$, $\pi_1(B)$, và $\pi_1(A \cap B)$. Đây là một trong những công cụ mạnh mẽ nhất để tính toán fundamental group—nó cho phép chúng ta tính toán fundamental group của một không gian phức tạp bằng cách chia nó thành các phần đơn giản hơn.

**Ví dụ:** Figure-eight (hình số 8) = hai hình tròn được nối tại một điểm. $\pi_1(\text{figure-eight}) = \mathbb{Z} * \mathbb{Z}$ (free product)—mỗi hình tròn đóng góp một copy của $\mathbb{Z}$, và chúng được kết hợp theo cách tự do không có relations nào giữa chúng.

**Bài học tiếp theo:** Chúng ta sẽ nghiên cứu phát biểu đầy đủ của định lý Van Kampen và các ứng dụng của nó. Đây là một công cụ cực kỳ mạnh mẽ cho phép chúng ta tính toán fundamental groups của nhiều không gian phức tạp.

---

### 4. Deformation Retract

**Nguyên lý:** Nếu $A$ là deformation retract của $X$, thì $\pi_1(A) \cong \pi_1(X)$. Đây là một phương pháp rất hữu ích vì nó cho phép chúng ta tính toán fundamental group của một không gian lớn bằng cách tính toán fundamental group của một không gian con đơn giản hơn.

**Ví dụ:** $S^1 \subseteq \mathbb{R}^2 \setminus \{0\}$ là deformation retract—chúng ta có thể co toàn bộ mặt phẳng trừ đi gốc tọa độ về hình tròn đơn vị. Do đó $\pi_1(\mathbb{R}^2 \setminus \{0\}) \cong \pi_1(S^1) \cong \mathbb{Z}$. Đây là một ví dụ tuyệt vời về cách deformation retract đơn giản hóa việc tính toán fundamental group.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Computed first examples: spheres, tori*

2. **Max Dehn & Poul Heegaard** - *Surface classification* (1907)  
   *π₁ of surfaces, genus formula*

3. **Herbert Seifert** - *"Topologie dreidimensionaler gefaserter Räume"* (1932)  
   *Seifert-van Kampen theorem*

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§1.1: Examples**  
   *Best geometric treatment, detailed computations*

5. **James R. Munkres** - *Topology*, **§53-54: Computing π₁**  
   *Rigorous proofs, covering space approach*

6. **William S. Massey** - *Algebraic Topology*, **Chapters 4-5**  
   *Comprehensive examples*

7. **Armstrong** - *Basic Topology*, **Chapters 5-6**  
   *Accessible computations*

---

## 🔗 Applications and Connections

### Complex Analysis - Residue Calculus
**Winding Numbers:** ∫_γ f(z)dz/(z-a) = 2πi · winding number của γ around a. π₁(ℂ \ {a}) ≅ ℤ essential.

### Robotics - Configuration Spaces
**Obstacle Avoidance:** Robot in plane với obstacle. Configuration space ≃ ℝ² \ {point} ⇒ π₁ ≅ ℤ. Paths classified by winding around obstacle.

### Physics - Aharonov-Bohm Effect
**Quantum Phases:** Electron path around magnetic flux. Phase shift ∝ winding number. π₁ determines observable effects.

### Data Science - Holes in Data
**Topological Data Analysis:** Point cloud với hole. π₁ detects "1-dimensional holes". Applications: shape recognition, sensor networks.

### Knot Theory
**Knot Complements:** K ⊆ S³ knot. π₁(S³ \ K) = knot group, distinguishes knots.

---

## Video tham khảo

- **xem trước** [3. Fundamental Group of the Circle - Pierre Albin](https://www.youtube.com/watch?v=GnQ1GuXH5vw) — Mat Neth, tiếng Anh. π₁ của đường tròn là ℤ, phép tính trung tâm của bài.
- [Algebraic topology: Calculating the fundamental group](https://www.youtube.com/watch?v=BDrKDk8PQ_A) — Richard E Borcherds, tiếng Anh. Borcherds tính nhóm cơ bản của vài không gian quen, sau khi đường tròn đã xong.
- [M-19. Fundamental group of circle and torus](https://www.youtube.com/watch?v=VxLnh4L5LcU) — e-Content-Science, tiếng Anh. Đường tròn và xuyến cạnh nhau, đúng hai ví dụ π₁(S¹) và π₁(T²) của bài.

## 🧩 Exercises

### Circle π₁(S¹)

1. **Winding Number:**  
   γ(t) = e^(4πit). Compute winding number và π₁-class [γ].

2. **Explicit Homotopy:**  
   γ₂(t) = e^(4πit) (wind twice). Write homotopy γ₂ ≃ γ₁ · γ₁.

3. **Lifting:**  
   γ(t) = e^(2πit/2). Lift to ℝ starting at 0. Find γ̃(1).

### Spheres π₁(S^n)

4. **S² Simply Connected:**  
   Write detailed proof any loop trong S² contractible.

5. **Higher Dimensions:**  
   Prove π₁(S³) = 0 using dimension argument.

6. **Punctured Sphere:**  
   S² \ {north pole} ≃ ? Compute π₁.

### Torus π₁(T²)

7. **Product Theorem:**  
   Prove π₁(X × Y) ≅ π₁(X) × π₁(Y) carefully.

8. **Generators:**  
   Describe explicit loops α (meridian) và β (longitude) trong T².

9. **Commutativity:**  
   Verify α · β ≃_p β · α geometrically.

### Surfaces

10. **Genus 2:**  
    Σ₂ (pretzel). How many generators trong π₁(Σ₂)? What relation?

11. **ℝP²:**  
    π₁(ℝP²) ≅ ℤ/2ℤ. Describe generator loop geometrically.

12. **Klein Bottle:**  
    π₁(K) non-abelian. Verify aba⁻¹b ≠ 1 implies non-commutativity.

### Techniques

13. **Homotopy Equivalence:**  
    ℝ² \ {two points} ≃ S¹ ∨ S¹ (figure-eight). Intuitive argument.

14. **Deformation Retract:**  
    ℝ² \ {0} deformation retracts to S¹. Explicit retraction r(x) = x/||x||.

15. **Covering Space:**  
    Covering p: ℝ → S¹. How does p help compute π₁(S¹)?

### Advanced

16. **Figure-Eight:**  
    π₁(S¹ ∨ S¹) = ℤ * ℤ (free product). Research Van Kampen application.

17. **ℝⁿ \ {k points}:**  
    What is π₁(ℝ² \ {p₁, ..., p_k})? (Answer: free group F_k.)

18. **Knot Complement:**  
    Trefoil knot K ⊆ S³. π₁(S³ \ K) ≠ ℤ. Research knot groups.

### Reflection

19. **Why ℤ?:**  
    Explain why π₁(S¹) = ℤ (not ℚ or ℝ). What makes integers natural?

20. **Dimension Matters:**  
    π₁(S¹) = ℤ but π₁(S²) = 0. Why does dimension change π₁ so drastically?

21. **Applications:**  
    Give real-world application where computing π₁ matters practically.

---

## 📚 Further Reading

- **Hatcher, §1.1:** Best geometric treatment
- **Munkres, §53-54:** Rigorous covering space approach
- **Massey, Chapters 4-5:** Comprehensive examples
- **Armstrong, Chapters 5-6:** Accessible style
- **Stillwell, Classical Topology:** Historical perspective

---

## 🎓 Summary

Trong bài này, chúng ta computed **π₁ cho standard spaces**:

✅ **π₁(S¹) ≅ ℤ:** Winding number, covering space proof  
✅ **π₁(S^n) = 0 (n≥2):** Dimension argument, loops contractible  
✅ **π₁(T²) ≅ ℤ²:** Product theorem, two generators  
✅ **π₁(Σ_g):** Genus g surfaces, 2g generators with relation  
✅ **π₁(ℝP²) ≅ ℤ/2ℤ:** Projective plane, 2-fold covering  
✅ **Techniques:** Covering spaces, homotopy equivalence, Van Kampen (preview)  

**Điểm chính:**
- Covering space method powerful (S¹)
- Dimension affects π₁ dramatically
- Product theorem enables torus computation
- Surfaces classified by genus
- Multiple techniques available

**Geometric intuition:**
- Winding number captures loops around circle
- Higher spheres allow contraction
- Torus has two independent loop directions
- Genus = # of "handles" / holes

**Practical wisdom:**
- Use homotopy equivalence first (simplify space)
- Covering spaces excellent when available
- Van Kampen for decomposable spaces
- Deformation retracts preserve π₁

**Tiếp theo:** Lecture 06.03 về **Covering Spaces**—systematic theory for lifting và computing π₁!

---

*"To compute π₁, find the right tool: covering spaces, Van Kampen, or homotopy equivalence."*

🎯 **Master these computations! They're the foundation.** 🎯

---

**Previous:** [Lecture 06.01: Fundamental Group](/contents/vi/topology-chapter06/06_01_Fundamental_Group/)  
**Next:** [Lecture 06.03: Covering Spaces](/contents/vi/topology-chapter06/06_03_Covering_Spaces/)
