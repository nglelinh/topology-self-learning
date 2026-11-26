---
layout: post
title: "Lecture 07.05: Tôpô Tổ Hợp, Bổ Đề Sperner và Tính Toán Phân Tán"
lang: vi
lang-ref: lecture-07-05
chapter: 7
lecture: 5
order: 5
categories: [chapter07]
tags: [combinatorial-topology, sperner-lemma, chromatic-subdivision, distributed-computing, simplicial-complex]
description: "Tôpô Tổ hợp ứng dụng trong Tính toán Phân tán: Phức giao thức, Bổ đề Sperner, Chia nhỏ sắc tố chuẩn và Định lý Khả tính Bất đồng bộ"
---

**Khi những "lỗ hổng" trong phức đơn hình quyết định thuật toán nào có thể chạy được**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Giả sử $n+1$ tiến trình máy tính giao tiếp qua bộ nhớ chia sẻ bất đồng bộ và một số tiến trình có thể bị treo bất kỳ lúc nào. Liệu chúng có thể **đồng thuận (consensus)** chọn ra một giá trị chung hay không? Năm 1985, Fischer–Lynch–Paterson chứng minh là *không*, bằng lập luận tổ hợp dài dòng. Đến thập niên 1990–2014, Herlihy, Shavit, Kozlov và Rajsbaum trong cuốn *Distributed Computing Through Combinatorial Topology* đã phát hiện ra chân lý gây chấn động: mọi trạng thái thực thi phân tán hợp thành một **phức đơn hình sắc tố**, và bài toán có giải được hay không phụ thuộc hoàn toàn vào **tính liên thông tôpô và Bổ đề Sperner**!

![Bổ đề Sperner và Chia nhỏ sắc tố chuẩn]({{ site.imgurl }}/chapter_img/chapter07/07_05_sperner_chromatic.png)

## 🗺️ Kiến thức cần nhớ: Ba trụ cột của Tôpô Tổ hợp Phân tán

1. **Mô hình hoá Hệ phân tán bằng Phức Đơn hình Sắc tố $(K, \chi)$:**
   Mỗi đỉnh $v = (p_i, \mathrm{state}_i)$ biểu diễn trạng thái cục bộ của tiến trình $p_i$ (màu sắc $\chi(v) = i$); mỗi $k$-đơn hình biểu diễn một lần thực thi khả dĩ mà $k+1$ tiến trình cùng nhìn thấy trạng thái của nhau.
2. **Chia nhỏ Sắc tố Chuẩn $\operatorname{Ch}(K)$ (Standard Chromatic Subdivision):**
   Khác với chia nhỏ trọng tâm (làm mất màu đỉnh ở giữa), $\operatorname{Ch}(K)$ dịch nhẹ các đỉnh mới để mọi đơn hình con vẫn giữ đủ $n+1$ màu phân biệt — tương ứng chính xác với một vòng đọc–ghi tức thời (immediate snapshot).
3. **Bổ đề Sperner & Định lý Khả tính Bất đồng bộ (ACT):**
   Một bài toán quyết định $(I, O, \Delta)$ giải được bằng giao thức bất đồng bộ wait-free khi và chỉ khi tồn tại phép chia nhỏ sắc tố $\operatorname{Div}(I)$ và ánh xạ đơn hình bảo toàn màu $\mu: \operatorname{Div}(I) \to O$ được mang bởi $\Delta$.

## 🧮 Ví dụ tính tay làm từng bước: Bổ đề Sperner chứng minh Không thể Đồng thuận 2 tiến trình

Xét 2 tiến trình $P_0$ (màu đỏ) và $P_1$ (màu xanh) với đầu vào nhị phân $\{0, 1\}$:
1. **Phức đầu vào $I$ và Phức đầu ra $O$:**
   - Phức đầu vào cho đồng thuận nhị phân gồm các khả năng đầu vào $(0,0), (0,1), (1,0), (1,1)$ — liên thông đường.
   - Phức đầu ra hợp lệ $O$ chỉ gồm **hai thành phần rời nhau**: đoạn thẳng mà cả hai cùng chọn $0$, và đoạn thẳng mà cả hai cùng chọn $1$ ($O$ **không liên thông**!).
2. **Phức giao thức sau $N$ vòng bất đồng bộ:**
   - Sau 1 vòng immediate snapshot trên đoạn $[v_0, v_1]$ (ứng với đầu vào $(0,1)$), phép chia nhỏ sắc tố $\operatorname{Ch}(\Delta^1)$ biến cạnh $[v_0, v_1]$ thành đường gấp khúc 3 cạnh liên tiếp $[v_0, u_1], [u_1, u_0], [u_0, v_1]$ — **vẫn liên thông**!
   - Quy nạp sau $N$ vòng, phức giao thức $\operatorname{Ch}^N(\Delta^1)$ luôn là một đường liên thông nối trạng thái "chỉ có $0$" (buộc chọn $0$) tới trạng thái "chỉ có $1$" (buộc chọn $1$).
3. **Áp dụng Bổ đề Sperner (chiều 1):**
   - Bất kỳ ánh xạ đơn hình $\mu: \operatorname{Ch}^N(\Delta^1) \to O$ nào gán nhãn hai đầu mút là $0$ và $1$ đều phải tồn tại ít nhất **một cạnh** (số lẻ) có một đầu nhãn $0$ và một đầu nhãn $1$ — nghĩa là hai tiến trình **quyết định khác nhau**, vi phạm đồng thuận!

## 🏛️ Định lý Khả tính Bất đồng bộ (Asynchronous Computability Theorem)

Theo Chương 11 & 15 của *Distributed Computing Through Combinatorial Topology* (Herlihy, Kozlov, Rajsbaum):

- **Định lý 11.2.1 / 15.3.4 (ACT):** Một bài toán $(I, O, \Delta)$ có giao thức bộ nhớ đọc–ghi bất đồng bộ wait-free khi và chỉ khi tồn tại phép chia nhỏ sắc tố $\sigma(I)$ và ánh xạ đơn hình bảo toàn màu $\mu: \sigma(I) \to O$ sao cho $\mu(s) \in \Delta(\operatorname{Car}(s, I))$ với mọi đỉnh $s$.
- **Tổng quát lên $k$-set agreement:** Với $n+1$ tiến trình muốn chọn tối đa $n$ giá trị khác nhau (thay vì 1 giá trị như đồng thuận), **Bổ đề Sperner chiều $n$** trên $\operatorname{Ch}^N(\Delta^n)$ bảo đảm luôn tồn tại ít nhất một $n$-đơn hình cầu vồng có đủ $n+1$ giá trị đầu ra phân biệt — nên bài toán $n$-set agreement **vô nghiệm** trong mô hình bất đồng bộ wait-free!

## 🧩 Bài tập

1. **Đếm đơn hình trong $\operatorname{Ch}(\Delta^1)$ và $\operatorname{Ch}(\Delta^2)$:** Kiểm tra trên hình minh hoạ xem $\operatorname{Ch}(\Delta^1)$ có bao nhiêu 1-đơn hình và $\operatorname{Ch}(\Delta^2)$ có bao nhiêu 2-đơn hình (tam giác con).
2. **Chứng minh Bổ đề Sperner 2D bằng đồ thị đối ngẫu:** Dựng đồ thị có đỉnh là các tam giác con và một đỉnh "bên ngoài"; nối hai đỉnh qua cạnh chung có hai màu `{Đỏ, Xanh}`. Chứng minh số tam giác đủ 3 màu luôn là số lẻ.
3. **Liên hệ Định lý Điểm bất động Brouwer:** Từ Bổ đề Sperner trên tam giác $\Delta^2$, hãy phác thảo cách suy ra Định lý Điểm bất động Brouwer cho ánh xạ liên tục $f: \Delta^2 \to \Delta^2$.
4. **Suy ngẫm về đồng điều:** Nếu phức giao thức vẫn $(k-1)$-liên thông ($H_i = 0$ với $i < k$) sau mọi vòng chạy, điều đó đặt ra ngưỡng cản tôpô nào cho bài toán $k$-set agreement?
