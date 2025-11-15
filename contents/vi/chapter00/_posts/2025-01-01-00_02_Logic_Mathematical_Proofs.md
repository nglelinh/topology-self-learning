---
layout: post
title: "Lecture 00.02: Logic and Mathematical Proofs"
lang: vi
lang-ref: lecture-00-02
chapter: 0
lecture: 2
categories: [chapter00]
tags: [logic, proof-techniques, induction, contradiction]
description: "Logic toán học, các kỹ thuật chứng minh: trực tiếp, phản chứng, quy nạp"
---

**Logic and Mathematical Proofs**

---

## 📖 Tổng quan

Topology là một môn học đòi hỏi **reasoning** chặt chẽ. Không giống như calculus nơi bạn "tính toán" để tìm đáp án, trong topology bạn **chứng minh** các mệnh đề bằng logic thuần túy. Một định lý topology có thể nói: "Mọi không gian compact và Hausdorff đều normal"—không có số, không có công thức, chỉ có logic và cấu trúc.

Để thành công trong topology, bạn cần thành thạo **proof techniques** (kỹ thuật chứng minh). Đây không phải "tricks"—chúng là cách tư duy có hệ thống để biến trực giác thành lập luận nghiêm ngặt.

Trong bài này, chúng ta sẽ học bốn pillars của mathematical reasoning. Đầu tiên, **propositional logic** teaches us làm sao combine simple statements thành complex ones using connectives như "and", "or", và crucially "implies". Thứ hai, **quantifiers** ("for all" và "there exists") cho phép ta make general statements about infinite collections—backbone của topology definitions. Thứ ba, **proof techniques** (direct, contrapositive, contradiction, induction) provide systematic strategies để transform intuition thành rigorous arguments. Cuối cùng, understanding **common pitfalls** helps us avoid logical traps mà even experienced mathematicians sometimes fall into.

**Tại sao bài này fundamental?** Mọi single theorem trong topology—from basic definitions đến deep results—relies on rigorous proof. Khi bạn đọc một topology textbook, understanding logical structure cho phép bạn "parse" complex proofs thành manageable pieces. Hơn nữa, these techniques không chỉ là tools để verify existing results; chúng empower bạn để discover new mathematics, to ask "what if" questions và answer them rigorously.

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Chứng minh

Tưởng tượng bạn là một thám tử. Bạn có một giả thuyết: "Người A là thủ phạm". Có nhiều cách tiếp cận: **Direct proof** involves chỉ ra bằng chứng trực tiếp—A có động cơ, có mặt tại hiện trường, fingerprints match. **Proof by contradiction** starts bằng cách giả sử opposite (A không phải thủ phạm), rồi show rằng điều này leads to một absurdity contradicting known evidence. **Proof by contrapositive** reasons: nếu ai đó không có mặt tại hiện trường, họ không thể là thủ phạm—establishing contrapositive của "thủ phạm ⇒ có mặt tại hiện trường".

Mathematical proofs work exactly như vậy! Một **chứng minh** là một carefully constructed chain of logical steps starting từ accepted **giả thiết** (hypotheses, axioms, previously proven theorems) và leading inexorably đến **kết luận** (conclusion). Mỗi step phải follow from previous ones by pure logic, creating an argument mà any reasonable person must accept một khi họ accept the starting assumptions.

**Ví dụ đơn giản:**

**Mệnh đề:** Nếu n là số chẵn, thì n² là số chẵn.

**Chứng minh:**  
Giả sử n chẵn. Theo định nghĩa, tồn tại k ∈ ℤ sao cho n = 2k.  
Khi đó: n² = (2k)² = 4k² = 2(2k²).  
Vì 2k² ∈ ℤ, nên n² chẵn. ∎

Đơn giản! Nhưng đây là nền tảng của mọi chứng minh topology phức tạp.

---

## 📐 Định nghĩa Hình thức

### 1. Propositional Logic (Logic Mệnh đề)

**Mệnh đề (Proposition):** Một câu có giá trị đúng (T) hoặc sai (F).

**Ví dụ:**
- "2 + 2 = 4" → T
- "Paris là thủ đô của Đức" → F
- "x > 5" → Không phải mệnh đề (phụ thuộc vào x)

#### Logical Connectives (Liên từ Logic)

| Ký hiệu | Tên | Định nghĩa | Ví dụ |
|---------|-----|------------|-------|
| ¬P | NOT (Phủ định) | Đảo giá trị P | Nếu P: "n chẵn", ¬P: "n lẻ" |
| P ∧ Q | AND (Hội) | Đúng khi cả P, Q đúng | "n chẵn VÀ n > 10" |
| P ∨ Q | OR (Tuyển) | Đúng khi ít nhất một đúng | "n chẵn HOẶC n > 10" |
| P ⇒ Q | Implication (Kéo theo) | "Nếu P thì Q" | "Nếu n chẵn thì n² chẵn" |
| P ⇔ Q | Biconditional (Tương đương) | P ⇒ Q và Q ⇒ P | "n chẵn ⇔ n = 2k" |

**Truth Table của Implication:**

| P | Q | P ⇒ Q |
|---|---|-------|
| T | T | T |
| T | F | F |
| F | T | T |
| F | F | T |

**Chú ý quan trọng:** P ⇒ Q đúng khi P sai! (Vacuous truth)

**Ví dụ kỳ lạ:** "Nếu 1 + 1 = 3 thì tôi là Napoleon" → Mệnh đề này ĐÚNG!

![Logic gates visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9f/Venn_diagram_for_OR.svg/300px-Venn_diagram_for_OR.svg.png)  
*Biểu đồ Venn cho OR logic - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Venn_diagram_for_OR.svg)*

---

### 2. Quantifiers (Lượng từ)

#### Universal Quantifier (∀)

**∀x ∈ S: P(x)** đọc là "Với mọi x trong S, P(x) đúng"

**Ví dụ:**
- ∀n ∈ ℕ: n² ≥ 0
- ∀x ∈ ℝ: x² - 1 = (x-1)(x+1)

**Phủ định:**
$$
\neg(\forall x: P(x)) \equiv \exists x: \neg P(x)
$$

"Không phải mọi x đều thỏa P" ⇔ "Tồn tại x không thỏa P"

#### Existential Quantifier (∃)

**∃x ∈ S: P(x)** đọc là "Tồn tại x trong S sao cho P(x) đúng"

**Ví dụ:**
- ∃n ∈ ℕ: n² = 16 (Đúng, n = 4)
- ∃x ∈ ℝ: x² = -1 (Sai trong ℝ, đúng trong ℂ)

**Phủ định:**
$$
\neg(\exists x: P(x)) \equiv \forall x: \neg P(x)
$$

"Không tồn tại x thỏa P" ⇔ "Mọi x đều không thỏa P"

#### Nested Quantifiers (Lượng từ lồng nhau)

**Thứ tự quan trọng!**

- **∀x ∃y: P(x,y)** ≠ **∃y ∀x: P(x,y)**

**Ví dụ:**
1. **∀x ∈ ℝ ∃y ∈ ℝ: y > x**  
   "Với mọi x, tồn tại y lớn hơn x" → ĐÚNG (chọn y = x + 1)

2. **∃y ∈ ℝ ∀x ∈ ℝ: y > x**  
   "Tồn tại y lớn hơn mọi x" → SAI (không có số lớn nhất)

**Trong topology:**

**Định nghĩa (Continuity):**
$$
\forall \varepsilon > 0 \; \exists \delta > 0 \; \forall x: (|x - a| < \delta \implies |f(x) - f(a)| < \varepsilon)
$$

Thứ tự quantifiers xác định chính xác khái niệm "liên tục"!

---

### 3. Proof Techniques (Kỹ thuật Chứng minh)

#### A. Direct Proof (Chứng minh Trực tiếp)

**Cấu trúc:** Giả sử P đúng → Suy luận từng bước → Kết luận Q đúng

**Ví dụ:**

**Mệnh đề:** Nếu a, b là số lẻ, thì a + b chẵn.

**Chứng minh:**  
Giả sử a, b lẻ. Theo định nghĩa:
- a = 2k + 1 với k ∈ ℤ
- b = 2m + 1 với m ∈ ℤ

Do đó:
$$
a + b = (2k + 1) + (2m + 1) = 2(k + m + 1)
$$

Vì k + m + 1 ∈ ℤ, nên a + b chẵn. ∎

**Khi nào dùng:** Khi có "đường" rõ ràng từ giả thiết đến kết luận.

---

#### B. Proof by Contrapositive (Chứng minh bằng Mệnh đề Đảo)

**Nguyên tắc:** Để chứng minh P ⇒ Q, ta chứng minh ¬Q ⇒ ¬P (tương đương logic!)

**Ví dụ:**

**Mệnh đề:** Nếu n² chẵn, thì n chẵn.

**Chứng minh (bằng contrapositive):**  
Ta chứng minh: Nếu n lẻ, thì n² lẻ.

Giả sử n lẻ, tức n = 2k + 1.  
Khi đó:
$$
n² = (2k + 1)² = 4k² + 4k + 1 = 2(2k² + 2k) + 1
$$

Nên n² lẻ. ∎

**Khi nào dùng:** Khi ¬Q dễ làm việc hơn Q (ví dụ: Q là phủ định)

---

#### C. Proof by Contradiction (Chứng minh bằng Phản chứng)

**Cấu trúc:** Giả sử kết luận SAI → Suy luận → Dẫn đến mâu thuẫn → Kết luận ban đầu ĐÚNG

**Ví dụ kinh điển:**

**Mệnh đề:** √2 là số vô tỉ.

**Chứng minh:**  
Giả sử (phản chứng) √2 hữu tỉ. Khi đó:
$$
\sqrt{2} = \frac{p}{q}
$$
với p, q ∈ ℤ, gcd(p,q) = 1 (tối giản).

Bình phương hai vế:
$$
2 = \frac{p²}{q²} \implies p² = 2q²
$$

Do đó p² chẵn ⇒ p chẵn (theo ví dụ trước) ⇒ p = 2k.

Thay vào:
$$
(2k)² = 2q² \implies 4k² = 2q² \implies q² = 2k²
$$

Do đó q² chẵn ⇒ q chẵn.

**Mâu thuẫn!** Cả p và q đều chẵn → gcd(p,q) ≥ 2, trái với giả thiết tối giản.

Vậy √2 vô tỉ. ∎

![Proof by contradiction flowchart](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Proof_by_Contradiction_Diagram.svg/400px-Proof_by_Contradiction_Diagram.svg.png)  
*Sơ đồ chứng minh phản chứng - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Proof_by_Contradiction_Diagram.svg)*

**Khi nào dùng:** Khi khó chứng minh trực tiếp, đặc biệt với các mệnh đề về sự "không tồn tại".

---

#### D. Mathematical Induction (Quy nạp Toán học)

**Nguyên tắc:** Để chứng minh P(n) đúng với mọi n ∈ ℕ:
1. **Base case:** Chứng minh P(1) đúng (hoặc P(0))
2. **Inductive step:** Giả sử P(k) đúng (inductive hypothesis), chứng minh P(k+1) đúng

**Ví dụ:**

**Mệnh đề:** Với mọi n ≥ 1:
$$
1 + 2 + 3 + \cdots + n = \frac{n(n+1)}{2}
$$

**Chứng minh:**

**Base case (n = 1):**
$$
1 = \frac{1 \cdot 2}{2} = 1 \quad \checkmark
$$

**Inductive step:**  
Giả sử công thức đúng với n = k:
$$
1 + 2 + \cdots + k = \frac{k(k+1)}{2}
$$

Ta cần chứng minh đúng với n = k + 1:
$$
1 + 2 + \cdots + k + (k+1) = \frac{(k+1)(k+2)}{2}
$$

Theo giả thiết quy nạp:
$$
1 + 2 + \cdots + k + (k+1) = \frac{k(k+1)}{2} + (k+1)
$$
$$
= \frac{k(k+1) + 2(k+1)}{2} = \frac{(k+1)(k+2)}{2} \quad \checkmark
$$

Vậy công thức đúng với mọi n ∈ ℕ. ∎

![Mathematical induction dominoes](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Dominoeffect.png/400px-Dominoeffect.png)  
*Hiệu ứng domino minh họa quy nạp - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Dominoeffect.png)*

**Biến thể:**
- **Strong induction:** Giả sử P(1), ..., P(k) đều đúng → chứng minh P(k+1)
- **Well-ordering principle:** Tương đương với induction

**Khi nào dùng:** Chứng minh công thức, tính chất phụ thuộc vào n ∈ ℕ

---

### 4. Common Logical Mistakes (Lỗi Logic Phổ biến)

#### Mistake 1: Converse Error

**Sai lầm:** P ⇒ Q đúng KHÔNG có nghĩa là Q ⇒ P đúng!

**Ví dụ:**
- **Đúng:** "Nếu trời mưa, đường ướt" (P ⇒ Q)
- **SAI:** "Nếu đường ướt, trời mưa" (Q ⇒ P) — có thể ai đó tưới nước!

**Trong topology:**
- **Đúng:** "Nếu không gian compact, mọi dãy có dãy con hội tụ"
- **SAI:** "Nếu mọi dãy có dãy con hội tụ, không gian compact" (Sai trong không gian không metric!)

#### Mistake 2: Quantifier Order

**Sai lầm:** Đổi thứ tự ∀ và ∃

**Ví dụ:**
- **∀ε ∃δ:** "Với mọi ε, tồn tại δ" → Continuity
- **∃δ ∀ε:** "Tồn tại δ với mọi ε" → Nonsense!

#### Mistake 3: Vacuous Truth Confusion

**Sai lầm:** Quên rằng P ⇒ Q đúng khi P sai

**Ví dụ:** "Mọi số chẵn lẻ đều chia hết cho 7" → ĐÚNG (vì không có số chẵn lẻ!)

---

## 🧠 Fundamental Papers & References

### Classic Logic Texts

1. **Aristotle** - *Organon* (~350 BCE)  
   *Nền tảng của logic hình thức phương Tây*

2. **Gottlob Frege** - *Begriffsschrift* (1879)  
   *Phát minh ký hiệu logic hiện đại, quantifiers*

3. **Bertrand Russell & Alfred N. Whitehead** - *Principia Mathematica* (1910–1913)  
   *Cố gắng xây dựng toàn bộ toán học từ logic*

4. **Kurt Gödel** - *Incompleteness Theorems* (1931)  
   *Chứng minh giới hạn của logic hình thức*

### Textbooks for Topology

5. **James R. Munkres** - *Topology*, 2nd Ed., **§2: Logical Implications**  
   *Brief nhưng đủ cho topology*

6. **Daniel J. Velleman** - *How to Prove It* (2006)  
   *Giáo trình proof-writing xuất sắc cho beginners*

7. **Richard Hammack** - *Book of Proof* (2013)  
   *Free online, rất accessible*

8. **Patrick Suppes** - *Introduction to Logic* (1957)  
   *Classic text, formal approach*

---

## 🔗 Applications and Connections

### Computer Science - Formal Verification
**Proof Assistants** như Coq, Lean, Isabelle sử dụng logic hình thức để verify tính đúng đắn của phần mềm. Mọi chứng minh toán học có thể được "formalize" thành code!

**Ví dụ:** Định lý Four Color Theorem đã được chứng minh hoàn toàn bằng computer (Coq).

### Mathematics - Gödel's Theorems
**Incompleteness Theorems:** Trong bất kỳ hệ thống hình thức đủ mạnh (chứa số học), luôn tồn tại mệnh đề không thể chứng minh hoặc bác bỏ được.

**Ý nghĩa:** Có giới hạn của "proof"—không phải mọi sự thật toán học đều chứng minh được!

### Philosophy - Foundations of Mathematics
**Intuitionistic Logic:** Một số toán học gia từ chối Law of Excluded Middle (P ∨ ¬P luôn đúng) và proof by contradiction.

**Ví dụ:** Trong toán học constructive, chứng minh "∃x: P(x)" cần phải chỉ ra tường minh x là gì!

### Real-World Example
**Legal Reasoning:** Hệ thống pháp luật sử dụng logic: "Nếu X phạm tội Y, thì X bị phạt Z". Proof by contradiction xuất hiện: "Giả sử bị cáo vô tội, nhưng bằng chứng cho thấy..."

---

## 🧩 Exercises

### Basic Logic

1. **Truth Tables:**  
   Tạo truth table cho (P ∨ Q) ⇒ (P ∧ Q). Điều kiện nào làm cho mệnh đề này đúng?

2. **Negations:**  
   Viết phủ định của các mệnh đề sau:
   - a) ∀x ∈ ℝ: x² ≥ 0
   - b) ∃n ∈ ℕ: n² < n
   - c) ∀ε > 0 ∃δ > 0: |x - a| < δ ⇒ |f(x) - f(a)| < ε

3. **Quantifier Order:**  
   Phát biểu bằng lời nói và xác định đúng/sai:
   - a) ∀x ∈ ℝ ∃y ∈ ℝ: x + y = 0
   - b) ∃y ∈ ℝ ∀x ∈ ℝ: x + y = 0
   - c) ∀x ∈ ℝ ∀y ∈ ℝ: (x < y ⇒ x² < y²)

### Proof Practice

4. **Direct Proof:**  
   Chứng minh: Nếu n chia hết cho 6, thì n chia hết cho 2 và 3.

5. **Contrapositive:**  
   Chứng minh: Nếu n² không chia hết cho 3, thì n không chia hết cho 3.

6. **Contradiction:**  
   Chứng minh: Không tồn tại số hữu tỉ r sao cho r² = 3.

7. **Induction:**  
   Chứng minh: Với mọi n ≥ 1,
   $$
   1² + 2² + 3² + \cdots + n² = \frac{n(n+1)(2n+1)}{6}
   $$

### Topology-Related

8. **Logical Structure:**  
   Định nghĩa topology: "Một họ 𝜏 của các tập con của X là topology nếu:
   - (i) ∅, X ∈ 𝜏
   - (ii) Hợp tùy ý các tập trong 𝜏 thuộc 𝜏
   - (iii) Giao hữu hạn các tập trong 𝜏 thuộc 𝜏"
   
   Viết lại (ii) và (iii) bằng ký hiệu logic với quantifiers.

9. **Continuity:**  
   Định nghĩa ε-δ của continuity:
   $$
   \forall \varepsilon > 0 \; \exists \delta > 0 \; \forall x: (|x - a| < \delta \implies |f(x) - f(a)| < \varepsilon)
   $$
   
   Viết định nghĩa "f không liên tục tại a" (phủ định).

10. **Proof Analysis:**  
    Đọc chứng minh sau và xác định kỹ thuật nào được dùng:
    
    **Mệnh đề:** Tập số nguyên tố là vô hạn.
    
    **Chứng minh:** Giả sử (phản chứng) chỉ có hữu hạn số nguyên tố: p₁, p₂, ..., pₙ.  
    Xét N = p₁p₂...pₙ + 1.  
    N không chia hết cho bất kỳ pᵢ nào (dư 1).  
    Do đó N nguyên tố hoặc có ước nguyên tố khác không nằm trong danh sách → Mâu thuẫn! ∎

### Advanced

11. **Constructive vs Non-constructive:**  
    Chứng minh: Tồn tại hai số vô tỉ a, b sao cho a^b hữu tỉ.
    
    **Hint:** Xét √2^√2. Nếu nó hữu tỉ → done. Nếu vô tỉ, xét (√2^√2)^√2 = √2^2 = 2.
    
    Chứng minh này có "constructive" không? (Có chỉ ra tường minh a, b không?)

12. **Meta-mathematics:**  
    Tìm hiểu về "Law of Excluded Middle": P ∨ ¬P luôn đúng.  
    - Tại sao intuitionistic logic từ chối nó?
    - Ứng dụng gì trong topology?

---

## 📚 Further Reading

- **Velleman, How to Prove It:** Chapters 1–3 (Propositional and Quantificational Logic)
- **Hammack, Book of Proof:** Chapters 4–6 (Direct Proof, Contrapositive, Contradiction)
- **Munkres, Topology:** §2 (Logical implications in set theory)
- **Eccles, An Introduction to Mathematical Reasoning:** Comprehensive proof techniques

---

## 🎓 Summary

Trong bài giảng này, chúng ta đã học:

✅ **Propositional Logic:** Connectives (¬, ∧, ∨, ⇒, ⇔)  
✅ **Quantifiers:** ∀ (universal), ∃ (existential), và thứ tự quan trọng  
✅ **Proof Techniques:**
   - Direct proof: P → ... → Q
   - Contrapositive: ¬Q → ... → ¬P
   - Contradiction: ¬Q → ... → False
   - Induction: P(1) ∧ [P(k) ⇒ P(k+1)] → ∀n: P(n)  
✅ **Common Mistakes:** Converse error, quantifier order, vacuous truth  

**Điểm chính:**
- Logic là ngôn ngữ của toán học—hiểu logic = hiểu chứng minh
- Mỗi kỹ thuật chứng minh có điểm mạnh riêng
- Quantifiers phải được sắp xếp cẩn thận
- Practice là chìa khóa: làm nhiều bài tập!

**Connection đến topology:**
- Mọi định nghĩa topology đều có cấu trúc quantifier phức tạp
- Proof by contradiction rất phổ biến (compactness, connectedness)
- Induction dùng cho các construction quy nạp (CW complexes)

**Tiếp theo:** Trong Lecture 00.03, chúng ta sẽ học về **Real Numbers và Euclidean Space**—chuẩn bị cho việc hiểu topology trên ℝⁿ, ví dụ cụ thể đầu tiên về không gian tô-pô.

---

*"A mathematician is a device for turning coffee into theorems." — Paul Erdős*

🎯 **Hãy practice chứng minh mỗi ngày! Logic như muscle: càng luyện càng mạnh.** 🎯

---

**Previous:** [Lecture 00.01: Cartesian Products and Zorn's Lemma](/contents/vi/topology-chapter00/00_01_Cartesian_Products_Zorns_Lemma/)  
**Next:** [Lecture 00.03: Real Numbers and Euclidean Space](/contents/vi/topology-chapter00/00_03_Real_Numbers_Euclidean_Space/)

