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

**Đồng luân và Đồng luân đường**

---

## 📖 Tổng quan

Lý thuyết đồng luân (homotopy theory) là nền tảng của tô-pô đại số. Ý tưởng trung tâm của nó là:

> **Hai đối tượng được coi là tương đương nếu một đối tượng có thể biến dạng liên tục thành đối tượng kia.**

Phép biến dạng liên tục đó được gọi là **đồng luân** (homotopy). Khái niệm này cho phép phân loại không gian theo *kiểu đồng luân* (yếu hơn đồng phôi nhưng dễ nghiên cứu hơn bằng đại số), xây dựng nhóm cơ bản $\pi_1$ từ các lớp đồng luân của vòng khép kín, và chứng minh nhiều kết quả kinh điển như định lý điểm bất động Brouwer hay định lý quả bóng có lông.

![Homotopy visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4a/Homotopy_Illustration.svg/500px-Homotopy_Illustration.svg.png)  
*Minh họa phép biến dạng liên tục (đồng luân) – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Homotopy_Illustration.svg)*

Trong bài học này, chúng ta sẽ tìm hiểu định nghĩa đồng luân giữa hai ánh xạ, tương đương đồng luân, không gian co rút được (contractible), đường đi và vòng khép kín, đồng luân đường (path homotopy), cũng như các khái niệm bổ trợ như tính chất mở rộng đồng luân (HEP) và co rút biến dạng (deformation retract).

Các bài học tiếp theo trong chương sẽ xây dựng nhóm cơ bản $\pi_1$, lý thuyết không gian phủ và định lý Seifert–van Kampen.

---

## 🔄 Đồng luân giữa các ánh xạ (Homotopy of Maps)

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đồng luân – Homotopy):**  
Cho $f, g: X \to Y$ là hai ánh xạ liên tục. Một **phép đồng luân** từ $f$ đến $g$ là một ánh xạ liên tục:

$$
F: X \times [0,1] \to Y
$$
</div>

thỏa mãn $F(x, 0) = f(x)$ và $F(x, 1) = g(x)$ với mọi $x \in X$.

**Ký hiệu:** $F: f \simeq g$ (hoặc $f \sim g$). Hai ánh xạ $f, g$ được gọi là **đồng luân** (homotopic) nếu tồn tại một phép đồng luân giữa chúng.

Về trực quan, có thể xem tham số $t \in [0,1]$ là "thời gian": tại $t = 0$ ta có ánh xạ $f$, tại $t = 1$ ta có ánh xạ $g$, và tại mỗi thời điểm trung gian $t \in (0,1)$, ánh xạ $f_t(x) = F(x,t)$ là một "khung hình" biến đổi liên tục từ $f$ sang $g$.

---

<div class="textbook-theorem" markdown="1">
**Định lý:** Quan hệ đồng luân $\simeq$ là một quan hệ tương đương trên tập các ánh xạ liên tục từ $X$ vào $Y$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**
- **Phản xạ:** $F(x,t) = f(x)$ là đồng luân từ $f$ đến chính nó.
- **Đối xứng:** Nếu $F: f \simeq g$ thì $G(x,t) = F(x, 1-t)$ là đồng luân từ $g$ đến $f$.
- **Bắc cầu:** Nếu $F: f \simeq g$ và $G: g \simeq h$, thì ánh xạ $H(x,t) = F(x, 2t)$ khi $0 \le t \le 1/2$ và $H(x,t) = G(x, 2t-1)$ khi $1/2 \le t \le 1$ liên tục (theo bổ đề dán) và là đồng luân từ $f$ đến $h$.
</div>

---

### 2. Các ví dụ

**Ví dụ 1: Đồng luân tầm thường**  
Mọi ánh xạ liên tục $f: X \to Y$ (chẳng hạn $f = \operatorname{id}_X$) đều đồng luân với chính nó qua $F(x,t) = f(x)$.

**Ví dụ 2: Các ánh xạ hằng vào không gian liên thông đường**  
Giả sử $f(x) = y_0$ và $g(x) = y_1$ là hai ánh xạ hằng từ $X$ vào không gian liên thông đường $Y$. Chọn đường đi liên tục $\alpha: [0,1] \to Y$ nối $y_0$ đến $y_1$; khi đó $F(x,t) = \alpha(t)$ là một đồng luân từ $f$ đến $g$.

**Ví dụ 3: Phép đối xứng gương và ánh xạ đồng nhất trên $S^1$**  
Xét đường tròn đơn vị $S^1 \subset \mathbb{C}$. Phép đối xứng gương (liên hợp phức) $f(z) = \bar{z}$ và ánh xạ đồng nhất $\operatorname{id}(z) = z$ **không** đồng luân với nhau: trên nhóm cơ bản $\pi_1(S^1) \cong \mathbb{Z}$, $\operatorname{id}$ cảm sinh phép nhân với $+1$ còn $f$ cảm sinh phép nhân với $-1$ (đảo ngược chiều quấn). (Lưu ý rằng phép đối cực $z \mapsto -z = e^{i\pi}z$ trên $S^1$ lại *đồng luân* với ánh xạ đồng nhất qua phép quay liên tục $F(z,t) = e^{i\pi t}z$.)

---

## 🏠 Tương đương đồng luân (Homotopy Equivalence)

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tương đương đồng luân):**  
Ánh xạ liên tục $f: X \to Y$ được gọi là một **tương đương đồng luân** nếu tồn tại ánh xạ liên tục $g: Y \to X$ sao cho:
- $g \circ f \simeq \text{id}_X$,
- $f \circ g \simeq \text{id}_Y$.
</div>

Khi đó $g$ được gọi là **nghịch đảo đồng luân** (homotopy inverse) của $f$, và hai không gian $X, Y$ được gọi là **tương đương đồng luân** (homotopy equivalent), ký hiệu $X \simeq Y$.

---

<div class="textbook-theorem" markdown="1">
**Định lý:** Quan hệ $\simeq$ là một quan hệ tương đương trên lớp các không gian tô-pô.
</div>

---

### 2. Các ví dụ

**Ví dụ 1: Không gian co rút được (Contractible Spaces)**

<div class="textbook-definition" markdown="1">
**Định nghĩa:** Không gian $X$ được gọi là **co rút được** (contractible) nếu $X \simeq \{pt\}$ (tương đương đồng luân với một không gian một điểm).
</div>

Điều này tương đương với việc ánh xạ đồng nhất $\operatorname{id}_X$ đồng luân với một ánh xạ hằng.

Các không gian co rút được quen thuộc gồm $\mathbb{R}^n$, đĩa đóng $D^n$, hình nón $CX$ trên bất kỳ không gian $X$ nào, và mọi tập hình sao (star-shaped) trong $\mathbb{R}^n$. Ngược lại, $S^1$, $S^n$ ($n \ge 1$) và hình xuyến $T^2$ không co rút được.

---

**Ví dụ 2: $D^2 \simeq \{pt\}$**  
Ánh xạ $F: D^2 \times [0,1] \to D^2$ cho bởi $F(x,t) = (1-t)x$ là đồng luân giữa $\operatorname{id}_{D^2}$ và ánh xạ hằng tại gốc tọa độ $0$, chứng tỏ $D^2$ co rút được.

**Ví dụ 3: $\mathbb{R}^n \setminus \{0\} \simeq S^{n-1}$**  
Xét phép co rút $r: \mathbb{R}^n \setminus \{0\} \to S^{n-1}$ cho bởi $r(x) = x/\|x\|$ và phép nhúng $i: S^{n-1} \hookrightarrow \mathbb{R}^n \setminus \{0\}$. Ta có $r \circ i = \operatorname{id}_{S^{n-1}}$, còn $i \circ r \simeq \operatorname{id}_{\mathbb{R}^n \setminus \{0\}}$ qua đồng luân $F(x,t) = (1-t)x + t(x/\|x\|)$ (luôn khác $0$ với mọi $t \in [0,1]$). Do đó $\mathbb{R}^n \setminus \{0\} \simeq S^{n-1}$ dù hai không gian không đồng phôi (một bên không compact, một bên compact).

---

### 3. Bất biến đồng luân (Homotopy Invariants)

Một tính chất hoặc đối tượng gán cho không gian tô-pô gọi là **bất biến đồng luân** nếu nó được bảo toàn qua tương đương đồng luân. Các bất biến đại số quan trọng như nhóm cơ bản $\pi_1(X)$, các nhóm đồng luân bậc cao $\pi_n(X)$, các nhóm đồng điều $H_n(X)$ và đối đồng điều $H^n(X)$ đều là bất biến đồng luân.

Ngược lại, các tính chất tô-pô thuần túy như tính compact hay tính Hausdorff không phải là bất biến đồng luân (chẳng hạn $\mathbb{R}^n \simeq \{pt\}$ nhưng $\mathbb{R}^n$ không compact). Tính liên thông và tính liên thông đường được bảo toàn qua tương đương đồng luân.

---

## 🛤️ Đường đi và Vòng khép kín (Paths và Loops)

### 1. Đường đi (Paths)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đường đi – Path):**  
Một **đường đi** trong $X$ từ $x_0$ đến $x_1$ là một ánh xạ liên tục:

$$
\gamma: [0,1] \to X
$$
</div>

thỏa mãn $\gamma(0) = x_0$ và $\gamma(1) = x_1$.

Một **vòng khép kín** (loop) có điểm cơ sở (basepoint) $x_0$ là một đường đi có điểm đầu và điểm cuối trùng nhau: $\gamma(0) = \gamma(1) = x_0$.

---

**Phép nối đường đi (Concatenation):**  
Nếu $\gamma$ và $\delta$ là hai đường đi thỏa $\gamma(1) = \delta(0)$, đường đi tích $\gamma \cdot \delta$ đi qua $\gamma$ trên $[0, 1/2]$ và $\delta$ trên $[1/2, 1]$:

$$
(\gamma \cdot \delta)(t) = \begin{cases}
\gamma(2t) & 0 \leq t \leq 1/2 \\
\delta(2t-1) & 1/2 \leq t \leq 1
\end{cases}
$$

**Đường đi ngược (Inverse path):** Với đường đi $\gamma$ từ $x_0$ đến $x_1$, đường đi ngược $\gamma^{-1}$ từ $x_1$ về $x_0$ được định nghĩa bởi $\gamma^{-1}(t) = \gamma(1-t)$.

---

### 2. Đồng luân đường (Path Homotopy)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đồng luân đường):**  
Cho $\gamma, \delta: [0,1] \to X$ là hai đường đi có cùng điểm đầu $x_0$ và điểm cuối $x_1$. Một **đồng luân đường** từ $\gamma$ đến $\delta$ (cố định hai đầu mút) là một ánh xạ liên tục:

$$
F: [0,1] \times [0,1] \to X
$$
</div>

thỏa mãn $F(s,0) = \gamma(s)$, $F(s,1) = \delta(s)$ với mọi $s \in [0,1]$, và $F(0,t) = x_0$, $F(1,t) = x_1$ với mọi $t \in [0,1]$.

**Ký hiệu:** $\gamma \simeq_p \delta$.

Việc giữ cố định hai đầu mút trong suốt quá trình biến dạng là cần thiết để phép nối đường đi cảm sinh một phép toán nhóm xác định tốt trên các lớp đồng luân của vòng khép kín.

![Path homotopy](https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Path_homotopy.svg/400px-Path_homotopy.svg.png)  
*Minh họa đồng luân đường với hai đầu mút cố định*

---

<div class="textbook-theorem" markdown="1">
**Định lý:** Quan hệ $\simeq_p$ là một quan hệ tương đương trên tập các đường đi có cùng điểm đầu và điểm cuối.
</div>

---

### 3. Lớp đồng luân

Ký hiệu $[\gamma]$ là lớp đồng luân đường của $\gamma$. Tập các vòng khép kín tại $x_0$ là:

$$
\Omega(X, x_0) = \{\text{loops } \gamma: [0,1] \to X, \gamma(0)=\gamma(1)=x_0\}
$$

Tập thương $\Omega(X,x_0) / {\simeq_p}$ gồm các lớp đồng luân của vòng khép kín tại $x_0$ sẽ trở thành **nhóm cơ bản** $\pi_1(X, x_0)$ ở bài học tiếp theo.

---

## 🎯 Một số khái niệm và định lý hỗ trợ

### 1. Tính chất mở rộng đồng luân (Homotopy Extension Property – HEP)

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Cho $(X, A)$ là một cặp không gian thỏa điều kiện chuẩn (chẳng hạn cặp phức CW). Cho trước ánh xạ liên tục $f: X \to Y$ và một phép đồng luân $F: A \times [0,1] \to Y$ thỏa $F(a, 0) = f(a)$ với mọi $a \in A$. Khi đó tồn tại phép đồng luân $\tilde{F}: X \times [0,1] \to Y$ mở rộng $F$ và thỏa $\tilde{F}(x, 0) = f(x)$.
</div>

---

### 2. Co rút biến dạng (Deformation Retract)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Co rút biến dạng):**  
Tập con $A \subseteq X$ được gọi là một **co rút biến dạng** (deformation retract) của $X$ nếu tồn tại phép co rút $r: X \to A$ ($r|_A = \operatorname{id}_A$) sao cho $i \circ r \simeq \operatorname{id}_X$ (với $i: A \hookrightarrow X$ là phép nhúng; nếu phép đồng luân cố định từng điểm trên $A$ thì gọi là *co rút biến dạng mạnh*).
</div>

**Ví dụ:** $S^{n-1}$ là co rút biến dạng mạnh của $\mathbb{R}^n \setminus \{0\}$.

<div class="textbook-theorem" markdown="1">
**Định lý:** Nếu $A$ là co rút biến dạng của $X$, thì $A \simeq X$.
</div>

---

### 3. Hệ quả của tính co rút được

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Nếu $X$ co rút được, thì $X$ liên thông đường, $\pi_1(X) = \{e\}$ và $H_n(X) = 0$ với mọi $n \geq 1$.
</div>

Chiều ngược lại không đúng trong trường hợp tổng quát (ví dụ nâng cao: đa tạp Whitehead).

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Henri Poincaré** – *"Analysis Situs"* (1895)  
   *Đặt nền móng cho tô-pô đại số và khái niệm biến dạng liên tục.*

2. **L.E.J. Brouwer** – *"Über Abbildung von Mannigfaltigkeiten"* (1911)  
   *Chứng minh định lý điểm bất động Brouwer bằng phương pháp tô-pô.*

3. **Heinz Hopf** – *"Über die Abbildungen der dreidimensionalen Sphäre"* (1931)  
   *Phân thớ Hopf và lý thuyết đồng luân bậc cao.*

4. **Witold Hurewicz** – *"Beiträge zur Topologie der Deformationen"* (1935–36)  
   *Hệ thống hóa lý thuyết đồng luân.*

### Giáo trình

5. **James R. Munkres** – *Topology*, 2nd Ed., **§51–52: Homotopy**

6. **Allen Hatcher** – *Algebraic Topology*, **§0–1: Homotopy and Fundamental Group**

7. **Edwin Spanier** – *Algebraic Topology*, **Chapter 1: Homotopy Theory**

8. **Glen E. Bredon** – *Topology and Geometry*, **Chapter I**

9. **Tammo tom Dieck** – *Algebraic Topology*, **Chapter 2**

---

## 🔗 Ứng dụng và liên kết

### Tô-pô – Phân loại theo kiểu đồng luân
Tương đương đồng luân phân loại không gian thô hơn đồng phôi nhưng vẫn bảo toàn các bất biến đại số ($\pi_n$, $H_n$).

### Giải tích – Định lý điểm bất động Brouwer
Mọi ánh xạ liên tục $f: D^n \to D^n$ đều có ít nhất một điểm bất động. Chứng minh phản chứng chỉ ra rằng nếu $f$ không có điểm bất động thì sẽ tồn tại một phép co rút $r: D^n \to S^{n-1}$, mâu thuẫn với tính chất đồng luân/đồng điều của đĩa và mặt cầu.

### Giải tích phức – Chỉ số vòng (Winding Numbers)
Tích phân đường $\int_\gamma f(z)\,dz$ của hàm chỉnh hình $f$ không thay đổi khi biến dạng đồng luân đường đi $\gamma$ (cố định hai đầu mút) bên trong miền chỉnh hình.

### Robotics – Không gian cấu hình
Các lớp đồng luân đường trong không gian cấu hình mô tả các chiến lược di chuyển khác nhau về mặt tô-pô (ví dụ vòng bên trái hay bên phải một chướng ngại vật).

### Vật lý – Lý thuyết chuẩn
Các lớp đồng luân của trường chuẩn giúp phân loại các cấu hình tô-pô như instanton trong lý thuyết Yang–Mills.

### Khoa học dữ liệu – Phân tích dữ liệu tô-pô (TDA)
Các nhóm đồng điều (bất biến đồng luân) được dùng trong đồng điều bền vững để phát hiện cấu trúc vòng và hốc của dữ liệu.

---

## Video tham khảo

- **xem trước** [Algebraic Topology 1: Homotopy Equivalence](https://www.youtube.com/watch?v=crQdC-k6AZE) — Math at Andrews University, tiếng Anh. Trình bày đồng luân ánh xạ và tương đương đồng luân, bám sát phần mở đầu của bài.
- [Lec 3.  Deformation Retract](https://www.youtube.com/watch?v=KMiNqTV2TAA) — The Trefoil, tiếng Anh. Giải thích co rút biến dạng và cách nhận biết không gian co rút được.
- [1. History of Algebraic Topology; Homotopy Equivalence - Pierre Albin](https://www.youtube.com/watch?v=XxFGokyYo6g) — Mat Neth, tiếng Anh. Lược sử tô-pô đại số và giới thiệu tương đương đồng luân.

## 🧩 Bài tập

### Định nghĩa đồng luân

1. **Kiểm tra quan hệ tương đương:**  
   Chứng minh chi tiết đồng luân $\simeq$ là quan hệ tương đương (phản xạ, đối xứng, bắc cầu).

2. **Đồng luân hằng:**  
   Với $f: X \to Y$, chứng minh $F(x,t) = f(x)$ là đồng luân từ $f$ đến chính nó.

3. **Đồng luân tường minh:**  
   Viết công thức tường minh $F: [0,1] \times \mathbb{R}^2 \to \mathbb{R}^2$ cho thấy $\mathbb{R}^2$ co rút được.

### Tương đương đồng luân

4. **Kiểm tra tương đương đồng luân:**  
   Viết tường minh các ánh xạ $f, g$ và các phép đồng luân chứng tỏ $D^2 \simeq \{pt\}$.

5. **$\mathbb{R}^n \setminus \{0\} \simeq S^{n-1}$:**  
   Kiểm tra tường minh $r \circ i = \operatorname{id}$ và $i \circ r \simeq \operatorname{id}$.

6. **Hình trụ:**  
   Tìm một tương đương đồng luân tường minh giữa $S^1 \times [0,1]$ và $S^1$.

### Không gian co rút được

7. **Tập hình sao:**  
   Chứng minh mọi tập hình sao $X \subseteq \mathbb{R}^n$ đều co rút được.

8. **Hình nón:**  
   Chứng minh hình nón $CX = (X \times [0,1])/(X \times \{0\})$ luôn co rút được.

9. **Không co rút được:**  
   Nêu lập luận trực quan vì sao $S^1$ không co rút được (chứng minh chặt chẽ dựa trên $\pi_1(S^1) \cong \mathbb{Z}$).

### Đồng luân đường

10. **Nối đường đi:**  
    Kiểm tra $(\gamma \cdot \delta)(t)$ xác định tốt và liên tục.

11. **Đường đi ngược:**  
    Chứng minh $\gamma \cdot \gamma^{-1} \simeq_p e_{x_0}$ (đường hằng tại $x_0$).

12. **Tính kết hợp sai khác đồng luân:**  
    Chứng minh $(\gamma \cdot \delta) \cdot \varepsilon \simeq_p \gamma \cdot (\delta \cdot \varepsilon)$.

### Co rút biến dạng

13. **$S^{n-1} \subseteq \mathbb{R}^n \setminus \{0\}$:**  
    Chứng minh $S^{n-1}$ là co rút biến dạng của $\mathbb{R}^n \setminus \{0\}$ với $r(x) = x/\|x\|$.

14. **Tính chất:**  
    Cho $A$ là co rút biến dạng của $X$. Chứng minh $A \simeq X$ (và nhận xét rằng $i_*: \pi_1(A) \to \pi_1(X)$ là đẳng cấu).

15. **Co rút biến dạng mạnh:**  
    Kiểm tra $S^1 \subseteq \mathbb{R}^2 \setminus \{0\}$ là co rút biến dạng mạnh.

### Tính chất mở rộng đồng luân (HEP)

16. **Ví dụ HEP:**  
    Cặp $(D^2, S^1)$ thỏa mãn HEP. Cho $f: D^2 \to Y$ và $F: S^1 \times I \to Y$, phác thảo cách dựng mở rộng $\tilde{F}: D^2 \times I \to Y$.

17. **Vai trò của HEP:**  
    Giải thích vì sao HEP hữu ích khi chứng minh các định lý về đồng luân.

### Nâng cao

18. **Tương đương đồng luân nhưng không đồng phôi:**  
    Chỉ ra hai không gian $X \simeq Y$ nhưng $X \not\cong Y$ (gợi ý: $\mathbb{R}$ và một điểm).

19. **Định lý Whitehead:**  
    Tìm hiểu phát biểu của định lý Whitehead cho ánh xạ giữa hai phức CW.

20. **Ứng dụng:**  
    Nêu $3$ ứng dụng của lý thuyết đồng luân trong vật lý, khoa học máy tính hoặc khoa học dữ liệu.

### Câu hỏi suy ngẫm

21. **Đồng luân và đồng phôi:**  
    So sánh các tính chất được bảo toàn bởi đồng phôi và bởi tương đương đồng luân; quan hệ nào thô hơn?

22. **Trực giác:**  
    Giải thích khái niệm đồng luân bằng hình ảnh biến dạng liên tục mà không dùng công thức.

23. **Vai trò của việc cố định đầu mút:**  
    Tại sao định nghĩa đồng luân đường yêu cầu giữ cố định điểm đầu và điểm cuối?

---

## 📚 Đọc thêm

- **Hatcher, Algebraic Topology:** §0–1
- **Munkres, Topology:** §51–52
- **Spanier, Algebraic Topology:** Chapter 1
- **Bredon, Topology and Geometry:** Chapter I
- **May, Concise Course:** Nền tảng lý thuyết đồng luân

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã giới thiệu các khái niệm mở đầu của lý thuyết đồng luân: phép đồng luân giữa hai ánh xạ liên tục, tương đương đồng luân giữa các không gian, không gian co rút được, co rút biến dạng và đồng luân đường cố định đầu mút. Tương đương đồng luân yếu hơn đồng phôi nhưng bảo toàn các bất biến đại số như $\pi_1$ và $H_n$; các lớp đồng luân đường của vòng khép kín tạo nền tảng trực tiếp để xây dựng nhóm cơ bản ở bài học kế tiếp.

**Tiếp theo:** Lecture 06.01 về **Nhóm cơ bản $\pi_1(X, x_0)$** — bất biến đại số đầu tiên từ lý thuyết đồng luân.

---

*"Homotopy is the art of continuous deformation."*

---

**Previous Chapter:** [Chapter 05: Quotient Spaces](/contents/vi/topology-chapter05/)  
**Next:** [Lecture 06.01: Fundamental Group](/contents/vi/topology-chapter06/06_01_Fundamental_Group/)
