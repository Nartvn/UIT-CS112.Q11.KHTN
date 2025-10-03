# Nhóm 9: Phân tích độ phức tạp thuật toán không đệ quy

Họ và tên: Hà Bùi Trọng Nghĩa <br>
MSSV: 24520020<br>
Nhóm: 8 <br>


Họ và tên: Nguyễn Duy Khang <br>
MSSV: 24520755 <br>
Nhóm: 8
---

## Bài tập 1

Độ phức tạp theo thứ tự tăng dần: $O(1)$ < $O(\log n)$ < $O(n)$ < $O(n \log n)$ < $O(n^2)$ < $O(n^3)$ < $O(2^n)$ < $O(n!)$

## Bài tập 2

$$
\lim_{n \to \infty} \frac{f(n)}{g(n)} = 5 \Rightarrow f(n) = \Theta(g(n))
$$

## Bài tập 3

Gồm các bước: xác định tham số, xác định phép toán cơ sở, đếm số phép đoán cơ sở, viết công thức tổng quát

- Xác định tham số: n
- Xác đinh phép toán cở sở: 1 lần thực hiện mỗi vòng lặp
- Đếm số phép đoán cơ sở: 
    - vòng lặp ngoài: $O(\log n)$
    - vòng lặp trong: chạy ``i`` lần
- Công thức tổng quát: $T(n) = \Theta(n)$

## Bài tập 4

**Quy tắc 1: Bỏ các hằng số**

$T(n) = n^2 + n + \log n + 1$

**Quy tắc 2: Ưu tiên bậc cao nhất**

$T(n) = n^2$

**Quy tắc 3: Bỏ các thành phần bậc thấp hơn**

$T(n) = n^2$

**Quy tắc 4: Viết kết quả bằng ký hiệu Theta**

$T(n) = \Theta(n^2)$



