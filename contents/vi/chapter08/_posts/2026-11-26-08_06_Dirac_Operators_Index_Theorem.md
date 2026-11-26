---
layout: post
title: "Lecture 08.06: Đại Số Clifford, Toán Tử Dirac và Định Lý Chỉ Số Atiyah–Singer"
lang: vi
lang-ref: lecture-08-06
chapter: 8
lecture: 6
order: 6
categories: [chapter08]
tags: [clifford-algebra, spin-geometry, dirac-operator, atiyah-singer, index-theorem]
description: "Cầu nối Tôpô – Hình học Vi phân – Giải tích: Đại số Clifford, nhóm Spin(n), Toán tử Dirac trên đa tạp và Định lý Chỉ số Atiyah–Singer"
---

**Nơi số nghiệm của một phương trình vi phân bằng đúng một bất biến tôpô toàn cục**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu bạn có một phương trình vi phân elliptic trên một mặt cong kín, số nghiệm độc lập tuyến tính của nó có thay đổi khi bạn bóp méo mêtric của mặt cong đó không? Từng chiều $\dim\ker D^+$ có thể nhảy, nhưng **hiệu số** $\operatorname{ind}(D^+) = \dim\ker D^+ - \dim\ker D^-$ lại hoàn toàn bất biến — và kỳ diệu hơn nữa, nó bằng đúng một tích phân đặc trưng tôpô trên đa tạp! Đó là **Định lý Chỉ số Atiyah–Singer (1963)**, được trình bày mạch lạc từ nền tảng hình học đến hạt nhân nhiệt trong giáo trình [*Geometry of Dirac Operators*](https://people.math.harvard.edu/~dafr/DiracNotes.pdf) của Daniel S. Freed.

![Cầu nối từ Cấu trúc Spin và Toán tử Dirac đến Định lý Chỉ số Atiyah-Singer]({{ site.imgurl }}/chapter_img/chapter08/08_06_dirac_atiyah_singer.png)

## 🗺️ Kiến thức cần nhớ: Ba trụ cột của Hình học Spin và Chỉ số

1. **Đại số Clifford $\operatorname{Cliff}(V)$ và Phủ kép $\operatorname{Spin}(n) \to SO(n)$:**
   Trong đại số Clifford sinh bởi không gian Euclid $(V, \langle\cdot,\cdot\rangle)$ với quan hệ $v \cdot w + w \cdot v = -2\langle v, w\rangle$, nhóm $\operatorname{Spin}(n)$ nằm tự nhiên như một **phủ kép liên thông đơn** ($n \ge 3$) của nhóm quay $SO(n)$:
   $$1 \longrightarrow \mathbb{Z}/2\mathbb{Z} \longrightarrow \operatorname{Spin}(n) \longrightarrow SO(n) \longrightarrow 1.$$
2. **Cấu trúc Spin trên Đa tạp & Toán tử Dirac $D$:**
   Một đa tạp định hướng Riemann $X$ có **cấu trúc Spin** khi lớp Stiefel–Whitney thứ hai $w_2(TX) = 0 \in H^2(X; \mathbb{Z}/2\mathbb{Z})$. Khi đó, bó spinor $S = S^+ \oplus S^-$ sở hữu **toán tử Dirac** $D = \sum_{i=1}^n e_i \cdot \nabla_{e_i}$, một toán tử vi phân elliptic bậc $1$ tự liên hợp thoả mãn công thức Lichnerowicz $D^2 = \nabla^*\nabla + \frac{R}{4}$.
3. **Phương pháp Hạt nhân Nhiệt & Chỉ số Atiyah–Singer:**
   Với toán tử nhiệt $e^{-tD^2}$, siêu vết $\operatorname{Tr}_s(e^{-tD^2}) = \operatorname{Tr}(e^{-tD^- D^+}) - \operatorname{Tr}(e^{-tD^+ D^-})$ **không phụ thuộc vào $t > 0$**: khi $t \to \infty$ nó cho $\operatorname{ind}(D^+)$, còn khi $t \to 0^+$ khai triển tiệm cận địa phương cho tích phân lớp đặc trưng!

## 🧮 Ví dụ tính tay làm từng bước: Phủ kép $\operatorname{Spin}(2) \to SO(2)$ trong $\operatorname{Cliff}(\mathbb{R}^2)$

Theo Mục 2.1 của [`DiracNotes.pdf`](https://people.math.harvard.edu/~dafr/DiracNotes.pdf), hãy kiểm tra trực tiếp phủ kép của $SO(2)$:
1. **Cơ sở của $\operatorname{Cliff}(\mathbb{R}^2)$:** Với cơ sở trực chuẩn $\{e_1, e_2\}$, ta có $e_1^2 = e_2^2 = -1$ và $e_1 e_2 = -e_2 e_1$. Đặt $J = e_1 e_2$; khi đó:
   $$J^2 = e_1 e_2 e_1 e_2 = -e_1^2 e_2^2 = -(-1)(-1) = -1.$$
2. **Đường cong trong $\operatorname{Spin}(2)$:** Xét phần tử $g(\theta) = \cos\theta + \sin\theta\, e_1 e_2 \in \operatorname{Cliff}^{\mathrm{even}}(\mathbb{R}^2)$.
   - Khi $\theta$ đi từ $0$ đến $\pi$, $g(0) = 1$ và $g(\pi) = -1$ (hai điểm phân biệt trong $\operatorname{Spin}(2)$!).
   - Tác động liên hợp $v \mapsto g(\theta)\, v\, g(\theta)^{-1}$ lên $e_1$ cho phép quay góc **$2\theta$** trong mặt phẳng $\mathbb{R}^2$! Do đó $g(\pi) = -1$ ứng với phép quay $2\pi$ (đồng nhất trong $SO(2)$), chứng minh $\operatorname{Spin}(2) \cong S^1 \xrightarrow{z \mapsto z^2} SO(2) \cong S^1$ là phủ bậc $2$.

## 🏆 Định lý Chỉ số Atiyah–Singer (Góc nhìn Tôpô & Giải tích)

Theo Chương 1 & Chương 5 của [`DiracNotes.pdf`](https://people.math.harvard.edu/~dafr/DiracNotes.pdf):

- **Trường hợp đa tạp Spin chẵn chiều $X$:** Toán tử Dirac tách thành $D^+: \Gamma(S^+) \to \Gamma(S^-)$, và:
  $$\operatorname{ind}(D^+) = \dim\ker D^+ - \dim\ker D^- = \int_X \hat{A}(X),$$
  trong đó $\hat{A}(X)$ là giống $\hat{A}$ xây dựng từ các lớp Pontryagin của bó tiếp tuyến $TX$.
- **Hệ quả hình học nổi tiếng (Định lý Lichnerowicz):** Nếu $X$ là đa tạp spin compact có **độ cong vô hướng dương $R > 0$**, công thức $D^2 = \nabla^*\nabla + \frac{R}{4}$ ép $\ker D = 0$, suy ra mọi đa tạp spin có $\hat{A}(X) \neq 0$ (như mặt K3) **không thể mang bất kỳ mêtric nào có $R > 0$**!
- **Công thức tổng quát (K-lý thuyết):** Với mọi toán tử elliptic $P$ trên đa tạp đóng $X$, chỉ số giải tích bằng chỉ số tôpô trong K-lý thuyết:
  $$\operatorname{ind}(P) = (-1)^n \langle \operatorname{ch}(\sigma(P)) \smile \operatorname{Td}(TX \otimes \mathbb{C}),\; [TX] \rangle.$$

## 🧩 Bài tập

1. **Kiểm tra tác động quay của $\operatorname{Spin}(2)$:** Tính tường minh $(\cos\theta + \sin\theta\,e_1e_2)\, e_1\, (\cos\theta - \sin\theta\,e_1e_2)$ trong $\operatorname{Cliff}(\mathbb{R}^2)$ và chứng minh kết quả bằng $\cos(2\theta)e_1 + \sin(2\theta)e_2$.
2. **Triệt tiêu siêu vết với $t > 0$:** Giả sử $D^+ \psi = \lambda \psi$ với $\lambda \neq 0$. Chứng minh $D^-(D^+ \psi) = \lambda (D^+ \psi)$ có cùng giá trị riêng $\lambda^2$ của $D^2$, nên mọi trạng thái khác $0$ triệt tiêu từng cặp trong $\operatorname{Tr}_s(e^{-tD^2})$.
3. **Điều kiện tồn tại cấu trúc Spin:** Vì sao $\mathbb{C}P^2$ không có cấu trúc Spin ($w_2(\mathbb{C}P^2) \neq 0$), còn $\mathbb{C}P^3$ thì có?
4. **Liên hệ Gauss–Bonnet:** Khi thay bó spinor bằng bó dạng vi phân $\Lambda^* T^*X$ và toán tử $d + d^*$, hãy kiểm tra xem $\operatorname{ind}(d+d^* : \Lambda^{\mathrm{even}} \to \Lambda^{\mathrm{odd}})$ cho ra bất biến tôpô quen thuộc nào!
