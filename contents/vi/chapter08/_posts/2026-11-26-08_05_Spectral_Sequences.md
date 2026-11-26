---
layout: post
title: "Lecture 08.05: Dãy Phổ (Spectral Sequences) — Leray–Serre, Gysin và Wang"
lang: vi
lang-ref: lecture-08-05
chapter: 8
lecture: 5
order: 5
categories: [chapter08]
tags: [spectral-sequences, leray-serre, gysin-sequence, homotopy-groups-of-spheres, cohomology]
description: "Dãy phổ trong Tôpô Đại số: Định lý Leray–Serre cho phân thớ, dãy Gysin & Wang, và cách tính nhóm đồng luân mặt cầu"
---

**Cỗ máy "xấp xỉ liên tiếp" mạnh nhất của Tôpô Đại số hiện đại**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Với phân thớ $F \hookrightarrow E \to B$, bạn biết đối đồng điều của không gian nền $H^*(B)$ và của thớ $H^*(F)$, nhưng làm sao khôi phục $H^*(E)$ (hoặc ngược lại, tính $H^*(F)$ từ $E$ và $B$)? Khác với tích trực tiếp $B \times F$ (có công thức Künneth), một phân thớ xoắn khiến $H^*(E)$ không chỉ là tích tensor! Năm 1946, Jean Leray phát minh ra **Dãy phổ (Spectral Sequence)** — một chuỗi các "trang sách" $(E_r, d_r)$ nơi mỗi trang $E_{r+1}$ là đồng điều của trang $E_r$, hội tụ về $H^*(E)$.

![Bảng dãy phổ Leray-Serre với các vi phân d_r]({{ site.imgurl }}/chapter_img/chapter08/08_05_spectral_sequence.png)

## 🗺️ Kiến thức cần nhớ: Cấu trúc một Dãy phổ Đối đồng điều

Theo Chương 10 của [*Algebraic Topology: A Comprehensive Introduction* (L. Maxim)](https://people.math.wisc.edu/~lmaxim/topbookf.pdf):

1. **Trang $E_r^{p,q}$ và Vi phân $d_r$:**
   Mỗi trang $E_r$ ($r \ge 2$) là một lưới các nhóm Abel phân bậc kép $E_r^{p,q}$ ($p, q \ge 0$), trang bị vi phân $d_r: E_r^{p,q} \to E_r^{p+r,\, q-r+1}$ thoả mãn $d_r^2 = 0$, và:
   $$E_{r+1}^{p,q} \cong \frac{\ker\left(d_r: E_r^{p,q} \to E_r^{p+r, q-r+1}\right)}{\operatorname{im}\left(d_r: E_r^{p-r, q+r-1} \to E_r^{p,q}\right)}.$$
2. **Định lý Dãy phổ Leray–Serre:**
   Cho phân thớ $F \hookrightarrow E \to B$ với $B$ đơn liên ($\pi_1(B)=0$). Khi đó tồn tại dãy phổ góc phần tư I hội tụ về $H^*(E; R)$ ($E_r^{p,q} \Rightarrow H^{p+q}(E; R)$) với trang khởi đầu:
   $$E_2^{p,q} \cong H^p\big(B;\, H^q(F; R)\big),$$
   và các vi phân $d_r$ tương thích với **tích cup** theo quy tắc Leibniz phân bậc!
3. **Hội tụ và Đọc kết quả theo đường chéo $p + q = n$:**
   Vì $d_r$ nhảy ra ngoài góc phần tư I khi $r$ đủ lớn, tại mỗi ô $(p,q)$ dãy dừng ở $E_\infty^{p,q}$, và $H^n(E)$ được lắp ghép từ các mảnh trên đường chéo $p + q = n$.

## 🧮 Ví dụ tính tay làm từng bước: Tính $H^*(\Omega S^n; \mathbb{Z})$ bằng Dãy phổ Leray–Serre

Xét phân thớ đường đi (path-loop fibration) trên mặt cầu $S^n$ ($n \ge 2$):
$$\Omega S^n \hookrightarrow PS^n \longrightarrow S^n,$$
trong đó không gian đường $PS^n$ **khả rút** ($H^k(PS^n) = 0$ với mọi $k > 0$)!

1. **Trang $E_2^{p,q} = H^p(S^n; H^q(\Omega S^n; \mathbb{Z}))$:**
   Vì $H^p(S^n; \mathbb{Z}) = \mathbb{Z}$ chỉ khác $0$ tại $p = 0$ và $p = n$, bảng $E_2$ chỉ có **đúng hai cột khác $0$** là cột $p = 0$ và cột $p = n$!
2. **Xác định vi phân sống sót duy nhất $d_n$:**
   Mọi vi phân $d_r$ với $r \neq n$ đều có nguồn hoặc đích rơi vào vùng $0$. Chỉ duy nhất $d_n: E_n^{0, q} \to E_n^{n, q - n + 1}$ có thể khác $0$.
3. **Ép điều kiện $E_\infty^{p,q} = 0$ (vì $PS^n$ khả rút):**
   Để mọi ô $(p,q) \neq (0,0)$ bị triệt tiêu ở $E_\infty$, mỗi $d_n: H^q(\Omega S^n) \to H^{q-n+1}(\Omega S^n)$ phải là **đẳng cấu** với mọi $q \ge n-1$, và $H^q(\Omega S^n) = 0$ với $0 < q < n-1$!
   Suy ra ngay bằng quy nạp:
   $$H^q(\Omega S^n; \mathbb{Z}) \cong \begin{cases} \mathbb{Z} & \text{nếu } q \text{ chia hết cho } n-1, \\ 0 & \text{trường hợp khác.} \end{cases}$$

## 🌊 Hai hệ quả đặc biệt: Dãy Gysin, Dãy Wang và $\pi_{n+1}(S^n)$

- **Dãy Gysin (khi thớ là $S^k$):** Bảng $E_2$ chỉ có hai hàng $q=0$ và $q=k$, rút gọn dãy phổ thành một **dãy khớp dài**:
  $$\cdots \to H^{m-k-1}(B) \xrightarrow{\smile e} H^m(B) \xrightarrow{\pi^*} H^m(E) \to H^{m-k}(B) \to \cdots$$
  Áp dụng cho phân thớ $\mathbb{C}P^n$: chứng minh ngay $H^*(\mathbb{C}P^n; \mathbb{Z}) \cong \mathbb{Z}[x]/(x^{n+1})$!
- **Dãy Wang (khi nền là $S^n$):** Bảng $E_2$ chỉ có hai cột $p=0$ và $p=n$ (như ví dụ $\Omega S^n$ ở trên).
- **Tính $\pi_{n+1}(S^n)$ và Định lý Hữu hạn Serre:** Bằng tháp Whitehead (Killing homotopy groups) và dãy phổ Serre, Chương 10.9–10.11 của [`topbookf.pdf`](https://people.math.wisc.edu/~lmaxim/topbookf.pdf) tính được $\pi_4(S^3) \cong \mathbb{Z}/2\mathbb{Z}$ và chứng minh định lý Serre: mọi $\pi_k(S^n)$ ($k > n$) đều là nhóm Abel hữu hạn, trừ trường hợp $k = 2n-1$ với $n$ chẵn!

## 🧩 Bài tập

1. **Dùng Dãy Gysin cho phân thớ Hopf $S^1 \hookrightarrow S^3 \to S^2$:** Viết dãy Gysin với $k=1, B=S^2, E=S^3$ và suy ra lớp Euler $e \in H^2(S^2; \mathbb{Z})$ phải là phần tử sinh $\pm 1$.
2. **Tính $H^*(\mathbb{C}P^\infty; \mathbb{Z})$:** Áp dụng dãy Gysin cho phân thớ $S^1 \hookrightarrow S^\infty \to \mathbb{C}P^\infty$ (với $S^\infty$ khả rút).
3. **Kiểm tra tích cup trên $\Omega S^n$:** Cho $n=3$, dùng quy tắc Leibniz $d_3(xy) = d_3(x)y + (-1)^{\deg x} x d_3(y)$ để chứng minh vành $H^*(\Omega S^3; \mathbb{Z})$ là một đại số đa thức chia (divided power algebra).
4. **Dãy phổ đồng điều của $S^2 \times S^3$:** Kiểm tra tất cả các vi phân $d_r$ đều bằng $0$ cho phân thớ tầm thường $S^3 \hookrightarrow S^2 \times S^3 \to S^2$.
