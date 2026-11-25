---
layout: post
title: "Lecture 02.02: Local Compactness and Compactification"
lang: vi
lang-ref: lecture-02-02
chapter: 2
lecture: 2
categories: [chapter02]
tags: [locally-compact, compactification, one-point-compactification, stone-cech]
description: "Locally compact spaces, one-point compactification, và Stone-Čech compactification"
---

**Tính Compact địa phương và Phép Compact hóa**

---

## 📖 Tổng quan

Hầu hết những không gian quan trọng nhất của vật lý và giải tích — như đường thẳng $$\mathbb{R}$$, mặt phẳng phức $$\mathbb{C}$$, hay không gian Euclid $$\mathbb{R}^n$$ — lại mang một "khuyết điểm" khó chịu: chúng **không compact**, vì chạy dài ra tới vô cực! Nhưng bạn hãy để ý hai điều kỳ diệu: thứ nhất, đứng tại *bất kỳ* điểm nào trên $$\mathbb{R}$$, chỉ cần bước vào một đoạn đóng nhỏ quanh nó (như $$[x-1, x+1]$$) là ta lại có ngay một thế giới compact ấm cúng (**compact địa phương**); thứ hai, chỉ cần khéo léo khâu thêm **đúng một điểm ở vô cực $$\infty$$**, đường thẳng $$\mathbb{R}$$ cuộn tròn ngay thành đường tròn $$S^1$$, còn mặt phẳng phức $$\mathbb{C}$$ khép kín thành **mặt cầu Riemann $$S^2$$**!

Bài giảng này mở ra nghệ thuật "thuần hóa vô cực" trong tô-pô học qua ba khái niệm nối tiếp nhau: **không gian compact địa phương**, **compact hóa một điểm (Alexandroff)** — phép đóng gói gọn gàng nhất — và **compact hóa Stone–Čech**, phiên bản "lớn nhất và phổ dụng nhất" cho phép mở rộng mọi hàm liên tục bị chặn.

![One-point compactification of R](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Compactification.svg/400px-Compactification.svg.png)  
*Compact hóa một điểm của $\mathbb{R}$ thành $S^1$ - Nguồn minh họa khái niệm*

**Mạch bài học:** Kiến thức cần nhớ (compact địa phương, compact hóa một điểm Alexandroff & compact hóa Stone–Čech) → Giải thích: cầm tay tính tọa độ phép chiếu nổi biến $$\mathbb{R} \cup \{\infty\}$$ thành đường tròn $$S^1$$ → Định nghĩa & Ví dụ kinh điển → Bài tập & Tóm tắt.

---

## Kiến thức cần nhớ: Tính Compact địa phương và Phép Compact hóa nghiên cứu những gì?

### 1. Không gian Compact địa phương (Locally Compact)

Một không gian Hausdorff $$X$$ là **compact địa phương** nếu mọi điểm $$x \in X$$ đều có một lân cận mở $$U$$ nằm gọn trong một tập con compact $$K$$ ($$x \in U \subseteq K$$). Mọi đa tạp hữu hạn chiều $$\mathbb{R}^n$$ đều compact địa phương; ngược lại, tập số hữu tỉ $$\mathbb{Q}$$ (bị thủng vô số lỗ vô tỉ trong mọi khoảng) và không gian Hilbert vô hạn chiều $$\ell^2$$ **không** compact địa phương!

### 2. Compact hóa một điểm (Alexandroff): phép đóng gói "nhỏ nhất"

Với mọi không gian Hausdorff compact địa phương nhưng không compact $$X$$, ta thêm đúng một điểm $$\infty \notin X$$ và quy ước các lân cận mở của $$\infty$$ chính là phần bù $$X^* \setminus K$$ của các tập compact $$K \subseteq X$$. Kết quả $$X^* = X \cup \{\infty\}$$ là không gian **compact và Hausdorff**, chứa $$X$$ như một tập con mở trù mật: $$\mathbb{R}^* \cong S^1$$, $$\mathbb{R}^2 \cup \{\infty\} \cong S^2$$, và tổng quát $$(\mathbb{R}^n)^* \cong S^n$$!

### 3. Compact hóa Stone–Čech $$\beta X$$: phép đóng gói "lớn nhất"

Trong khi Alexandroff thêm *ít điểm nhất* (chỉ 1 điểm), **compact hóa Stone–Čech** $$\beta X$$ thêm đủ nhiều điểm ở biên để **mọi hàm liên tục bị chặn $$f: X \to [0, 1]$$ đều mở rộng duy nhất được thành hàm liên tục $$\tilde{f}: \beta X \to [0, 1]$$**. (Chẳng hạn hàm $$\sin(x)$$ trên $$\mathbb{R}$$ không có giới hạn khi $$x \to \infty$$ nên không mở rộng được lên $$\mathbb{R} \cup \{\infty\}$$, nhưng lại mở rộng trơn tru lên $$\beta\mathbb{R}$$!)

---

### Giải thích: Cầm tay kiểm chứng phép chiếu nổi $$\mathbb{R} \cup \{\infty\} \cong S^1$$

Đặt đường tròn đơn vị $$S^1 = \{(u, v) \in \mathbb{R}^2 : u^2 + v^2 = 1\}$$ với cực Bắc $$N = (0, 1)$$. Nối đường thẳng từ $$N(0, 1)$$ qua điểm $$(x, 0)$$ trên trục hoành $$\mathbb{R}$$, ta cắt đường tròn tại đúng một điểm thứ hai $$\varphi(x) = (u, v)$$:
$$
\varphi(x) = \left(\frac{2x}{x^2 + 1},\; \frac{x^2 - 1}{x^2 + 1}\right) \quad (x \in \mathbb{R}), \qquad \varphi(\infty) = (0, 1) = N.
$$
Hãy tự tay kiểm tra công thức này ở từng bước:

1. **Kiểm tra điểm ảnh nằm chính xác trên đường tròn $$S^1$$:**
   $$
   u^2 + v^2 = \frac{4x^2 + (x^2 - 1)^2}{(x^2 + 1)^2} = \frac{4x^2 + x^4 - 2x^2 + 1}{(x^2 + 1)^2} = \frac{(x^2 + 1)^2}{(x^2 + 1)^2} = \mathbf{1}!
   $$
2. **Thay 4 giá trị cụ thể của $$x$$ để thấy trục số cuộn thành đường tròn:**
   - $$x = 0 \implies \varphi(0) = (0,\; -1)$$ (đúng **cực Nam** của đường tròn).
   - $$x = 1 \implies \varphi(1) = (1,\; 0)$$ (đúng **cực Đông**); tương tự $$x = -1 \mapsto (-1,\; 0)$$ (**cực Tây**).
   - $$x = 10 \implies \varphi(10) = \left(\frac{20}{101},\; \frac{99}{101}\right) \approx (0.198,\; 0.980)$$ — tiến sát cực Bắc $$N(0, 1)$$ từ phía phải!
   - $$x = -10 \implies \varphi(-10) = \left(-\frac{20}{101},\; \frac{99}{101}\right) \approx (-0.198,\; 0.980)$$ — tiến sát cực Bắc $$N(0, 1)$$ từ phía trái!
3. **Kiểm tra lân cận của $$\infty$$:** Một chỏm mở nhỏ quanh cực Bắc $$N$$ (ví dụ $$v > \frac{99}{101}$$) có ảnh ngược dưới $$\varphi$$ chính là $$\{x \in \mathbb{R} : \lvert x \rvert > 10\} \cup \{\infty\} = (\mathbb{R} \cup \{\infty\}) \setminus [-10, 10]$$ — khớp **chính xác 100%** với định nghĩa lân cận của $$\infty$$ là phần bù của tập compact $$[-10, 10]$$ trong compact hóa Alexandroff!

---

## 📐 Không gian compact địa phương (Locally Compact Spaces)

### 1. Định nghĩa và ví dụ

<div class="textbook-definition" markdown="1">
**Định nghĩa (Compact địa phương):**  
Không gian tô-pô $X$ là **compact địa phương** (*locally compact*) nếu mỗi điểm $x \in X$ đều có ít nhất một **lân cận compact**, tức tồn tại tập compact $K$ và tập mở $U$ sao cho:

$$
\forall x \in X: \exists K \text{ compact}, \exists U \in \tau: x \in U \subseteq K
$$
</div>

*(Trong không gian Hausdorff, điều kiện này tương đương với dạng mạnh hơn: với mọi $x \in X$ và mọi lân cận $V$ của $x$, tồn tại tập compact $K$ sao cho $x \in \text{int}(K) \subseteq K \subseteq V$.)*

**Ví dụ:**
- **$\mathbb{R}^n$:** Compact địa phương vì mọi điểm $x$ đều có hình cầu đóng $\overline{B}(x, 1)$ compact (theo Định lý Heine–Borel).
- **Đa tạp $n$ chiều:** Mọi đa tạp đều compact địa phương vì cục bộ đồng phôi với $\mathbb{R}^n$.
- **Không gian rời rạc:** Compact địa phương vì $\{x\}$ là lân cận compact của $x$.

**Phản ví dụ:**
- **$\mathbb{Q}$ (với tô-pô con từ $\mathbb{R}$):** Không compact địa phương.

<div class="textbook-proof" markdown="1">
**Chứng minh:** Mọi tập con compact $K$ của $\mathbb{Q}$ đều có phần trong rỗng trong $\mathbb{Q}$ (vì nếu $K$ chứa một khoảng $(a, b) \cap \mathbb{Q}$, ta chọn số vô tỉ $r \in (a, b)$ và một dãy trong $(a, b) \cap \mathbb{Q}$ hội tụ về $r \notin \mathbb{Q}$, trái với tính compact của $K$). Do đó không có điểm nào của $\mathbb{Q}$ có lân cận compact.
</div>

- **Không gian Hilbert vô hạn chiều $\ell^2$:** Không compact địa phương (theo định lý Riesz).

---

### 2. Tính chất

<div class="textbook-theorem" markdown="1">
**Định lý (Không gian con đóng):**  
Nếu $X$ compact địa phương Hausdorff và $F \subseteq X$ đóng, thì $F$ compact địa phương.
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Không gian con mở):**  
Nếu $X$ compact địa phương Hausdorff và $U \subseteq X$ mở, thì $U$ compact địa phương.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Dành làm bài tập (sử dụng cơ sở lân cận compact trong không gian Hausdorff).
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Tích hữu hạn):**  
Nếu $X$ và $Y$ compact địa phương, thì $X \times Y$ compact địa phương.
</div>

*(Lưu ý: tích vô hạn của các không gian compact địa phương nói chung không còn compact địa phương, trừ khi hầu hết các nhân tử đều compact.)*

---

## 📐 Compact hóa một điểm (One-Point Compactification)

### 1. Cách xây dựng (Alexandroff Compactification)

Cho $X$ là không gian Hausdorff compact địa phương và **không compact**. Bổ sung một điểm mới $\infty \notin X$ và đặt:
$$
X^* = X \cup \{\infty\}
$$

Ta trang bị cho $X^*$ tô-pô $\tau^*$ gồm:
- Tất cả các tập mở $U \in \tau$ của $X$;
- Các tập dạng $X^* \setminus K = \{\infty\} \cup (X \setminus K)$, với $K \subseteq X$ là tập con compact (và do đó đóng trong $X$).

Viết gọn lại:
$$
\tau^* = \tau \cup \{X^* \setminus K : K \subseteq X \text{ compact closed}\}
$$

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Không gian $X^*$ là một không gian **compact Hausdorff**, chứa $X$ như một không gian con mở và trù mật.
</div>

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:**
</div>

- **Tính Hausdorff:** Hai điểm phân biệt trong $X$ được tách bằng tính Hausdorff của $X$. Nếu một điểm là $x \in X$ và điểm kia là $\infty$, chọn lân cận compact $K$ của $x$; khi đó $U = \text{int}(K)$ và $V = X^* \setminus K$ là hai tập mở rời nhau tách $x$ và $\infty$.
- **Tính compact:** Cho $\{U_\alpha\}$ là một phủ mở của $X^*$. Chọn $U_{\alpha_0}$ chứa $\infty$; khi đó $U_{\alpha_0} = X^* \setminus K$ với $K \subseteq X$ compact. Phần còn lại $K$ được phủ bởi $\{U_\alpha\}_{\alpha \neq \alpha_0}$ nên có phủ con hữu hạn; hợp phủ con đó với $U_{\alpha_0}$ ta được phủ con hữu hạn của $X^*$. ∎

---

### 2. Các ví dụ kinh điển

- **Đường thẳng thực $\mathbb{R}$:** $\mathbb{R}^* = \mathbb{R} \cup \{\infty\} \cong S^1$ thông qua phép chiếu nổi (ánh xạ $\infty$ vào cực Bắc của đường tròn).

![Stereographic projection](https://upload.wikimedia.org/wikipedia/commons/thumb/6/69/Stereoprojzero.svg/400px-Stereoprojzero.svg.png)  
*Phép chiếu nổi: $\mathbb{R} \cup \{\infty\} \cong S^1$ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Stereoprojzero.svg)*

- **Không gian Euclid $\mathbb{R}^n$:** $(\mathbb{R}^n)^* \cong S^n$.
- **Mặt phẳng phức $\mathbb{C}$:** $\mathbb{C}^* = \mathbb{C} \cup \{\infty\} \cong S^2$ được gọi là **mặt cầu Riemann** (*Riemann sphere*), công cụ trung tâm trong giải tích phức để nghiên cứu hàm phân hình.
- **Đĩa mở đơn vị $D^2$:** Vì $D^2 \cong \mathbb{R}^2$, ta có $(D^2)^* \cong S^2$.

---

### 3. Tính duy nhất

<div class="textbook-theorem" markdown="1">
**Định lý (Tính duy nhất):**  
Nếu $X$ là không gian Hausdorff compact địa phương không compact, thì compact hóa một điểm của $X$ là duy nhất sai khác một phép đồng phôi cố định trên $X$.
</div>

<div class="textbook-proof" markdown="1">
**Ghi chú chứng minh:** Nếu $Y$ là không gian compact Hausdorff chứa $X$ với $Y \setminus X = \{p\}$, thì ánh xạ đồng nhất trên $X$ và gửi $\infty \mapsto p$ là một phép đồng phôi $X^* \to Y$.
</div>

---

## 📐 Compact hóa Stone–Čech (Stone–Čech Compactification)

### 1. Tính chất phổ dụng

Compact hóa một điểm tuy đơn giản nhưng không bảo đảm mọi hàm thực liên tục bị chặn trên $X$ đều mở rộng liên tục lên $X^*$ (ví dụ $f(x) = \arctan(x)$ trên $\mathbb{R}$ có hai giới hạn khác nhau ở $+\infty$ và $-\infty$ nên không mở rộng được lên $\mathbb{R}^* = S^1$). **Compact hóa Stone–Čech** $\beta X$ khắc phục điều này bằng cách trở thành compact hóa Hausdorff "lớn nhất" có thể.

<div class="textbook-theorem" markdown="1">
**Định lý (Stone–Čech):**  
Với mọi không gian Tychonoff ($T_{3\frac{1}{2}}$) $X$, tồn tại một không gian compact Hausdorff $\beta X$ cùng một phép nhúng $i: X \to \beta X$ (với $i(X)$ trù mật trong $\beta X$) thỏa mãn tính chất phổ dụng sau:
</div>

**Tính chất phổ dụng:** Với mọi không gian compact Hausdorff $K$ và mọi ánh xạ liên tục $f: X \to K$, tồn tại **duy nhất** một ánh xạ liên tục mở rộng $\bar{f}: \beta X \to K$ sao cho $\bar{f} \circ i = f$.

```
X ---f---> K
|          
i|         
v          
βX --f̄--> K
```

---

### 2. Phác thảo cách xây dựng

Xét tập $\mathcal{F} = C(X, [0, 1])$ tất cả các hàm liên tục từ $X$ vào $[0, 1]$. Định nghĩa ánh xạ đánh giá $e: X \to [0, 1]^{\mathcal{F}}$ bởi:
$$
x \mapsto (\ldots, f(x), \ldots)
$$
Vì $X$ là không gian Tychonoff, $e$ là một phép nhúng. Lấy bao đóng $\beta X = \overline{e(X)}$ trong không gian compact $[0, 1]^{\mathcal{F}}$ (compact theo Định lý Tychonoff), ta thu được compact hóa Stone–Čech của $X$.

Cách xây dựng này mang tính phi xây dựng (dựa trên Định lý Tychonoff / Tiên đề Lựa chọn) và tạo ra không gian rất lớn: chẳng hạn $|\beta\mathbb{N}| = 2^{2^{\aleph_0}}$, và phần dư $\beta\mathbb{N} \setminus \mathbb{N}$ đồng nhất với không gian các siêu lọc tự do trên $\mathbb{N}$.

---

### 3. Một số ví dụ

- **Không gian compact Hausdorff $X$:** Khi $X$ đã compact, $\beta X = X$.
- **$\mathbb{N}$ (tô-pô rời rạc):** $|\beta\mathbb{N}| = 2^{2^{\aleph_0}}$, lớn hơn rất nhiều so với compact hóa một điểm $\mathbb{N}^* = \mathbb{N} \cup \{\infty\}$ (đếm được).
- **Khoảng mở $(0, 1)$:** Mặc dù $[0, 1]$ là một compact hóa của $(0, 1)$, nhưng $\beta(0, 1) \neq [0, 1]$ vì hàm liên tục bị chặn $f(x) = \sin(1/x)$ trên $(0, 1)$ không thể mở rộng liên tục tại $0$; thực tế vì $(0, 1) \cong \mathbb{R}$ nên $\beta(0, 1) \cong \beta\mathbb{R}$.
- **Đường thẳng thực $\mathbb{R}$:** $\beta\mathbb{R}$ khác và lớn hơn rất nhiều so với $\mathbb{R}^* \cong S^1$.

---

## 🔗 Ứng dụng

- **Tô-pô đại số — Đầu vô cực (*Ends*):** Phần dư của các phép compact hóa (như compact hóa Freudenthal và $\beta X \setminus X$) mô tả hành vi hình học ở vô cực: $\mathbb{R}$ có $2$ đầu vô cực ($\pm\infty$), còn $\mathbb{R}^n$ ($n \ge 2$) có $1$ đầu vô cực.
- **Giải tích phức — Mặt cầu Riemann:** Hàm phân hình trên $\mathbb{C}$ được hiểu là ánh xạ chỉnh hình từ $\mathbb{C}$ vào mặt cầu Riemann $\mathbb{C}^*$, trong đó các cực điểm nhận giá trị $\infty$.
- **Giải tích hàm — Đại số Banach:** Không gian các i-đê-an cực đại của đại số hàm liên tục bị chặn $C_b(X)$ đồng phôi với $\beta X$ (qua phép biến đổi Gelfand).
- **Lý thuyết tập hợp và tổ hợp:** $\beta\mathbb{N} \setminus \mathbb{N}$ tương ứng với không gian các siêu lọc không chính (*non-principal ultrafilters*) trên $\mathbb{N}$.

---

## Video tham khảo

- **xem trước** [Basic Topology 8 | Locally Compact Hausdorff Spaces](https://www.youtube.com/watch?v=UN86A94iz6I) — The Bright Side of Mathematics, tiếng Anh. Compact địa phương Hausdorff: mỗi điểm có một lân cận compact, đúng nửa đầu bài.
- [one point compactification -- Topology Video 18](https://www.youtube.com/watch?v=5tdsgjHlMtA) — MathMajor, tiếng Anh. Compact hóa một điểm, phép thêm một điểm ở vô cực mà bài xây ở nửa sau.
- [Lecture 31: One point compactification](https://www.youtube.com/watch?v=os9m6Q4gAzM) — NPTEL IIT Bombay, tiếng Anh. Cùng phép compact hóa một điểm, trong một bài giảng đại học đủ chậm để đối chiếu chứng minh.

## 🧩 Bài tập

### Tính compact địa phương

1. **Kiểm tra:** Chứng minh $\mathbb{R}^n$ là không gian compact địa phương.
2. **$\mathbb{Q}$ không compact địa phương:** Trình bày chứng minh chi tiết rằng $\mathbb{Q}$ không compact địa phương.
3. **Tích hữu hạn:** Chứng minh rằng nếu $X, Y$ compact địa phương thì $X \times Y$ compact địa phương.

### Compact hóa một điểm

4. **Compact hóa của $\mathbb{R}$:** Mô tả các tập mở chứa $\infty$ trong $\mathbb{R}^* = \mathbb{R} \cup \{\infty\}$ và chứng minh $\mathbb{R}^* \cong S^1$.
5. **Compact hóa của $\mathbb{R}^n$:** Xây dựng phép đồng phôi tường minh giữa $(\mathbb{R}^n)^*$ và $S^n$ bằng phép chiếu nổi.
6. **Vai trò của tính compact địa phương:** Giải thích vì sao phép xây dựng $X^*$ trên $X = \mathbb{Q}$ không tạo ra không gian Hausdorff.

### Compact hóa Stone–Čech

7. **Tính chất phổ dụng:** Cho $f: \mathbb{N} \to [0, 1]$ xác định bởi $f(n) = 1/n$. Ánh xạ mở rộng $\bar{f}: \beta\mathbb{N} \to [0, 1]$ nhận giá trị bằng bao nhiêu trên phần dư $\beta\mathbb{N} \setminus \mathbb{N}$?
8. **Lực lượng của $\beta\mathbb{N}$:** Tìm hiểu vì sao $|\beta\mathbb{N}| = 2^{2^{\aleph_0}}$ (*Gợi ý:* liên hệ với số siêu lọc trên $\mathbb{N}$).

### Nâng cao

9. **So sánh hai compact hóa:** So sánh $\mathbb{R}^*$ và $\beta\mathbb{R}$; nêu một hàm liên tục bị chặn trên $\mathbb{R}$ mở rộng được lên $\beta\mathbb{R}$ nhưng không mở rộng được lên $\mathbb{R}^*$.
10. **Số đầu vô cực:** Giải thích trực quan vì sao $\mathbb{R}$ có $2$ đầu vô cực còn $\mathbb{R}^2$ và $\mathbb{R}^3$ chỉ có $1$ đầu vô cực.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §29 (Local Compactness), §38 (Stone–Čech)
- **Willard, General Topology:** Chapter 6
- **Engelking, General Topology:** Chapter 3.5–3.6

---

## 🎓 Tóm tắt

✅ **Compact địa phương:** Mọi điểm đều có một lân cận compact (ví dụ $\mathbb{R}^n$ và các đa tạp).  
✅ **Compact hóa một điểm:** $X^* = X \cup \{\infty\}$ với tô-pô Alexandroff cho không gian compact Hausdorff duy nhất.  
✅ **Các trường hợp chuẩn:** $(\mathbb{R}^n)^* \cong S^n$ qua phép chiếu nổi.  
✅ **Compact hóa Stone–Čech $\beta X$:** Compact hóa phổ dụng cho không gian Tychonoff, cho phép mở rộng duy nhất mọi ánh xạ liên tục vào không gian compact Hausdorff.

**Tiếp theo:** Chương 03 sẽ nghiên cứu các **Tiên đề tách** (*Separation Axioms*).

---

🎯 **Hãy vẽ hình minh họa phép chiếu nổi biến $\mathbb{R}$ thành $S^1$ và $\mathbb{R}^2$ thành $S^2$.** 🎯

---

**Previous:** [Lecture 02.01: Compact Spaces](/contents/vi/topology-chapter02/02_01_Compact_Spaces/)  
**Next Chapter:** [Chapter 03: Separation Axioms](/contents/vi/topology-chapter03/)
