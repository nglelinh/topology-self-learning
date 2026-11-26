---
layout: post
title: "Lecture 06.05: Wild Topology — Không Gian Vượt Ngoài Phức CW"
lang: vi
lang-ref: lecture-06-05
chapter: 6
lecture: 5
order: 5
categories: [chapter06]
tags: [wild-topology, hawaiian-earring, warsaw-circle, peano-continuum, fundamental-group]
description: "Tôpô Hoang dã (Wild Topology): Hawaiian Earring, Warsaw Circle, Harmonic Archipelago và giới hạn của các định lý cổ điển ngoài phạm trù phức CW"
---

**Thế giới "hoang dã" nơi trực giác đại số thông thường bị thử thách**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Trong Chương 05 và Chương 06, ta quen làm việc với những không gian "hiền lành" như đa tạp và phức CW — nơi mọi điểm đều có lân cận co rút được, và nhóm cơ bản $\pi_1$ dễ dàng tính qua định lý Seifert–Van Kampen. Nhưng điều gì xảy ra nếu ta lấy vô hạn đường tròn bán kính $1/n$ tiếp xúc tại một điểm? Không gian đó **compact, liên thông đường**, trông có vẻ vô hại — vậy mà nhóm cơ bản của nó bỗng trở thành **không đếm được**, không có không gian phủ phổ dụng, và làm sụp đổ phép quy nạp chuẩn của phức CW! Chào mừng bạn đến với **Tôpô Hoang dã (Wild Topology)**, bộ sưu tập kỳ thú được hệ thống hoá tại [Wild Topology Bestiary](https://wildtopology.com/bestiary/).

![Khuyên tai Hawaii và Vòng tròn Warsaw]({{ site.imgurl }}/chapter_img/chapter06/06_01_wild_topology.png)

## 🗺️ Kiến thức cần nhớ: Tôpô Hoang dã nghiên cứu những gì?

1. **Ranh giới giữa "Tame" (Phức CW) và "Wild":** Một không gian có tính chất tôpô toàn cục tốt (compact, mêtric hoá được, liên thông đường) vẫn có thể có **kỳ dị địa phương (local pathology)** khiến các công cụ đại số như không gian phủ phổ dụng hoặc định lý Seifert–Van Kampen mất hiệu lực.
2. **Điều kiện nửa đơn liên địa phương (Semilocally Simply Connected):** Để $X$ có không gian phủ phổ dụng, mọi điểm $x \in X$ phải có lân cận $U$ sao cho phép nhúng $i_*: \pi_1(U, x) \to \pi_1(X, x)$ là đồng cấu tầm thường.
3. **Nhóm cơ bản tôpô (Topological Fundamental Group):** Khi $\pi_1(X, x_0)$ quá lớn (không đếm được), ta trang bị cho nó tôpô thương từ không gian vòng $\Omega(X, x_0)$ để giữ lại thông tin hội tụ của các dãy vòng nhỏ dần.

## 🧮 Ví dụ tính tay làm từng bước: So sánh $\bigvee_{n=1}^\infty S^1$ và Khuyên tai Hawaii $\mathbb{E}$

Xét hai không gian có cùng tập điểm nền là hợp của vô hạn đường tròn $C_n$ ($n \ge 1$) chung nhau đúng một điểm $p$:

1. **Trường hợp 1 — Bó vô hạn đường tròn $W = \bigvee_{n=1}^\infty S^1$ (tôpô CW yếu):**
   - Một tập $U \subset W$ mở khi và chỉ khi $U \cap C_n$ mở trên từng đường tròn. Do đó ta có thể chọn lân cận $U$ không chứa trọn bất kỳ $C_n$ nào.
   - Bất kỳ vòng liên tục $\gamma: [0,1] \to W$ nào đều có ảnh là tập **compact**, nên $\gamma([0,1])$ chỉ cắt hữu hạn đường tròn $C_1, \dots, C_N$. Vậy:
     $$\pi_1(W, p) \cong \ast_{n=1}^{\infty} \mathbb{Z} \quad (\text{nhóm tự do đếm được sinh}).$$
2. **Trường hợp 2 — Khuyên tai Hawaii $\mathbb{E} = \bigcup_{n=1}^\infty C_n \subset \mathbb{R}^2$ với $C_n = \{(x,y) : (x - \frac{1}{n})^2 + y^2 = \frac{1}{n^2}\}$:**
   - Trong tôpô không gian con của $\mathbb{R}^2$, mọi quả cầu mở $B(p, \varepsilon)$ đều chứa trọn mọi $C_n$ với $n > 2/\varepsilon$.
   - Ta có thể dựng một vòng liên tục $\gamma: [0,1] \to \mathbb{E}$ đi qua vòng $C_1$ trên $[0, 1/2]$, vòng $C_2$ trên $[1/2, 3/4]$, vòng $C_n$ trên $[1 - 2^{-(n-1)}, 1 - 2^{-n}]$, và dừng tại $p$ ở $t=1$ (liên tục vì bán kính $1/n \to 0$).
   - Tương ứng mỗi dãy nhị phân $(a_n) \in \{0,1\}^{\mathbb{N}}$ với vòng đi qua $C_n$ nếu $a_n = 1$, phép chiếu rút $r_n: \mathbb{E} \to C_n$ chứng minh các lớp đồng luân của chúng phân biệt đôi một. Vì $|\{0,1\}^{\mathbb{N}}| = \mathfrak{c}$, nhóm $\pi_1(\mathbb{E}, p)$ **không đếm được**!

## 🦁 Bộ sưu tập Kinh điển từ Wild Topology Bestiary

Theo [Wild Topology Bestiary](https://wildtopology.com/bestiary/) và [*Algebraic Topology* (L. Maxim, Mục 4.1)](https://people.math.wisc.edu/~lmaxim/topbookf.pdf), bốn "sinh vật" nổi tiếng nhất giúp kiểm tra giới hạn của mọi định lý tôpô gồm:

| Không gian | Mô tả hình học | Đặc điểm bất ngờ |
|---|---|---|
| **Hawaiian Earring** ($\mathbb{E}$) | Vô hạn đường tròn bán kính $1/n$ tiếp xúc tại $(0,0)$ | Compact, liên thông đường, $\pi_1$ không đếm được, không có phủ phổ dụng |
| **Warsaw Circle** | Đóng kín đường cong $\sin(1/x)$ bằng một cung ngoài | Liên thông đường, $\pi_1 = 0$, nhưng **không co rút được** |
| **Griffiths Twin Cone** | Hai nón dựng trên Khuyên tai Hawaii dán đỉnh tại $p$ | Hợp hai không gian co rút được nhưng $\pi_1$ không tầm thường (phá vỡ Van Kampen nếu không có điều kiện mở) |
| **Harmonic Archipelago** | Vô hạn "ngọn núi" trên đĩa $D^2$ dựng trên từng vòng của $\mathbb{E}$ | Đơn liên? Không — $\pi_1$ không đếm được dù mỗi vòng nhỏ đều co rút qua các ngọn núi |

## 🧩 Bài tập

1. **Chứng minh tính liên tục của vòng vô hạn trên $\mathbb{E}$:** Cho ánh xạ $\gamma: [0,1] \to \mathbb{E}$ đi qua vòng $C_n$ trên đoạn $[1 - 2^{-(n-1)}, 1 - 2^{-n}]$ và $\gamma(1) = (0,0)$. Hãy chứng minh $\gamma$ liên tục tại $t=1$ bằng định nghĩa $\varepsilon$-$\delta$.
2. **Phép chiếu rút lên $C_k$:** Với mỗi $k \ge 1$, xét $r_k: \mathbb{E} \to C_k$ giữ nguyên $C_k$ và đưa mọi $C_n$ ($n \neq k$) về $(0,0)$. Chứng minh $r_k$ liên tục và suy ra đồng cấu toàn ánh $\Phi: \pi_1(\mathbb{E}) \to \prod_{n=1}^\infty \mathbb{Z}$.
3. **Vòng tròn Warsaw:** Giải thích vì sao Vòng tròn Warsaw không đồng luân tương đương với điểm (dùng tính bất biến liên thông địa phương hoặc ánh xạ lên $S^1$).
4. **Phân biệt tôpô yếu và tôpô không gian con:** Chứng minh ánh xạ đồng nhất $\mathrm{id}: \bigvee_{n=1}^\infty S^1 \to \mathbb{E}$ liên tục nhưng **không phải là đồng phôi**.
