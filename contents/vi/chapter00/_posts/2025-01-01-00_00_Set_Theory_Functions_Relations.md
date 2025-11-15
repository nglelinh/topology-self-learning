---
layout: post
title: "Lecture 00.00: Set Theory, Functions, and Relations"
lang: vi
lang-ref: lecture-00-00
chapter: 0
lecture: 0
categories: [chapter00]
tags: [set-theory, functions, relations, cardinality]
description: "Nền tảng lý thuyết tập hợp: các tiên đề, hàm số, quan hệ, và khái niệm về lực lượng (cardinality)"
---

**Set Theory, Functions, and Relations**

---

## 📖 Tổng quan

Chào mừng bạn đến với bài giảng đầu tiên trong hành trình khám phá Tô-pô học! Trước khi chúng ta có thể hiểu được những khái niệm kỳ diệu của topology—nơi mà cái cốc cà phê và cái bánh donut được coi là "giống nhau"—chúng ta cần xây dựng nền móng vững chắc từ lý thuyết tập hợp.

Tô-pô học là nghiên cứu về các tính chất của không gian mà không thay đổi dưới các phép biến dạng liên tục. Nhưng để định nghĩa chính xác "không gian", "liên tục", và "không thay đổi", chúng ta cần ngôn ngữ của lý thuyết tập hợp. Đây không chỉ là formalism khô khan—lý thuyết tập hợp là cách toán học hiện đại tổ chức và suy nghĩ về mọi thứ.

**Tại sao bài này quan trọng?** Lý thuyết tập hợp không chỉ là một khởi đầu technical mà còn là bối cảnh conceptual cho toàn bộ topology. Tập hợp đóng vai trò như "nguyên tử" của toán học hiện đại—mọi đối tượng toán học, từ số tự nhiên đến không gian tô-pô phức tạp nhất, đều được xây dựng từ tập hợp. Hàm số là cầu nối giữa các không gian, cho phép chúng ta so sánh, kết nối và hiểu mối quan hệ giữa chúng. Quan hệ tương đương mở ra cách tư duy powerful về việc "gán nhận" các phần tử để tạo ra không gian mới—đây chính là ý tưởng behind quotient spaces, một trong những construction quan trọng nhất trong topology. Cuối cùng, cardinality sẽ giúp chúng ta phân biệt các "loại vô hạn" khác nhau, một insight sâu sắc sẽ xuất hiện lại khi ta nghiên cứu về countability axioms và separability.

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Tập hợp

Hãy tưởng tượng bạn đang đứng trong một căn phòng chứa đầy những vật thể: sách, cốc, bút, và đồ nội thất. Một **tập hợp** (set) đơn giản là một "bộ sưu tập" các vật thể mà bạn quyết định nhóm lại với nhau theo một tiêu chí nào đó. Bạn có thể tạo tập hợp S₁ gồm tất cả sách trên kệ, hoặc S₂ gồm tất cả vật màu đỏ, hay S₃ chứa những vật bạn có thể cầm bằng một tay. Điều kỳ diệu là trong toán học, chúng ta có thể định nghĩa nghiêm ngặt những "bộ sưu tập" này và xây dựng toàn bộ tòa nhà của toán học từ chúng. Mọi cấu trúc toán học—từ số tự nhiên, đến hàm số, đến không gian vô hạn chiều—cuối cùng đều được reduce về những câu hỏi về membership trong các tập hợp.

### Nghịch lý Russell: Lời cảnh báo

Nhưng không phải mọi "bộ sưu tập" đều là tập hợp hợp lệ. Năm 1901, Bertrand Russell đã phát hiện ra một nghịch lý đáng sợ:

> **Xét tập hợp R của tất cả các tập hợp không chứa chính nó.**  
> Câu hỏi: R có chứa chính nó không?

Hãy thử trả lời câu hỏi này. Nếu R ∈ R (R chứa chính nó), thì theo định nghĩa của R, nó chỉ chứa những tập hợp không chứa chính nó, do đó R không nên chứa chính nó—mâu thuẫn! Ngược lại, nếu R ∉ R (R không chứa chính nó), thì R thỏa mãn tiêu chí để được membership trong R (là một tập hợp không chứa chính nó), vậy R phải chứa chính nó—lại mâu thuẫn! Chúng ta rơi vào deadlock logic, không có cách nào thoát ra.

![Russell's Paradox illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Russell%27s_paradox.svg/400px-Russell%27s_paradox.svg.png)  
*Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Russell%27s_paradox.svg)*

Nghịch lý này không phải là trò chơi chữ clever—nó là một catastrophe cho nền móng toán học! Nó cho thấy rằng chúng ta không thể naive định nghĩa tập hợp như "bất kỳ bộ sưu tập nào ta nghĩ ra được". Naive set theory của Cantor và Frege, dù trực quan và powerful, chứa đựng contradictions ở bên trong. Để tránh những nghịch lý như vậy, toán học hiện đại đã phải rebuild lý thuyết tập hợp từ đầu, sử dụng một hệ thống **tiên đề** (axioms) cẩn thận để đảm bảo consistency. Đây là một trong những moments quan trọng nhất trong lịch sử toán học—khi chúng ta nhận ra rằng even những khái niệm "hiển nhiên" nhất cũng cần phải được formalize một cách rigorous.

---

## 📐 Định nghĩa Hình thức

### 1. Tiên đề Zermelo-Fraenkel (ZF)

Toán học hiện đại sử dụng hệ tiên đề **ZF** (hoặc ZFC với Axiom of Choice) để định nghĩa tập hợp. Dưới đây là một số tiên đề quan trọng:

**Tiên đề Extensionality (Tính mở rộng):**  
Hai tập hợp bằng nhau khi và chỉ khi chúng có cùng các phần tử.

$$
\forall A, B: (A = B) \iff (\forall x: x \in A \iff x \in B)
$$

**Trực giác:** Tiên đề này nói rằng một tập hợp hoàn toàn được xác định bởi các phần tử của nó, không quan trọng "cách" bạn mô tả chúng. Đây là một principle fundamental: hai tập hợp identical about membership thì identical as mathematical objects. Điều này có nghĩa là {1, 2, 3} và {3, 1, 2} là cùng một tập hợp vì chúng chứa chính xác cùng các phần tử, dù được liệt kê theo thứ tự khác nhau. Tương tự, {1, 2, 2, 3} và {1, 2, 3} là giống nhau vì sự "trùng lặp" không có ý nghĩa trong tập hợp—một phần tử hoặc là member, hoặc là không, không có khái niệm "xuất hiện nhiều lần".

**Tiên đề Pairing (Ghép đôi):**  
Với hai tập hợp A và B bất kỳ, tồn tại tập hợp {A, B}.

$$
\forall A, B: \exists C: \forall x: (x \in C \iff (x = A \lor x = B))
$$

**Tiên đề Union (Hợp):**  
Với một tập hợp các tập hợp, tồn tại tập hợp chứa tất cả phần tử của các tập hợp đó.

$$
\forall \mathcal{F}: \exists U: \forall x: (x \in U \iff \exists A \in \mathcal{F}: x \in A)
$$

**Tiên đề Power Set (Tập hợp lũy thừa):**  
Với mọi tập hợp A, tồn tại tập hợp P(A) chứa tất cả các tập con của A.

$$
\forall A: \exists P: \forall X: (X \in P \iff X \subseteq A)
$$

**Ví dụ:** Nếu A = {1, 2}, thì:
$$
\mathcal{P}(A) = \{\emptyset, \{1\}, \{2\}, \{1,2\}\}
$$

![Power set visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Hasse_diagram_of_powerset_of_3.svg/300px-Hasse_diagram_of_powerset_of_3.svg.png)  
*Hasse diagram của P({1,2,3}) - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hasse_diagram_of_powerset_of_3.svg)*

---

### 2. Hàm số (Functions)

Trong topology, hàm số (hay ánh xạ) là cách chúng ta so sánh và kết nối các không gian với nhau.

**Định nghĩa (Hàm số):**  
Một **hàm số** từ tập A đến tập B là một quy tắc f gán cho mỗi phần tử của A đúng một phần tử của B. Ký hiệu: f: A → B, trong đó A được gọi là domain (miền xác định), B là codomain (miền giá trị), và với mỗi a ∈ A, ta có f(a) ∈ B.

**Định nghĩa hình thức:** Một hàm f: A → B là một tập con của A × B sao cho:
$$
\forall a \in A: \exists! b \in B: (a, b) \in f
$$

**Tại sao định nghĩa này quan trọng?** Định nghĩa hình thức này nói rằng một hàm không phải là một "quy tắc magic" mà là một set of ordered pairs thỏa mãn constraint đặc biệt: mỗi element trong A xuất hiện đúng một lần ở vị trí đầu tiên. Điều này đảm bảo tính deterministic—mỗi input có đúng một output. Tuy nhiên, constraint này không symmetrical: nhiều inputs khác nhau có thể map đến cùng một output (ví dụ f(2) = f(-2) = 4 trong hàm f(x) = x²), nhưng một input không thể có nhiều outputs. Asymmetry này là cốt lõi của khái niệm function.

#### Các Loại Hàm

**Injective (Đơn ánh - One-to-one):**  
Các phần tử khác nhau trong A được ánh xạ đến các phần tử khác nhau trong B.

$$
\forall a_1, a_2 \in A: (f(a_1) = f(a_2)) \implies (a_1 = a_2)
$$

**Ví dụ:** f: ℝ → ℝ, f(x) = 2x + 1 là injective.

**Surjective (Toàn ánh - Onto):**  
Mọi phần tử trong B đều là ảnh của ít nhất một phần tử trong A.

$$
\forall b \in B: \exists a \in A: f(a) = b
$$

**Ví dụ:** f: ℝ → ℝ, f(x) = x³ là surjective.

**Bijective (Song ánh):**  
Vừa injective vừa surjective. Có thể "đảo ngược" hoàn hảo.

$$
f \text{ is bijective} \iff f \text{ is injective and surjective}
$$

![Function types visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Injective_composition.svg/500px-Injective_composition.svg.png)  
*Các loại hàm - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Injective_composition.svg)*

**Tại sao những phân loại này quan trọng trong topology?** Sự phân biệt giữa injective, surjective, và bijective không chỉ là technical classification mà reflect những properties geometric sâu sắc. **Homeomorphism**, khái niệm trung tâm của topology, chính là một bijection đặc biệt—nó không chỉ là bijection thuần túy mà còn preserve cấu trúc topological theo cả hai chiều. Injective maps bảo toàn tính "phân biệt"—nếu hai điểm khác nhau ở không gian nguồn, chúng vẫn khác nhau ở không gian đích, không bị "collapse" vào nhau. Điều này crucial khi ta muốn embed một không gian vào không gian khác. Ngược lại, surjective maps đảm bảo rằng ta "cover" toàn bộ không gian đích, không để sót bất kỳ điểm nào—property này quan trọng khi ta nghiên cứu quotient maps và covering spaces.

---

### 3. Quan hệ (Relations)

**Định nghĩa (Quan hệ):**  
Một **quan hệ** R trên tập A là một tập con của A × A. Ký hiệu: a R b có nghĩa là (a, b) ∈ R.

Quan hệ là cách toán học formalize các "connections" giữa các elements. Ví dụ, quan hệ **≤** trên ℝ nắm bắt khái niệm "ordering", quan hệ **=** mô tả "identity", và một quan hệ như "là anh em với" trên tập người có thể được formalized as a subset of (người × người). Sự khác biệt giữa quan hệ và hàm là quan hệ không yêu cầu mỗi element trong A phải liên kết với đúng một element khác—một element có thể không liên kết với ai, hoặc liên kết với nhiều elements khác.

#### Quan hệ Tương đương

**Định nghĩa (Quan hệ tương đương):**  
Một quan hệ ∼ trên A là **tương đương** nếu nó thỏa mãn ba tính chất: (1) **Phản xạ (Reflexive):** ∀a ∈ A: a ∼ a; (2) **Đối xứng (Symmetric):** ∀a,b ∈ A: (a ∼ b) ⇒ (b ∼ a); (3) **Bắc cầu (Transitive):** ∀a,b,c ∈ A: (a ∼ b) ∧ (b ∼ c) ⇒ (a ∼ c).

Tại sao ba properties này lại đặc biệt? Chúng capture ý tưởng intuitive của "giống nhau theo một cách nào đó". Reflexivity nói rằng mọi object "giống chính nó"—điều này nghe có vẻ trivial nhưng essential for consistency. Symmetry đảm bảo rằng nếu a giống b thì b cũng giống a—không có hierarchy hay direction trong mối quan hệ này. Transitivity cho phép ta "chain" các similarities: nếu a giống b và b giống c, thì a phải giống c. Ba axioms này together tạo nên một notion of "sameness" mathematically precise.

Xét ví dụ **đồng dư modulo n**: hai số a và b tương đương nếu (a - b) chia hết cho n. Đây là quan hệ tương đương vì: (1) a - a = 0 luôn chia hết cho n (reflexive); (2) nếu a - b chia hết cho n thì b - a = -(a-b) cũng chia hết cho n (symmetric); (3) nếu a - b và b - c chia hết cho n thì a - c = (a-b) + (b-c) cũng chia hết cho n (transitive). Một ví dụ geometric là quan hệ **song song** giữa các đường thẳng (bao gồm trùng nhau): hai đường thẳng "tương đương" nếu chúng có cùng hướng. Trong topology, **homeomorphism** là một equivalence relation giữa các không gian—hai không gian "topologically equivalent" nếu có một bijection liên tục với inverse liên tục giữa chúng.

**Lớp tương đương (Equivalence class):**  
Với a ∈ A, lớp tương đương của a là:
$$
[a] = \{x \in A : x \sim a\}
$$

**Phân hoạch (Partition):**  
Các lớp tương đương chia A thành các tập con rời nhau, không rỗng, có hợp là A.

![Equivalence classes visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/Equivalence_relation_on_set.svg/400px-Equivalence_relation_on_set.svg.png)  
*Phân hoạch bởi quan hệ tương đương - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Equivalence_relation_on_set.svg)*

**Tại sao quan trọng trong topology?**  
Quan hệ tương đương dẫn đến **không gian thương** (quotient spaces)—một cách mạnh mẽ để xây dựng không gian mới từ không gian cũ bằng cách "gán nhận" các điểm.

---

### 4. Lực lượng (Cardinality)

Một trong những khám phá vĩ đại nhất của Georg Cantor là: **không phải tất cả vô hạn đều bằng nhau!**

**Định nghĩa (Lực lượng):**  
Hai tập A và B có **cùng lực lượng** (same cardinality) nếu tồn tại một bijection f: A → B.

Ký hiệu: |A| = |B| hoặc A ∼ B.

**Trực giác:** Hai tập "cùng kích thước" nếu ta có thể "đếm" chúng bằng cách ghép đôi 1-1.

#### Các Loại Vô hạn

**Countable (Đếm được):**  
Một tập A là **countable** nếu |A| = |ℕ| (có bijection với tập số tự nhiên).

**Ví dụ về tập countable:** Tập số nguyên **ℤ** = {..., -2, -1, 0, 1, 2, ...} là countable dù nó "lớn hơn" ℕ về mặt intuitive. Tại sao? Vì ta có thể tìm được một bijection tường minh: định nghĩa f(n) = n/2 nếu n chẵn, và f(n) = -(n+1)/2 nếu n lẻ. Bijection này ánh xạ 0↦0, 1↦-1, 2↦1, 3↦-2, 4↦2, ... coverage tất cả integers. Một kết quả surprising hơn là tập số hữu tỉ **ℚ** cũng countable! Cantor đã chứng minh điều này bằng phương pháp "đường chéo" clever: sắp xếp tất cả phân số theo tổng (tử + mẫu), rồi đếm theo đường zigzag. Kết quả này counterintuitive vì ℚ là dense trong ℝ (giữa hai số hữu tỉ bất kỳ luôn có vô số số hữu tỉ khác), nhưng vẫn "chỉ" countable!

![Cantor's diagonal argument for rationals](https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Diagonal_argument.svg/500px-Diagonal_argument.svg.png)  
*Chứng minh ℚ đếm được - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Diagonal_argument.svg)*

**Uncountable (Không đếm được):**  
Một tập là **uncountable** nếu nó không countable—không có bijection với ℕ.

**Định lý (Cantor):**  
**ℝ** (số thực) là uncountable.

**Chứng minh (sketch):** Giả sử ℝ countable, liệt kê tất cả số thực:
```
r₁ = 0.a₁₁ a₁₂ a₁₃ ...
r₂ = 0.a₂₁ a₂₂ a₂₃ ...
r₃ = 0.a₃₁ a₃₂ a₃₃ ...
...
```

Xây dựng số mới: x = 0.b₁ b₂ b₃ ... với bᵢ ≠ aᵢᵢ.  
Khi đó x ∉ {r₁, r₂, r₃, ...} → mâu thuẫn!

**Kết luận quan trọng:**
$$
|\mathbb{N}| < |\mathbb{R}|
$$

Có "nhiều loại vô hạn" khác nhau!

**Cardinality trong topology:** Những khái niệm về countability này không chỉ là abstract curiosities—chúng xuất hiện everywhere trong topology và có ý nghĩa geometric deep. Một không gian được gọi là **separable** nếu nó chứa một countable dense subset, nghĩa là có một tập đếm được mà mỗi open set đều chứa ít nhất một điểm từ tập này. Ví dụ, ℝ là separable vì ℚ (countable) dense trong ℝ. Một không gian là **first countable** nếu mỗi điểm có một countable basis of neighborhoods—property này cho phép ta sử dụng sequences để describe continuity. Một không gian là **second countable** nếu toàn bộ topology có một countable basis—điều này stronger hơn first countable và có nhiều consequences powerful, bao gồm metrization theorems. Ba khái niệm này form một hierarchy quan trọng trong classification of topological spaces.

---

## 🧠 Fundamental Papers & References

### Classic Papers
1. **Georg Cantor** - *"Über eine Eigenschaft des Inbegriffes aller reellen algebraischen Zahlen"* (1874)  
   *Bài báo chứng minh ℝ uncountable - khởi đầu lý thuyết tập hợp hiện đại*

2. **Bertrand Russell** - *"Letter to Frege"* (1902)  
   *Giới thiệu nghịch lý Russell, dẫn đến cuộc khủng hoảng nền móng toán học*

3. **Ernst Zermelo** - *"Untersuchungen über die Grundlagen der Mengenlehre I"* (1908)  
   *Tiên đề hóa lý thuyết tập hợp, tránh các nghịch lý*

### Textbooks
4. **James R. Munkres** - *Topology*, 2nd Ed., **Chapter 1: Set Theory and Logic**  
   *Giới thiệu ngắn gọn nhưng đầy đủ về nền tảng tập hợp cho topology*

5. **Herbert B. Enderton** - *Elements of Set Theory* (1977)  
   *Giáo trình chi tiết về lý thuyết tập hợp tiên đề*

6. **Paul R. Halmos** - *Naive Set Theory* (1960)  
   *Approach trực quan, dễ đọc về lý thuyết tập hợp*

---

## 🔗 Applications and Connections

### Physics
**Quantum Mechanics:** Các trạng thái lượng tử được mô tả trong Hilbert spaces—không gian vô hạn chiều với cấu trúc tô-pô phức tạp. Hiểu về cardinality giúp ta phân biệt discrete spectrum vs continuous spectrum.

### Computer Science
**Computability Theory:** Turing đã chứng minh rằng tập các hàm computable là countable, nhưng tập tất cả các hàm ℕ → ℕ là uncountable. Do đó, "hầu hết" các hàm không thể tính được!

### Data Science
**Network Analysis:** Graph theory sử dụng quan hệ tương đương để nhóm các nodes thành communities. Equivalence classes tương ứng với các connected components.

### Ví dụ Thực tế
**GPS Navigation:** Khi tính đường đi ngắn nhất, ta sử dụng equivalence relation "cùng kết nối đến điểm A". Các lớp tương đương là các vùng có thể tiếp cận được từ A.

---

## 🧩 Exercises

### Conceptual Questions

1. **Vẽ diagram minh họa:**  
   Vẽ Venn diagrams cho hai hàm f: A → B và g: A → B, trong đó f là injective nhưng không surjective, còn g là surjective nhưng không injective. Giải thích tại sao.

2. **Tìm quan hệ tương đương:**  
   Trên tập hợp các điểm trong mặt phẳng ℝ², xét quan hệ: "hai điểm ∼ nếu chúng có cùng khoảng cách đến gốc tọa độ".  
   - Chứng minh đây là quan hệ tương đương.
   - Mô tả hình học các lớp tương đương.

3. **Cardinality puzzle:**  
   Chứng minh rằng |ℕ × ℕ| = |ℕ| bằng cách xây dựng một bijection tường minh.  
   (*Hint:* Sử dụng phương pháp "đường chéo" của Cantor)

4. **Power set cardinality:**  
   Nếu |A| = n (hữu hạn), chứng minh rằng |𝒫(A)| = 2ⁿ.  
   Tại sao ký hiệu 2^A được dùng cho tập hợp lũy thừa?

5. **Topology preview:**  
   Trong mặt phẳng ℝ², xét quan hệ: "hai hình ∼ nếu có thể biến dạng liên tục từ hình này sang hình kia mà không cắt hay dán".  
   - Đây có phải là quan hệ tương đương không?
   - Tam giác và hình vuông có tương đương không?
   - Hình tròn và hình chữ "8" có tương đương không?

### Reflection Questions

6. **Philosophical:**  
   Nghịch lý Russell cho thấy gì về việc định nghĩa các khái niệm toán học? Tại sao chúng ta cần tiên đề?

7. **Historical context:**  
   Tìm hiểu về "cuộc khủng hoảng nền móng" (foundational crisis) trong toán học đầu thế kỷ 20. Các tiên đề ZF đã giải quyết vấn đề như thế nào?

8. **Big picture:**  
   Tại sao topology cần lý thuyết tập hợp? Những khái niệm nào trong bài này bạn nghĩ sẽ quan trọng nhất cho các bài giảng sau?

---

## 📚 Further Reading

- **Munkres, Topology:** §1–2 (Set Theory fundamentals)
- **Enderton, Elements of Set Theory:** Chapters 1–3 (Rigorous treatment)
- **Hrbacek & Jech, Introduction to Set Theory:** Chapter 1 (Modern approach)
- **Morris, Topology Without Tears:** Chapter 1, §1.1 (Gentle introduction)

---

## 🎓 Summary

Trong bài giảng này, chúng ta đã xây dựng nền móng essential cho toàn bộ journey topology phía trước. Chúng ta bắt đầu với **lý thuyết tập hợp**, nơi Bertrand Russell's paradox cảnh báo chúng ta rằng naive intuition không đủ—chúng ta cần hệ tiên đề ZF rigorous để avoid contradictions. Tiếp theo, chúng ta học về **hàm số** và ba classifications quan trọng (injective, surjective, bijective) mà sẽ reappear liên tục trong topology như embeddings, quotient maps, và homeomorphisms. **Quan hệ tương đương** mở ra powerful paradigm về việc nhóm elements theo "sameness", dẫn đến equivalence classes và partition—ideas này fundamental cho quotient topology. Cuối cùng, **cardinality** tiết lộ rằng infinity không phải là monolithic: có nhiều "sizes" của vô hạn, với countable (như ℕ, ℤ, ℚ) nhỏ hơn uncountable (như ℝ).

**Core insights từ bài này:** Tập hợp là "atomic building blocks" của toán học hiện đại, nhưng phải được formalized carefully qua axioms. Bijections cung cấp precise way để compare "sizes" của sets, even infinite ones. Equivalence relations capture notion of "sameness" và form foundation cho quotient constructions. Và perhaps most surprisingly, not all infinities are equal—|ℕ| < |ℝ| reveals một hierarchy of infinite cardinalities mà sẽ inform nhiều distinctions trong topology.

**Tiếp theo:** Trong Lecture 00.01, chúng ta sẽ học về **Tích Cartesian** và **Bổ đề Zorn**—công cụ mạnh mẽ để chứng minh sự tồn tại của các đối tượng tô-pô.

---

*"In mathematics, you don't understand things. You just get used to them." — John von Neumann*

🎯 **Hãy làm bài tập và vẽ nhiều hình! Topology là môn học hình học.** 🎯

---

**Next:** [Lecture 00.01: Cartesian Products and Zorn's Lemma](/contents/vi/topology-chapter00/00_01_Cartesian_Products_Zorns_Lemma/)

