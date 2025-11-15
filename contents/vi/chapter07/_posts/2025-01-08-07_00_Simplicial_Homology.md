---
layout: post
title: "Lecture 07.00: Simplicial Homology - Foundations"
lang: vi
lang-ref: lecture-07-00
chapter: 7
lecture: 0
categories: [chapter07]
tags: [simplicial-homology, chain-complex, boundary-operator, betti-numbers]
description: "Simplicial homology: simplices, chain complexes, boundary operator, và homology groups - second algebraic invariant"
---

**H_n(X) - Detecting Holes of All Dimensions**

---

## 📖 Tổng quan

Chúng ta đã học **fundamental group $\pi_1(X)$**—bất biến đại số đầu tiên. Nó phát hiện "1-dimensional holes" (loops).

**Nhưng còn các lỗ ở chiều cao hơn thì sao?** Hình cầu $S^2$ có "2-dimensional hole" (hollow interior)—một khoảng trống hai chiều bên trong. Tuy nhiên, $\pi_1(S^2) = 0$ không phát hiện được điều này! Điều này cho thấy rằng fundamental group chỉ có thể phát hiện các lỗ một chiều, và chúng ta cần một công cụ mạnh mẽ hơn để phát hiện các lỗ ở mọi chiều. Đó chính là **homology groups $H_n(X)$**.

**Lý thuyết Homology** cung cấp:
- **$H_n(X)$ cho mọi $n \geq 0$:** Phát hiện các lỗ $n$-chiều. Đây là một tổng quát hóa tự nhiên của fundamental group—thay vì chỉ phát hiện các lỗ một chiều, homology groups phát hiện các lỗ ở mọi chiều.
- **Có thể tính toán được hơn** so với $\pi_1$ (abelian groups, algorithmic). Đây là một lợi thế lớn—vì các homology groups là abelian, chúng ta có thể sử dụng các kỹ thuật đại số tuyến tính để tính toán chúng một cách có hệ thống.
- **Functorial:** $f: X \to Y$ cảm ứng $f_*: H_n(X) \to H_n(Y)$. Điều này có nghĩa là homology groups không chỉ là các nhóm được gán cho mỗi không gian, mà còn là một functor từ category của các topological spaces đến category của các abelian groups.
- **Homotopy invariant:** $X \simeq Y$ ⇒ $H_n(X) \cong H_n(Y)$. Đây là một tính chất cực kỳ mạnh mẽ—homology groups chỉ phụ thuộc vào homotopy type của không gian, không phụ thuộc vào chi tiết cụ thể của cấu trúc tô-pô.

![Homology detecting holes](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Simplicial_complex_example.svg/500px-Simplicial_complex_example.svg.png)  
*Simplicial complex structure - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

**Hai cách tiếp cận:**
1. **Simplicial homology** (bài học này): Yêu cầu triangulation—chia không gian thành các simplices. Đây là cách tiếp cận cổ điển và trực quan nhất.
2. **Singular homology** (bài học tiếp theo): Hoạt động cho mọi không gian—không yêu cầu triangulation. Đây là cách tiếp cận tổng quát hơn và mạnh mẽ hơn.

Trong bài học này, chúng ta sẽ khám phá simplicial homology một cách có hệ thống. Chúng ta sẽ nghiên cứu **Simplices**—các building blocks cơ bản (vertices, edges, triangles, tetrahedra). Chúng ta sẽ học về **Simplicial complexes**—các không gian được xây dựng từ các simplices. Chúng ta sẽ định nghĩa **Chain groups $C_n$**—các tổng hình thức của các $n$-simplices. Chúng ta sẽ nghiên cứu **Boundary operator $\partial$**—một cách đại số để tính toán boundary của một simplex. Chúng ta sẽ xây dựng **Chain complex**—một dãy các nhóm và các ánh xạ: $\cdots \to C_n \to C_{n-1} \to \cdots$. Chúng ta sẽ tính toán **Homology groups**—$H_n = \ker(\partial_n) / \text{im}(\partial_{n+1})$, các nhóm này phát hiện các lỗ $n$-chiều. Cuối cùng, chúng ta sẽ học về **Betti numbers**—$\text{rank}(H_n)$ đếm số lượng các lỗ $n$-chiều.

**Tại sao đây là kiến thức quan trọng?** Đây là **nền tảng** của algebraic topology—homology là một trong những công cụ quan trọng nhất trong topology đại số. Nó **có thể tính toán được**—tồn tại các thuật toán để tính toán homology groups. Nó **phổ quát**—áp dụng cho mọi chiều, không chỉ một chiều như fundamental group. Cuối cùng, các **ứng dụng** rộng rãi trong TDA (Topological Data Analysis), data analysis, physics, và biology cho thấy tầm quan trọng của homology trong các lĩnh vực khác nhau.

---

## 🔺 Simplices và Simplicial Complexes

### 1. Geometric Simplices

**Định nghĩa (n-Simplex):**  
Cho $v_0, v_1, \ldots, v_n \in \mathbb{R}^N$ **affinely independent** (không có $v_i$ nào nằm trong affine span của các điểm còn lại).

**n-simplex** $\sigma = [v_0, v_1, \ldots, v_n]$ là convex hull:

$$
\sigma = \left\{\sum_{i=0}^n t_i v_i : t_i \geq 0, \sum t_i = 1\right\}
$$

**Vertices:** $v_0, \ldots, v_n$ ($n+1$ vertices). Điều kiện affinely independent đảm bảo rằng các vertices không nằm trên cùng một hyperplane—chúng tạo thành một tập hợp độc lập về mặt affine.

**Dimension:** $\dim(\sigma) = n$. Một $n$-simplex là đối tượng cơ bản nhất trong không gian $n$-chiều—nó là "filled triangle" tổng quát hóa trong $n$ chiều.

---

**Các ví dụ:**

**0-simplex:** Một điểm duy nhất $[v_0]$ (vertex). Đây là đối tượng đơn giản nhất—chỉ là một điểm trong không gian.

**1-simplex:** $[v_0, v_1]$ = đoạn thẳng giữa hai điểm (edge). Đây là một đoạn thẳng với hai đầu mút—đối tượng cơ bản nhất trong không gian một chiều.

**2-simplex:** $[v_0, v_1, v_2]$ = filled triangle (face). Đây là một tam giác được "đổ đầy"—không chỉ là chu vi mà còn là toàn bộ vùng bên trong tam giác.

**3-simplex:** $[v_0, v_1, v_2, v_3]$ = filled tetrahedron. Đây là một tứ diện được "đổ đầy"—không chỉ là bề mặt mà còn là toàn bộ thể tích bên trong.

**n-simplex:** Generalized "filled triangle" trong $n$ dimensions. Đây là tổng quát hóa tự nhiên của tam giác đổ đầy trong không gian $n$-chiều—một đối tượng đơn giản nhất có thể có trong không gian $n$-chiều.

![Simplices](https://upload.wikimedia.org/wikipedia/commons/thumb/6/60/Simplexes.svg/500px-Simplexes.svg.png)  
*0,1,2,3-simplices - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplexes.svg)*

---

### 2. Faces of Simplices

**Định nghĩa (Face):**  
Một subset của vertices của $\sigma$ xác định một **face**. Trực giác hình học là một face là một "mặt" của simplex—một phần của simplex được xác định bởi một tập con các vertices.

**i-th face:** Loại bỏ vertex $v_i$:

$$
\partial_i \sigma = [v_0, \ldots, \hat{v}_i, \ldots, v_n]
$$

(ký hiệu hat = bỏ qua $v_i$). Đây là face đối diện với vertex $v_i$—nó là simplex được tạo thành bởi tất cả các vertices còn lại.

**Tất cả các faces:** Tất cả các subsets của vertices. Một $n$-simplex có $2^{n+1}$ faces tổng cộng—mỗi subset của vertices xác định một face.

**Ví dụ:** Tam giác $[v_0, v_1, v_2]$ có:
- 3 vertices (0-faces): $[v_0]$, $[v_1]$, $[v_2]$—các đỉnh của tam giác
- 3 edges (1-faces): $[v_0,v_1]$, $[v_1,v_2]$, $[v_0,v_2]$—các cạnh của tam giác
- 1 face (chính nó): $[v_0,v_1,v_2]$—toàn bộ tam giác

---

### 3. Simplicial Complexes

**Định nghĩa (Simplicial Complex):**  
$K$ = collection của các simplices trong $\mathbb{R}^N$ sao cho:
1. **Closed under faces:** Nếu $\sigma \in K$ và $\tau$ là face của $\sigma$, thì $\tau \in K$. Điều này có nghĩa là nếu một simplex nằm trong complex, thì tất cả các faces của nó cũng phải nằm trong complex.
2. **Proper intersections:** Nếu $\sigma, \tau \in K$, thì $\sigma \cap \tau$ là face của cả hai (hoặc rỗng). Điều này đảm bảo rằng các simplices chỉ giao nhau tại các faces chung của chúng, không giao nhau một cách "tùy ý".

**$|K|$ = geometric realization** = union của tất cả các simplices (topological space). Đây là không gian tô-pô được tạo thành bởi việc "dán" tất cả các simplices lại với nhau theo các faces chung của chúng.

---

**Các ví dụ:**

**Ví dụ 1: Boundary của tam giác**
- 3 vertices: $v_0$, $v_1$, $v_2$
- 3 edges: $[v_0,v_1]$, $[v_1,v_2]$, $[v_0,v_2]$
- KHÔNG có 2-face (hollow triangle—chỉ có chu vi, không có phần bên trong)

Đây là một 1-dimensional complex homeomorphic với $S^1$. Trực giác hình học là chúng ta chỉ có chu vi của tam giác, không có phần bên trong, và điều này tạo thành một hình tròn.

---

**Ví dụ 2: Filled triangle**
- 3 vertices
- 3 edges  
- 1 filled triangle $[v_0,v_1,v_2]$

Đây là một 2-dimensional complex homeomorphic với $D^2$ (disk). Trực giác hình học là chúng ta có toàn bộ tam giác bao gồm cả phần bên trong, và điều này tạo thành một đĩa.

---

**Ví dụ 3: Torus triangulation**
- Triangulate hình vuông, đồng nhất các cạnh một cách thích hợp
- Kết quả là một simplicial complex với $|K| \cong T^2$

Đây là một ví dụ phức tạp hơn—chúng ta có thể triangulate torus bằng cách chia một hình vuông thành các tam giác và sau đó đồng nhất các cạnh đối diện để tạo thành torus.

---

## 🔗 Chain Groups

### 1. Definition

**Định nghĩa (Chain Group):**  
Cho $K$ là simplicial complex. **n-chain group:**

$$
C_n(K) = \text{free abelian group generated by oriented n-simplices}
$$

**Các phần tử:** Các tổng hình thức với hệ số nguyên:

$$
c = \sum_{i} n_i \sigma_i \quad (n_i \in \mathbb{Z}, \sigma_i \text{ là các n-simplices})
$$

**Phép cộng:** Component-wise—chúng ta cộng các hệ số tương ứng của các simplices giống nhau.

**Ví dụ:** Nếu $\sigma_1$, $\sigma_2$ là các n-simplices, thì:
- $3\sigma_1 + 2\sigma_2 \in C_n$—một tổ hợp tuyến tính của các simplices
- $\sigma_1 - \sigma_1 = 0$—một simplex trừ đi chính nó bằng không
- $-\sigma_1$ = "$\sigma_1$ với opposite orientation"—đảo ngược hướng của simplex

Trực giác hình học là một chain là một "tổ hợp tuyến tính" của các simplices—chúng ta có thể nhân một simplex với một số nguyên và cộng các simplices lại với nhau.

---

### 2. Orientation

**Các n-simplices cần orientation:**
- **Ordering vertices:** $[v_0, \ldots, v_n]$—thứ tự của các vertices xác định orientation
- **Even permutation:** Same orientation—nếu chúng ta hoán vị các vertices bằng một even permutation, orientation không thay đổi
- **Odd permutation:** Opposite orientation—nếu chúng ta hoán vị các vertices bằng một odd permutation, orientation đảo ngược

**Ký hiệu:** $[v_0, v_1, v_2] = -[v_1, v_0, v_2]$—đảo ngược thứ tự của hai vertices đầu tiên đảo ngược orientation.

**Tại sao?** Boundary operator cần consistent signs—khi chúng ta tính toán boundary của một simplex, chúng ta cần biết hướng của các faces để có thể gán các dấu đúng. Orientation cho phép chúng ta làm điều này một cách nhất quán.

---

### 3. Properties

**$C_n(K)$ là free abelian group:**
- **Generators:** Tất cả các oriented n-simplices—mỗi oriented n-simplex là một generator
- **Rank:** Số lượng các n-simplices trong $K$—đây là số lượng các generators độc lập

**Nếu $K$ finite:** $C_n(K) \cong \mathbb{Z}^r$ trong đó $r$ = số lượng các n-simplices. Đây là một kết quả quan trọng—chain group của một simplicial complex hữu hạn là một nhóm abelian tự do với rank bằng số lượng các simplices.

**Nếu $n > \dim(K)$:** $C_n(K) = 0$ (không có n-simplices). Điều này có nghĩa là nếu chiều của complex nhỏ hơn $n$, thì không có $n$-simplices nào, và do đó chain group tầm thường.

---

## ∂ Boundary Operator

### 1. Definition

**Định nghĩa (Boundary Operator):**  
**$\partial_n: C_n(K) \to C_{n-1}(K)$** được định nghĩa trên n-simplex:

$$
\partial_n([v_0, \ldots, v_n]) = \sum_{i=0}^n (-1)^i [v_0, \ldots, \hat{v}_i, \ldots, v_n]
$$

**Mở rộng tuyến tính** đến tất cả các chains. Điều này có nghĩa là nếu chúng ta có một chain $c = \sum_i n_i \sigma_i$, thì $\partial_n(c) = \sum_i n_i \partial_n(\sigma_i)$.

---

**Trực giác hình học:** $\partial(\sigma)$ = oriented boundary của $\sigma$. Boundary operator tính toán boundary của một simplex một cách đại số—nó lấy tổng của tất cả các faces với các dấu phù hợp để đảm bảo orientation nhất quán.

**Ví dụ 1 (Edge):**  
$\sigma = [v_0, v_1]$ (oriented edge từ $v_0$ đến $v_1$).

$$
\partial([v_0, v_1]) = [v_1] - [v_0]
$$

**Orientation:** "Flows" từ $v_0$ đến $v_1$. Trực giác hình học là boundary của một đoạn thẳng là hai điểm đầu mút, nhưng với các dấu khác nhau để phản ánh hướng—điểm cuối có dấu dương và điểm đầu có dấu âm.

---

**Ví dụ 2 (Triangle):**  
$\sigma = [v_0, v_1, v_2]$ (counterclockwise).

$$
\partial([v_0, v_1, v_2]) = [v_1, v_2] - [v_0, v_2] + [v_0, v_1]
$$

**Ba edges với induced orientations.** Trực giác hình học là boundary của một tam giác là ba cạnh của nó, mỗi cạnh có orientation được cảm ứng từ orientation của tam giác. Các dấu alternating đảm bảo rằng khi chúng ta đi vòng quanh tam giác, các orientations nhất quán với nhau.

![Triangle boundary](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Triangle_boundary.svg/300px-Triangle_boundary.svg.png)  
*Oriented boundary của triangle - Nguồn concept*

---

**Ví dụ 3 (Tetrahedron):**  
$\sigma = [v_0, v_1, v_2, v_3]$.

$$
\partial(\sigma) = [v_1, v_2, v_3] - [v_0, v_2, v_3] + [v_0, v_1, v_3] - [v_0, v_1, v_2]
$$

**Bốn faces với alternating signs.** Trực giác hình học là boundary của một tứ diện là bốn mặt tam giác của nó, mỗi mặt có orientation được cảm ứng từ orientation của tứ diện. Các dấu alternating đảm bảo rằng các orientations nhất quán với nhau.

---

### 2. Key Property: ∂² = 0

**Định lý (Fundamental):**  
$\partial_{n-1} \circ \partial_n = 0$ (composition = zero map).

**Ký hiệu:** $\partial^2 = 0$ hoặc $\partial\partial = 0$.

**Ý nghĩa:** Boundary của boundary = 0. Đây là một tính chất cơ bản và quan trọng nhất của boundary operator—nếu chúng ta tính boundary của một simplex, và sau đó tính boundary của kết quả đó, chúng ta luôn nhận được không.

---

**Chứng minh (cho tam giác):**  
$\sigma = [v_0, v_1, v_2]$.

$\partial(\sigma) = [v_1, v_2] - [v_0, v_2] + [v_0, v_1]$

Áp dụng $\partial$ lần nữa:
- $\partial([v_1, v_2]) = [v_2] - [v_1]$
- $\partial([v_0, v_2]) = [v_2] - [v_0]$
- $\partial([v_0, v_1]) = [v_1] - [v_0]$

$$
\partial^2(\sigma) = ([v_2] - [v_1]) - ([v_2] - [v_0]) + ([v_1] - [v_0]) = 0
$$

Mọi thứ đều triệt tiêu! ✓ Điều này xảy ra vì mỗi vertex xuất hiện đúng hai lần với các dấu đối nhau—một lần từ một edge và một lần từ edge khác.

**Chứng minh tổng quát:** Combinatorial—các dấu triệt tiêu một cách có hệ thống. ✓

---

**Ý nghĩa hình học:**  
Boundary của tam giác = ba edges tạo thành closed loop.  
Boundary của closed loop = các endpoints triệt tiêu = 0.

**$\partial^2 = 0$ là CƠ BẢN cho lý thuyết homology!** Đây là tính chất cho phép chúng ta định nghĩa homology groups—nếu không có tính chất này, chúng ta không thể định nghĩa cycles và boundaries một cách nhất quán.

---

## 📊 Chain Complex và Homology

### 1. Chain Complex

**Định nghĩa:**  
Một dãy các abelian groups với các homomorphisms:

$$
\cdots \xrightarrow{\partial_{n+2}} C_{n+1} \xrightarrow{\partial_{n+1}} C_n \xrightarrow{\partial_n} C_{n-1} \xrightarrow{\partial_{n-1}} \cdots \xrightarrow{\partial_1} C_0 \xrightarrow{\partial_0} 0
$$

thỏa mãn **$\partial^2 = 0$** (im($\partial_{n+1}$) $\subseteq$ ker($\partial_n$)).

**Đây là chain complex của $K$.** Trực giác hình học là một chain complex là một dãy các chain groups được kết nối bởi các boundary operators—mỗi chain group chứa các chains ở một chiều cụ thể, và boundary operator ánh xạ chúng xuống chiều thấp hơn. Điều kiện $\partial^2 = 0$ đảm bảo rằng image của một boundary operator nằm trong kernel của boundary operator tiếp theo.

---

### 2. Cycles và Boundaries

**Định nghĩa (n-Cycles):**  
$Z_n(K) = \ker(\partial_n) = \{c \in C_n : \partial c = 0\}$

**Chains với no boundary.** Trực giác hình học là một cycle là một chain không có boundary—nó "đóng kín" trong một cách nào đó. Ví dụ, một closed loop trong một graph là một 1-cycle—nó không có điểm đầu và điểm cuối.

**Ví dụ:** Closed loop trong graph = 1-cycle. Đây là một ví dụ trực quan—một vòng lặp đóng trong một graph là một cycle vì nó không có boundary.

---

**Định nghĩa (n-Boundaries):**  
$B_n(K) = \text{im}(\partial_{n+1}) = \{\partial d : d \in C_{n+1}\}$

**Chains that ARE boundaries của something.** Trực giác hình học là một boundary là một chain mà chính nó là boundary của một chain ở chiều cao hơn. Ví dụ, boundary của một tam giác là boundary của chính tam giác đó.

**Ví dụ:** Triangle boundary = boundary của filled triangle = 1-boundary. Đây là một ví dụ cụ thể—chu vi của một tam giác là boundary của chính tam giác đó.

---

**Bổ đề:** $B_n \subseteq Z_n$ (boundaries are cycles).

**Chứng minh:** Nếu $c \in B_n$, thì $c = \partial d$ cho một số $d$.  
$\partial c = \partial(\partial d) = \partial^2 d = 0$ ⇒ $c \in Z_n$. ✓

**Điều này suy ra từ $\partial^2 = 0$!** Đây là một kết quả quan trọng—mọi boundary đều là một cycle, nhưng không phải mọi cycle đều là một boundary. Sự khác biệt giữa cycles và boundaries chính là homology groups.

---

### 3. Homology Groups

**Định nghĩa (Homology Groups):**

$$
H_n(K) = Z_n(K) / B_n(K) = \ker(\partial_n) / \text{im}(\partial_{n+1})
$$

**Quotient group: cycles modulo boundaries.** Trực giác hình học là homology group đo lường các "lỗ" $n$-chiều trong không gian—nó là tập hợp các cycles không phải là boundaries, được xác định modulo các boundaries. Nếu một cycle là boundary của một chain ở chiều cao hơn, thì nó được coi là "tầm thường" trong homology group. Chỉ những cycles không phải là boundaries mới đại diện cho các "lỗ" thực sự trong không gian.

---

**Trực giác:**

**$H_n$ phát hiện "n-dimensional holes":**
- **Cycles:** Bao quanh các lỗ—một cycle là một chain đóng kín có thể bao quanh một lỗ
- **Boundaries:** Không phải lỗ thực sự (filled)—một boundary là boundary của một chain ở chiều cao hơn, nghĩa là nó "được lấp đầy"
- **$H_n$:** Các lỗ thực sự = các cycles không phải là boundaries—đây là các cycles không thể được "lấp đầy" bởi một chain ở chiều cao hơn

**Ví dụ:** Hollow sphere $S^2$:
- Closed surface = 2-cycle—bề mặt đóng của hình cầu là một 2-cycle
- Không phải boundary (hollow inside)—nó không phải là boundary của một 3-chain vì bên trong là rỗng
- ⇒ Non-zero element trong $H_2(S^2) \cong \mathbb{Z}$—điều này có nghĩa là hình cầu có một lỗ hai chiều

---

### 4. Properties

**$H_n(K)$ là abelian group** (luôn luôn! Khác với $\pi_1$ có thể không abelian). Đây là một lợi thế lớn của homology so với fundamental group—vì các homology groups là abelian, chúng ta có thể sử dụng các kỹ thuật đại số tuyến tính để tính toán chúng.

**Finitely generated:** Nếu $K$ là finite complex. Điều này có nghĩa là homology group có thể được biểu diễn như một tổng hữu hạn của các cyclic groups.

**Structure Theorem:** $H_n(K) \cong \mathbb{Z}^r \oplus$ (torsion). Đây là một kết quả quan trọng trong lý thuyết nhóm abelian—mọi nhóm abelian hữu hạn sinh đều có thể được phân tích thành một phần tự do (tổng của các $\mathbb{Z}$) và một phần torsion (các nhóm cyclic hữu hạn).

**Betti number:** $\beta_n = \text{rank}(H_n)$ = số lượng các $\mathbb{Z}$ summands (đếm các lỗ). Đây là một số quan trọng trong topology—nó cho biết có bao nhiêu lỗ $n$-chiều trong không gian.

**Torsion:** Các nhóm cyclic hữu hạn (subtle topology). Phần torsion của homology group phản ánh các tính chất topology tinh tế hơn—những tính chất không thể được phát hiện chỉ bằng cách đếm các lỗ.

---

## 🔢 Examples

### Ví dụ 1: Điểm

$K$ = single vertex.

**Chain groups:**
- $C_0 = \mathbb{Z}$ (one generator—chỉ có một vertex)
- $C_n = 0$ cho $n > 0$ (không có simplices ở chiều cao hơn)

**Boundaries:** $B_0 = 0$, $B_n = 0$ $\forall n$ (không có boundaries vì không có simplices ở chiều cao hơn)

**Cycles:** $Z_0 = \mathbb{Z}$, $Z_n = 0$ ($n > 0$) (mọi 0-chain đều là cycle vì không có boundary operator từ $C_0$)

**Homology:**
- $H_0 = \mathbb{Z}/0 = \mathbb{Z}$ (connected component)
- $H_n = 0$ cho $n > 0$ (không có lỗ ở chiều cao hơn)

**Giải thích:** Điểm là connected ($H_0 = \mathbb{Z}$), không có lỗ ở chiều cao hơn. Đây là ví dụ đơn giản nhất—một điểm chỉ có một thành phần liên thông và không có lỗ nào.

---

### Ví dụ 2: Hình tròn $S^1$

Triangulate với 3 vertices, 3 edges (minimal—triangulation nhỏ nhất có thể).

**Chain groups:**
- $C_0 = \mathbb{Z}^3$ (3 vertices—mỗi vertex là một generator)
- $C_1 = \mathbb{Z}^3$ (3 edges—mỗi edge là một generator)
- $C_n = 0$ ($n \geq 2$) (không có simplices ở chiều cao hơn)

**Tính toán boundaries:**
- $\partial$(mỗi edge) = difference của vertices—boundary của mỗi edge là hiệu của hai vertices đầu mút
- Sum của 3 edges (full loop) → $\partial = 0$—tổng của ba edges tạo thành một vòng lặp đóng, và boundary của nó bằng không

**Kết quả:**
- **$H_0(S^1) = \mathbb{Z}$** (connected—hình tròn là connected)
- **$H_1(S^1) = \mathbb{Z}$** (one 1-dimensional hole—the loop!—hình tròn có một lỗ một chiều, chính là vòng lặp)
- $H_n = 0$ ($n \geq 2$) (không có lỗ ở chiều cao hơn)

**$\beta_0 = 1$, $\beta_1 = 1$:** Hình tròn có một "lỗ". Đây là một ví dụ quan trọng—hình tròn có một thành phần liên thông và một lỗ một chiều, được phản ánh trong $H_0$ và $H_1$.

---

### Ví dụ 3: Hình cầu $S^2$

Triangulate (ví dụ, icosahedron—chia hình cầu thành các tam giác).

**Tính toán cho:**
- **$H_0(S^2) = \mathbb{Z}$** (connected—hình cầu là connected)
- **$H_1(S^2) = 0$** (no 1-holes—không có lỗ một chiều vì mọi loop đều có thể co lại về một điểm)
- **$H_2(S^2) = \mathbb{Z}$** (hollow 2-dimensional interior!—hình cầu có một lỗ hai chiều, chính là khoảng trống bên trong)
- $H_n = 0$ ($n \geq 3$) (không có lỗ ở chiều cao hơn)

**Giải thích:** Hình cầu bao quanh một lỗ hai chiều. Đây là một ví dụ quan trọng cho thấy cách homology phát hiện các lỗ ở chiều cao hơn—fundamental group không thể phát hiện lỗ hai chiều này ($\pi_1(S^2) = 0$), nhưng homology group $H_2(S^2) = \mathbb{Z}$ phát hiện được nó.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Henri Poincaré** - *"Analysis Situs"* (1895-1904)  
   *Introduced homology implicitly*

2. **Emmy Noether** - *Group theory approach* (1920s)  
   *Algebraic foundations*

3. **Leopold Vietoris** - *"Über den höheren Zusammenhang"* (1927)  
   *Homology theory formalized*

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§2.1: Simplicial Homology**  
   *Outstanding modern treatment*

5. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapters 1-2**  
   *Clear, computational*

6. **Glen E. Bredon** - *Topology and Geometry*, **Chapter IV**

7. **Joseph J. Rotman** - *An Introduction to Algebraic Topology*, **Chapters 5-6**

---

## 🔗 Applications and Connections

### Topological Data Analysis (TDA)
**Persistent Homology:** Compute H_n at multiple scales. Detects features (holes) in point cloud data. Applications: shape recognition, biology, sensor networks.

### Computational Topology
**Algorithm:** Matrix reduction computes H_n. Software: CHomP, Dionysus, GUDHI. Used in graphics, robotics.

### Physics - Condensed Matter
**Topological Phases:** Homology classifies topological insulators. Betti numbers = topological invariants.

### Biology - Protein Structure
**Void Analysis:** Cavities trong proteins characterized by H₁, H₂. Drug binding sites detection.

### Sensor Networks
**Coverage Holes:** H₁ detects gaps trong sensor coverage. Network optimization.

---

## 🧩 Exercises

### Simplices

1. **Draw:** Sketch 0,1,2,3-simplices. Label vertices.

2. **Faces:** List all faces của [v₀,v₁,v₂,v₃]. How many of each dimension?

3. **Dimension:** n-simplex has how many k-faces? (Binomial coefficient.)

### Chain Groups

4. **Compute:** K = triangle boundary. What is C₀, C₁, C₂?

5. **Orientation:** [v₀,v₁,v₂] = -[v₁,v₀,v₂]. Verify này preserves boundary formula.

### Boundary Operator

6. **Verify ∂²=0:** For tetrahedron [v₀,v₁,v₂,v₃], compute ∂²(σ) explicitly.

7. **Geometric:** Explain intuitively why boundary of boundary = 0.

### Homology Computation

8. **Point:** Verify H₀(point) = ℤ, H_n = 0 (n>0).

9. **Two Points:** Compute H₀(v₀ ⊔ v₁) = ℤ ⊕ ℤ (two components).

10. **Circle:** Triangulate S¹ với 4 vertices. Compute H₀, H₁ carefully.

### Examples

11. **Disk D²:** Triangulate. Compute H₀ = ℤ, H₁ = H₂ = 0.

12. **Torus T²:** Sketch triangulation. Predict H₀ = ℤ, H₁ = ℤ², H₂ = ℤ.

### Advanced

13. **Euler Characteristic:** χ = Σ(-1)ⁿ β_n. Verify for S¹, S², T².

14. **Connected Sum:** H_*(Σ_g) for genus g surface. Research formula.

15. **ℝP²:** Compute H₀ = ℤ, H₁ = ℤ/2ℤ, H₂ = 0 (non-orientable!).

---

## 📚 Further Reading

- **Hatcher, §2.1:** Best modern treatment
- **Munkres, Elements:** Computational focus
- **Rotman:** Detailed computations
- **Edelsbrunner & Harer:** *Computational Topology* (TDA)

---

## 🎓 Summary

Trong bài này, chúng ta learned **simplicial homology**—foundation của homology theory:

✅ **Simplices:** Geometric building blocks (vertices → tetrahedra)  
✅ **Chain Groups:** C_n = free abelian on n-simplices  
✅ **Boundary Operator:** ∂_n: C_n → C_(n-1) với ∂² = 0  
✅ **Chain Complex:** ... → C_n → C_(n-1) → ...  
✅ **Homology:** H_n = ker(∂_n) / im(∂_(n+1))  
✅ **Examples:** H_*(point), H_*(S¹), H_*(S²)  

**Điểm chính:**
- Homology detects holes of all dimensions
- ∂² = 0 is fundamental
- H_n = cycles / boundaries
- Computable via matrices
- Abelian (simpler than π₁)

**Geometric intuition:**
- Cycles surround holes
- Boundaries are "filled"
- H_n counts true holes

**Tiếp theo:** Lecture 07.01 về **Singular Homology**—works for ANY space!

---

*"Homology: where chains become algebra, and holes become numbers."*

🎯 **Master simplicial homology! It's the computational foundation.** 🎯

---

**Previous Chapter:** [Chapter 06: Fundamental Group](/contents/vi/topology-chapter06/)  
**Next:** [Lecture 07.01: Singular Homology](/contents/vi/topology-chapter07/07_01_Singular_Homology/)
