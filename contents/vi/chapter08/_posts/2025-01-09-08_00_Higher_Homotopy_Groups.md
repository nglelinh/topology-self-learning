---
layout: post
title: "Lecture 08.00: Higher Homotopy Groups πₙ(X)"
lang: vi
lang-ref: lecture-08-00
chapter: 8
lecture: 0
categories: [chapter08]
tags: [higher-homotopy-groups, πn, homotopy-spheres, whitehead-theorem]
description: "Higher homotopy groups π_n(X): definition, properties, examples, Whitehead Theorem, và computational challenges"
---

**$\pi_n(X, x_0)$ - Beyond the Fundamental Group**

---

## 📖 Tổng quan

Chúng ta đã thành thạo **fundamental group $\pi_1(X, x_0)$**—nhóm các lớp đồng luân của các đường cong đóng dựa trên điểm cơ sở. Đây là một công cụ mạnh mẽ để phát hiện "lỗ" một chiều trong không gian, như cách một vòng dây có thể quấn quanh một cái lỗ trong mặt phẳng hoặc một quả cầu. Nhưng tự nhiên, một câu hỏi nảy sinh: điều gì xảy ra khi chúng ta xem xét các hình cầu có chiều cao hơn? Nếu $\pi_1$ phát hiện các lỗ một chiều bằng cách ánh xạ $S^1$ vào không gian, thì liệu chúng ta có thể phát hiện các "lỗ" nhiều chiều hơn bằng cách ánh xạ $S^2$, $S^3$, hay thậm chí $S^n$ vào không gian không?

Câu trả lời là có, và đây là nơi mà **higher homotopy groups $\pi_n(X, x_0)$** xuất hiện. Nhóm đồng luân bậc $n$ được định nghĩa như tập hợp các lớp đồng luân của các ánh xạ liên tục từ hình cầu $n$ chiều $S^n$ vào không gian $X$, với điều kiện điểm cơ sở của $S^n$ được ánh xạ tới điểm cơ sở $x_0$ của $X$. Điều này có vẻ như một khái quát hóa tự nhiên của fundamental group, nhưng thực tế nó mở ra một thế giới toán học hoàn toàn mới với những tính chất sâu sắc và những thách thức tính toán đáng kinh ngạc.

Tại sao các nhóm đồng luân bậc cao lại cách mạng? Đầu tiên, chúng cung cấp các bất biến đồng luân hoàn chỉnh: nếu chúng ta biết tất cả các nhóm $\pi_n(X)$ và $\pi_n(Y)$ cho mọi $n$, và chúng đẳng cấu với nhau, thì đối với các phức CW, chúng ta có thể kết luận rằng $X$ và $Y$ đồng luân tương đương. Đây là một kết quả mạnh mẽ mà homology không thể cung cấp—có những không gian có cùng homology nhưng không đồng luân tương đương. Thứ hai, một tính chất quan trọng là $\pi_n(X)$ là nhóm abelian cho mọi $n \geq 2$, điều này làm cho cấu trúc đại số của chúng đơn giản hơn nhiều so với $\pi_1$, có thể không giao hoán. Tính chất này xuất phát từ một lý luận hình học sâu sắc: trong không gian nhiều chiều, có đủ "chỗ" để các đường cong trượt qua nhau một cách liên tục, cho phép chúng ta hoán đổi thứ tự của các phép toán mà không thay đổi kết quả đồng luân.

Các nhóm đồng luân bậc cao cũng kết nối topology với đại số và hình học theo những cách sâu sắc. Chúng xuất hiện trong obstruction theory, nơi chúng kiểm soát các chướng ngại vật khi cố gắng mở rộng các ánh xạ từ các skeleton của một phức CW. Chúng là nền tảng của bundle theory, nơi các nhóm đồng luân của các Grassmannian phân loại các vector bundle. Và trong stable homotopy theory, một lĩnh vực nghiên cứu tích cực, các mẫu hình xuất hiện khi chúng ta xem xét giới hạn của $\pi_{n+k}(S^n)$ khi $n$ tiến tới vô cùng, tạo ra các stable homotopy groups $\pi_k^s$ có cấu trúc đại số phong phú và kết nối với cobordism theory và K-theory.

![Higher homotopy groups](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Hopf_Fibration.png/400px-Hopf_Fibration.png)  
*Hopf fibration - một ví dụ kinh điển cho thấy $\pi_3(S^2) = \mathbb{Z}$, minh chứng rằng các hình cầu có thể "quấn" quanh các không gian có chiều thấp hơn theo những cách không tầm thường - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hopf_Fibration.png)*

Tuy nhiên, cùng với sức mạnh này đi kèm những thách thức tính toán đáng kinh ngạc. Ngay cả việc tính toán $\pi_n(S^m)$ cho các giá trị nhỏ của $n$ và $m$ cũng là một bài toán cực kỳ khó khăn, và hầu hết các giá trị này vẫn chưa được biết. Không có thuật toán tổng quát để tính toán các nhóm đồng luân bậc cao, không giống như homology, nơi chúng ta có các công cụ như Mayer-Vietoris sequence và các phương pháp tính toán hiệu quả. Một điều đáng ngạc nhiên là $\pi_n(S^m)$ có thể khác không ngay cả khi $n$ lớn hơn nhiều so với $m$—ví dụ, $\pi_3(S^2) = \mathbb{Z}$ mặc dù chiều của $S^3$ lớn hơn chiều của $S^2$. Điều này phản ánh sự phức tạp sâu sắc của topology: các không gian có thể có cấu trúc đồng luân phong phú mà không thể được phát hiện chỉ bằng cách xem xét các chiều của chúng.

Trong bài học này, chúng ta sẽ khám phá định nghĩa hình thức của $\pi_n(X)$ và cấu trúc nhóm của nó, được xây dựng thông qua phép cộng dựa trên suspension và pinch map. Chúng ta sẽ hiểu tại sao $\pi_n$ lại là abelian cho $n \geq 2$ thông qua lý luận Eckmann-Hilton, một lý luận hình học đẹp đẽ cho thấy rằng trong không gian nhiều chiều, có đủ "chỗ" để các phép toán giao hoán. Chúng ta sẽ nghiên cứu các ví dụ cơ bản: $\pi_n$ của một điểm, của các không gian co rút được, và quan trọng nhất là $\pi_n(S^m)$ cho các giá trị khác nhau của $n$ và $m$. Chúng ta sẽ khám phá các định lý cơ bản như Whitehead Theorem, cho thấy rằng một ánh xạ cảm sinh đẳng cấu trên tất cả các nhóm đồng luân thì chính nó là một tương đương đồng luân, và Hurewicz Theorem, kết nối các nhóm đồng luân với homology. Chúng ta cũng sẽ xem xét long exact sequence của fibrations, một công cụ tính toán mạnh mẽ, và cuối cùng, chúng ta sẽ thảo luận về những thách thức tính toán và lý do tại sao việc tính toán các nhóm đồng luân lại khó khăn đến vậy.

Tại sao bài học này quan trọng? Các nhóm đồng luân bậc cao là các bất biến hoàn chỉnh khi kết hợp với homology—chúng cung cấp thông tin về cấu trúc đồng luân của không gian mà homology không thể nắm bắt. Chúng là nền tảng của obstruction theory, một kỹ thuật mạnh mẽ để xây dựng và phân loại các ánh xạ và các cấu trúc hình học. Chúng cần thiết trong bundle theory, nơi chúng phân loại các vector bundle và principal bundle. Và cuối cùng, chúng đại diện cho một số bài toán toán học sâu sắc nhất và chưa được giải quyết—việc tính toán stable homotopy groups của các hình cầu là một lĩnh vực nghiên cứu tích cực với những kết nối sâu sắc với đại số, hình học và vật lý lý thuyết.

---

## 🎯 Definition and Basic Properties

### 1. Định nghĩa và Trực giác Hình học

Hãy bắt đầu với một cách nhìn hình học về những gì chúng ta đang cố gắng đo lường. Khi chúng ta nghiên cứu fundamental group $\pi_1$(X, $x_0$), chúng ta đang hỏi: có bao nhiêu cách khác nhau (lên đến đồng luân) để một đường cong đóng có thể quấn quanh không gian X? Một cách hình học để nghĩ về điều này là xem xét các ánh xạ từ hình tròn $S^1$ vào X, với điều kiện điểm cơ sở của $S^1$ được ánh xạ tới điểm cơ sở $x_0$ của X. Hai ánh xạ như vậy được coi là tương đương nếu chúng có thể được biến dạng liên tục thành nhau trong khi giữ điểm cơ sở cố định.

Bây giờ, hãy tưởng tượng chúng ta nâng cấp khái niệm này lên các chiều cao hơn. Thay vì ánh xạ từ một hình tròn một chiều, chúng ta xem xét các ánh xạ từ một hình cầu n chiều $S^n$ vào không gian X. Hình cầu n chiều là tập hợp tất cả các điểm trong không gian Euclid (n+1) chiều có khoảng cách từ gốc tọa độ bằng 1. Đối với n = 1, đây là đường tròn đơn vị; đối với n = 2, đây là mặt cầu thông thường; đối với n = 3, đây là hình cầu ba chiều trong không gian bốn chiều, và cứ thế. Mỗi hình cầu như vậy có một điểm cơ sở tự nhiên, thường được chọn là điểm (1, 0, 0, ..., 0) trong tọa độ Cartesian.

**Định nghĩa (Nhóm Đồng luân Bậc n):**  
Cho X là một không gian tô-pô và $x_0$ ∈ X là một điểm cơ sở. Một **ánh xạ dựa trên điểm cơ sở** (based map) là một ánh xạ liên tục f: $S^n$ → X sao cho f($s_0$) = $x_0$, trong đó $s_0$ là điểm cơ sở của $S^n$. Hai ánh xạ dựa trên điểm cơ sở f và g được gọi là **đồng luân dựa trên điểm cơ sở** (based homotopic) nếu tồn tại một đồng luân H: $S^n$ × [0,1] → X sao cho H_t($s_0$) = $x_0$ cho mọi t ∈ [0,1], nghĩa là điểm cơ sở luôn được giữ cố định trong suốt quá trình biến dạng.

Nhóm đồng luân bậc n $\pi_n$(X, $x_0$) được định nghĩa là tập hợp tất cả các lớp đồng luân [f] của các ánh xạ dựa trên điểm cơ sở từ $S^n$ vào X. Đây là một cách tự nhiên để khái quát hóa fundamental group: trong khi $\pi_1$ đo lường cách các đường cong một chiều có thể quấn quanh không gian, $\pi_n$ đo lường cách các "bề mặt" n chiều có thể được ánh xạ vào không gian.

Một cách định nghĩa tương đương nhưng đôi khi hữu ích hơn về mặt tính toán là sử dụng các khối lập phương thay vì hình cầu. Chúng ta có thể định nghĩa $\pi_n$(X, $x_0$) như tập hợp các lớp đồng luân của các ánh xạ từ khối lập phương n chiều $I^n$ vào X, với điều kiện toàn bộ biên ∂$I^n$ của khối lập phương được ánh xạ tới điểm cơ sở $x_0$. Hai định nghĩa này tương đương vì có một phép đồng phôi tự nhiên giữa $I^n$/∂$I^n$ và $S^n$—chúng ta có thể co rút biên của khối lập phương thành một điểm để tạo ra một hình cầu. Định nghĩa bằng khối lập phương thường thuận tiện hơn trong các chứng minh vì nó cho phép chúng ta chia khối lập phương thành các phần nhỏ hơn và xây dựng các ánh xạ từng phần.

$$
\pi_n(X, x_0) = [(I^n, \partial I^n), (X, x_0)]
$$

Cách nhìn này làm rõ ý tưởng rằng chúng ta đang nghiên cứu cách một "khối" n chiều có thể được ánh xạ vào không gian trong khi biên của nó được giữ cố định tại điểm cơ sở. Điều này có một cách giải thích hình học đẹp: chúng ta đang hỏi về các cách khác nhau để "điền đầy" một hình cầu n chiều trong không gian X, với điều kiện điểm cơ sở được giữ cố định.

---

### 2. Cấu trúc Nhóm và Phép Cộng

Để $\pi_n$(X, $x_0$) trở thành một nhóm, chúng ta cần định nghĩa một phép toán hai ngôi trên tập hợp các lớp đồng luân. Phép toán này được gọi là phép cộng, và nó được xây dựng bằng cách sử dụng một kỹ thuật hình học gọi là "pinch map" hoặc "suspension". Ý tưởng cơ bản là chúng ta muốn "kết hợp" hai ánh xạ từ $S^n$ vào X để tạo ra một ánh xạ mới, và cách tự nhiên để làm điều này là chia hình cầu thành hai phần và ánh xạ mỗi phần bằng một trong hai ánh xạ ban đầu.

Cách xây dựng cụ thể như sau. Nhớ lại rằng chúng ta có thể xem $S^n$ như là thương của khối lập phương $I^n$ bằng cách co rút biên của nó thành một điểm. Bây giờ, hãy chia khối lập phương $I^n$ thành hai nửa dọc theo tọa độ đầu tiên: nửa đầu tương ứng với các điểm có tọa độ đầu tiên trong [0, 1/2], và nửa thứ hai tương ứng với các điểm có tọa độ đầu tiên trong [1/2, 1]. Chúng ta định nghĩa ánh xạ tổng f + g bằng cách ánh xạ nửa đầu bằng f (sau khi co giãn nó để phù hợp với toàn bộ khối lập phương) và ánh xạ nửa thứ hai bằng g (cũng sau khi co giãn). Hai nửa này gặp nhau tại mặt phẳng tọa độ đầu tiên bằng 1/2, và tại đó cả hai ánh xạ đều ánh xạ tới điểm cơ sở $x_0$ (vì biên của khối lập phương được ánh xạ tới $x_0$), vì vậy chúng có thể được "dán" lại với nhau một cách liên tục.

![Group operation](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Sum_in_homotopy_groups.svg/400px-Sum_in_homotopy_groups.svg.png)  
*Phép cộng trong $\pi_n$ được xây dựng bằng cách chia hình cầu thành hai phần và ánh xạ mỗi phần bằng một trong hai ánh xạ ban đầu - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Sum_in_homotopy_groups.svg)*

Phép toán này có các tính chất của một nhóm. Phần tử đơn vị là lớp đồng luân của ánh xạ hằng [c], trong đó c ánh xạ toàn bộ $S^n$ tới điểm cơ sở $x_0$. Để thấy tại sao đây là phần tử đơn vị, hãy xem xét f + c: chúng ta chia hình cầu thành hai nửa, ánh xạ nửa đầu bằng f và nửa thứ hai bằng ánh xạ hằng. Nhưng ánh xạ hằng có thể được biến dạng liên tục để mở rộng ra toàn bộ nửa thứ hai, và sau đó chúng ta có thể co rút nửa thứ hai này thành một điểm trong khi giữ nửa đầu không đổi. Kết quả là chúng ta thu được một ánh xạ đồng luân với f, cho thấy rằng f + c = f.

Phần tử nghịch đảo của [f] được xây dựng bằng cách lấy ánh xạ f và hợp nó với một phép phản chiếu của $S^n$. Cụ thể, chúng ta định nghĩa -f như là ánh xạ thu được bằng cách ánh xạ một điểm trên $S^n$ tới cùng điểm mà f ánh xạ điểm đối diện của nó (qua phép phản chiếu qua điểm cơ sở). Để thấy tại sao đây là phần tử nghịch đảo, hãy xem xét f + (-f): chúng ta chia hình cầu thành hai nửa và ánh xạ chúng bằng f và -f tương ứng. Nhưng vì -f là phản chiếu của f, chúng ta có thể biến dạng liên tục ánh xạ này để nó trở thành ánh xạ hằng trên toàn bộ hình cầu, cho thấy rằng f + (-f) = 0.

Tính kết hợp (f + g) + h = f + (g + h) được chứng minh bằng cách quan sát rằng cả hai biểu thức đều có thể được biến dạng liên tục thành một ánh xạ chia hình cầu thành ba phần bằng nhau và ánh xạ mỗi phần bằng f, g, và h tương ứng. Chi tiết kỹ thuật liên quan đến việc điều chỉnh các tham số của phép chia và sử dụng tính liên tục của các đồng luân.

Với những tính chất này, $\pi_n$(X, $x_0$) trở thành một nhóm, với phép cộng làm phép toán nhóm. Đây là một khái quát hóa tự nhiên của fundamental group $\pi_1$, và trong trường hợp n = 1, chúng ta thực sự thu được cùng một cấu trúc như fundamental group mà chúng ta đã nghiên cứu trước đó.

---

### 3. Tính Giao hoán và Lý luận Eckmann-Hilton

Một trong những tính chất quan trọng nhất của các nhóm đồng luân bậc cao là chúng là abelian (giao hoán) cho mọi $n \geq 2$. Đây là một sự khác biệt cơ bản so với fundamental group $\pi_1$, có thể không giao hoán như chúng ta đã thấy trong các ví dụ như fundamental group của một hình xuyến hoặc một không gian với nhiều lỗ. Tính chất này có một cách giải thích hình học sâu sắc và đẹp đẽ, được thể hiện qua lý luận Eckmann-Hilton.

**Định lý (Eckmann-Hilton):**  
Cho $n \geq 2$, nhóm đồng luân $\pi_n$(X, $x_0$) là **abelian**, nghĩa là [f] + [g] = [g] + [f] cho mọi [f], [g] ∈ $\pi_n$(X, $x_0$).

Ý tưởng cốt lõi của chứng minh là quan sát rằng trong không gian nhiều chiều ($n \geq 2$), có đủ "chỗ" để các đường cong và bề mặt trượt qua nhau một cách liên tục. Hãy xem xét cách chúng ta định nghĩa phép cộng: [f] + [g] được xây dựng bằng cách chia hình cầu $S^n$ thành hai nửa dọc theo tọa độ đầu tiên, ánh xạ nửa đầu bằng f và nửa thứ hai bằng g. Ngược lại, [g] + [f] được xây dựng bằng cách chia hình cầu theo cùng cách nhưng ánh xạ nửa đầu bằng g và nửa thứ hai bằng f.

Bây giờ, điểm then chốt là: vì $n \geq 2$, hình cầu $S^n$ có đủ chiều để chúng ta có thể xoay cấu hình này một cách liên tục. Cụ thể, chúng ta có thể xây dựng một đồng luân biến đổi [f] + [g] thành [g] + [f] bằng cách xoay cách chia hình cầu. Hãy tưởng tượng chúng ta chia hình cầu thành bốn phần thay vì hai phần: hai phần ở "cực bắc" và hai phần ở "cực nam". Ban đầu, chúng ta ánh xạ phần cực bắc bằng f và phần cực nam bằng g. Sau đó, chúng ta có thể xoay cách chia này một cách liên tục để cuối cùng phần cực bắc được ánh xạ bằng g và phần cực nam được ánh xạ bằng f. Điều này hoạt động vì trong không gian nhiều chiều, các "đường phân chia" này có thể trượt qua nhau mà không cắt nhau—một điều không thể xảy ra trong không gian một chiều.

![Eckmann-Hilton argument visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Sum_in_homotopy_groups.svg/400px-Sum_in_homotopy_groups.svg.png)  
*Lý luận Eckmann-Hilton dựa trên khả năng xoay và trượt các cấu hình trong không gian nhiều chiều - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Sum_in_homotopy_groups.svg)*

Tại sao điều này không hoạt động cho n = 1? Khi n = 1, $S^1$ là một đường tròn một chiều. Khi chúng ta chia đường tròn thành hai nửa và ánh xạ chúng bằng f và g, hai nửa này gặp nhau tại hai điểm (đầu và cuối của mỗi nửa). Để hoán đổi thứ tự, chúng ta sẽ cần "vượt qua" điểm gặp nhau này, nhưng trong không gian một chiều, không có cách nào để làm điều này mà không làm gián đoạn tính liên tục của ánh xạ. Đây là lý do tại sao fundamental group $\pi_1$ có thể không giao hoán—các đường cong một chiều không thể "trượt qua" nhau trong không gian một chiều.

Một cách chính thức hơn để hiểu điều này là quan sát rằng phép cộng trong $\pi_n$ có thể được định nghĩa theo hai cách tương đương: một cách sử dụng tọa độ đầu tiên để chia hình cầu, và cách khác sử dụng bất kỳ tọa độ nào khác. Lý luận Eckmann-Hilton cho thấy rằng hai cách định nghĩa này phải trùng nhau, và điều này buộc phép toán phải giao hoán. Chi tiết kỹ thuật liên quan đến việc xây dựng một đồng luân rõ ràng giữa hai cách kết hợp này, sử dụng tính chất rằng trong không gian nhiều chiều, chúng ta có thể điều chỉnh các tham số của phép chia một cách liên tục.

**Hệ quả:** Với $n \geq 2$, $\pi_n(X)$ là một **nhóm abelian**, và thường được viết theo ký hiệu cộng thay vì nhân. Điều này làm cho cấu trúc đại số của các nhóm đồng luân bậc cao đơn giản hơn nhiều so với fundamental group, và cho phép chúng ta áp dụng nhiều công cụ từ lý thuyết nhóm abelian, chẳng hạn như cấu trúc của các nhóm abelian hữu hạn sinh và các định lý về các nhóm abelian tự do.

---

### 4. Độc lập với Điểm Cơ sở

Một tính chất quan trọng khác của các nhóm đồng luân là chúng không phụ thuộc vào việc chọn điểm cơ sở, miễn là không gian là liên thông đường. Điều này có nghĩa là nếu chúng ta chọn hai điểm cơ sở khác nhau $x_0$ và $x_1$ trong cùng một thành phần liên thông đường, thì các nhóm $\pi_n$(X, $x_0$) và $\pi_n$(X, $x_1$) sẽ đẳng cấu với nhau, mặc dù có thể không đồng nhất.

**Định lý:** Nếu X là một không gian liên thông đường, thì với mọi hai điểm cơ sở $x_0$, $x_1$ ∈ X, các nhóm $\pi_n$(X, $x_0$) và $\pi_n$(X, $x_1$) đẳng cấu với nhau.

Chứng minh của định lý này tương tự như chứng minh cho fundamental group. Ý tưởng là sử dụng một đường cong γ từ $x_0$ đến $x_1$ để xây dựng một đẳng cấu giữa hai nhóm. Cụ thể, cho một ánh xạ dựa trên điểm cơ sở f: ($S^n$, $s_0$) → (X, $x_0$), chúng ta có thể "dán" đường cong γ vào đầu và cuối của ánh xạ để tạo ra một ánh xạ mới f': ($S^n$, $s_0$) → (X, $x_1$). Ánh xạ này được định nghĩa bằng cách đi dọc theo γ từ $x_0$ đến $x_1$, sau đó đi theo f, và cuối cùng đi ngược lại dọc theo γ từ $x_1$ về $x_0$. Vì chúng ta đang làm việc với các lớp đồng luân, chúng ta có thể co rút đường cong γ thành một điểm trong khi giữ điểm cơ sở cố định, cho thấy rằng ánh xạ này thực sự là một ánh xạ dựa trên điểm cơ sở tại $x_1$.

Ánh xạ này cảm sinh một đồng cấu nhóm từ $\pi_n$(X, $x_0$) đến $\pi_n$(X, $x_1$), và bằng cách sử dụng đường cong ngược lại từ $x_1$ đến $x_0$, chúng ta có thể xây dựng một đồng cấu ngược lại. Hai đồng cấu này là nghịch đảo của nhau, cho thấy rằng chúng là các đẳng cấu.

Điều này có nghĩa là đối với các không gian liên thông đường, chúng ta thường có thể viết $\pi_n(X)$ mà không cần chỉ định điểm cơ sở, vì tất cả các điểm cơ sở trong cùng một thành phần liên thông đường đều cho cùng một nhóm (lên đến đẳng cấu). Tuy nhiên, điều quan trọng cần lưu ý là đẳng cấu này không phải là tự nhiên—nó phụ thuộc vào việc chọn đường cong γ. Nếu không gian có fundamental group không tầm thường, thì các đẳng cấu khác nhau có thể được cảm sinh bởi các đường cong khác nhau, và chúng có thể khác nhau bởi một tự đẳng cấu trong của $\pi_n$(X, $x_0$) được cảm sinh bởi một phần tử của $\pi_1$(X, $x_0$).

---

## 📊 Ví dụ và Tính toán

Bây giờ chúng ta sẽ khám phá một số ví dụ cơ bản về các nhóm đồng luân bậc cao. Những ví dụ này sẽ giúp chúng ta hiểu cách các nhóm này hoạt động và tại sao việc tính toán chúng lại khó khăn đến vậy.

### Ví dụ 1: Không gian Một Điểm

Trường hợp đơn giản nhất là khi X chỉ là một điểm duy nhất, ký hiệu là {pt}. Trong trường hợp này, mọi ánh xạ từ $S^n$ vào {pt} đều phải là ánh xạ hằng, vì không có điểm nào khác để ánh xạ tới. Do đó, chỉ có một lớp đồng luân duy nhất, và nhóm đồng luân bậc n của một điểm là nhóm tầm thường: **$\pi_n$(pt) = 0** cho mọi $n \geq 1$. Điều này có ý nghĩa trực quan: một điểm không có "cấu trúc" nào để các hình cầu có thể quấn quanh hoặc phát hiện, vì vậy tất cả các ánh xạ đều tương đương với ánh xạ hằng.

---

### Ví dụ 2: Không gian Co rút được

Một không gian được gọi là co rút được (contractible) nếu nó đồng luân tương đương với một điểm. Điều này có nghĩa là tồn tại một đồng luân liên tục biến đổi không gian thành một điểm. Các ví dụ điển hình bao gồm không gian Euclid $\mathbb{R}^n$, đĩa n chiều $D^n$, và các hình nón (cones) của bất kỳ không gian nào.

Một tính chất quan trọng của các nhóm đồng luân là chúng được bảo toàn bởi các tương đương đồng luân: nếu hai không gian đồng luân tương đương, thì các nhóm đồng luân tương ứng của chúng đẳng cấu với nhau. Do đó, nếu X là một không gian co rút được, thì $\pi_n(X)$ ≅ $\pi_n$(pt) = 0 cho mọi $n \geq 1$. Điều này có nghĩa là một không gian co rút được không có "lỗ" ở bất kỳ chiều nào—mọi hình cầu đều có thể được co rút liên tục thành một điểm trong không gian.

Đây là một kết quả mạnh mẽ và trực quan: nếu một không gian có thể được "co rút" thành một điểm, thì không có cách nào để một hình cầu quấn quanh một cấu trúc không tầm thường, vì toàn bộ không gian có thể được biến dạng liên tục thành một điểm duy nhất.

---

### Ví dụ 3: $\pi_n$($S^n$) = $\mathbb{Z}$ - Trường hợp Cơ bản

Một trong những ví dụ quan trọng nhất là tính toán $\pi_n$($S^n$), nhóm đồng luân bậc n của chính hình cầu n chiều. Kết quả đẹp đẽ và cơ bản là **$\pi_n$($S^n$) ≅ $\mathbb{Z}$**, nhóm các số nguyên với phép cộng.

Để hiểu tại sao điều này đúng, chúng ta cần khái niệm về bậc (degree) của một ánh xạ từ $S^n$ vào chính nó. Bậc của một ánh xạ f: $S^n$ → $S^n$ là một số nguyên đo lường "số lần" ánh xạ này bao phủ hình cầu đích. Cụ thể, nếu chúng ta chọn một điểm y trên $S^n$ và đếm số điểm trong nghịch ảnh f⁻¹(y) (với các dấu hiệu phù hợp), chúng ta thu được một số nguyên không phụ thuộc vào việc chọn y. Số nguyên này được gọi là bậc của f, ký hiệu là deg(f).

Ánh xạ đồng nhất id: $S^n$ → $S^n$ có bậc 1, và nó tạo ra nhóm $\pi_n$($S^n$). Mọi ánh xạ f: $S^n$ → $S^n$ có một bậc d ∈ $\mathbb{Z}$, và hai ánh xạ có cùng bậc thì đồng luân với nhau. Ngược lại, hai ánh xạ đồng luân thì có cùng bậc. Do đó, có một tương ứng một-một giữa các lớp đồng luân [f] và các số nguyên d = deg(f).

Hơn nữa, phép cộng trong $\pi_n$($S^n$) tương ứng với phép cộng các bậc: deg(f + g) = deg(f) + deg(g). Điều này có thể được thấy bằng cách quan sát rằng khi chúng ta kết hợp hai ánh xạ bằng cách chia hình cầu thành hai nửa, tổng số lần bao phủ của ánh xạ tổng bằng tổng số lần bao phủ của hai ánh xạ thành phần. Do đó, ánh xạ gửi [f] tới deg(f) là một đẳng cấu nhóm từ $\pi_n$($S^n$) đến $\mathbb{Z}$.

Kết quả này có một cách giải thích hình học đẹp: lớp đồng luân của ánh xạ đồng nhất tương ứng với số nguyên 1, và bằng cách "quấn" hình cầu quanh chính nó nhiều lần (theo hướng thuận hoặc ngược), chúng ta có thể tạo ra bất kỳ số nguyên nào. Đây là một khái quát hóa tự nhiên của kết quả cho fundamental group $\pi_1$($S^1$) = $\mathbb{Z}$, nơi chúng ta đo lường số lần một đường cong quấn quanh đường tròn.

---

### Ví dụ 4: $\pi_k$($S^n$) khi $k < n$ - Không có Quấn quanh

Một kết quả quan trọng khác là khi chúng ta cố gắng ánh xạ một hình cầu có chiều thấp hơn vào một hình cầu có chiều cao hơn. Cụ thể, **định lý** phát biểu rằng nếu $k < n$, thì $\pi_k$($S^n$) = 0.

Để hiểu tại sao điều này đúng, hãy xem xét một ánh xạ f: $S^k$ → $S^n$ với $k < n$. Ảnh của ánh xạ này là một tập hợp con k chiều của $S^n$, một không gian n chiều. Điều quan trọng là trong một không gian nhiều chiều, một tập hợp con có chiều thấp hơn có thể được "đẩy ra" khỏi bất kỳ điểm nào. Cụ thể, vì ảnh của f có chiều k nhỏ hơn n, chúng ta có thể liên tục dịch chuyển nó để tránh điểm cơ sở của $S^n$ (hoặc bất kỳ điểm nào khác).

Một khi chúng ta đã dịch chuyển ảnh ra khỏi điểm cơ sở, chúng ta có thể co rút nó thành một điểm trong khi giữ điểm cơ sở cố định. Điều này có thể được thực hiện vì $S^n$ \ {point} là co rút được—chúng ta có thể liên tục co rút toàn bộ hình cầu trừ một điểm thành một điểm khác. Do đó, mọi ánh xạ f: $S^k$ → $S^n$ với $k < n$ đều đồng luân với ánh xạ hằng, cho thấy rằng $\pi_k$($S^n$) = 0.

Trực giác hình học đằng sau kết quả này là một hình cầu có chiều thấp hơn không thể "quấn quanh" một hình cầu có chiều cao hơn theo cách không tầm thường. Ví dụ, một đường tròn ($S^1$) không thể quấn quanh một mặt cầu ($S^2$) theo cách tạo ra một lớp đồng luân không tầm thường—bất kỳ đường tròn nào trên mặt cầu đều có thể được co rút thành một điểm. Tương tự, một mặt cầu hai chiều không thể quấn quanh một hình cầu ba chiều theo cách không tầm thường.

---

### Ví dụ 5: $\pi_k$($S^n$) khi $k > n$ - Bí ẩn và Sự Phức tạp

Đây là nơi mọi thứ trở nên thú vị và bất ngờ! Khi chúng ta cố gắng ánh xạ một hình cầu có chiều cao hơn vào một hình cầu có chiều thấp hơn, kết quả không phải lúc nào cũng tầm thường như người ta có thể mong đợi. Trong thực tế, đây là một trong những lĩnh vực sâu sắc và khó khăn nhất của topology đại số.

Ví dụ kinh điển và đẹp đẽ nhất là **$\pi_3(S^2)$ = $\mathbb{Z}$**. Điều này đáng ngạc nhiên vì $S^3$ có chiều 3 lớn hơn chiều 2 của $S^2$, nhưng vẫn tồn tại các ánh xạ không tầm thường từ $S^3$ vào $S^2$! Ánh xạ quan trọng nhất trong trường hợp này là **Hopf fibration**, một cấu trúc hình học đẹp đẽ ánh xạ $S^3$ vào $S^2$ với các thớ (fibers) là các đường tròn $S^1$. Hopf fibration này là một generator của nhóm $\pi_3(S^2)$, và nó minh họa một cách hoàn hảo cách một không gian có chiều cao hơn có thể được ánh xạ vào một không gian có chiều thấp hơn theo cách không tầm thường.

![Hopf fibration](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/Hopf_Fibration_showing_Hopf_coordinate_system.png/500px-Hopf_Fibration_showing_Hopf_coordinate_system.png)  
*Hopf fibration - một cấu trúc hình học đẹp đẽ ánh xạ $S^3$ vào $S^2$, minh họa cách các không gian nhiều chiều có thể được tổ chức theo những cách phức tạp - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hopf_Fibration_showing_Hopf_coordinate_system.png)*

Nhưng những bất ngờ không dừng lại ở đó. Khi chúng ta tiếp tục khám phá, chúng ta gặp phải các nhóm đồng luân có cấu trúc phức tạp hơn. Ví dụ, **$\pi_4(S^3)$ = $\mathbb{Z}/2\mathbb{Z}$**, nhóm cyclic có hai phần tử. Điều này có nghĩa là có một ánh xạ không tầm thường từ S⁴ vào $S^3$, nhưng khi chúng ta kết hợp nó với chính nó, chúng ta thu được ánh xạ hằng. Tương tự, **$\pi_5$($S^3$) = $\mathbb{Z}/2\mathbb{Z}$**, cho thấy một mẫu hình phức tạp đang xuất hiện.

Nhưng có một mẫu hình không? Câu trả lời là có và không. Định lý Freudenthal Suspension cho chúng ta một số hy vọng: trong một "stable range", các nhóm đồng luân bắt đầu ổn định. Cụ thể, **định lý Freudenthal Suspension** phát biểu rằng với k ≤ 2n - 2, chúng ta có:

$$
\pi_{n+k}(S^n) = \pi_{n+k+1}(S^{n+1})
$$

Điều này có nghĩa là khi chúng ta tăng chiều của hình cầu đích, các nhóm đồng luân cuối cùng sẽ ổn định. Các nhóm ổn định này được gọi là **stable homotopy groups of spheres** và được ký hiệu là $\pi_k$^s. Chúng có cấu trúc đại số phong phú và kết nối sâu sắc với nhiều lĩnh vực khác của toán học, bao gồm cobordism theory và K-theory.

Tuy nhiên, ngay cả trong stable range, việc tính toán các nhóm này vẫn cực kỳ khó khăn. Hầu hết các giá trị vẫn chưa được biết, và không có công thức đơn giản nào để tính toán chúng. Đây là một lĩnh vực nghiên cứu tích cực với những kết nối sâu sắc với đại số, hình học và vật lý lý thuyết. Việc tính toán stable homotopy groups của các hình cầu là một trong những bài toán mở quan trọng nhất trong topology đại số hiện đại.

---

### Ví dụ 6: $\pi_n$($S^1$) - Trường hợp Đặc biệt

Một ví dụ quan trọng khác là tính toán $\pi_n$($S^1$), các nhóm đồng luân bậc cao của đường tròn. Đường tròn $S^1$ có một tính chất đặc biệt: nó là một Eilenberg-MacLane space K($\mathbb{Z}$, 1), có nghĩa là nó có fundamental group là $\mathbb{Z}$ và tất cả các nhóm đồng luân bậc cao đều tầm thường.

Cụ thể, chúng ta có **$\pi_1$($S^1$) = $\mathbb{Z}$**, như chúng ta đã biết từ việc nghiên cứu fundamental group. Tuy nhiên, **$\pi_n$($S^1$) = 0** cho mọi $n \geq 2$. Để hiểu tại sao điều này đúng, chúng ta có thể sử dụng covering space ℝ → $S^1$. Không gian phủ ℝ là co rút được, và mọi ánh xạ từ $S^n$ (với $n \geq 2$) vào $S^1$ có thể được nâng lên thành một ánh xạ vào ℝ. Vì ℝ là co rút được, ánh xạ nâng này đồng luân với ánh xạ hằng, và do đó ánh xạ ban đầu vào $S^1$ cũng đồng luân với ánh xạ hằng.

Một cách giải thích hình học là đường tròn $S^1$ có thể được coi như không gian thương của đường thẳng ℝ dưới tác động của nhóm $\mathbb{Z}$ (dịch chuyển theo các bội số nguyên). Khi chúng ta cố gắng ánh xạ một hình cầu nhiều chiều vào đường tròn, chúng ta có thể "nâng" ánh xạ này lên đường thẳng, nơi nó có thể được co rút thành một điểm. Điều này cho thấy rằng đường tròn không có "cấu trúc" ở các chiều cao hơn—tất cả các nhóm đồng luân bậc cao đều tầm thường.

---

## 🔗 Các Định lý Cơ bản

Các nhóm đồng luân bậc cao không chỉ là các bất biến hữu ích—chúng còn có những tính chất sâu sắc kết nối chúng với cấu trúc đồng luân của không gian. Trong phần này, chúng ta sẽ khám phá hai định lý cơ bản nhất: Whitehead Theorem và Hurewicz Theorem. Những định lý này cho thấy sức mạnh của các nhóm đồng luân như các bất biến và cách chúng liên quan với các bất biến khác như homology.

### 1. Định lý Whitehead - Bất biến Hoàn chỉnh

Một trong những kết quả quan trọng nhất về các nhóm đồng luân là định lý Whitehead, được đặt tên theo nhà toán học J.H.C. Whitehead. Định lý này phát biểu rằng đối với các phức CW, các nhóm đồng luân là các bất biến hoàn chỉnh—nếu tất cả các nhóm đồng luân của hai không gian đẳng cấu với nhau, thì hai không gian đó đồng luân tương đương.

**Định lý (J.H.C. Whitehead):**  
Cho f: X → Y là một ánh xạ liên tục giữa các phức CW. Nếu f cảm sinh các đẳng cấu:

$$
f_* : \pi_n(X) \xrightarrow{\cong} \pi_n(Y) \quad \forall n \geq 0
$$

thì **f là một tương đương đồng luân**.

Ý nghĩa của định lý này là sâu sắc: nếu một ánh xạ cảm sinh đẳng cấu trên tất cả các nhóm đồng luân, thì chính ánh xạ đó phải là một tương đương đồng luân. Điều này có nghĩa là các nhóm đồng luân, khi được xem xét cùng nhau, chứa đựng tất cả thông tin về kiểu đồng luân của không gian. Nếu hai không gian có tất cả các nhóm đồng luân đẳng cấu với nhau, thì chúng phải đồng luân tương đương.

Đây là một kết quả mạnh mẽ mà homology không thể cung cấp. Có những không gian có cùng homology nhưng không đồng luân tương đương—homology mất mát thông tin về cấu trúc đồng luân của không gian. Ví dụ, có những không gian có cùng homology nhưng khác nhau về fundamental group hoặc các nhóm đồng luân bậc cao. Định lý Whitehead cho thấy rằng các nhóm đồng luân là một bất biến tinh tế hơn—chúng nắm bắt nhiều thông tin hơn về cấu trúc đồng luân của không gian.

Tuy nhiên, điều quan trọng cần lưu ý là định lý này chỉ áp dụng cho các phức CW. Đối với các không gian tổng quát hơn, có thể có các ánh xạ cảm sinh đẳng cấu trên tất cả các nhóm đồng luân nhưng không phải là tương đương đồng luân. Nhưng đối với hầu hết các không gian mà chúng ta quan tâm trong topology đại số, định lý Whitehead cung cấp một công cụ mạnh mẽ để xác định xem hai không gian có đồng luân tương đương hay không.

---

### 2. Định lý Hurewicz - Kết nối với Homology

Một trong những kết quả quan trọng nhất kết nối các nhóm đồng luân với homology là định lý Hurewicz, được đặt tên theo nhà toán học Witold Hurewicz. Định lý này cho thấy rằng trong một số điều kiện nhất định, nhóm đồng luân đầu tiên không tầm thường đẳng cấu với nhóm homology tương ứng. Đây là một công cụ mạnh mẽ vì homology thường dễ tính toán hơn các nhóm đồng luân.

**Định lý (Hurewicz):**  
Cho X là một không gian liên thông đường.

**Phần 1:** Nếu $\pi_1$(X) là abelian, thì tồn tại một đồng cấu nhóm tự nhiên:

$$
h : \pi_1(X) \to H_1(X)
$$

được định nghĩa bằng cách gửi một lớp đồng luân của một đường cong đóng tới lớp homology của nó. Đồng cấu này là **toàn ánh**, và kernel của nó là nhóm con giao hoán tử của $\pi_1$(X). Do đó, $H_1$(X) đẳng cấu với abelianization của $\pi_1$(X), tức là $\pi_1$(X) chia cho nhóm con giao hoán tử của nó.

**Phần 2 (Hurewicz Bậc cao):**  
Cho X là một không gian đơn liên (simply connected) và $n \geq 2$. Định nghĩa **ánh xạ Hurewicz**:

$$
h_n : \pi_n(X) \to $H_n(X)$
$$

bằng cách gửi một lớp đồng luân [f] của một ánh xạ f: $S^n$ → X tới lớp homology f_*([$S^n$]) ∈ $H_n(X)$, trong đó [$S^n$] là lớp cơ bản của $S^n$ trong $H_n$($S^n$) ≅ $\mathbb{Z}$.

**Định lý:** Nếu $\pi_k$(X) = 0 cho mọi $k < n$, thì ánh xạ Hurewicz:

$$
h_n : \pi_n(X) \xrightarrow{\cong} $H_n(X)$
$$

là một **đẳng cấu**.

Ý nghĩa của định lý này là sâu sắc: nếu một không gian đơn liên có tất cả các nhóm đồng luân bậc thấp hơn n đều tầm thường, thì nhóm đồng luân đầu tiên không tầm thường $\pi_n(X)$ đẳng cấu với nhóm homology $H_n(X)$. Điều này có nghĩa là trong trường hợp này, homology và homotopy trùng nhau ở bậc đầu tiên không tầm thường.

**Ứng dụng:** Nếu $X$ là một không gian đơn liên với $\pi_2 = \pi_3 = \cdots = \pi_{n-1} = 0$, thì $\pi_n(X) \cong H_n(X)$. Điều này cho phép chúng ta tính toán nhóm đồng luân đầu tiên không tầm thường bằng cách tính toán homology, thường dễ dàng hơn nhiều.

**Ví dụ:** $S^2$ là đơn liên và $\pi_2(S^2)$ là nhóm đồng luân đầu tiên không tầm thường. Định lý Hurewicz cho thấy rằng $\pi_2(S^2)$ ≅ $H_2(S^2)$ ≅ $\mathbb{Z}$, một kết quả mà chúng ta đã biết từ trước.

Tuy nhiên, điều quan trọng cần lưu ý là định lý Hurewicz chỉ áp dụng cho nhóm đồng luân đầu tiên không tầm thường. Sau đó, homology và homotopy có thể phân kỳ. Ví dụ, **$\pi_3(S^2)$ ≠ $H_3(S^2)$**—chúng ta có $\pi_3(S^2)$ = $\mathbb{Z}$ (nhờ Hopf fibration) nhưng $H_3(S^2)$ = 0 vì $S^2$ là một không gian hai chiều. Điều này cho thấy rằng homology chỉ "xấp xỉ" homotopy lên đến nhóm đồng luân đầu tiên không tầm thường—sau đó, các nhóm đồng luân có thể có cấu trúc phức tạp hơn nhiều so với homology.

---

### 3. Dãy Khớp Dài của Fibration

Một công cụ tính toán mạnh mẽ khác là dãy khớp dài của một fibration. Một fibration là một cấu trúc tương tự như fiber bundle, trong đó chúng ta có một ánh xạ p: E → B với tính chất rằng mọi điểm trong B có một lân cận U sao cho p⁻¹(U) đồng phôi với U × F, trong đó F là không gian thớ (fiber). Ký hiệu F → E → B để chỉ một fibration với thớ F, tổng không gian E, và không gian cơ sở B.

**Định lý:** Một fibration F → E → B cảm sinh một dãy khớp dài:

$$
\cdots \to \pi_n(F) \to \pi_n(E) \to \pi_n(B) \xrightarrow{\partial} \pi_{n-1}(F) \to \cdots
$$

Dãy này là một công cụ tính toán mạnh mẽ vì nó cho phép chúng ta tính toán các nhóm đồng luân của một không gian từ các nhóm đồng luân của các không gian liên quan. Cụ thể, nếu chúng ta biết các nhóm đồng luân của F và B, chúng ta có thể sử dụng dãy khớp dài để tính toán các nhóm đồng luân của E.

**Ví dụ (Hopf fibration):**  
Một ví dụ kinh điển là Hopf fibration $S^1$ → $S^3$ → $S^2$. Dãy khớp dài cho chúng ta:

$$
\pi_3(S^1) \to \pi_3(S^3) \to \pi_3(S^2) \xrightarrow{\partial} \pi_2(S^1)
$$

Chúng ta biết rằng $\pi_3$($S^1$) = 0 (vì $S^1$ là K($\mathbb{Z}$, 1)), $\pi_3$($S^3$) = $\mathbb{Z}$ (từ Ví dụ 3), và $\pi_2$($S^1$) = 0. Do đó, dãy khớp dài trở thành:

$$
0 \to \mathbb{Z} \to \pi_3(S^2) \to 0
$$

Tính khớp của dãy này cho thấy rằng ánh xạ từ $\mathbb{Z}$ vào $\pi_3(S^2)$ phải là một đẳng cấu, do đó **$\pi_3(S^2)$ ≅ $\mathbb{Z}$**. Đây là một cách tính toán đẹp đẽ và elegant của kết quả quan trọng này mà không cần phải xây dựng trực tiếp Hopf fibration.

---

## 🧮 Thách thức Tính toán

Việc tính toán các nhóm đồng luân bậc cao là một trong những bài toán khó khăn nhất trong topology đại số. Ngay cả việc tính toán $\pi_n$($S^m$) cho các giá trị nhỏ của n và m cũng đòi hỏi những kỹ thuật tinh vi và sâu sắc. Trong phần này, chúng ta sẽ khám phá tại sao việc tính toán các nhóm này lại khó khăn đến vậy và một số kết quả đã biết.

### Tại sao $\pi_n$($S^m$) lại Khó Tính?

Có nhiều lý do tại sao việc tính toán các nhóm đồng luân bậc cao lại khó khăn đến vậy. Đầu tiên, không có định lý Van Kampen cho các nhóm đồng luân bậc cao—chúng ta không thể phân tích một không gian thành các phần nhỏ hơn và tính toán các nhóm đồng luân từ các phần đó. Điều này khác với fundamental group, nơi chúng ta có thể sử dụng Van Kampen theorem để tính toán $\pi_1$ của một không gian từ $\pi_1$ của các phần của nó.

Thứ hai, không có Mayer-Vietoris sequence cho các nhóm đồng luân. Trong homology, chúng ta có thể sử dụng Mayer-Vietoris sequence để tính toán homology của một không gian từ homology của các phần của nó, nhưng kỹ thuật này không hoạt động cho các nhóm đồng luân. Điều này có nghĩa là chúng ta không có cách nào để "ghép" các nhóm đồng luân từ các phần của không gian.

Thứ ba, các nhóm đồng luân có sự tương tác phức tạp với nhau. Trong obstruction theory, chúng ta thấy rằng $\pi_n$ phụ thuộc vào TẤT CẢ các nhóm đồng luân bậc thấp hơn $\pi_k$ với $k < n$. Điều này có nghĩa là để tính toán $\pi_n$, chúng ta cần biết tất cả các $\pi_k$ trước đó, tạo ra một vấn đề tính toán tích lũy.

Thứ tư, các nhóm đồng luân không ổn định—$\pi_n$($S^m$) thay đổi mạnh mẽ với n và m. Không có công thức đơn giản nào để tính toán chúng, và các mẫu hình chỉ xuất hiện trong stable range, nơi các nhóm bắt đầu ổn định.

Cuối cùng, có một sự tương tác sâu sắc giữa topology và đại số—các nhóm đồng luân không chỉ phụ thuộc vào cấu trúc tô-pô của không gian mà còn vào cấu trúc đại số phức tạp của các nhóm abelian. Không có công thức đơn giản nào để tính toán chúng—mỗi trường hợp đều đòi hỏi những kỹ thuật riêng và sâu sắc.

### Các Kết quả Đã Biết (Mẫu)

Mặc dù có những thách thức này, một số kết quả đã được tính toán. Dưới đây là một bảng một phần cho các giá trị nhỏ:

| n \ m | $S^1$  | $S^2$  | $S^3$    | S⁴    |
|-------|-----|-----|-------|-------|
| 1     | $\mathbb{Z}$   | 0   | 0     | 0     |
| 2     | 0   | $\mathbb{Z}$   | 0     | 0     |
| 3     | 0   | $\mathbb{Z}$   | $\mathbb{Z}$     | 0     |
| 4     | 0   | $\mathbb{Z}$/2 | $\mathbb{Z}$/2   | $\mathbb{Z}$     |
| 5     | 0   | $\mathbb{Z}$/2 | $\mathbb{Z}$/2   | $\mathbb{Z}$/2   |

Như bạn có thể thấy, không có mẫu hình rõ ràng nào—các giá trị thay đổi một cách không thể đoán trước. Hầu hết các mục cho các giá trị lớn của n và m vẫn chưa được biết, và đây là một lĩnh vực nghiên cứu tích cực.

### Stable Homotopy Groups

Một hy vọng đến từ định lý Freudenthal Suspension: trong stable range, các nhóm đồng luân bắt đầu ổn định. Cụ thể, $\pi_{n+k}(S^n)$ ổn định khi $n$ lớn (với $k$ cố định). Các nhóm ổn định này được ký hiệu là $\pi_k^s$ và được định nghĩa là giới hạn:

$$
\pi_k^s = \lim_{n \to \infty} \pi_{n+k}(S^n)
$$

Một số giá trị đã biết:
- $\pi_0^s$ = $\mathbb{Z}$
- $\pi_1$^s = $\mathbb{Z}/2\mathbb{Z}$
- $\pi_2$^s = $\mathbb{Z}/2\mathbb{Z}$
- $\pi_3$^s = $\mathbb{Z}$/24

Ngay cả các stable homotopy groups này cũng cực kỳ khó tính toán, và đây là một lĩnh vực nghiên cứu tích cực với những kết nối sâu sắc với cobordism theory và stable homotopy category. Việc tính toán các stable homotopy groups của các hình cầu là một trong những bài toán mở quan trọng nhất trong topology đại số hiện đại.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Heinz Hopf** - *"Über die Abbildungen der dreidimensionalen Sphäre"* (1931)  
   *Hopf fibration, $\pi_3(S^2)$ = $\mathbb{Z}$*

2. **Witold Hurewicz** - *"Beiträge zur Topologie der Deformationen"* (1935-36)  
   *Hurewicz theorem*

3. **Hans Freudenthal** - *"Über die Klassen der Sphärenabbildungen"* (1937)  
   *Suspension theorem, stable homotopy*

4. **J.H.C. Whitehead** - *"Combinatorial homotopy"* (1949)  
   *Whitehead theorem*

5. **Jean-Pierre Serre** - *"Groupes d'homotopie et classes de groupes abéliens"* (1953)  
   *Computations, spectral sequences*

### Textbooks

6. **Allen Hatcher** - *Algebraic Topology*, **§4.1: Higher Homotopy Groups**

7. **Edwin H. Spanier** - *Algebraic Topology*, **Chapter 7**

8. **Robert M. Switzer** - *Algebraic Topology - Homotopy and Homology*

9. **George W. Whitehead** - *Elements of Homotopy Theory*

---

## 🔗 Applications and Connections

### Obstruction Theory
**Extending Maps:** $\pi_n(Y)$ controls obstructions to extending $f: X^n \to Y$ to $X^{n+1}$. If $\pi_n(Y) = 0$, no obstruction.

### Vector Bundles
**Classification:** Homotopy groups of Grassmannians classify vector bundles. Essential in differential topology.

### Cobordism Theory
**Thom Spaces:** Stable homotopy groups compute (co)bordism rings. Connects topology ↔ smooth manifolds.

### String Theory
**Branes and Wrapping:** Maps $S^n$ → M (target space) = BPS states. Homotopy groups classify wrapping numbers.

### Robotics
**Configuration Spaces:** $\pi_n$ detects higher-dimensional "holes" in configuration spaces. Motion planning algorithms.

---

## Video tham khảo

- **xem trước** [A Sphere is a Loop of Loops (Visualizing Homotopy Groups)](https://www.youtube.com/watch?v=CxGtAuJdjYI) — Dennis Sweeney, tiếng Anh. Hình cầu như một vòng của các vòng, để thấy πₙ trước định nghĩa hình thức.
- [The fundamental group and higher homotopy groups](https://www.youtube.com/watch?v=7RYu7uvomUs) — DanielChanMaths, tiếng Anh. Daniel Chan nối π₁ với các nhóm đồng luân cao hơn, sát phần tính toán của bài.

## 🧩 Exercises

### Definitions

1. **Verify Group:** Check $\pi_n(X)$ satisfies group axioms explicitly for $S^1$.

2. **Abelian:** Explain why $\pi_2$(X) abelian (using "room to rotate").

### Examples

3. **Compute:** $\pi_n$(point) for all n.

4. **Contractible:** $\mathbb{R}^3$ contractible ⇒ $\pi_n$($\mathbb{R}^3$) = ?

5. **$S^1$:** Verify $\pi_n$($S^1$) = 0 for $n \geq 2$ using covering space ℝ → $S^1$.

### Whitehead

6. **Apply:** X, Y CW complexes với $\pi_n(X)$ ≅ $\pi_n$(Y) ∀n. What conclude?

7. **Counterexample:** Homology isomorphism doesn't imply homotopy equivalence. Find example.

### Hurewicz

8. **$S^2$:** Use Hurewicz: $\pi_2(S^2)$ ≅ $H_2(S^2)$ = $\mathbb{Z}$.

9. **Failure:** Why Hurewicz doesn't give $\pi_3(S^2)$? ($H_3(S^2)$ = 0 but $\pi_3$ = $\mathbb{Z}$.)

### Hopf Fibration

10. **Research:** Read about Hopf fibration $S^3$ → $S^2$. Why generator of $\pi_3(S^2)$?

11. **Visualize:** Study visualizations of Hopf fibration. Describe fiber structure.

### Long Exact Sequence

12. **Apply:** $S^1$ → $S^3$ → $S^2$. Use LES to compute $\pi_3(S^2)$ from $\pi_*(S^1)$, $\pi_*(S^3)$.

13. **General:** $F \to E \to B$ fibration. How does $\partial: \pi_n(B) \to \pi_{n-1}(F)$ work?

### Advanced

14. **$\pi_4(S^3)$:** Research how $\pi_4(S^3)$ = $\mathbb{Z}/2\mathbb{Z}$ computed. (Very non-trivial!)

15. **Stable:** What is stable homotopy group $\pi_1$^s? ($\mathbb{Z}/2\mathbb{Z}$ - Hopf element.)

16. **Postnikov Tower:** Research Postnikov towers—kill homotopy groups systematically.

### Reflection

17. **Why Hard?:** List reasons computing $\pi_n$($S^m$) so difficult.

18. **Compare:** $\pi_n$ vs $H_n$. Which easier to compute? Which more information?

19. **Applications:** Where do higher homotopy groups appear in applications?

20. **Open Problems:** Research current open problems in homotopy theory.

---

## 📚 Further Reading

- **Hatcher, §4:** Higher homotopy groups, fibrations
- **Whitehead:** *Elements of Homotopy Theory* (comprehensive)
- **Spanier, Chapter 7:** Detailed theory
- **Switzer:** *Algebraic Topology* (stable homotopy)
- **Ravenel:** *Complex Cobordism and Stable Homotopy Groups* (advanced)

---

## 🎓 Tóm tắt

Các nhóm đồng luân bậc cao $\pi_n$(X, $x_0$) là các bất biến hoàn chỉnh nhưng cực kỳ khó tính toán. Chúng được định nghĩa như các lớp đồng luân của các ánh xạ dựa trên điểm cơ sở từ hình cầu n chiều $S^n$ vào không gian X, và có cấu trúc nhóm được xây dựng thông qua phép cộng dựa trên suspension. Một tính chất quan trọng là $\pi_n$ là abelian cho mọi $n \geq 2$, làm cho cấu trúc đại số của chúng đơn giản hơn nhiều so với fundamental group $\pi_1$. Các ví dụ cơ bản bao gồm $\pi_n$($S^n$) = $\mathbb{Z}$ và $\pi_k$($S^n$) = 0 khi $k < n$, nhưng khi $k > n$, các nhóm đồng luân trở nên cực kỳ khó tính toán và hầu hết các giá trị vẫn chưa được biết.

Định lý Whitehead cho thấy rằng các nhóm đồng luân là các bất biến hoàn chỉnh cho các phức CW—nếu tất cả các nhóm đồng luân của hai không gian đẳng cấu với nhau, thì hai không gian đó đồng luân tương đương. Định lý Hurewicz kết nối các nhóm đồng luân với homology, cho thấy rằng nhóm đồng luân đầu tiên không tầm thường đẳng cấu với nhóm homology tương ứng trong một số điều kiện nhất định. Dãy khớp dài của fibrations là một công cụ tính toán mạnh mẽ, cho phép chúng ta tính toán các nhóm đồng luân của một không gian từ các nhóm đồng luân của các không gian liên quan. Trong stable range, các nhóm đồng luân bắt đầu ổn định theo định lý Freudenthal Suspension, tạo ra các stable homotopy groups $\pi_k$^s có cấu trúc đại số phong phú.

Trực giác hình học đằng sau các nhóm đồng luân bậc cao là chúng phát hiện cách các "bề mặt" n chiều có thể được ánh xạ vào không gian. Trong không gian nhiều chiều, có đủ "chỗ" để các đường cong và bề mặt trượt qua nhau một cách liên tục, cho phép các phép toán giao hoán—đây là lý do tại sao $\pi_n$ là abelian cho $n \geq 2$. Trong stable range, các mẫu hình cuối cùng xuất hiện, và fibrations cung cấp một công cụ tính toán mạnh mẽ để khám phá các mẫu hình này.

Trong thực tế, định lý Whitehead là công cụ chính để xác định xem hai không gian có đồng luân tương đương hay không, trong khi định lý Hurewicz cho phép chúng ta tính toán các nhóm đồng luân từ homology trong một số trường hợp đặc biệt. Fibrations thường là phương pháp thực tế duy nhất để tính toán các nhóm đồng luân, nhưng ngay cả với các công cụ này, hầu hết các giá trị $\pi_n$($S^m$) vẫn chưa được biết—một lời nhắc nhở khiêm tốn về độ phức tạp sâu sắc của topology đại số.

**Tiếp theo:** Fiber Bundles—rich geometric structures!

---

*"Homotopy groups: where spheres become mysteries, and topology meets the unknown."*

🎯 **Master the theory! Computing is an art.** 🎯

---

**Previous Chapter:** [Chapter 07: Homology Theory](/contents/vi/topology-chapter07/)  
**Next:** [Lecture 08.01: Fiber Bundles](/contents/vi/topology-chapter08/08_01_Fiber_Bundles/)
