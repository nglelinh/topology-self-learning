---
layout: post
title: "Lecture 07.02: Homology Computations"
lang: vi
lang-ref: lecture-07-02
chapter: 7
lecture: 2
categories: [chapter07]
tags: [homology-computations, euler-characteristic, betti-numbers]
description: "Computing H_n: systematic examples (Sⁿ, surfaces, CW complexes), Euler characteristic, cellular homology"
---

**Systematic Methods and Standard Examples**

---

## 📖 Tổng quan

**Lý thuyết đẹp, nhưng làm sao TÍNH TOÁN $H_n(X)$?**

Tính toán trực tiếp từ định nghĩa (singular chains) = thường là không thể! Có vô số singular simplices, các chain groups được sinh bởi vô số generators, và chúng ta cần các phương pháp thông minh hơn.

**Các phương pháp tính toán:**
1. **Homotopy equivalence:** $X \simeq Y$, $H_n(X) = H_n(Y)$—sử dụng homotopy equivalence để đơn giản hóa không gian trước khi tính toán
2. **CW complexes:** Cellular homology (finite computations!)—sử dụng cấu trúc CW để tính toán homology một cách hữu hạn
3. **Mayer-Vietoris sequence:** Phân tích không gian—chia không gian thành các phần và tính toán homology từ các phần đó
4. **Long exact sequences:** Các cặp $(X, A)$, fibrations—sử dụng các dãy khớp dài để tính toán homology
5. **Spectral sequences:** Công cụ có hệ thống nâng cao—một công cụ mạnh mẽ cho các tính toán phức tạp

Trong bài học này, chúng ta sẽ tập trung vào các ví dụ chuẩn và cellular homology—những công cụ thực tế nhất để tính toán homology.

![CW complex structure](https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/CW-komplex-1.svg/400px-CW-komplex-1.svg.png)  
*CW complex built from cells - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:CW-komplex-1.svg)*

**Nội dung:**
- **Point, contractible spaces:** Trivial homology—các không gian đơn giản nhất với homology tầm thường
- **Spheres $S^n$:** Fundamental examples—các ví dụ cơ bản cho thấy cách homology phát hiện các lỗ ở mọi chiều
- **Torus $T^2$:** First nontrivial surface—surface đầu tiên không tầm thường với homology thú vị
- **Surfaces $\Sigma_g$:** Genus $g$ classification—phân loại các surfaces theo genus và cách homology phản ánh điều này
- **CW complexes:** Cellular homology algorithm—thuật toán thực tế để tính toán homology của CW complexes
- **Euler characteristic:** Topological invariant—bất biến tô-pô quan trọng liên quan đến homology
- **Betti numbers:** Counting holes—đếm số lượng các lỗ trong không gian

**Tại sao đây là kiến thức quan trọng?** Đây là **các tính toán chuẩn** mà mọi người phải biết—những ví dụ này xuất hiện khắp nơi trong topology. **Pattern recognition**—nhìn thấy cách homology phát hiện các lỗ giúp chúng ta hiểu sâu hơn về lý thuyết. **Computational tools**—Cellular homology = practical algorithm cho phép chúng ta tính toán homology một cách có hệ thống. Cuối cùng, đây là **nền tảng** để xây dựng trực giác cho lý thuyết tổng quát.

---

## 🎯 Basic Computations

### Ví dụ 1: Điểm

$X = \{\text{pt}\}$.

**Lập luận homotopy:** Điểm = 0-dimensional, minimal. Đây là không gian đơn giản nhất có thể có.

**Tính toán trực tiếp:**
- $C_n = \mathbb{Z}$ (single constant map $\Delta^n \to \text{pt}$)—chỉ có một cách ánh xạ standard simplex vào một điểm, đó là ánh xạ hằng
- All $\partial = 0$ (no other simplices to map to)—không có simplices khác để ánh xạ đến, nên boundary operator bằng không
- $Z_n = C_n$, $B_n = 0$ (except $B_0$)—mọi chain đều là cycle vì boundary bằng không

**Kết quả:**

$$
H_n(\text{pt}) = \begin{cases}
\mathbb{Z} & n = 0 \\
0 & n > 0
\end{cases}
$$

**Giải thích:** Connected (một thành phần liên thông), không có lỗ ở chiều cao hơn. Đây là ví dụ cơ bản nhất—một điểm chỉ có một thành phần liên thông và không có lỗ nào.

---

### Ví dụ 2: Không gian Contractible

$X$ contractible ⇒ $X \simeq \text{pt}$.

**Homotopy invariance:**

$$
H_n(X) \cong H_n(\text{pt})
$$

**Kết quả:**  
$H_0(X) = \mathbb{Z}$, $H_n(X) = 0$ ($n > 0$). Đây là một kết quả quan trọng—mọi không gian contractible đều có homology giống như một điểm.

**Các ví dụ:**
- **$\mathbb{R}^n$:** Contractible ⇒ trivial homology—không gian Euclid có homology tầm thường
- **$D^n$ (disk):** Contractible ⇒ trivial homology—đĩa có homology tầm thường
- **Star-shaped regions:** Contractible—các vùng hình sao có thể co về một điểm
- **Cone $CX$:** Always contractible—cone của bất kỳ không gian nào đều contractible

Đây là một lớp không gian rộng lớn với homology tầm thường—bất kỳ không gian nào có thể co về một điểm đều có homology giống như một điểm.

**Powerful principle:** Reduce to homotopy equivalence!

---

## 🔵 Spheres

### Định lý: $H_n(S^k)$

**Định lý:**

$$
H_n(S^k) = \begin{cases}
\mathbb{Z} & n = 0 \\
\mathbb{Z} & n = k \\
0 & \text{otherwise}
\end{cases}
$$

**Hai homology groups không tầm thường:**
- **$H_0 = \mathbb{Z}$:** Connected—hình cầu là connected
- **$H_k = \mathbb{Z}$:** k-dimensional "hole" (hollow interior)—hình cầu có một lỗ $k$-chiều, chính là khoảng trống bên trong

Đây là một kết quả quan trọng—hình cầu $k$-chiều có homology tầm thường ở mọi chiều ngoại trừ chiều $0$ và chiều $k$. Điều này phản ánh cách hình cầu có một lỗ ở chiều cao nhất của nó.

---

### Chứng minh Sketch (Phương pháp CW Complex)

**CW structure cho $S^k$:**
- One 0-cell $e^0$ (point)—một điểm
- One k-cell $e^k$ (attach $D^k$ to point)—một $k$-cell được dán vào điểm

**Cellular chain complex:**

$$
0 \to \mathbb{Z} \xrightarrow{\partial_k} \mathbb{Z} \to 0
$$

(Chỉ $C_0$ và $C_k$ không tầm thường)

**Boundary map $\partial_k$:**  
Attaching map $S^{k-1} \to e^0$ = constant (degree 0). Đây là điểm quan trọng—attaching map là constant, nghĩa là nó ánh xạ toàn bộ boundary của $k$-cell vào một điểm.

**$\partial_k = 0$!** Điều này có nghĩa là boundary map bằng không vì attaching map là constant.

**Homology:**
- $H_0 = \mathbb{Z}/0 = \mathbb{Z}$—một thành phần liên thông
- $H_k = \mathbb{Z}/0 = \mathbb{Z}$—một lỗ $k$-chiều
- Others = 0—không có lỗ ở các chiều khác

✓ **QED**

---

### Các trường hợp cụ thể

**$S^0$ = hai điểm:**  
$H_0(S^0) = \mathbb{Z} \oplus \mathbb{Z}$ (hai components!)—hình cầu không chiều là hai điểm rời nhau, nên có hai thành phần liên thông.

**$S^1$ (circle):**  
$H_0(S^1) = \mathbb{Z}$, $H_1(S^1) = \mathbb{Z}$, $H_n = 0$ ($n \geq 2$). Hình tròn có một thành phần liên thông và một lỗ một chiều—chính là vòng lặp.

**$S^2$ (sphere):**  
$H_0(S^2) = \mathbb{Z}$, $H_2(S^2) = \mathbb{Z}$, $H_1 = 0$. Hình cầu hai chiều có một thành phần liên thông và một lỗ hai chiều—khoảng trống bên trong. Điều thú vị là $H_1 = 0$—không có lỗ một chiều vì mọi loop đều có thể co lại về một điểm.

**$S^3$:**  
$H_0(S^3) = \mathbb{Z}$, $H_3(S^3) = \mathbb{Z}$. Hình cầu ba chiều có một thành phần liên thông và một lỗ ba chiều.

**Pattern rõ ràng!** Mỗi hình cầu $S^k$ có một thành phần liên thông ($H_0 = \mathbb{Z}$) và một lỗ ở chiều cao nhất của nó ($H_k = \mathbb{Z}$), và không có lỗ ở các chiều khác.

---

## 🍩 Torus T²

### CW Structure

**Torus $T^2 = S^1 \times S^1$:**

**CW complex:**
- 1 vertex $e^0$—một đỉnh
- 2 edges $a$, $b$ (loops)—hai cạnh tạo thành các vòng lặp
- 1 square $e^2$ (2-cell)—một ô vuông được dán vào skeleton

**Attaching:** Square boundary = $aba^{-1}b^{-1}$ (commutator). Đây là cách chúng ta dán square vào skeleton—boundary của square được ánh xạ vào skeleton theo thứ tự $a$, $b$, $a^{-1}$, $b^{-1}$.

---

### Cellular Chain Complex

**Chain groups:**
- $C_0 = \mathbb{Z}$ (one vertex)—một generator cho vertex
- $C_1 = \mathbb{Z}^2$ (two edges $a$, $b$)—hai generators cho hai edges
- $C_2 = \mathbb{Z}$ (one 2-cell)—một generator cho square

**Boundary maps:**

$$
C_2 \xrightarrow{\partial_2} C_1 \xrightarrow{\partial_1} C_0
$$

**$\partial_2(e^2)$:** Boundary của square = $a + b - a - b = 0$ (after cancellation). Đây là điểm quan trọng—boundary của square triệt tiêu vì chúng ta đi qua mỗi edge hai lần với các dấu đối nhau.

**$\partial_1(a) = \partial_1(b) = 0$** (loops based at vertex). Các edges là loops nên không có boundary—chúng bắt đầu và kết thúc tại cùng một vertex.

---

### Tính toán Homology

**$H_1$:**
- **$Z_1 = \ker(\partial_1) = \mathbb{Z}^2$** (cả hai loops đều đóng—chúng không có boundary vì là loops)
- **$B_1 = \text{im}(\partial_2) = \{0\}$** ($\partial_2 = 0$ vì boundary của square triệt tiêu)
- **$H_1 = \mathbb{Z}^2 / \{0\} = \mathbb{Z}^2$** ✓

Điều này có nghĩa là torus có hai lỗ một chiều độc lập—một theo hướng meridian và một theo hướng longitude.

**$H_0$:**
- **$Z_0 = \ker(\partial_0) = \mathbb{Z}$** (tất cả các 0-chains đều đóng—không có boundary operator từ $C_0$)
- **$B_0 = \text{im}(\partial_1) = \{0\}$** (không có boundaries vì các edges là loops)
- **$H_0 = \mathbb{Z}$** ✓ (connected—torus là connected)

**$H_2$:**
- **$Z_2 = \ker(\partial_2 \to C_1) = \mathbb{Z}$** ($\partial_2 = 0$ nên mọi 2-chain đều là cycle)
- **$B_2 = \text{im}(\partial_3) = \{0\}$** (không có 3-cells)
- **$H_2 = \mathbb{Z}$** ✓

Điều này có nghĩa là torus có một lỗ hai chiều—khoảng trống bên trong torus.

---

### Kết quả

$$
H_*(T^2) = \mathbb{Z}, \mathbb{Z}^2, \mathbb{Z}, 0, 0, \ldots
$$

**Giải thích:**
- **$H_0 = \mathbb{Z}$:** Connected—torus có một thành phần liên thông
- **$H_1 = \mathbb{Z}^2$:** Hai lỗ một chiều độc lập (meridian, longitude)—torus có hai hướng độc lập để tạo thành loops
- **$H_2 = \mathbb{Z}$:** Một lỗ hai chiều (hollow interior)—torus có một khoảng trống hai chiều bên trong

**Betti numbers:** $\beta_0 = 1$, $\beta_1 = 2$, $\beta_2 = 1$. Đây là các số đếm số lượng các lỗ ở mỗi chiều—torus có một thành phần liên thông, hai lỗ một chiều, và một lỗ hai chiều.

**Euler characteristic:** $\chi(T^2) = 1 - 2 + 1 = 0$. Đây là một tính chất quan trọng của torus—Euler characteristic bằng không, phản ánh cách torus có thể được xây dựng từ một hình vuông với các cạnh đối diện được đồng nhất.

---

## 🏔️ Surfaces Σ_g

### Phân loại

**Orientable closed surface genus $g$:**

![Genus surfaces](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Torus_cycles.png/400px-Torus_cycles.png)  
*Torus với các cycles cơ bản - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus_cycles.png)*

**CW structure:**
- 1 vertex—một đỉnh
- $2g$ edges (loops $a_1$, $b_1$, $\ldots$, $a_g$, $b_g$)—$2g$ cạnh tạo thành các vòng lặp, mỗi "lỗ" đóng góp hai loops
- 1 face ($4g$-gon với boundary relation)—một mặt được tạo thành từ một đa giác $4g$ cạnh với boundary relation phản ánh cách các edges được dán lại

---

### Homology

**Tính toán Cellular:**

**$H_0(\Sigma_g) = \mathbb{Z}$** (connected—mọi surface đều connected)

**$H_1(\Sigma_g) = \mathbb{Z}^{2g}$** ($2g$ independent loops—mỗi "lỗ" đóng góp hai loops độc lập, một cho mỗi hướng)

**$H_2(\Sigma_g) = \mathbb{Z}$** (surface encloses hollow region—surface bao quanh một vùng rỗng hai chiều)

Đây là một kết quả quan trọng—homology của một surface chỉ phụ thuộc vào genus $g$, không phụ thuộc vào cách cụ thể mà surface được xây dựng.

---

### Các trường hợp cụ thể

**$g = 0$ ($S^2$):**  
$H_1 = 0$ (no loops—simply connected). Hình cầu không có lỗ một chiều vì mọi loop đều có thể co lại về một điểm.

**$g = 1$ ($T^2$):**  
$H_1 = \mathbb{Z}^2$ (two loops). Torus có hai lỗ một chiều độc lập—một theo hướng meridian và một theo hướng longitude.

**$g = 2$:**  
$H_1 = \mathbb{Z}^4$ (four loops). Surface với genus 2 có bốn lỗ một chiều độc lập—mỗi "lỗ" đóng góp hai loops.

**Tổng quát:** Rank của $H_1$ = $2g$ = genus invariant! Đây là một kết quả quan trọng—rank của $H_1$ hoàn toàn xác định genus của surface, và đây là một bất biến tô-pô mạnh mẽ.

---

### Euler Characteristic

**$\chi(\Sigma_g) = 2 - 2g$**

**Các ví dụ:**
- $S^2$ ($g=0$): $\chi = 2$—hình cầu có Euler characteristic dương
- $T^2$ ($g=1$): $\chi = 0$—torus có Euler characteristic bằng không
- Genus 2: $\chi = -2$—surfaces với genus cao hơn có Euler characteristic âm

**$\chi$ xác định genus cho orientable surfaces!** Đây là một kết quả quan trọng—Euler characteristic hoàn toàn xác định genus của một orientable surface, và đây là một cách thuận tiện để tính toán genus.

---

## 🏗️ Cellular Homology

### 1. CW Complexes Review

**CW complex $X$:** Được xây dựng một cách quy nạp:
- Bắt đầu: discrete 0-cells (vertices)—bắt đầu với một tập hợp các điểm rời rạc
- Attach n-cells: glue $D^n$ along boundary $S^{n-1}$—dán các $n$-cells vào skeleton hiện có dọc theo boundary của chúng

**n-skeleton $X^{(n)}$:** Tất cả các cells có chiều $\leq n$. Đây là "bộ xương" của CW complex—tất cả các cells từ chiều 0 đến chiều $n$.

**Các ví dụ:** Spheres, tori, surfaces, manifolds, hầu hết các không gian "nice". CW complexes là một lớp không gian rất rộng và quan trọng trong topology.

---

### 2. Cellular Chain Complex

**Cellular chain groups:**

$$
C_n^{CW}(X) = H_n(X^{(n)}, X^{(n-1)})
$$

**(Relative homology của các skeleta)** Trực giác hình học là cellular chain group ở chiều $n$ đo lường các "cells" $n$-chiều trong CW complex—nó là relative homology của $n$-skeleton modulo $(n-1)$-skeleton.

**Finitely generated:** Nếu finite CW complex, mỗi $C_n$ là free abelian với rank = số lượng các $n$-cells. Đây là một lợi thế lớn so với singular homology—cellular chain groups là hữu hạn sinh cho finite CW complexes.

**Boundary map $\partial_n$:** Được cảm ứng bởi các inclusions (công thức rõ ràng qua degree). Boundary map được tính toán bằng cách xem xét cách các $n$-cells được dán vào $(n-1)$-skeleton.

---

### 3. Định lý Cellular Homology

**Định lý:**  
Cho CW complex $X$:

$$
H_n^{CW}(X) \cong H_n(X)
$$

**(Cellular homology = singular homology)** Đây là một kết quả cực kỳ mạnh mẽ—cellular homology và singular homology cho cùng kết quả, nhưng cellular homology thường dễ tính toán hơn nhiều.

**Sức mạnh:** Cellular chains FINITELY GENERATED (cho finite CW complexes)! Đây là điểm quan trọng—thay vì làm việc với vô số singular simplices, chúng ta chỉ cần làm việc với một số hữu hạn các cells.

**Thuật toán:** Tính toán $H_n$ bằng đại số tuyến tính trên chain complex hữu hạn chiều. Đây là một thuật toán thực tế—chúng ta có thể tính toán homology bằng cách giải các hệ phương trình tuyến tính trên các không gian vector hữu hạn chiều.

---

### 4. Ví dụ: $\mathbb{R}P^2$

**CW structure:**
- 1 vertex $e^0$—một đỉnh
- 1 edge $e^1$ (loop)—một cạnh tạo thành vòng lặp
- 1 disk $e^2$ (attach với antipodal identification)—một đĩa được dán với đồng nhất đối cực

**Cellular chains:**
- $C_0 = \mathbb{Z}$—một generator cho vertex
- $C_1 = \mathbb{Z}$—một generator cho edge
- $C_2 = \mathbb{Z}$—một generator cho disk

**Boundary:** $\partial_2(e^2) = 2e^1$ (boundary wraps twice). Đây là điểm quan trọng—boundary của disk được ánh xạ vào edge hai lần vì antipodal identification, nên boundary map nhân với 2.

**Homology:**
- $H_0 = \mathbb{Z}$ (connected)—projective plane là connected
- $H_1 = \mathbb{Z}/2\mathbb{Z}$ (torsion!)—đây là ví dụ đầu tiên về torsion trong homology
- $H_2 = 0$ (cycle = 2 × boundary)—không có lỗ hai chiều vì cycle là bội của boundary

**Ví dụ đầu tiên về torsion!** Đây là một khám phá quan trọng—projective plane có homology với torsion, không chỉ là free abelian groups. Điều này phản ánh tính chất không định hướng được của projective plane.

---

## 🔢 Euler Characteristic

### Định nghĩa

**Euler characteristic:**

$$
\chi(X) = \sum_{n=0}^\infty (-1)^n \beta_n
$$

trong đó $\beta_n = \text{rank}(H_n(X))$ (Betti numbers).

**Alternating sum của các ranks của homology.** Trực giác hình học là Euler characteristic là một cách đo lường "tổng thể" của topology của không gian—nó là tổng alternating của các Betti numbers, phản ánh cách các lỗ ở các chiều khác nhau tương tác với nhau.

---

### Định lý (Euler-Poincaré)

Cho CW complex:

$$
\chi(X) = \sum_{n=0}^\infty (-1)^n (\text{số lượng các } n\text{-cells})
$$

**Đồng ý với công thức cổ điển $V - E + F$!** Đây là một kết quả đẹp—Euler characteristic có thể được tính toán từ homology groups hoặc từ số lượng các cells trong CW complex, và cả hai cách cho cùng kết quả. Đối với các polyhedra trong không gian ba chiều, công thức này trở thành $V - E + F$ (vertices - edges + faces).

---

### Các ví dụ

**$S^2$:**  
$\chi = \beta_0 - \beta_1 + \beta_2 = 1 - 0 + 1 = 2$

CW: 2 vertices, 1 edge, 1 face (nghĩ về hemisphere decomposition).  
Alternative: 1 vertex, 0 edges, 1 2-cell ⇒ $1 - 0 + 1 = 2$. ✓ Cả hai cách tính đều cho cùng kết quả, minh họa tính nhất quán của Euler characteristic.

**$T^2$:**  
$\chi = 1 - 2 + 1 = 0$. Torus có Euler characteristic bằng không, phản ánh cách nó có thể được xây dựng từ một hình vuông với các cạnh đối diện được đồng nhất.

**$\Sigma_g$:**  
$\chi = 1 - 2g + 1 = 2 - 2g$. Đây là công thức tổng quát cho orientable surfaces—Euler characteristic giảm khi genus tăng.

**$\mathbb{R}P^2$:**  
$\chi = 1 - 0 + 0 = 1$ (sử dụng $\beta_1$ = torsion rank 0). Projective plane có Euler characteristic bằng 1, khác với hình cầu mặc dù cả hai đều là surfaces.

---

### Các tính chất

1. **Homotopy invariant:** $X \simeq Y$ ⇒ $\chi(X) = \chi(Y)$. Đây là một tính chất mạnh mẽ—Euler characteristic chỉ phụ thuộc vào homotopy type của không gian.

2. **Multiplicative:** $\chi(X \times Y) = \chi(X) \cdot \chi(Y)$. Euler characteristic của tích là tích của các Euler characteristics.

3. **Additive:** $\chi(X \cup Y) = \chi(X) + \chi(Y) - \chi(X \cap Y)$ (nếu intersection "nice"). Đây là một tính chất quan trọng cho phép chúng ta tính toán Euler characteristic bằng cách chia không gian thành các phần.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Leonhard Euler** - *"Solutio problematis ad geometriam situs pertinentis"* (1736)  
   *V - E + F formula*

2. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Homology and Betti numbers*

3. **J.H.C. Whitehead** - *"Combinatorial homotopy"* (1949)  
   *CW complexes and cellular homology*

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§2.1-2.2**

5. **Glen E. Bredon** - *Topology and Geometry*, **Chapter IV**

6. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapter 2**

---

## 🔗 Applications

### Computer Graphics - Mesh Processing
**Euler Characteristic Check:** Verify 3D mesh topology. Detect errors in scanned models.

### Robotics - Configuration Spaces
**Homology Computation:** Understand configuration space topology. Motion planning algorithms.

### Data Science - Shape Analysis
**Persistent Homology:** Track Betti numbers across scales. Feature detection in data.

---

## 🧩 Exercises

### Basic Computations

1. **Two Points:**  
   X = {pt₁, pt₂} (discrete). Compute H_n(X).

2. **Interval:**  
   X = [0,1]. Use contractibility: H_n = ?

3. **Figure-Eight:**  
   S¹ ∨ S¹. Compute H₁ (hint: wedge axiom).

### Spheres

4. **Verify:**  
   H_n(S³) using CW complex (one 0-cell, one 3-cell).

5. **Suspension:**  
   Σ(Sⁿ) = Sⁿ⁺¹. Verify homology agrees.

### Surfaces

6. **Klein Bottle:**  
   CW structure: 1 vertex, 2 edges, 1 face.  
   Compute H_n. (Answer: H₁ = ℤ ⊕ ℤ/2ℤ)

7. **ℝP³:**  
   H_n(ℝP³) = ℤ, ℤ/2ℤ, 0, ℤ. Verify using CW complex.

### Euler Characteristic

8. **Cube:**  
   8 vertices, 12 edges, 6 faces. χ = ?  
   (Answer: 8 - 12 + 6 = 2 = χ(S²))

9. **Genus 5:**  
   χ(Σ₅) = ?

10. **Product:**  
    χ(S² × S²) using χ(X × Y) = χ(X)χ(Y).

### CW Complexes

11. **Attach 2-cell:**  
    Start S¹. Attach D² via degree 2 map.  
    Compute H_n. (ℝP²!)

12. **Wedge:**  
    Prove: H_n(X ∨ Y) ≅ H_n(X) ⊕ H_n(Y) (n > 0).

### Cellular Homology

13. **Compute by Hand:**  
    T² using cellular chains explicitly.

14. **ℝP²:**  
    Verify H₁(ℝP²) = ℤ/2ℤ via cellular boundary ∂₂(e²) = 2e¹.

### Advanced

15. **Research:**  
    What is H_n(ℂP²)? (Complex projective plane)

16. **Homology Sphere:**  
    3-manifold with H_n = H_n(S³) but not S³. Research Poincaré homology sphere.

---

## 📚 Further Reading

- **Hatcher, §2.1-2.2:** Detailed examples and cellular homology
- **Bredon, Chapter IV:** Comprehensive
- **Munkres, Elements:** Careful computations

---

## 🎓 Summary

**Systematic homology computations:**

✅ **Contractible spaces:** H₀ = ℤ, others = 0  
✅ **Spheres Sⁿ:** H₀ = Hₙ = ℤ, others = 0  
✅ **Torus T²:** H₀ = ℤ, H₁ = ℤ², H₂ = ℤ  
✅ **Surfaces Σ_g:** H₁ = ℤ^(2g) determines genus  
✅ **Cellular homology:** Finite algorithm via CW complexes  
✅ **Euler characteristic χ:** Homotopy invariant, computable  
✅ **Betti numbers β_n:** Count n-dimensional holes  

**Tiếp theo:** Mayer-Vietoris—powerful computational tool!

---

**Previous:** [Lecture 07.01: Singular Homology](/contents/vi/topology-chapter07/07_01_Singular_Homology/)  
**Next:** [Lecture 07.03: Mayer-Vietoris Sequence](/contents/vi/topology-chapter07/07_03_Mayer_Vietoris/)
