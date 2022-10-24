# Chapter 3 Mô hình giải quyết vấn đề

## 3.1 Tổng quan và động lực

Trong chương này, chúng ta thảo luận về bốn mô hình giải quyết vấn đề thường được sử dụng để công phá các vấn đề trong các cuộc thi lập trình, đó là 
Complete Search, Divide và Conquer, cách tiếp cận Greedy và Quy hoạch động. Tất cả các lập trình viên thi đấu, bao gồm các thí sinh IOI và ICPC, cần phải nắm 
vững các mô hình giải quyết vấn đề này (và hơn thế nữa) để có thể giải quyết một vấn đề nhất định bằng ‘công cụ’ thích hợp. Xử lý mọi vấn đề với các giải pháp Brute Force 
sẽ không cho phép bất kỳ ai thể hiện tốt trong các cuộc thi. Để minh họa, chúng ta thảo luận bốn tác vụ đơn giản dưới đây liên quan đến mảng A chứa n ≤ 10K số nguyên 
nhỏ ≤ 100K (ví dụ: A = {10, 7, 3, 5, 8, 2, 9}, n = 7) để cung cấp tổng quan về điều gì sẽ xảy ra nếu chúng tôi cố gắng giải quyết mọi vấn đề với Brute Force là mô hình 
duy nhất của chúng tôi.

1. Tìm phần tử lớn nhất và nhỏ nhất của A. (10 và 2 trong ví dụ đã cho).
2. Tìm phần tử nhỏ thứ k trong A. (nếu k = 2 thì kết quả là 3 đối với ví dụ đã cho).
3. Tìm khoảng trống lớn nhất g sao cho x, y ∈ A và g = | x - y |. (8 trong ví dụ đã cho).
4. Tìm dãy con tăng dần dài nhất của A. ({3, 5, 8, 9} trong ví dụ đã cho).

Câu trả lời cho nhiệm vụ đầu tiên rất đơn giản: Hãy thử từng phần tử của A và kiểm tra xem nó có phải là phần tử lớn nhất (hoặc nhỏ nhất) 
được thấy cho đến nay hay không. Đây là một giải pháp Complete Search O(n).

Nhiệm vụ thứ hai khó hơn một chút. Chúng ta có thể sử dụng giải pháp ở trên để tìm giá trị nhỏ nhất và thay thế nó bằng một giá trị lớn 
(ví dụ: 1M) để ‘xóa’ nó. Sau đó chúng ta có thể tiến hành tìm lại giá trị nhỏ nhất (giá trị nhỏ thứ hai trong mảng ban đầu) và thay thế 
bằng 1M. Lặp lại quá trình này k lần, chúng ta sẽ tìm được giá trị nhỏ nhất thứ k. Điều này hoạt động, nhưng nếu k = n/2 (trung vị), giải pháp 
Coplete Search này chạy trong O(n/2 × n) = O(n^2). Thay vào đó, chúng ta có thể sắp xếp mảng A theo O(nlogn), trả về câu trả lời đơn giản là A[k-1]. 
Tuy nhiên, một giải pháp tốt hơn cho một số lượng nhỏ các truy vấn là giải pháp O(n) mong đợi được trình bày trong Phần 9.29. Các nghiệm O(nlogn) và O(n) ở 
trên là các nghiệm Divide và Conquer.

Đối với nhiệm vụ thứ ba, chúng ta có thể xem xét tương tự tất cả hai số nguyên x và y có thể có trong A, kiểm tra xem khoảng cách giữa chúng có 
lớn nhất đối với mỗi cặp hay không. Phương pháp Tìm kiếm Toàn bộ này chạy trong O (n2). Nó hoạt động, nhưng chậm và không hiệu quả. Ta có thể chứng minh 
rằng g có thể nhận được bằng cách tìm hiệu giữa phần tử nhỏ nhất và lớn nhất của A. Hai số nguyên này có thể tìm được với nghiệm của nhiệm vụ đầu tiên 
trong O (n). Không có sự kết hợp nào khác của hai số nguyên trong A có thể tạo ra khoảng cách lớn hơn. Đây là một giải pháp Tham lam.

Đối với nhiệm vụ thứ tư, việc thử tất cả các dãy con có thể có O (2n) để tìm dãy con dài nhất tăng dần là không khả thi với mọi n ≤ 10K. Trong Phần 3.5.2, 
chúng ta thảo luận về giải pháp Lập trình động O (n2) đơn giản và giải pháp Tham lam O (n log k) nhanh hơn cho tác vụ này.