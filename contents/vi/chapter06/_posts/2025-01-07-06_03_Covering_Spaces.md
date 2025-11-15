---
layout: post
title: "Lecture 06.03: Covering Spaces Theory"
lang: vi
lang-ref: lecture-06-03
chapter: 6
lecture: 3
categories: [chapter06]
tags: [covering-spaces, universal-cover, deck-transformations, lifting]
description: "Covering spaces: định nghĩa, lifting properties, universal cover, deck transformations, và classification theorem"
---

**p: X̃ → X - Local Homeomorphisms**

---

## 📖 Tổng quan

**Covering spaces** là một trong những khái niệm đẹp và mạnh mẽ nhất trong topology. Chúng cung cấp:

> **Local simplicity describing global complexity.**

**Ý tưởng:** Không gian $\tilde{X}$ "covers" $X$—về mặt địa phương trông giống như nhiều bản sao của $X$ được xếp chồng lên nhau, nhưng về mặt toàn cục có thể rất khác biệt (đơn giản hơn!).

**Tại sao đây là một cuộc cách mạng?** Poincaré và các nhà toán học đầu thế kỷ 20 đã có những khám phá đáng kinh ngạc. Họ phát hiện ra rằng **thông tin địa phương** được mã hóa trong các lân cận evenly covered, kết hợp với **global connectivity**, hoàn toàn xác định cấu trúc covering space. **Universal cover** $\tilde{X}$ xuất hiện như một không gian simply connected tiết lộ mọi thứ về base space $X$—tất cả độ phức tạp được "mở ra". Đáng chú ý nhất, **$\pi_1(X)$ hoạt động như một symmetry group** của universal cover, với mỗi loop tương ứng với một deck transformation. Điều này đạt đến đỉnh cao trong **Classification Theorem**: tất cả các coverings của $X$ được phân loại hoàn toàn bởi các subgroups của $\pi_1(X)$, thiết lập một kết nối sâu sắc giữa topology và lý thuyết nhóm.

![Covering space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Covering_space.svg/500px-Covering_space.svg.png)  
*Covering space: multiple sheets over base - Nguồn concept*

Trong bài học này, chúng ta sẽ khám phá lý thuyết phong phú này một cách có hệ thống. Bắt đầu với **định nghĩa** chính xác sử dụng evenly covered neighborhoods—điều kiện đảm bảo local triviality. Chúng ta sẽ khám phá các **ví dụ** chuẩn: đường thẳng thực $\mathbb{R}$ covering hình tròn $S^1$ (infinite-sheeted), các hình cầu $S^n$ covering các projective spaces $\mathbb{R}P^n$ (double cover), và các multi-sheeted coverings tiết lộ cấu trúc sâu hơn. **Lifting theorems** chứng minh rằng paths và homotopies lift một cách duy nhất khi cho basepoint, cho phép các kỹ thuật tính toán mạnh mẽ. **Universal cover** $\tilde{X}$ xuất hiện như một không gian simply connected với tính chất đẹp $X = \tilde{X}/\pi_1(X)$. **Deck transformations** tạo thành symmetry group $\text{Aut}(\tilde{X}/X)$ tác động lên covering space. Viên ngọc quý là **Classification Theorem** thiết lập một song ánh: coverings $\leftrightarrow$ subgroups của $\pi_1$.

Các ứng dụng trải dài khắp toán học: Tính toán $\pi_1$ (công cụ chính của chúng ta từ bài học trước!), Riemann surfaces trong giải tích phức nơi các hàm đa trị trở thành đơn trị trên covers, sự tương tự đáng chú ý với Galois theory (coverings:topology :: field extensions:algebra), và các ứng dụng vật lý trong gauge theory và instantons nơi topology gặp quantum field theory.

**Tại sao đây là kiến thức cơ bản?** Covering spaces cung cấp **công cụ tính toán mạnh mẽ nhất** cho fundamental groups—nhiều tính toán $\pi_1$ không thể thực hiện được nếu không có chúng. **Universal cover** đơn giản hóa các vấn đề một cách có hệ thống bằng cách "mở ra" độ phức tạp. Lý thuyết sở hữu vẻ đẹp hiếm có của **complete classification**—chúng ta hiểu TẤT CẢ các coverings thông qua lý thuyết nhóm. **Các ứng dụng rộng rãi** từ giải tích (Riemann surfaces) qua đại số (Galois connection) đến hình học và vật lý chứng minh tính phổ quát của các ý tưởng.

---

## 🎯 Definition của Covering Space

### 1. Evenly Covered Neighborhoods

**Định nghĩa (Covering Space):**  
$p: \tilde{X} \to X$ là một **covering space** (hay **covering projection**) nếu:

**$\forall x \in X$: $\exists$ open neighborhood $U$ của $x$ ("evenly covered"):**

$$
p^{-1}(U) = \bigsqcup_{\alpha \in A} V_\alpha
$$

trong đó disjoint union có nghĩa là các $V_\alpha$ là pairwise disjoint và open trong $\tilde{X}$, và quan trọng là **$p|_{V_\alpha}: V_\alpha \to U$ là homeomorphism** cho mọi $\alpha$—mỗi sheet ánh xạ hoàn hảo lên $U$.

**Thuật ngữ:** $\tilde{X}$ là **covering space** (hoặc total space) nằm "phía trên", $X$ là **base space** "phía dưới", $p$ là **covering map** (hoặc projection) kết nối chúng, và $V_\alpha$ là các **sheets over $U$**—mỗi cái là một bản sao homeomorphic của $U$ được xếp chồng trong $\tilde{X}$.

**Trực giác:** Về mặt địa phương, $\tilde{X}$ trông giống như nhiều bản sao disjoint của $X$ được xếp chồng lên nhau. Projection $p$ "collapse" các sheets xuống. Hãy tưởng tượng một cuốn sách với nhiều trang—mỗi trang là một sheet, và projection là cách chúng ta "ép" các trang lại với nhau để tạo thành một trang duy nhất.

![Evenly covered neighborhood](https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/Covering_map.svg/400px-Covering_map.svg.png)  
*Evenly covered neighborhood - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Covering_map.svg)*

---

### 2. Key Properties

**Định lý:** Covering map $p: \tilde{X} \to X$ có các tính chất sau:
1. **Continuous** (theo định nghĩa)
2. **Surjective** (covers toàn bộ $X$—mọi điểm trong $X$ đều có ít nhất một preimage trong $\tilde{X}$)
3. **Open map** (ảnh của các tập mở là tập mở—điều này đảm bảo rằng covering map "bảo toàn" topology)
4. **Local homeomorphism** (về mặt địa phương là homeomorphism—mỗi điểm có một lân cận được ánh xạ homeomorphically)

**Chứng minh:** Bài tập—sử dụng tính chất evenly covered. ✓

**Quan trọng:** Covering map KHÔNG nhất thiết phải là homeomorphism toàn cục! Đây là một điểm quan trọng—mặc dù về mặt địa phương covering map là homeomorphism, nhưng về mặt toàn cục nó có thể không phải là song ánh hoặc không có nghịch đảo liên tục. Ví dụ, $\mathbb{R} \to S^1$ là covering map nhưng không phải là homeomorphism vì nó không phải là song ánh.

---

## 📊 Standard Examples

### Example 1: ℝ → S¹ (Universal Cover of Circle)

**Định nghĩa:** $p: \mathbb{R} \to S^1$, $p(t) = e^{2\pi it}$.

**Xác minh covering:**
- **Surjective:** Mọi điểm $z \in S^1 = e^{i\theta} = p(\theta/(2\pi))$ đều có preimage trên đường thẳng thực. ✓
- **Evenly covered:** Cho $z = e^{i\theta}$, lấy $U = S^1 \setminus \{-z\}$ (complement của điểm đối cực).  
  $p^{-1}(U) = \bigcup_{n \in \mathbb{Z}} (\theta/(2\pi) - 1/2 + n, \theta/(2\pi) + 1/2 + n)$ (các khoảng disjoint).  
  Mỗi khoảng homeomorphic với $U$. ✓

**Trực giác hình học:** $\mathbb{R}$ = infinite helix quấn quanh hình tròn. Hãy tưởng tượng một đường thẳng được quấn quanh một hình tròn vô số lần—mỗi điểm trên hình tròn có vô số preimages trên đường thẳng, cách nhau một khoảng nguyên.

**Sheets:** Countably many (indexed by $\mathbb{Z}$)—mỗi số nguyên tương ứng với một "vòng quấn" của đường thẳng quanh hình tròn.

**Đây là UNIVERSAL COVER của $S^1$!** Universal cover là covering space đơn giản nhất—nó có fundamental group tầm thường và có thể được sử dụng để tính toán fundamental group của base space.

---

### Example 2: z ↦ z^n on S¹

**Định nghĩa:** $p: S^1 \to S^1$, $p(z) = z^n$ ($n \geq 2$).

**Xác minh covering:**
- Cho $z_0 \in S^1$, lấy $U = S^1 \setminus \{-z_0\}$.
- $p^{-1}(U) = n$ disjoint arcs, mỗi arc được ánh xạ homeomorphically lên $U$.

**Sheets:** $n$ sheets ($n$-fold covering)—mỗi điểm trên hình tròn có $n$ preimages, tương ứng với $n$ căn bậc $n$ của số phức.

**Deck transformations:** Rotations bởi $2\pi k/n$, $k = 0, \ldots, n-1$. Đây là các phép quay quanh hình tròn một góc $2\pi k/n$—chúng là các symmetries của covering space giữ nguyên base space.

---

### Example 3: S^n → ℝP^n (Antipodal Quotient)

**Định nghĩa:** $p: S^n \to \mathbb{R}P^n$, quotient map $x \sim -x$.

**Xác minh covering:**
- $\mathbb{R}P^n$ = các đường thẳng đi qua gốc tọa độ trong $\mathbb{R}^{n+1}$.
- Mỗi đường thẳng cắt $S^n$ tại hai điểm đối cực.
- Evenly covered: Chọn các lân cận nhỏ tránh các đồng nhất đối cực.

**Sheets:** 2 sheets (2-fold covering)—mỗi điểm trên projective space có hai preimages trên hình cầu, tương ứng với hai điểm đối cực.

**Đây là universal cover của $\mathbb{R}P^n$!** (Vì $\pi_1(S^n) = 0$.) Điều này có nghĩa là hình cầu là covering space đơn giản nhất của projective space—nó có fundamental group tầm thường và có thể được sử dụng để tính toán fundamental group của projective space.

---

### Example 4: ℝ² → T² (Torus)

**Định nghĩa:** $p: \mathbb{R}^2 \to T^2$, $p(x,y) = (e^{2\pi ix}, e^{2\pi iy})$.

**Quotient:** Đồng nhất $\mathbb{R}^2$ bởi lattice $\mathbb{Z}^2$ (translate bởi các số nguyên).

**Xác minh covering:**
- $T^2 = \mathbb{R}^2/\mathbb{Z}^2$ (hình vuông với các cạnh đối diện được dán lại).
- Evenly covered: Các lân cận đủ nhỏ tránh các phép tịnh tiến lattice.

**Sheets:** Countably infinite (indexed by $\mathbb{Z}^2$)—mỗi điểm trên torus có vô số preimages trên mặt phẳng, tương ứng với các điểm trong lattice $\mathbb{Z}^2$.

**Universal cover của torus!** Mặt phẳng là covering space đơn giản nhất của torus—nó có fundamental group tầm thường và có thể được sử dụng để tính toán fundamental group của torus.

---

### Example 5: Figure-Eight Universal Cover

**$X = S^1 \vee S^1$** (hai hình tròn được nối tại một điểm).

**Universal cover $\tilde{X}$:** Infinite tree (Cayley graph của free group $\mathbb{Z} * \mathbb{Z}$).

**Mỗi vertex:** có 4 edges (branching)—mỗi đỉnh có bốn nhánh, tương ứng với bốn hướng có thể đi từ điểm đó.

**Sheets:** Countably infinite, nhưng cấu trúc = tree (simply connected). Đây là một ví dụ tuyệt vời về cách universal cover có thể rất khác biệt về mặt topology so với base space—base space là hai hình tròn được nối tại một điểm, nhưng universal cover là một cây vô hạn!

**Điều này chứng minh:** Universal cover có thể rất khác biệt về mặt topology so với base space! Đây là một khám phá quan trọng—mặc dù về mặt địa phương universal cover trông giống như base space, nhưng về mặt toàn cục nó có thể có cấu trúc hoàn toàn khác.

---

## 🔼 Lifting Properties

### 1. Path Lifting Theorem

**Định lý (Path Lifting):**  
Cho $p: \tilde{X} \to X$ là covering, $\gamma: [0,1] \to X$ là một path, và $\tilde{x}_0 \in p^{-1}(\gamma(0))$.

Khi đó tồn tại duy nhất một **lift** $\tilde{\gamma}: [0,1] \to \tilde{X}$ sao cho:
- $p \circ \tilde{\gamma} = \gamma$ ($\tilde{\gamma}$ projects down to $\gamma$)
- $\tilde{\gamma}(0) = \tilde{x}_0$ (bắt đầu tại điểm được chỉ định)

**Tính duy nhất là quan trọng:** Cho điểm bắt đầu, lift là duy nhất! Điều này có nghĩa là nếu chúng ta chọn một điểm bắt đầu trên covering space, thì có đúng một cách để lift path lên covering space.

**Chứng minh sketch:**
- Phân chia $[0,1]$ thành các khoảng nhỏ
- Mỗi khoảng: $\gamma$ ánh xạ vào một evenly covered neighborhood
- Lift từng phần một bằng cách sử dụng local homeomorphisms
- Dán lại với nhau một cách liên tục
- Tính duy nhất: Hai lifts đồng ý tại một điểm thì đồng ý ở mọi nơi (connectedness)

✓

![Path lifting](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e1/Covering_space_path_lifting.svg/400px-Covering_space_path_lifting.svg.png)  
*Path lifting uniquely - Nguồn concept*

---

**Ứng dụng cho $\pi_1$:**

**Định lý:** Cho $\gamma, \delta: [0,1] \to X$ là các paths từ $x_0$ đến $x_1$, và $\gamma \simeq_p \delta$.

Các lifts $\tilde{\gamma}$, $\tilde{\delta}$ bắt đầu tại cùng một điểm $\tilde{x}_0 \in p^{-1}(x_0)$ có **cùng điểm cuối**.

**Chứng minh:** Homotopy lifting (phần tiếp theo). ✓

**Hệ quả:** Homotopy class $[\gamma]$ xác định điểm cuối của lift!  
Đây chính là CÁCH chúng ta tính toán $\pi_1(S^1) \cong \mathbb{Z}$—winding number xuất hiện tự nhiên như sự khác biệt giữa các điểm cuối của lift.

---

### 2. Homotopy Lifting Theorem

**Định lý (Homotopy Lifting):**  
Cho $p: \tilde{X} \to X$ là covering, $F: [0,1] \times [0,1] \to X$ là một homotopy.

Cho lift $\tilde{F}_0: [0,1] \to \tilde{X}$ của $F(\cdot, 0)$, tồn tại duy nhất một lift $\tilde{F}: [0,1] \times [0,1] \to \tilde{X}$:
- $p \circ \tilde{F} = F$ (projects down)
- $\tilde{F}(s, 0) = \tilde{F}_0(s)$ (đồng ý tại $t=0$)

**Trực giác hình học:** Homotopies lift một cách duy nhất! Điều này có nghĩa là nếu chúng ta có một homotopy giữa hai paths, chúng ta có thể lift toàn bộ homotopy lên covering space một cách duy nhất.

**Chứng minh:** Tương tự như path lifting, sử dụng cấu trúc tích. ✓

---

**Hệ quả (Homotopy Invariance):**

**Nếu $\gamma \simeq_p \delta$ (path homotopic), các lifts $\tilde{\gamma}$, $\tilde{\delta}$ từ cùng điểm bắt đầu KẾT THÚC tại cùng một điểm.**

**Đây là CHÌA KHÓA:** Covering spaces phát hiện homotopy! Đây là một khám phá quan trọng—covering spaces có thể phân biệt giữa các paths đồng luân và không đồng luân bằng cách xem xét các điểm cuối của các lifts của chúng.

---

### 3. Lifting Criterion

**Định lý (Lifting Criterion):**  
Cho $p: \tilde{X} \to X$ là covering, $f: Y \to X$ liên tục, $f(y_0) = x_0$, và $\tilde{x}_0 \in p^{-1}(x_0)$.

Lift $\tilde{f}: Y \to \tilde{X}$ ($\tilde{f}(y_0) = \tilde{x}_0$, $p \circ \tilde{f} = f$) tồn tại $\Longleftrightarrow$:

$$
f_*(\pi_1(Y, y_0)) \subseteq p_*(\pi_1(\tilde{X}, \tilde{x}_0))
$$

**Bằng lời:** $f$ lifts $\Longleftrightarrow$ $f_*$ ánh xạ $\pi_1(Y)$ vào subgroup $p_*(\pi_1(\tilde{X}))$.

**Mạnh mẽ:** Giảm câu hỏi về lifting xuống đại số (subgroup inclusion)! Đây là một kết quả cực kỳ mạnh mẽ—nó cho phép chúng ta quyết định xem một ánh xạ có thể được lift lên covering space hay không bằng cách kiểm tra một điều kiện đại số đơn giản về fundamental groups.

---

## 🌟 Universal Covering Space

### 1. Definition

**Định nghĩa (Universal Cover):**  
$\tilde{X}$ là **universal covering space** của $X$ nếu:
1. $p: \tilde{X} \to X$ là covering space
2. **$\tilde{X}$ simply connected:** $\pi_1(\tilde{X}) = \{e\}$

**"Universal":** $\tilde{X}$ = "most general" covering—tất cả các coverings khác đều là quotients của $\tilde{X}$. Đây là một tính chất đẹp—universal cover là covering space đơn giản nhất, và mọi covering space khác đều có thể được xây dựng như một quotient của universal cover.

---

### 2. Existence

**Theorem (Existence of Universal Cover):**  
X has universal cover if X:
1. **Path-connected**
2. **Locally path-connected**
3. **Semilocally simply connected:** ∀x: ∃U neighborhood: loops trong U contractible trong X

**Most "nice" spaces satisfy these!**

**Examples satisfying:**
- Manifolds ✓
- CW complexes ✓
- Most spaces we care about ✓

**Counterexample:** Hawaiian earring (infinite wedge shrinking circles) NOT semilocally simply connected.

---

### 3. Uniqueness

**Theorem (Uniqueness):**  
Universal covers X̃₁, X̃₂ of X are **isomorphic** (as covering spaces).

**Meaning:** Unique up to covering space isomorphism.

**Notation:** Often write "**the** universal cover" X̃.

---

### 4. Examples Revisited

**ℝ → S¹:**
- ℝ simply connected ✓
- ℝ = universal cover of S¹

**ℝ² → T²:**
- ℝ² simply connected ✓
- ℝ² = universal cover of T²

**S^n → ℝP^n:**
- S^n simply connected (n ≥ 2) ✓
- S^n = universal cover of ℝP^n

**Tree → Figure-eight:**
- Tree simply connected (contractible) ✓
- Tree = universal cover of S¹ ∨ S¹

---

## 🔄 Deck Transformations

### 1. Definition

**Định nghĩa (Deck Transformation):**  
p: X̃ → X covering. **Deck transformation** (hay **covering automorphism**) là homeomorphism f: X̃ → X̃ such that:

$$
p \circ f = p
$$

**Geometric:** f permutes sheets, preserving projection.

**Set:** Aut(X̃/X) = {deck transformations} = **deck transformation group**.

---

### 2. Group Structure

**Theorem:** Aut(X̃/X) is group under composition.

**Proof:**
- **Identity:** id_{X̃} deck transformation ✓
- **Composition:** f, g deck ⇒ f ∘ g deck ✓
- **Inverses:** f deck, homeomorphism ⇒ f^(-1) deck ✓

---

### 3. Universal Cover Case

**Theorem (Main Result):**  
X̃ universal cover of X, X path-connected, locally path-connected.

Then:

$$
\text{Aut}(\tilde{X}/X) \cong \pi_1(X)
$$

**Profound:** π₁(X) = symmetry group of universal cover!

**Proof sketch:**
- Each [γ] ∈ π₁(X, x₀) defines deck transformation
- Lift γ uniquely, endpoint = f_{[γ]}(x̃₀)
- f_{[γ]} extends to entire X̃ (by lifting)
- Map [γ] ↦ f_{[γ]} is isomorphism

✓

---

**Consequence:**

$$
X = \tilde{X} / \pi_1(X)
$$

**X is quotient of universal cover by π₁ action!**

**Examples:**
- S¹ = ℝ/ℤ (ℤ = translations)
- T² = ℝ²/ℤ² (ℤ² = lattice translations)
- ℝP^n = S^n/(ℤ/2ℤ) (ℤ/2ℤ = antipodal map)

---

### 4. Computing Deck Transformations

**Example 1: ℝ → S¹**

Deck transformations: f_n: ℝ → ℝ, f_n(t) = t + n (n ∈ ℤ).

Aut(ℝ/S¹) = {f_n : n ∈ ℤ} ≅ ℤ ≅ π₁(S¹). ✓

---

**Example 2: S² → ℝP²**

Deck transformation: f: S² → S², f(x) = -x (antipodal).

Aut(S²/ℝP²) = {id, f} ≅ ℤ/2ℤ ≅ π₁(ℝP²). ✓

---

## 📋 Classification of Coverings

### 1. Correspondence Theorem

**Theorem (Classification of Coverings):**  
X path-connected, locally path-connected, semilocally simply connected.

**Bijection:**

$$
\{\text{Coverings of } X\} / \text{isomorphism} \leftrightarrow \{\text{Subgroups of } \pi_1(X)\} / \text{conjugacy}
$$

**Specifically:** Covering p: X̃ → X ↔ subgroup p_*(π₁(X̃)) ≤ π₁(X).

**Universal cover:** Corresponds to trivial subgroup {e}.

**Beautiful:** Topology (coverings) ↔ Algebra (subgroups)!

---

### 2. Normal Coverings

**Định nghĩa:** Covering p: X̃ → X **normal** (hay **regular**) if p_*(π₁(X̃)) is **normal subgroup** of π₁(X).

**Theorem:** Normal covering ⟺ Aut(X̃/X) acts transitively on fibers.

**Example:** Universal cover always normal (trivial subgroup normal).

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Introduced covering spaces implicitly*

2. **Hermann Weyl** - *"Die Idee der Riemannschen Fläche"* (1913)  
   *Riemann surfaces as covering spaces*

3. **Heinz Hopf** - *"Fundamentalgruppe und zweite Bettische Gruppe"* (1941)  
   *Covering space theory systematized*

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§1.3: Covering Spaces**  
   *Outstanding modern treatment, geometric and rigorous*

5. **James R. Munkres** - *Topology*, **§53-54: Covering Spaces**  
   *Classic careful treatment*

6. **William S. Massey** - *Algebraic Topology*, **Chapters 5-6**

7. **Edwin Spanier** - *Algebraic Topology*, **Chapter 2**

8. **Glen E. Bredon** - *Topology and Geometry*, **Chapter II**

---

## 🔗 Applications and Connections

### Complex Analysis - Riemann Surfaces
**Multi-valued Functions:** √z, log z single-valued on universal cover. Monodromy = deck transformations. Riemann surfaces = coverings of ℂ or ℂP¹.

### Galois Theory Analogy
**Covering Spaces ↔ Field Extensions:** Deck transformations ↔ Galois group. Classification theorem ↔ Fundamental theorem of Galois theory. Beautiful parallel!

### Differential Geometry - Riemannian Coverings
**Metric Lifts:** Riemannian metric on X lifts to X̃. Geodesics lift to geodesics. Universal cover studies local geometry.

### Physics - Gauge Theory
**Principal Bundles:** U(1) bundles = circle bundles. Covering theory = abelian case. Instantons classified using covering spaces.

### Number Theory - Modular Forms
**Modular Curve:** ℍ/SL₂(ℤ) (upper half-plane quotient). ℍ = universal cover. Deck transformations = modular group.

---

## 🧩 Exercises

### Definition và Basic Properties

1. **Verify Covering:**  
   p: ℝ → S¹, p(t) = e^(2πit). Prove p is covering map với explicit evenly covered neighborhoods.

2. **Not Covering:**  
   f: [0,1) → S¹, f(t) = e^(2πit). Why NOT covering? (Not surjective.)

3. **Sheets Count:**  
   p: S¹ → S¹, p(z) = z³. How many sheets? Describe fiber p^(-1)(1).

### Lifting

4. **Path Lifting:**  
   p: ℝ → S¹. γ(t) = e^(4πit) (wind twice). Lift starting at 0 ∈ ℝ. Find γ̃(1).

5. **Homotopy Lifting:**  
   Homotopy F: [0,1]² → S¹ connecting two loops. Explain how F lifts to ℝ.

6. **Lifting Criterion:**  
   Can constant map f: S² → S¹ lift to ℝ? Use lifting criterion (π₁(S²) = 0).

### Universal Cover

7. **ℝ² → T²:**  
   Prove ℝ² simply connected. Verify ℝ² = universal cover of T².

8. **S² → ℝP²:**  
   Verify S² simply connected (n=2). Why is S² universal cover of ℝP²?

9. **Figure-Eight:**  
   Universal cover của S¹ ∨ S¹ = infinite tree. Sketch structure. Why simply connected?

### Deck Transformations

10. **ℝ → S¹:**  
    Deck transformations = translations. Prove f_n(t) = t + n deck transformation.

11. **Composition:**  
    Verify Aut(ℝ/S¹) ≅ ℤ explicitly. What is generator?

12. **Antipodal:**  
    S^n → ℝP^n. Deck transformation f(x) = -x. Verify p ∘ f = p.

### Classification

13. **Subgroups ↔ Coverings:**  
    π₁(S¹) = ℤ. List all subgroups. What coverings do they correspond to?

14. **n-fold Cover:**  
    p: S¹ → S¹, p(z) = z^n. What subgroup of ℤ corresponds to this covering?

15. **Normal Covering:**  
    Universal cover always normal covering. Why? (Trivial subgroup normal.)

### Advanced

16. **Monodromy:**  
    Research monodromy action: π₁(X) acts on fiber p^(-1)(x₀). Relate to deck transformations.

17. **Galois Correspondence:**  
    Read about analogy: Covering spaces ↔ Galois theory. List parallels.

18. **Hawaiian Earring:**  
    Hawaiian earring (⋁_{n=1}^∞ S¹_n shrinking) has NO universal cover. Why? (Not semilocally simply connected.)

### Reflection

19. **Why "Universal"?:**  
    Explain why universal cover is "universal" (all coverings factor through it).

20. **Geometric Intuition:**  
    Explain covering spaces đến non-mathematician using real-world analogy (multi-story parking garage?).

21. **Applications:**  
    List three applications of covering space theory in different fields.

---

## 📚 Further Reading

- **Hatcher, §1.3:** Best modern treatment, geometric
- **Munkres, §53-54:** Careful, rigorous
- **Massey, Chapters 5-6:** Comprehensive
- **Bredon, Chapter II:** Advanced perspective
- **Spanier, Chapter 2:** Encyclopedic

---

## 🎓 Summary

Trong bài này, chúng ta học **covering space theory**—powerful tool trong algebraic topology:

✅ **Definition:** p: X̃ → X với evenly covered neighborhoods  
✅ **Examples:** ℝ → S¹, S^n → ℝP^n, ℝ² → T², tree → figure-eight  
✅ **Path Lifting:** Unique lift given starting point  
✅ **Homotopy Lifting:** Homotopies lift uniquely  
✅ **Universal Cover:** X̃ simply connected, exists under mild conditions  
✅ **Deck Transformations:** Aut(X̃/X) ≅ π₁(X) (universal cover case)  
✅ **Classification:** Coverings ↔ subgroups of π₁(X)  

**Điểm chính:**
- Covering spaces = local simplicity + global complexity
- Lifting theorems = powerful computational tools
- Universal cover = simplest covering (simply connected)
- π₁(X) = symmetry group of universal cover
- Classification theorem = topology ↔ algebra

**Geometric intuition:**
- Multiple sheets stacked over base
- Projection locally homeomorphic
- Homotopy detected by lifting
- Universal cover "unravels" space

**Practical wisdom:**
- Compute π₁ via covering spaces (most powerful method)
- Universal cover simplifies many problems
- Classification theorem reduces topology to algebra
- Deck transformations reveal symmetries

**Tiếp theo:** Lecture 06.04 về **Seifert-Van Kampen Theorem**—compute π₁ from pieces!

---

*"Covering spaces: where local meets global, and geometry becomes algebra."*

🎯 **Master covering spaces! They're the key to algebraic topology.** 🎯

---

**Previous:** [Lecture 06.02: Computing π₁](/contents/vi/topology-chapter06/06_02_Computing_Fundamental_Group/)  
**Next:** [Lecture 06.04: Van Kampen's Theorem](/contents/vi/topology-chapter06/06_04_Van_Kampen_Theorem/)
