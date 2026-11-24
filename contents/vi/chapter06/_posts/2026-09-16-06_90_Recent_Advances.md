---
layout: post
title: "Lecture 06.90: Tiến bộ gần đây (2022–2026) — Homotopy của mạng nơ-ron và mode connectivity"
lang: vi
lang-ref: lecture-06-90
chapter: 6
lecture: 90
order: 90
lesson_type: optional
categories: [chapter06]
tags: [optional, recent-advances, homotopy, mode-connectivity, neural-networks]
description: "Bài tùy chọn: π₁ và homotopy gặp topology của mạng nơ-ron và mode connectivity. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Các khái niệm đồng luân, $\pi_1$ và không gian phủ của Chapter 06 vẫn giữ nguyên; ở đây ta thay không gian nền $X$ bằng cảnh quan hàm mất mát (loss landscape), không gian kích hoạt hoặc dữ liệu sau từng tầng của mạng nơ-ron.

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu bạn huấn luyện cùng một mạng nơ-ron sâu hai lần từ hai bộ trọng số ngẫu nhiên hoàn toàn khác nhau, hai mô hình cuối cùng sẽ dừng ở hai điểm trọng số $$w_0$$ và $$w_1$$ nằm cách xa nhau hàng trăm đơn vị trong không gian hàng tỷ chiều. Trực giác cổ điển dự đoán rằng hai điểm đó nằm ở hai "thung lũng cô lập" cách nhau bởi núi cao mất mát — nhưng thực nghiệm học sâu hiện đại lại phát hiện một điều kỳ diệu gọi là **Mode Connectivity**: *giữa $$w_0$$ và $$w_1$$ hầu như luôn tồn tại một con đường liên tục $$\gamma(t)$$ đi xuyên qua thung lũng hàm mất mát thấp!* Và chính ngôn ngữ **đồng luân, $$\pi_0, \pi_1$$ và không gian phủ (do đối xứng hoán vị nơ-ron)** của Chương 06 là lăng kính toán học giải mã bí ẩn đó!

Một phép đồng luân là một biến dạng liên tục giữa hai ánh xạ. Trong học sâu, hai bộ trọng số $w_0, w_1$ nằm trong cùng một "mode" nếu tồn tại một đường đi liên tục $\gamma$ nối chúng sao cho hàm mất mát $L(\gamma(t))$ không vượt quá một ngưỡng thấp $c$ — tức $w_0$ và $w_1$ thuộc cùng một thành phần liên thông đường trong tập mức dưới (sublevel set) $S_c = \{w : L(w) \le c\}$. Khảo sát của Ballester–Casacuberta–Escalera (2023) cùng các nghiên cứu về tính liên thông mode (mode connectivity) giai đoạn 2025–2026 cho thấy ngôn ngữ của Chapter 06 có thể áp dụng trực tiếp khi đọc các bài báo thực nghiệm hiện đại.

![Mạng nơ-ron](https://upload.wikimedia.org/wikipedia/commons/4/46/Colored_neural_network.svg)
*Một mạng truyền thẳng (feedforward) là ánh xạ hợp $f:X\to Y$ qua các tầng — đối tượng tự nhiên để xét đồng luân. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Colored_neural_network.svg)*

![Phủ vòng tròn](https://upload.wikimedia.org/wikipedia/commons/5/54/Covering_map.png)
*Ánh xạ phủ $\mathbb{R}\to S^1$: hình mẫu cho cấu trúc nhiều nghịch ảnh trên cùng một đối tượng đáy. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Covering_map.png)*

---

## 🎯 Trực giác

Naitzat, Zhitnikov và Lim (2020) — công trình tiếp tục được trích dẫn rộng rãi sau năm 2022 — cho thấy mạng nơ-ron sâu có xu hướng *đơn giản hóa cấu trúc tô-pô của dữ liệu*: các số Betti của tập dữ liệu giảm dần qua các tầng, tương tự quá trình biến dạng hướng về không gian đơn giản hơn. Ở chiều đối ngẫu, nghiên cứu về mode connectivity đặt câu hỏi về cấu trúc tô-pô của *không gian tham số*: tập mức dưới $S_c$ có liên thông đường hay có nhiều thành phần tách biệt?

---

## 🗺️ Bản đồ kiến thức nền: Tô-pô của Cảnh quan Hàm Mất mát (Loss Landscape)

### 1. Tập mức dưới $$S_c = \{w : L(w) \le c\}$$ và Liên thông Mode ($$\pi_0(S_c)$$)
- **Bản chất:** Mọi mạng nơ-ron có bộ tham số $$w \in \mathbb{R}^P$$ và hàm mất mát $$L(w)$$. Hai nghiệm $$w_0, w_1$$ có **liên thông mode** ở ngưỡng $$c$$ khi và chỉ khi chúng nằm trong **cùng một thành phần liên thông đường** của $$S_c$$ — tức $$[w_0] = [w_1]$$ trong $$\pi_0(S_c)$$!

### 2. Liên thông Mode Tuyến tính (LMC) & Trộn Mô hình (Model Merging)
- **Bản chất:** Nếu không chỉ tồn tại đường cong bất kỳ mà **đúng đoạn thẳng** $$\gamma(t) = (1-t)w_0 + t\,w_1$$ nằm trọn trong $$S_c$$, ta có **Linear Mode Connectivity (LMC)** — cơ sở toán học của kỹ thuật trộn trọng số (*model soup*, *Git Re-Basin*) trên các mô hình LLM/Transformer hàng tỷ tham số!

### 3. Đối xứng Hoán vị Nơ-ron & Không gian Thương (Cầu nối với Phủ Chương 06)
- **Bản chất:** Trong một tầng ẩn gồm $$m$$ nơ-ron, đổi chỗ thứ tự 2 nơ-ron không làm thay đổi hàm đầu ra của mạng! Do đó nhóm đối xứng $$S_m$$ tác động lên không gian trọng số $$\mathbb{R}^P$$ tạo ra tới $$m!$$ bản sao y hệt của cùng một cực tiểu — hệt như các lá của một không gian phủ chiếu xuống không gian hàm!

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc: Đếm $$\pi_0(S_c)$$ trên hàm hai đáy $$L(w) = (w^2 - 1)^2$$

Xét hàm mất mát 1 chiều kinh điển có hai đáy cực tiểu tại $$w = -1$$ và $$w = +1$$:
$$
L(w) = (w^2 - 1)^2, \qquad S_c = \{w \in \mathbb{R} : (w^2 - 1)^2 \le c\}.
$$
Hãy giải bất phương trình $$(w^2 - 1)^2 \le c$$ bằng tay theo từng giá trị ngưỡng $$c$$ và đếm số thành phần liên thông đường $$\lvert \pi_0(S_c)\rvert$$:

1. **Khi $$c < 0$$:** Vì $$(w^2-1)^2 \ge 0$$ nên $$S_c = \emptyset \implies \lvert \pi_0(S_c)\rvert = 0$$.
2. **Khi $$c = 0$$:** $$S_0 = \{-1, +1\}$$ gồm 2 điểm cực tiểu rời nhau $$\implies \lvert \pi_0(S_0)\rvert = 2$$.
3. **Khi $$0 < c < 1$$:** Ta có $$1 - \sqrt{c} \le w^2 \le 1 + \sqrt{c}$$ với $$1 - \sqrt{c} > 0$$, nên $$S_c$$ là hợp của **2 đoạn đóng tách biệt hoàn toàn**:
   $$
   S_c = \bigl[-\sqrt{1+\sqrt{c}},\; -\sqrt{1-\sqrt{c}}\bigr] \;\cup\; \bigl[\sqrt{1-\sqrt{c}},\; \sqrt{1+\sqrt{c}}\bigr]
   \quad\Longrightarrow\quad
   \lvert \pi_0(S_c)\rvert = 2!
   $$
   Ở ngưỡng $$c < 1$$, hai cực tiểu bị ngăn cách bởi ngọn đồi tại $$w = 0$$ (cao $$L(0) = 1$$) — **chưa có mode connectivity**!
4. **Khi $$c \ge 1$$:** Vì $$1 - \sqrt{c} \le 0$$ nên $$w^2 \le 1 + \sqrt{c}$$, tức $$S_c = [-\sqrt{1+\sqrt{c}},\; \sqrt{1+\sqrt{c}}]$$ — **1 đoạn liên thông duy nhất** $$\implies \lvert \pi_0(S_c)\rvert = 1$$!

*(Góc nhìn chiều cao: Trong 1 chiều, muốn đi từ $$-1$$ sang $$+1$$ bạn bắt buộc phải trèo qua đỉnh đồi $$w=0$$. Trong không gian triệu chiều của mạng sâu, thay vì trèo qua đồi, các đường đi dễ dàng **đi vòng qua thung lũng** ở các chiều phụ — đó là lý do mạng càng rộng, $$\pi_0(S_c)$$ càng dễ sụp về 1!)*

### Khung giải thích: 4 bước đọc nghiên cứu Tô-pô Mạng Nơ-ron (2022–2026) (nên đọc chậm)

#### Bước 1: Định vị rõ không gian đang khảo sát
Trong các bài báo TDA/Homotopy cho AI, luôn kiểm tra họ đang nghiên cứu tô-pô của: (1) **dữ liệu qua từng tầng** (số Betti giảm dần khi mạng phân loại), hay (2) **không gian trọng số $$S_c = \{L \le c\}$$** (mode connectivity).

#### Bước 2: Dùng phép hoán vị nơ-ron (Git Re-Basin) để căn chỉnh lá phủ
Hai cực tiểu $$w_0, w_1$$ ban đầu có thể không có *linear* mode connectivity vì thứ tự nơ-ron bị tráo đổi; sau khi tác động phép hoán vị $$\sigma \in S_m$$ đưa $$w_1$$ về cùng "lá phủ" với $$w_0$$, đoạn thẳng nối $$w_0$$ với $$\sigma(w_1)$$ thường có hàng rào mất mát gần bằng $$0$$!

#### Bước 3: Mở rộng sang mô hình sinh, MoE và Machine Unlearning (2025–2026)
Các công trình mới khảo sát xem khi "xóa trí nhớ" một mẫu dữ liệu (unlearning), đường đi liên thông giữa mô hình cũ và mô hình mới có bị đứt gãy hay không.

#### Bước 4: Biên giới mở — Từ $$\pi_0$$ sang $$\pi_1$$ của cảnh quan mất mát
Đo $$\pi_0(S_c)$$ (có đường nối hay không) đã khá chín muồi, nhưng đo $$\pi_1(S_c)$$ (có những "vòng lỗ" cản trở tối ưu hóa nào tồn tại trong cảnh quan mất mát hàng tỷ tham số không?) vẫn là một chân trời nghiên cứu mở cực kỳ hấp dẫn!

$$
\text{Trọng số }w_0, w_1 \in S_c
\;\xrightarrow{\;\text{Hoán vị }\sigma \in S_m\;}\;
\text{Đường đi / Đồng luân tuyến tính }\gamma(t) \subset S_c
\;\xrightarrow{\;\pi_0(S_c) = 1\;}\;
\text{Trộn mô hình (Model Merging)}.
$$

---

## 📐 Bốn tiến bộ cụ thể

### 1. Tổng quan về phân tích dữ liệu tô-pô (TDA) cho mạng nơ-ron

Ballester, Casacuberta và Escalera (2023/2024) tổng hợp cách $\pi_1$, thuật toán Mapper và đồng điều bền vững được áp dụng trên ba đối tượng: (i) dữ liệu đầu vào, (ii) biểu diễn kích hoạt ở các tầng ẩn, và (iii) không gian trọng số.

- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *Topological Data Analysis for Neural Network Analysis: A Comprehensive Survey*, arXiv:2312.05840 (2023).
- Gregory Naitzat, Andrey Zhitnikov, Lek-Heng Lim, *Topology of deep neural networks*, *JMLR* (2020), arXiv:2004.06093 — công trình nền tảng tiếp tục định hướng các nghiên cứu giai đoạn 2022–2026.

### 2. Tính liên thông mode ngoài bài toán phân loại

Yao, Zhang và Tian (2026) tìm thấy bằng chứng về mode connectivity ở các mô hình sinh và mô hình học tương phản (contrastive), cho thấy tính liên thông trong tập mức dưới $S_c = \{L \le c\}$ không chỉ giới hạn ở mạng phân loại dùng softmax. Cheng và Amiri (2026) dùng ngôn ngữ đường đi trong $S_c$ để nghiên cứu bài toán quên máy (machine unlearning): liệu việc loại bỏ một điểm dữ liệu có làm đứt đường nối giữa hai cực tiểu hay không?

- Chengzheyi Yao, Yongzhao Zhang, Yongding Tian, *Mode Connectivity Beyond Classifiers*, arXiv:2608.30366 (2026).
- Jiali Cheng, Hadi Amiri, *Understanding Machine Unlearning Through the Lens of Mode Connectivity*, arXiv:2607.23970 (2026).

### 3. Liên thông mode tuyến tính (Linear Mode Connectivity) và trộn mô hình

Nếu toàn bộ đoạn thẳng nối hai cực tiểu nằm trọn trong $S_c$, ta thu được một phép đồng luân *tuyến tính* giữa hai mạng. Li và Shen (2026) mở rộng khảo sát tính chất này lên các mô hình Transformer quy mô hàng tỷ tham số; Tran và cộng sự (2025–2026) phân tích kiến trúc Mixture-of-Experts (MoE) và cơ chế attention. Về mặt hình thức, bài toán liên thông mode đặt câu hỏi về tập thành phần liên thông đường $\pi_0(S_c)$:

$$
[\gamma]\in\pi_0\bigl(\{w:L(w)\le c\}\bigr).
$$
(trong khi nhóm cơ bản $\pi_1(S_c)$ ở quy mô lớn vẫn còn ít được đo đạc thực nghiệm.)

- Tianyi Li, Zhiqiang Shen, *Scaling Linear Mode Connectivity and Merging to Billion Parameter Pretrained Transformers*, arXiv:2606.23607 (2026).
- Viet-Hoang Tran, Van Hoan Trinh, Khanh Vinh Bui, Tan M. Nguyen, *On Linear Mode Connectivity of Mixture-of-Experts Architectures*, arXiv:2509.11348 (2025).

### 4. Đồng luân như đặc trưng của dữ liệu qua các tầng

Su và cộng sự (2025) tổng quan các hướng phát triển TDA vượt ra ngoài đồng điều bền vững, trong đó cấu trúc đồng luân và phức tế bào bắt đầu được dùng làm đặc trưng. Theo ngôn ngữ của Chapter 06, mỗi tầng $f_\ell$ cảm sinh đồng cấu $(f_\ell)_*$ trên $\pi_1$, và các nghiên cứu gần đây bắt đầu khảo sát nhân và đối nhân của đồng cấu này trên dữ liệu thực nghiệm.

- Zhe Su et al., *Topological Data Analysis and Topological Deep Learning Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

---

## 🧠 Tài liệu

- Hatcher, *Algebraic Topology*, Ch. 1.
- Munkres, *Topology*, Ch. 9, 13.
- Các bài báo arXiv liệt kê ở trên.

## 🔗 Ứng dụng

Kỹ thuật trộn trọng số (model soup / weight averaging) chỉ đạt hiệu quả khi đoạn thẳng nối giữa các checkpoint là một đường đi có hàm mất mát thấp — tức tồn tại một phép đồng luân tuyến tính trong tập mức dưới $S_c$.

## Video tham khảo

- **xem trước** [[NeurIPS 2018] Loss Surfaces, Mode Connectivity, and Fast Ensembling of DNNs](https://www.youtube.com/watch?v=UwKdNzb_Q6U) — Timur Garipov, tiếng Anh. Trình bày các đường nối mode trên bề mặt hàm mất mát, bám sát chủ đề của bài.
- [Introduction to Topological Deep Learning](https://www.youtube.com/watch?v=N67GABKImZA) — Mathilde Papillon, tiếng Anh. Giới thiệu khung học sâu tô-pô.

## 🧩 Bài tập

1. Với $L(x)=(x^2-1)^2$, xác định số phần tử của $\pi_0(S_c)$ theo tham số $c \in \mathbb{R}$.
2. Giải thích vì sao tính liên thông mode tuyến tính (linear mode connectivity) là điều kiện mạnh hơn tính liên thông đường thông thường.
3. Phác họa một ánh xạ phủ $2$ lá của $S^1$ và diễn giải ngắn gọn ý nghĩa của việc hai cực tiểu khác nhau trong không gian tham số có thể chiếu xuống cùng một hàm trên không gian thương (do đối xứng hoán vị nơ-ron).
