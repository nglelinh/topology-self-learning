---
layout: post
title: "Bài 09.09: Hình học và tô-pô"
lang: vi
lang-ref: lecture-09-09
chapter: 9
lecture: 9
order: 9
categories: [chapter09]
tags: [geometry, topology, so-sánh, khái-niệm-cơ-bản]
description: "Hình học đo độ dài và góc; tô-pô giữ những gì còn sau kéo–uốn. Không nhầm mặt đóng với có biên; vuông đặc ≠ đường tròn."
---

**Hình học** đo độ dài, góc, diện tích, độ cong. **Tô-pô** hỏi những tính chất còn lại khi kéo, nén, uốn — không cắt, không dán. Ly có quai và torus khác nhau về hình học, đồng phôi về tô-pô: [Bài 09.01]({{ site.baseurl }}/contents/vi/chapter09/09_01_Coffee_Donut/). Định nghĩa đồng phôi: [Bài 01.03]({{ site.baseurl }}/contents/vi/chapter01/01_03_Continuous_Functions_Homeomorphisms/).

![Ly biến thành torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)

Ly có quai biến dạng liên tục thành torus. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif).

## Cùng vật, hai câu hỏi

![Hình vuông](https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Square.svg/500px-Square.svg.png)

Hình vuông: cạnh, góc, diện tích là hình học. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Square.svg).

![Hình cầu](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Sphere_wireframe_10deg_6r.svg/500px-Sphere_wireframe_10deg_6r.svg.png)

Hình cầu: bán kính và thể tích là hình học. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Sphere_wireframe_10deg_6r.svg).

Hai hình vuông cạnh 5 cm và 10 cm **khác** về hình học, **đồng phôi** về tô-pô (cùng kiểu: đĩa đóng). Hai hình cầu bán kính khác nhau cũng vậy.

![Hình lập phương](https://upload.wikimedia.org/wikipedia/commons/thumb/0/02/Cube.svg/500px-Cube.svg.png)

Bề mặt lập phương: góc và độ dài cạnh là hình học; đồng phôi với mặt cầu là tô-pô. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cube.svg).

## Không nhầm các cặp này

| Cặp | Hình học | Tô-pô |
|---|---|---|
| Vuông **đặc** và đĩa đóng | Góc / cạnh khác | Đồng phôi: cả hai là 2-đĩa đóng |
| Đường tròn $$S^1$$ và đĩa đóng | Cong / phẳng | **Không** đồng phôi: đường tròn không biên; đĩa có biên |
| Mặt cầu $$S^2$$ và khối cầu $$B^3$$ | Vỏ / đặc | **Không** đồng phôi: chiều khác |
| Mặt cầu và torus | Cả hai “tròn” | **Không** đồng phôi: $$g=0$$ khác $$g=1$$ |

**Mặt đóng** nghĩa là compact **và không biên**. Đĩa đóng compact nhưng **có biên** — không phải mặt đóng. Đừng gọi đĩa là “hình tròn đóng” khi đang nói đồng phôi.

## Khi nào dùng cái nào

- Tính diện tích, góc, khoảng cách ngắn nhất: hình học (hoặc hình học Riemann).
- Hỏi “có lỗ không”, “có biên không”, “kéo được thành cái kia không”: tô-pô.
- Hai không gian đồng phôi có thể mang metric rất khác nhau.

Tương đương đồng luân yếu hơn đồng phôi: khối cầu đặc co được về một điểm, mặt cầu thì không — [Bài 09.01]({{ site.baseurl }}/contents/vi/chapter09/09_01_Coffee_Donut/).

## Bài tập

1.  Hình vuông đặc và đường tròn $$S^1$$ có đồng phôi không? Vì sao?

Đáp án

Không. Vuông đặc (đĩa đóng) có biên; $$S^1$$ không biên. Bỏ một điểm: đĩa còn liên thông đường, $$S^1$$ thì không.

1.  “Mặt đóng” có đồng nghĩa “compact” không?

Đáp án

Không. Mặt đóng = compact **và không biên**. Đĩa đóng compact nhưng có biên.

1.  Hai hình cầu bán kính khác nhau đồng phôi không? Đẳng cự không?

Đáp án

Đồng phôi: có (cùng kiểu $$S^2$$). Đẳng cự: không (bán kính khác — đó là hình học).

::: {style="margin-top: 20px; padding: 10px; background-color: #f8f9fa; border-left: 4px solid #007bff;"}
[← Quay lại đầu chương]({{ site.baseurl }}/contents/vi/chapter09/){style="text-decoration: none; color: #007bff; font-weight: bold;"}
:::
