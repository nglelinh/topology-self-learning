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

**Lý thuyết tập hợp, Ánh xạ và Quan hệ**

---

## 📖 Tổng quan

Bài giảng mở đầu này đặt nền móng ngôn ngữ cho toàn bộ môn Tô-pô học. Trước khi làm việc với các khái niệm đặc trưng của tô-pô — chẳng hạn lý do chiếc cốc có quai và hình xuyến (bánh donut) được xem là tương đương về mặt tô-pô — ta cần xây dựng nền tảng chặt chẽ từ lý thuyết tập hợp.

Tô-pô học nghiên cứu các tính chất của không gian không thay đổi dưới các phép biến dạng liên tục. Để định nghĩa chính xác các khái niệm "không gian", "liên tục" và "bất biến", ta sử dụng ngôn ngữ của lý thuyết tập hợp. Đây không đơn thuần là hình thức hóa khô khan, mà là khung tổ chức cơ bản của toán học hiện đại.

**Tại sao bài này quan trọng?** Lý thuyết tập hợp cung cấp cả công cụ kỹ thuật lẫn nền tảng khái niệm cho toàn bộ môn tô-pô. Mọi đối tượng toán học, từ tập số tự nhiên đến các không gian tô-pô trừu tượng, đều được xây dựng từ tập hợp. Ánh xạ (hàm số) đóng vai trò cầu nối giữa các không gian, giúp so sánh và liên kết cấu trúc của chúng. Quan hệ tương đương cho phép đồng nhất các phần tử theo một tiêu chí nhất định để tạo ra không gian mới — đó chính là ý tưởng của không gian thương (*quotient space*), một phép xây dựng quan trọng trong tô-pô. Cuối cùng, khái niệm lực lượng (*cardinality*) giúp phân biệt các mức độ vô hạn khác nhau, vốn sẽ xuất hiện trực tiếp khi nghiên cứu các tiên đề đếm được và tính khả ly.

---

## 🎯 Từ trực giác đến hình thức

### Khái niệm tập hợp

Hãy hình dung một căn phòng chứa nhiều đồ vật như sách, cốc, bút và bàn ghế. Một **tập hợp** (*set*) có thể hiểu trực quan là một bộ sưu tập các đối tượng được gom lại theo một tiêu chí nào đó: chẳng hạn tập $S_1$ gồm tất cả các cuốn sách trên kệ, $S_2$ gồm các vật màu đỏ, hay $S_3$ gồm những vật có thể cầm bằng một tay. Trong toán học, khái niệm "bộ sưu tập" này được định nghĩa chặt chẽ để làm cơ sở xây dựng mọi cấu trúc phức tạp hơn — từ tập số tự nhiên, ánh xạ, đến các không gian vô hạn chiều — bằng cách quy về quan hệ thuộc ($\in$) trong các tập hợp.

### Nghịch lý Russell: Lời cảnh báo

Tuy nhiên, không phải mọi "bộ sưu tập" tùy ý đều tạo thành một tập hợp hợp lệ. Năm 1901, Bertrand Russell đã chỉ ra một mâu thuẫn nổi tiếng:

> **Xét tập hợp $R$ gồm tất cả các tập hợp không chứa chính nó.**  
> Câu hỏi: $R$ có chứa chính nó không?

Nếu $R \in R$ (tức $R$ chứa chính nó), thì theo định nghĩa của $R$, nó chỉ gồm những tập hợp không chứa chính nó, suy ra $R \notin R$ — mâu thuẫn. Ngược lại, nếu $R \notin R$, thì $R$ thỏa mãn điều kiện để trở thành phần tử của $R$, suy ra $R \in R$ — lại mâu thuẫn. Lập luận rơi vào bế tắc logic không thể hóa giải.

![Russell's Paradox illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Russell%27s_paradox.svg/400px-Russell%27s_paradox.svg.png)  
*Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Russell%27s_paradox.svg)*

Nghịch lý này không phải trò chơi chữ, mà là một vấn đề nghiêm trọng đối với nền móng toán học. Nó cho thấy ta không thể định nghĩa tập hợp một cách ngây thơ là "bất kỳ bộ sưu tập nào mô tả được bằng một tính chất". Lý thuyết tập hợp ngây thơ của Cantor và Frege tuy trực quan nhưng tiềm ẩn mâu thuẫn nội tại. Để khắc phục, toán học hiện đại phải xây dựng lại lý thuyết tập hợp dựa trên một hệ **tiên đề** (*axioms*) chặt chẽ nhằm bảo đảm tính nhất quán, cho thấy ngay cả những khái niệm tưởng chừng hiển nhiên nhất cũng cần được hình thức hóa cẩn thận.

---

## 📐 Định nghĩa hình thức

### 1. Hệ tiên đề Zermelo–Fraenkel (ZF)

Toán học hiện đại sử dụng hệ tiên đề **ZF** (hoặc **ZFC** khi bổ sung Tiên đề Lựa chọn) để định nghĩa tập hợp. Dưới đây là một số tiên đề cơ bản:

**Tiên đề Ngoại diên (Extensionality):**  
Hai tập hợp bằng nhau khi và chỉ khi chúng có cùng các phần tử.

$$
\forall A, B: (A = B) \iff (\forall x: x \in A \iff x \in B)
$$

**Trực giác:** Tiên đề này khẳng định một tập hợp được xác định hoàn toàn bởi các phần tử của nó, không phụ thuộc vào cách mô tả hay thứ tự liệt kê. Do đó, $\{1, 2, 3\}$ và $\{3, 1, 2\}$ là cùng một tập hợp. Tương tự, $\{1, 2, 2, 3\}$ và $\{1, 2, 3\}$ bằng nhau vì một phần tử hoặc thuộc tập hợp, hoặc không thuộc tập hợp, chứ không xét đến số lần lặp lại.

**Tiên đề Cặp (Pairing):**  
Với hai tập hợp $A$ và $B$ bất kỳ, tồn tại tập hợp $\{A, B\}$.

$$
\forall A, B: \exists C: \forall x: (x \in C \iff (x = A \lor x = B))
$$

**Tiên đề Hợp (Union):**  
Với một tập hợp các tập hợp, tồn tại tập hợp chứa tất cả phần tử của các tập hợp đó.

$$
\forall \mathcal{F}: \exists U: \forall x: (x \in U \iff \exists A \in \mathcal{F}: x \in A)
$$

**Tiên đề Tập lũy thừa (Power Set):**  
Với mọi tập hợp $A$, tồn tại tập hợp $\mathcal{P}(A)$ chứa tất cả các tập con của $A$.

$$
\forall A: \exists P: \forall X: (X \in P \iff X \subseteq A)
$$

**Ví dụ:** Nếu $A = \{1, 2\}$, thì:
$$
\mathcal{P}(A) = \{\emptyset, \{1\}, \{2\}, \{1,2\}\}
$$

![Power set visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Hasse_diagram_of_powerset_of_3.svg/300px-Hasse_diagram_of_powerset_of_3.svg.png)  
*Biểu đồ Hasse của $\mathcal{P}(\{1,2,3\})$ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hasse_diagram_of_powerset_of_3.svg)*

---

### 2. Hàm số / Ánh xạ (Functions)

Trong tô-pô, hàm số (hay ánh xạ) là công cụ để so sánh và liên kết các không gian với nhau.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Hàm số / Ánh xạ):**  
Một **hàm số** (hay **ánh xạ**) từ tập $A$ đến tập $B$ là một quy tắc $f$ gán cho mỗi phần tử của $A$ đúng một phần tử của $B$. Ký hiệu: $f: A \to B$, trong đó $A$ được gọi là miền xác định (*domain*), $B$ là miền đích (*codomain*), và với mỗi $a \in A$, ta có $f(a) \in B$.
</div>

**Định nghĩa hình thức:** Một hàm $f: A \to B$ là một tập con của $A \times B$ sao cho:
$$
\forall a \in A: \exists! b \in B: (a, b) \in f
$$

**Ý nghĩa của định nghĩa hình thức:** Cách định nghĩa này quy khái niệm hàm số về một tập hợp các cặp có thứ tự thỏa mãn điều kiện chặt chẽ: mỗi phần tử trong $A$ xuất hiện đúng một lần ở tọa độ thứ nhất. Điều này bảo đảm tính xác định — mỗi đầu vào tương ứng với đúng một đầu ra. Ngược lại, điều kiện này không đối xứng: nhiều đầu vào khác nhau có thể cùng ánh xạ đến một đầu ra (ví dụ $f(2) = f(-2) = 4$ với $f(x) = x^2$), nhưng một đầu vào không thể có nhiều đầu ra.

#### Các loại ánh xạ

**Đơn ánh (Injective / One-to-one):**  
Các phần tử khác nhau trong $A$ được ánh xạ đến các phần tử khác nhau trong $B$.

$$
\forall a_1, a_2 \in A: (f(a_1) = f(a_2)) \implies (a_1 = a_2)
$$

**Ví dụ:** $f: \mathbb{R} \to \mathbb{R}$, $f(x) = 2x + 1$ là đơn ánh.

**Toàn ánh (Surjective / Onto):**  
Mọi phần tử trong $B$ đều là ảnh của ít nhất một phần tử trong $A$.

$$
\forall b \in B: \exists a \in A: f(a) = b
$$

**Ví dụ:** $f: \mathbb{R} \to \mathbb{R}$, $f(x) = x^3$ là toàn ánh.

**Song ánh (Bijective):**  
Vừa là đơn ánh vừa là toàn ánh, do đó có ánh xạ ngược xác định trên toàn bộ $B$.

$$
f \text{ is bijective} \iff f \text{ is injective and surjective}
$$

![Function types visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Injective_composition.svg/500px-Injective_composition.svg.png)  
*Các loại ánh xạ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Injective_composition.svg)*

**Vai trò trong tô-pô:** Sự phân biệt giữa đơn ánh, toàn ánh và song ánh phản ánh trực tiếp các tính chất hình học và cấu trúc của không gian. **Phép đồng phôi** (*homeomorphism*), khái niệm trung tâm của tô-pô, là một song ánh liên tục có ánh xạ ngược cũng liên tục, qua đó bảo toàn cấu trúc tô-pô theo cả hai chiều. Ánh xạ đơn ánh bảo toàn tính phân biệt giữa các điểm (không có hai điểm phân biệt nào bị gộp làm một), đóng vai trò thiết yếu khi nhúng (*embed*) một không gian vào không gian khác. Ngược lại, ánh xạ toàn ánh bảo đảm ảnh phủ toàn bộ không gian đích, rất quan trọng khi xét ánh xạ thương (*quotient map*) và không gian phủ (*covering space*).

---

### 3. Quan hệ (Relations)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Quan hệ):**  
Một **quan hệ** $R$ trên tập $A$ là một tập con của $A \times A$. Ký hiệu $a R b$ có nghĩa là $(a, b) \in R$.
</div>

Quan hệ là cách toán học hình thức hóa các mối liên hệ giữa các phần tử trong một tập hợp. Chẳng hạn, quan hệ $\le$ trên $\mathbb{R}$ mô tả thứ tự, quan hệ $=$ mô tả sự bằng nhau, còn quan hệ "là anh em với" trên một tập hợp người là một tập con của tích Đề-các của tập người đó với chính nó. Khác với ánh xạ, quan hệ không đòi hỏi mỗi phần tử phải liên kết với đúng một phần tử khác: một phần tử có thể không có liên kết nào, hoặc liên kết với nhiều phần tử cùng lúc.

#### Quan hệ tương đương

<div class="textbook-definition" markdown="1">
**Định nghĩa (Quan hệ tương đương):**  
Một quan hệ $\sim$ trên $A$ là **quan hệ tương đương** nếu nó thỏa mãn ba tính chất: (1) **Phản xạ (Reflexive):** $\forall a \in A: a \sim a$; (2) **Đối xứng (Symmetric):** $\forall a,b \in A: (a \sim b) \Rightarrow (b \sim a)$; (3) **Bắc cầu (Transitive):** $\forall a,b,c \in A: (a \sim b) \land (b \sim c) \Rightarrow (a \sim c)$.
</div>

Ba tính chất này hình thức hóa trực giác về sự "tương đồng" theo một tiêu chí nhất định. Tính phản xạ khẳng định mọi đối tượng đều tương đương với chính nó. Tính đối xứng bảo đảm quan hệ không phân biệt chiều: nếu $a$ tương đương với $b$ thì $b$ cũng tương đương với $a$. Tính bắc cầu cho phép nối chuỗi các sự tương đương: nếu $a \sim b$ và $b \sim c$ thì $a \sim c$.

Ví dụ, quan hệ **đồng dư modulo $n$** trên $\mathbb{Z}$ (hai số $a, b$ tương đương nếu $a - b$ chia hết cho $n$) là một quan hệ tương đương vì: (1) $a - a = 0$ luôn chia hết cho $n$ (phản xạ); (2) nếu $a - b$ chia hết cho $n$ thì $b - a = -(a - b)$ cũng chia hết cho $n$ (đối xứng); (3) nếu $a - b$ và $b - c$ chia hết cho $n$ thì $a - c = (a - b) + (b - c)$ cũng chia hết cho $n$ (bắc cầu). Một ví dụ hình học là quan hệ **song song** giữa các đường thẳng (kể cả trùng nhau), trong đó hai đường thẳng tương đương nếu chúng cùng phương. Trong tô-pô, quan hệ **đồng phôi** là một quan hệ tương đương trên lớp các không gian tô-pô: hai không gian tương đương nhau về mặt tô-pô nếu tồn tại một song ánh liên tục có ánh xạ ngược liên tục giữa chúng.

**Lớp tương đương (Equivalence class):**  
Với $a \in A$, lớp tương đương của $a$ là:
$$
[a] = \{x \in A : x \sim a\}
$$

**Phân hoạch (Partition):**  
Tập hợp các lớp tương đương chia $A$ thành các tập con đôi một rời nhau, khác rỗng, có hợp bằng $A$.

![Equivalence classes visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/Equivalence_relation_on_set.svg/400px-Equivalence_relation_on_set.svg.png)  
*Phân hoạch bởi quan hệ tương đương - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Equivalence_relation_on_set.svg)*

**Vai trò trong tô-pô:**  
Quan hệ tương đương dẫn đến khái niệm **không gian thương** (*quotient space*) — phương pháp xây dựng không gian mới từ không gian cũ bằng cách đồng nhất (dán) các điểm thuộc cùng một lớp tương đương.

---

### 4. Lực lượng (Cardinality)

Một trong những phát hiện có ảnh hưởng lớn của Georg Cantor là: **không phải mọi tập vô hạn đều có cùng kích thước.**

<div class="textbook-definition" markdown="1">
**Định nghĩa (Lực lượng):**  
Hai tập $A$ và $B$ có **cùng lực lượng** (*same cardinality*) nếu tồn tại một song ánh $f: A \to B$.
</div>

Ký hiệu: $|A| = |B|$ hoặc $A \sim B$.

**Trực giác:** Hai tập có cùng lực lượng khi ta có thể ghép đôi 1–1 mọi phần tử của tập này với tập kia.

#### Các loại tập vô hạn

**Đếm được (Countable):**  
Một tập $A$ là **vô hạn đếm được** (thường gọi gọn là **đếm được**, *countable*; theo nghĩa rộng còn bao gồm cả tập hữu hạn) nếu $|A| = |\mathbb{N}|$, tức tồn tại song ánh giữa $A$ và tập số tự nhiên.

**Ví dụ về tập đếm được:** Tập số nguyên $\mathbb{Z} = \{\dots, -2, -1, 0, 1, 2, \dots\}$ là tập đếm được dù về trực giác có vẻ "lớn hơn" $\mathbb{N}$. Với quy ước $\mathbb{N} = \{0, 1, 2, \dots\}$, ta có thể xây dựng một song ánh tường minh $f: \mathbb{N} \to \mathbb{Z}$ bởi $f(n) = n/2$ nếu $n$ chẵn, và $f(n) = -(n+1)/2$ nếu $n$ lẻ. Ánh xạ này cho $0 \mapsto 0, 1 \mapsto -1, 2 \mapsto 1, 3 \mapsto -2, 4 \mapsto 2, \dots$, phủ toàn bộ $\mathbb{Z}$. Đáng chú ý hơn, tập số hữu tỉ $\mathbb{Q}$ cũng đếm được: Cantor đã chứng minh bằng cách sắp xếp các phân số theo bảng hai chiều rồi đếm lần lượt theo đường chéo ziczac. Kết quả này đi ngược trực giác thông thường vì $\mathbb{Q}$ trù mật (*dense*) trong $\mathbb{R}$ (giữa hai số hữu tỉ bất kỳ luôn có vô số số hữu tỉ khác), nhưng lực lượng của nó vẫn chỉ bằng $|\mathbb{N}|$.

![Cantor's diagonal argument for rationals](https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Diagonal_argument.svg/500px-Diagonal_argument.svg.png)  
*Chứng minh $\mathbb{Q}$ đếm được - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Diagonal_argument.svg)*

**Không đếm được (Uncountable):**  
Một tập hợp là **không đếm được** nếu nó vô hạn và không tồn tại song ánh với $\mathbb{N}$.

<div class="textbook-theorem" markdown="1">
**Định lý (Cantor):**  
Tập số thực $\mathbb{R}$ là tập không đếm được.
</div>

**Phác thảo chứng minh:** Giả sử $\mathbb{R}$ đếm được; khi đó khoảng $(0, 1) \subset \mathbb{R}$ cũng đếm được và có thể liệt kê toàn bộ các phần tử của nó dưới dạng thập phân:
```
r₁ = 0.a₁₁ a₁₂ a₁₃ ...
r₂ = 0.a₂₁ a₂₂ a₂₃ ...
r₃ = 0.a₃₁ a₃₂ a₃₃ ...
...
```

Xây dựng số mới $x = 0.b_1 b_2 b_3 \dots \in (0, 1)$ bằng cách chọn $b_i \in \{1, 2\}$ sao cho $b_i \neq a_{ii}$ (chọn chữ số $1$ hoặc $2$ để tránh trường hợp hai biểu diễn thập phân khác nhau cùng chỉ một số, như đuôi lặp vô hạn chữ số $0$ hay $9$).  
Khi đó $x \notin \{r_1, r_2, r_3, \dots\}$, dẫn đến mâu thuẫn.

**Kết luận quan trọng:**
$$
|\mathbb{N}| < |\mathbb{R}|
$$

Như vậy, tồn tại nhiều mức độ vô hạn khác nhau.

**Lực lượng trong tô-pô:** Các khái niệm đếm được xuất hiện xuyên suốt trong tô-pô và gắn với những tính chất cấu trúc quan trọng. Một không gian tô-pô được gọi là **khả ly** (*separable*) nếu nó chứa một tập con trù mật đếm được, nghĩa là mọi tập mở khác rỗng đều chứa ít nhất một điểm của tập con này (chẳng hạn $\mathbb{R}$ khả ly vì $\mathbb{Q}$ đếm được và trù mật trong $\mathbb{R}$). Một không gian thỏa mãn **tiên đề đếm được thứ nhất** (*first countable*) nếu mỗi điểm đều có một cơ sở lân cận đếm được — tính chất cho phép dùng dãy điểm để mô tả tính liên tục. Một không gian thỏa mãn **tiên đề đếm được thứ hai** (*second countable*) nếu toàn bộ tô-pô có một cơ sở đếm được — điều kiện mạnh hơn tiên đề đếm được thứ nhất và đóng vai trò trung tâm trong các định lý mê-tric hóa. Ba khái niệm này tạo nên một hệ phân tầng cơ bản khi phân loại không gian tô-pô.

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Bài báo kinh điển
1. **Georg Cantor** - *"Über eine Eigenschaft des Inbegriffes aller reellen algebraischen Zahlen"* (1874)  
   *Bài báo chứng minh $\mathbb{R}$ không đếm được — dấu mốc mở đầu lý thuyết tập hợp hiện đại.*

2. **Bertrand Russell** - *"Letter to Frege"* (1902)  
   *Trình bày nghịch lý Russell, dẫn đến cuộc khủng hoảng nền móng toán học đầu thế kỷ 20.*

3. **Ernst Zermelo** - *"Untersuchungen über die Grundlagen der Mengenlehre I"* (1908)  
   *Tiên đề hóa lý thuyết tập hợp nhằm tránh các nghịch lý.*

### Giáo trình
4. **James R. Munkres** - *Topology*, 2nd Ed., **Chapter 1: Set Theory and Logic**  
   *Giới thiệu ngắn gọn, đầy đủ về nền tảng tập hợp cho tô-pô.*

5. **Herbert B. Enderton** - *Elements of Set Theory* (1977)  
   *Giáo trình chi tiết về lý thuyết tập hợp tiên đề.*

6. **Paul R. Halmos** - *Naive Set Theory* (1960)  
   *Cách trình bày trực quan, dễ tiếp cận về lý thuyết tập hợp.*

---

## 🔗 Ứng dụng và liên hệ

### Vật lý
**Cơ học lượng tử:** Các trạng thái lượng tử được mô tả trong không gian Hilbert — không gian vô hạn chiều có cấu trúc tô-pô và hình học. Khái niệm lực lượng giúp phân biệt phổ rời rạc (*discrete spectrum*) với phổ liên tục (*continuous spectrum*).

### Khoa học máy tính
**Lý thuyết tính toán được (Computability Theory):** Turing đã chỉ ra rằng tập các hàm tính toán được là đếm được, trong khi tập tất cả các hàm $\mathbb{N} \to \mathbb{N}$ là không đếm được. Vì vậy, phần lớn các hàm không thể tính được bằng thuật toán.

### Khoa học dữ liệu
**Phân tích mạng lưới:** Lý thuyết đồ thị dùng quan hệ tương đương (chẳng hạn "có đường đi nối giữa hai đỉnh") để phân chia đồ thị thành các thành phần liên thông (*connected components*), tương ứng với các lớp tương đương.

### Ví dụ thực tế
**Định vị GPS:** Khi tìm đường đi giữa các vị trí trên bản đồ giao thông, quan hệ "có thể đi tới nhau" là một quan hệ tương đương; mỗi lớp tương đương xác định một vùng mạng lưới có thể tiếp cận được từ một điểm xuất phát cho trước.

---

## Video tham khảo

- **xem trước** [Surjective (onto) and injective (one-to-one) functions | Linear Algebra | Khan Academy](https://www.youtube.com/watch?v=xKNX8BUWR0g) — Khan Academy, tiếng Anh. Xem cách tách đơn ánh, toàn ánh và song ánh trước khi dùng chúng để nói về lực lượng.
- [INJECTIVE, SURJECTIVE, and BIJECTIVE FUNCTIONS - DISCRETE MATHEMATICS](https://www.youtube.com/watch?v=bZred_Ksz2k) — TrevTutor, tiếng Anh. Thêm ví dụ rời rạc cho cùng ba loại hàm, sát phần hàm của bài.
- [MATH0005 L13: equivalence relations and partitions](https://www.youtube.com/watch?v=kvtwnWEpv4E) — Matthew Towers, tiếng Anh. Quan hệ tương đương và phân hoạch, đúng phần quan hệ ở cuối bài.

## 🧩 Bài tập

### Câu hỏi khái niệm

1. **Vẽ sơ đồ minh họa:**  
   Vẽ sơ đồ Venn cho hai ánh xạ $f: A \to B$ và $g: A \to B$, trong đó $f$ là đơn ánh nhưng không toàn ánh, còn $g$ là toàn ánh nhưng không đơn ánh. Giải thích lý do.

2. **Tìm quan hệ tương đương:**  
   Trên tập hợp các điểm trong mặt phẳng $\mathbb{R}^2$, xét quan hệ: hai điểm tương đương ($\sim$) nếu chúng có cùng khoảng cách đến gốc tọa độ.  
   - Chứng minh đây là một quan hệ tương đương.
   - Mô tả hình học các lớp tương đương.

3. **Bài toán lực lượng:**  
   Chứng minh rằng $|\mathbb{N} \times \mathbb{N}| = |\mathbb{N}|$ bằng cách xây dựng một song ánh tường minh.  
   (*Gợi ý:* Sử dụng phương pháp đếm theo đường chéo của Cantor.)

4. **Lực lượng của tập lũy thừa:**  
   Nếu $|A| = n$ (hữu hạn), chứng minh rằng $|\mathcal{P}(A)| = 2^n$.  
   Giải thích vì sao ký hiệu $2^A$ thường được dùng để chỉ tập lũy thừa của $A$.

5. **Gợi mở về tô-pô:**  
   Trong mặt phẳng $\mathbb{R}^2$, xét quan hệ: hai hình tương đương ($\sim$) nếu có thể biến dạng liên tục từ hình này sang hình kia mà không cắt hay dán.  
   - Đây có phải là một quan hệ tương đương không?
   - Hình tam giác và hình vuông có tương đương không?
   - Đường tròn và hình số "8" có tương đương không?

### Câu hỏi suy ngẫm

6. **Về nền móng:**  
   Nghịch lý Russell cho thấy điều gì về cách định nghĩa các khái niệm toán học? Vì sao ta cần hệ tiên đề?

7. **Bối cảnh lịch sử:**  
   Tìm hiểu về "cuộc khủng hoảng nền móng" (*foundational crisis*) trong toán học đầu thế kỷ 20. Hệ tiên đề ZF đã giải quyết vấn đề này như thế nào?

8. **Bức tranh tổng thể:**  
   Vì sao tô-pô cần lý thuyết tập hợp? Theo bạn, những khái niệm nào trong bài này sẽ xuất hiện thường xuyên nhất ở các bài giảng sau?

---

## 📚 Đọc thêm

- **Munkres, Topology:** §1–2 (Set Theory fundamentals)
- **Enderton, Elements of Set Theory:** Chapters 1–3 (Rigorous treatment)
- **Hrbacek & Jech, Introduction to Set Theory:** Chapter 1 (Modern approach)
- **Morris, Topology Without Tears:** Chapter 1, §1.1 (Gentle introduction)

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã xây dựng bốn khái niệm nền tảng cho tô-pô học. Thứ nhất là **lý thuyết tập hợp**, nơi nghịch lý Russell cho thấy trực giác ngây thơ là chưa đủ và cần đến hệ tiên đề ZF để bảo đảm tính nhất quán. Thứ hai là **ánh xạ** cùng ba phân loại cơ bản (đơn ánh, toàn ánh, song ánh), vốn gắn trực tiếp với các phép nhúng, ánh xạ thương và phép đồng phôi trong tô-pô. Thứ ba là **quan hệ tương đương**, dẫn đến lớp tương đương và phân hoạch — cơ sở cho phép xây dựng không gian thương. Cuối cùng là **lực lượng**, cho thấy tồn tại các mức độ vô hạn khác nhau, trong đó các tập đếm được (như $\mathbb{N}, \mathbb{Z}, \mathbb{Q}$) có lực lượng nhỏ hơn tập không đếm được như $\mathbb{R}$.

**Ý chính cần ghi nhớ:** Tập hợp là đơn vị cấu thành cơ bản của toán học hiện đại và cần được tiên đề hóa chặt chẽ; song ánh là tiêu chuẩn so sánh lực lượng giữa các tập hợp kể cả khi vô hạn; quan hệ tương đương hình thức hóa khái niệm đồng nhất và tạo nền cho không gian thương; và bất đẳng thức $|\mathbb{N}| < |\mathbb{R}|$ phản ánh sự phân tầng lực lượng sẽ được dùng nhiều trong các chương sau.

**Tiếp theo:** Trong Bài 00.01, ta sẽ tìm hiểu về **Tích Đề-các** (*Cartesian Product*) và **Bổ đề Zorn** — công cụ quan trọng để chứng minh sự tồn tại của nhiều đối tượng trong tô-pô.

---

*"In mathematics, you don't understand things. You just get used to them." — John von Neumann*

🎯 **Hãy làm bài tập và vẽ hình minh họa thường xuyên khi học tô-pô.** 🎯

---

**Next:** [Lecture 00.01: Cartesian Products and Zorn's Lemma](/contents/vi/topology-chapter00/00_01_Cartesian_Products_Zorns_Lemma/)
