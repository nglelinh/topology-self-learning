---
layout: post
title: "Lecture 06.04: Seifert-Van Kampen Theorem"
lang: vi
lang-ref: lecture-06-04
chapter: 6
lecture: 4
categories: [chapter06]
tags: [van-kampen, fundamental-group, free-product, amalgamated-product]
description: "Seifert-Van Kampen Theorem: computing π₁ từ decomposition, free products, amalgamated products"
---

**Định lý Seifert–van Kampen**

---

## 📖 Tổng quan

Bên cạnh phương pháp không gian phủ và tương đương đồng luân, **Định lý Seifert–van Kampen** cung cấp phương pháp thứ ba rất linh hoạt để tính nhóm cơ bản theo chiến lược chia để trị:

> **Phân tách không gian $X = A \cup B$ thành hai tập mở liên thông đường, rồi tính $\pi_1(X)$ từ $\pi_1(A)$, $\pi_1(B)$ và $\pi_1(A \cap B)$ qua tích tự do có hợp nhất (amalgamated free product).**

Định lý này (do Herbert Seifert thiết lập năm 1931 và Egbert van Kampen tổng quát hóa năm 1933) đặc biệt hữu ích khi tính nhóm cơ bản của tổng chụm (wedge sum), các mặt đóng, phức CW và phần bù của nút trong $S^3$.

![Van Kampen decomposition](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Seifert-van_Kampen.svg/500px-Seifert-van_Kampen.svg.png)  
*Minh họa phân tách không gian $X = A \cup B$ trong định lý Seifert–van Kampen*

Trong bài học này, chúng ta sẽ nhắc lại khái niệm tích tự do và tích tự do có hợp nhất, phát biểu Định lý Seifert–van Kampen cùng các hệ quả đặc biệt, trình bày các ứng dụng tiêu chuẩn (hình số $8$, tổng chụm $n$ đường tròn, hình xuyến, mặt giống $g$, $\mathbb{R}P^2$) và phác thảo ý tưởng chứng minh.

---

## 🎯 Phát biểu Định lý Seifert–van Kampen

### 1. Tích tự do và Tích tự do có hợp nhất

**Nhắc lại (Tích tự do – Free Product):**  
Cho hai nhóm $G$ và $H$. **Tích tự do** $G * H$ là nhóm sinh bởi các phần tử của $G$ và $H$, chỉ giữ nguyên các quan hệ vốn có trong $G$ và trong $H$ mà không thêm quan hệ mới nào giữa hai nhóm. Ví dụ: $\mathbb{Z} * \mathbb{Z}$ là nhóm tự do trên hai phần tử sinh (nhóm không giao hoán).

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tích tự do có hợp nhất – Amalgamated Free Product):**  
Cho các nhóm $G, H, K$ cùng hai đồng cấu nhóm $\phi: K \to G$ và $\psi: K \to H$. **Tích tự do có hợp nhất** $G *_K H$ thu được từ tích tự do $G * H$ bằng cách lấy thương theo nhóm con chuẩn tắc sinh bởi các quan hệ $\phi(k) = \psi(k)$ với mọi $k \in K$.
</div>

Nói cách khác, $G *_K H$ kết hợp $G$ và $H$ đồng thời đồng nhất hai ảnh của nhóm trung gian $K$ trong $G$ và $H$.

---

### 2. Định lý Seifert–van Kampen

<div class="textbook-theorem" markdown="1">
**Định lý (Seifert–van Kampen):**  
Cho không gian tô-pô $X$ và hai tập con mở $A, B \subseteq X$ thỏa mãn:
- $X = A \cup B$,
- $A$, $B$ và $A \cap B$ đều liên thông đường,
- Chọn điểm cơ sở $x_0 \in A \cap B$.
</div>

Khi đó:

$$
\pi_1(X, x_0) \cong \pi_1(A, x_0) *_{\pi_1(A \cap B, x_0)} \pi_1(B, x_0)
$$

trong đó phép hợp nhất thực hiện theo hai đồng cấu cảm sinh bởi các phép nhúng $i_A: A \cap B \hookrightarrow A$ và $i_B: A \cap B \hookrightarrow B$.

**Góc nhìn lý thuyết phạm trù:**  
Định lý Seifert–van Kampen khẳng định biểu đồ sau là một **pushout** trong phạm trù các nhóm:

```
π₁(A ∩ B) -----> π₁(A)
    |              |
    |              |
    ↓              ↓
  π₁(B)  -----> π₁(X)
```

---

### 3. Các trường hợp đặc biệt

**Trường hợp 1: $A \cap B$ đơn liên ($\pi_1(A \cap B) = \{e\}$)**

$$
\pi_1(X) \cong \pi_1(A) * \pi_1(B)
$$

Không phát sinh thêm quan hệ hợp nhất nào; kết quả là tích tự do thuần túy.

**Trường hợp 2: $A$ đơn liên ($\pi_1(A) = \{e\}$)**

$$
\pi_1(X) \cong \pi_1(B) / N
$$

trong đó $N$ là nhóm con chuẩn tắc nhỏ nhất của $\pi_1(B)$ chứa ảnh $(i_B)_*(\pi_1(A \cap B))$.

**Trường hợp 3: Tổng chụm (Wedge Sum)**  
Với $X = A \vee B$ (dán tại điểm cơ sở $x_0$, giả sử $x_0$ có lân cận co rút được trong cả $A$ và $B$):

$$
\pi_1(A \vee B) \cong \pi_1(A) * \pi_1(B)
$$

---

## 📊 Các ứng dụng tiêu chuẩn

### Ứng dụng 1: Lưu ý khi áp dụng cho $S^1$

Nếu phân tách $S^1 = A \cup B$ với $A = S^1 \setminus \{N\}$ và $B = S^1 \setminus \{S\}$, thì $A \cap B$ gồm hai cung rời nhau — **không liên thông đường**, nên dạng cổ điển của định lý Van Kampen không áp dụng trực tiếp được (cần dùng phiên bản nhóm-phỏng/groupoid của Brown, hoặc dùng phương pháp không gian phủ $\mathbb{R} \to S^1$ vốn đơn giản hơn nhiều).

---

### Ứng dụng 2: Hình số $8$ ($S^1 \vee S^1$)

Chọn $A$ là đường tròn thứ nhất mở rộng thêm một lân cận nhỏ quanh điểm chung $x_0$ trên đường tròn thứ hai, và $B$ tương tự cho đường tròn thứ hai. Khi đó $A \simeq S^1$, $B \simeq S^1$, và $A \cap B$ co rút được về $x_0$. Áp dụng Van Kampen:

$$
\pi_1(X) \cong \mathbb{Z} * \mathbb{Z}
$$

(nhóm tự do trên hai phần tử sinh).

![Figure-eight fundamental group](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Wedge_of_circles.svg/400px-Wedge_of_circles.svg.png)  
*Minh họa hình số 8 và các vòng sinh*

---

### Ứng dụng 3: Hình xuyến $T^2$

Xem $T^2$ như phức CW gồm $1$-khung $S^1 \vee S^1$ dán thêm một $2$-tế bào dọc theo từ biên $aba^{-1}b^{-1}$. Chọn $A$ là phần trong của $2$-tế bào (co rút được) và $B = T^2 \setminus \{p\}$ (với $p$ là tâm của $2$-tế bào, nên $B$ co rút biến dạng về $1$-khung $S^1 \vee S^1$). Giao $A \cap B$ đồng luân với $S^1$, và ảnh của phần tử sinh $\pi_1(A \cap B)$ trong $\pi_1(B) \cong \langle a, b \rangle$ chính là hoán tử $aba^{-1}b^{-1}$. Theo trường hợp 2 của Van Kampen:
$\pi_1(T^2) \cong \langle a, b \mid aba^{-1}b^{-1} = 1 \rangle \cong \mathbb{Z} \times \mathbb{Z}$.

---

### Ứng dụng 4: Mặt định hướng được giống $g$ ($\Sigma_g$)

Tương tự như hình xuyến, biểu diễn $\Sigma_g$ bằng đa giác $4g$ cạnh có từ biên $[a_1,b_1]\cdots[a_g,b_g]$, khoét một điểm tâm để lấy $B \simeq \bigvee_{i=1}^{2g} S^1$ và $A$ là đĩa mở quanh điểm tâm. Áp dụng Van Kampen cho:

$$
\pi_1(\Sigma_g) = \langle a_1, b_1, \ldots, a_g, b_g \mid [a_1,b_1] \cdots [a_g,b_g] = 1 \rangle
$$

Với $g \geq 2$, nhóm này không giao hoán.

---

### Ứng dụng 5: Mặt phẳng xạ ảnh $\mathbb{R}P^2$

Xem $\mathbb{R}P^2$ là đĩa $D^2$ đồng nhất biên đối cực. Chọn $A$ là đĩa mở nhỏ hơn nằm gọn bên trong $D^2$ ($\pi_1(A) = \{e\}$) và $B = \mathbb{R}P^2 \setminus \{0\}$ (là một dải Möbius mở, co rút biến dạng về đường tròn biên $\mathbb{R}P^1 \cong S^1$, nên $\pi_1(B) \cong \mathbb{Z}$). Giao $A \cap B$ là hình vành khăn ($\pi_1(A \cap B) \cong \mathbb{Z}$).

Khi đi một vòng quanh hình vành khăn $A \cap B$, ảnh của nó đi **hai vòng** quanh lõi của dải Möbius $B$, nên phép nhúng $A \cap B \hookrightarrow B$ cảm sinh phép nhân với $2$ trên $\pi_1$ ($\gamma \mapsto \gamma^2$), trong khi $A \cap B \hookrightarrow A$ cảm sinh đồng cấu tầm thường. Theo Van Kampen (trường hợp 2), quan hệ hợp nhất áp đặt $\gamma^2 = e$, suy ra $\pi_1(\mathbb{R}P^2) \cong \langle \gamma \mid \gamma^2 = 1 \rangle \cong \mathbb{Z}/2\mathbb{Z}$.

---

### Ứng dụng 6: Tổng chụm $n$ đường tròn

Áp dụng quy nạp định lý Van Kampen cho $X = \bigvee_{i=1}^n S^1$:

$$
\pi_1\left(\bigvee_{i=1}^n S^1\right) \cong \mathbb{Z} * \mathbb{Z} * \cdots * \mathbb{Z} \quad (n \text{ times})
$$

Đây là nhóm tự do $F_n$ trên $n$ phần tử sinh (không giao hoán khi $n \geq 2$).

---

## 🧮 Phác thảo chứng minh

### 1. Ý tưởng chính

Mọi vòng trong $X = A \cup B$ đều có thể chia thành hữu hạn đoạn nhỏ nằm hoàn toàn trong $A$ hoặc trong $B$, với các điểm chuyển tiếp nằm trong $A \cap B$; nối các điểm chuyển tiếp với $x_0$ bên trong tập liên thông đường $A \cap B$ sẽ phân tích vòng thành tích các vòng thuộc $\pi_1(A, x_0)$ và $\pi_1(B, x_0)$.

### 2. Các bước xây dựng

1. **Định nghĩa đồng cấu $\Phi$:** Từ các phép nhúng $j_A: A \hookrightarrow X$ và $j_B: B \hookrightarrow X$, tính chất phổ dụng của tích tự do có hợp nhất cảm sinh đồng cấu $\Phi: \pi_1(A) *_{\pi_1(A \cap B)} \pi_1(B) \to \pi_1(X)$.
2. **Tính toàn ánh của $\Phi$:** Dùng bổ đề số Lebesgue để chia mọi vòng $\gamma: [0,1] \to X$ thành hữu hạn đoạn thuộc $A$ hoặc $B$, rồi chèn các đường nối về $x_0$ trong $A \cap B$.
3. **Tính đơn ánh của $\Phi$:** Nếu hai tích vòng cho cùng một lớp trong $\pi_1(X)$, tồn tại phép đồng luân đường $F: [0,1]^2 \to X$. Chia $[0,1]^2$ thành lưới ô nhỏ sao cho mỗi ô rơi vào $A$ hoặc $B$, rồi kiểm tra rằng bước đi qua từng ô chỉ thay đổi từ biểu diễn bởi các quan hệ hợp nhất trong $\pi_1(A) *_{\pi_1(A \cap B)} \pi_1(B)$.

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Herbert Seifert** – *"Konstruktion dreidimensionaler geschlossener Räume"* (1931)

2. **Egbert van Kampen** – *"On the connection between the fundamental groups"* (1933)

3. **Ronald Brown** – *"Groupoids and Van Kampen's theorem"* (1967)  
   *Phát biểu hiện đại bằng ngôn ngữ nhóm-phỏng (groupoids).*

### Giáo trình

4. **Allen Hatcher** – *Algebraic Topology*, **§1.2: Van Kampen's Theorem**

5. **James R. Munkres** – *Topology*, **§70: Seifert–van Kampen Theorem**

6. **William S. Massey** – *Algebraic Topology*, **Chapter 6**

7. **Glen E. Bredon** – *Topology and Geometry*, **Chapter II**

8. **Joseph J. Rotman** – *An Introduction to Algebraic Topology*, **Chapter 7**

---

## 🔗 Ứng dụng và liên kết

### Phức CW – Tính toán quy nạp
Khi xây dựng phức CW: dán $1$-tế bào thêm phần tử sinh, dán $2$-tế bào thêm quan hệ vào $\pi_1$ (theo Van Kampen), còn dán $n$-tế bào với $n \ge 3$ không làm thay đổi $\pi_1$.

### Lý thuyết nút – Nhóm nút
Phân tách phần bù $S^3 \setminus K$ bằng định lý Van Kampen dẫn đến biểu diễn Wirtinger của nhóm nút $\pi_1(S^3 \setminus K)$.

### 3-đa tạp – Phân tách Heegaard
Biểu diễn 3-đa tạp thành hai thể tay cầm (handlebodies) dán dọc theo biên cho phép tính $\pi_1$ từ ánh xạ dán.

### Lý thuyết nhóm – Lý thuyết Bass–Serre
Tích tự do có hợp nhất và mở rộng HNN là đối tác đại số trực tiếp của định lý Van Kampen.

---

## Video tham khảo

- **xem trước** [Algebraic Topology 6: Seifert-Van Kampen Theorem](https://www.youtube.com/watch?v=pmNcHER9K9I) — Math at Andrews University, tiếng Anh. Phát biểu định lý Seifert–van Kampen và cách ghép nhóm cơ bản từ hai mảnh.
- [6. Applications and Proof of the van Kampen Theorem - Pierre Albin](https://www.youtube.com/watch?v=0msWLft-lT0) — Mat Neth, tiếng Anh. Chứng minh và ứng dụng định lý Van Kampen.

## 🧩 Bài tập

### Hiểu phát biểu

1. **Tích tự do:**  
   Mô tả cấu trúc các phần tử của $\mathbb{Z} * (\mathbb{Z}/2\mathbb{Z})$. Nhóm này có giao hoán không?

2. **Tích tự do có hợp nhất:**  
   Xác định nhóm $\mathbb{Z} *_{\mathbb{Z}} \mathbb{Z}$ khi cả hai đồng cấu $\mathbb{Z} \to \mathbb{Z}$ đều là ánh xạ đồng nhất (gợi ý: $\mathbb{Z}$).

3. **Giả thiết liên thông đường:**  
   Giải thích vì sao định lý yêu cầu $A, B$ và $A \cap B$ đều liên thông đường; lấy $S^1$ làm phản ví dụ khi $A \cap B$ không liên thông đường.

### Ứng dụng trực tiếp

4. **Hình số $8$:**  
   Trình bày chi tiết các bước áp dụng Van Kampen để chứng minh $\pi_1(S^1 \vee S^1) \cong \mathbb{Z} * \mathbb{Z}$.

5. **Ba đường tròn chụm tại một điểm:**  
   Áp dụng Van Kampen tính $\pi_1(S^1 \vee S^1 \vee S^1) \cong F_3$.

6. **Hình xuyến:**  
   Trình bày chi tiết phép phân tách $T^2 = A \cup B$ để suy ra $\pi_1(T^2) \cong \mathbb{Z}^2$.

### Các mặt

7. **Mặt giống $2$:**  
   Áp dụng Van Kampen cho $\Sigma_2$ để thu được $\langle a_1, b_1, a_2, b_2 \mid [a_1,b_1][a_2,b_2] = 1 \rangle$.

8. **Chai Klein:**  
   Áp dụng Van Kampen để chứng minh $\pi_1(K) \cong \langle a, b \mid aba^{-1}b = 1 \rangle$.

9. **$\mathbb{R}P^2$:**  
   Trình bày chi tiết phép tính $\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$ bằng Van Kampen.

### Phức CW

10. **Dán một $2$-tế bào:**  
    Xuất phát từ $S^1$ ($\pi_1 = \langle a \rangle \cong \mathbb{Z}$), dán một $2$-tế bào theo ánh xạ quấn $2$ vòng ($a^2$). Dùng Van Kampen chứng minh $\pi_1 \cong \langle a \mid a^2 = 1 \rangle \cong \mathbb{Z}/2\mathbb{Z}$.

11. **Mũ Dunce (Dunce Hat):**  
    Xét tam giác có ba cạnh được dán với nhau theo nhãn $a, a, a^{-1}$. Dùng Van Kampen chứng minh $\pi_1 = \{e\}$ (từ đó cùng với đồng điều bằng $0$ suy ra không gian co rút được).

12. **Phức CW tổng quát:**  
    Giải thích cách dùng định lý Van Kampen để tính $\pi_1$ của một phức CW bất kỳ từ $2$-khung của nó.

### Nâng cao

13. **Biểu đồ pushout:**  
    Giải thích phát biểu phạm trù: định lý Van Kampen nói rằng $\pi_1$ bảo toàn pushout.

14. **Nhóm-phỏng (Groupoids):**  
    Tìm hiểu phiên bản Van Kampen của Ronald Brown sử dụng nhóm-phỏng cơ bản (xử lý được cả trường hợp $A \cap B$ không liên thông đường).

15. **Phiên bản chiều cao:**  
    Tìm hiểu vì sao định lý kiểu Van Kampen cho các nhóm đồng luân bậc cao $\pi_n$ ($n \ge 2$) phức tạp hơn nhiều.

### So sánh các phương pháp

16. **So sánh tính $\pi_1(S^1)$:**  
    So sánh độ thuận tiện giữa phương pháp không gian phủ và định lý Van Kampen khi tính $\pi_1(S^1)$.

17. **Chọn công cụ phù hợp:**  
    Nêu một ví dụ không gian phù hợp nhất cho từng phương pháp: không gian phủ, Van Kampen và tương đương đồng luân.

### Câu hỏi suy ngẫm

18. **Phạm vi áp dụng:**  
    Định lý Van Kampen xử lý tốt nhất những loại không gian nào?

19. **Hạn chế:**  
    Nêu các hạn chế của định lý Van Kampen (chẳng hạn điều kiện giao liên thông đường hoặc bài toán nhận diện nhóm từ biểu diễn sinh–quan hệ).

20. **Kết nối tô-pô và đại số:**  
    Phân tích cách định lý Van Kampen chuyển thao tác dán không gian tô-pô thành phép hợp nhất trong lý thuyết nhóm.

---

## 📚 Đọc thêm

- **Hatcher, §1.2**
- **Munkres, §70**
- **Massey, Chapter 6**
- **Rotman, Chapter 7**
- **Brown, *Topology and Groupoids***

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu **Định lý Seifert–van Kampen**: nếu $X = A \cup B$ với $A, B$ mở và $A, B, A \cap B$ liên thông đường, thì $\pi_1(X) \cong \pi_1(A) *_{\pi_1(A \cap B)} \pi_1(B)$. Khi $A \cap B$ đơn liên, kết quả rút gọn thành tích tự do $\pi_1(A) * \pi_1(B)$ (đặc biệt cho tổng chụm $A \vee B$). Định lý này cho phép tính hệ thống nhóm cơ bản của hình số $8$, các mặt đóng $\Sigma_g$, $\mathbb{R}P^2$, chai Klein và các phức CW.

**Hoàn thành Chapter 06.** Chúng ta đã đi qua bốn trụ cột mở đầu của tô-pô đại số: đồng luân, nhóm cơ bản $\pi_1$, không gian phủ và định lý Seifert–van Kampen.

**Tiếp theo:** Chapter 07 về **Lý thuyết đồng điều (Homology Theory)** — bất biến đại số có khả năng tính toán hệ thống hơn và phát hiện cấu trúc ở mọi chiều.

---

*"Van Kampen: divide and conquer, from topology to algebra."*

---

**Previous:** [Lecture 06.03: Covering Spaces](/contents/vi/topology-chapter06/06_03_Covering_Spaces/)  
**Next Chapter:** [Chapter 07: Homology Theory](/contents/vi/topology-chapter07/)
