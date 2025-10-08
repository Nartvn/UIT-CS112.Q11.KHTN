# Nhóm 9: Phân tích độ phức tạp thuật toán không đệ quy

Họ và tên: Hà Bùi Trọng Nghĩa <br>
MSSV: 24520020<br>
Nhóm: 8 <br>


Họ và tên: Nguyễn Duy Khang <br>
MSSV: 24520755 <br>
Nhóm: 8

---

## Bài tập 1

Gọi $f(n)$ là số ô bị tô màu sau $n$ đơn vị thời gian.
- Cở sở: $f(0) = 1$
- Bước đệ quy: Mỗi đơn vị thời gian, màu lan ra 4 hướng từ các ô biên mới được tô ở bước trước.

Ta có đoạn code giải như sau:

```python
def f(n):
    if n == 0:
        return 1
    return f(n - 1) + 4 * n
```

Công thức truy hồi: <br>
***<p style="text-align:center;">
$f(0) = 1$ <br>
$f(n)=f(n−1)+1$ <br></p>***
Ta giải công thức trên:
- $f(1) = f(0) + 1 = 1 + 1 = 2$
- $f(2) = f(1) + 1 = (f(0) + 1) + 1 = 3$
- $f(3) = f(2) + 1 = (f(1) + 1) + 1 = 4$
- ...

Tổng quát:

$$
f(n) = f(0) + n = O(n)
$$

Vậy độ phức tạp là: $O(n)$

------

## Bài tập 2

fhdhagiohsdiofhjoie

------

## Bài tập 3

- Xác định tham số kích thước input: **$n$**.
- Xác định phép toán cơ bản: **nhân hoặc cộng**.
- Xác định xem số phép toán có thay đổi với cùng độ lớn input không: **Không**.
- Thiết lập công thức truy hồi:
    - $T(n) = \sum_{i=0}^{n-1} [T(i) + (n-1-i)] + O(n)$ .
    - Nhưng vì $T(n) = T(n - i - 1)$ nên có có rút gọn công thức: $T(n) = 2 \sum_{i=0}^{n-1} T(i) + O(n)$.
    - Bài toán cơ sở: $T(0) = T(1) = O(1)$
- Giải phương trình truy hồi bằng phương pháp hàm sinh:
$$
T(0) = 1, \quad T(n) = 2 \sum_{i=0}^{n-1} T(i), \quad (n \ge 1)
$$
 **Bước 1**. Đặt hàm sinh
 $$
 G(x) = \sum_{n \ge 0} T(n)x^n
 $$
 **Bước 2**. Nhân cả hai vế truy hồi với (x^n) và lấy tổng cho $(n \ge 1)$
 $$
 \sum_{n \ge 1} T(n)x^n = 2 \sum_{n \ge 1} x^n \sum_{i=0}^{n-1} T(i)
 $$
 Vế trái:
 $$G(x) - T(0) = G(x) - 1$$

 **Bước 3**. Đổi thứ tự tổng ở vế phải
 $$
 \sum_{n \ge 1} x^n \sum_{i=0}^{n-1} T(i)
= \sum_{i \ge 0} T(i) \sum_{n \ge i+1} x^n
= \sum_{i \ge 0} T(i) \frac{x^{i+1}}{1 - x}
= \frac{x}{1 - x} G(x)
$$

**Bước 4**. Lập phương trình cho (G(x))

$$
G(x) - 1 = 2 \frac{x}{1 - x} G(x)
$$
$$G(x) \left( 1 - \frac{2x}{1 - x} \right) = 1$$
$$G(x) \frac{1 - 3x}{1 - x} = 1$$
$$\Rightarrow \boxed{G(x) = \frac{1 - x}{1 - 3x}}$$

**Bước 5**. Khai triển chuỗi
$$\frac{1 - x}{1 - 3x} = \frac{1}{1 - 3x} - \frac{x}{1 - 3x}
= \sum_{n \ge 0} 3^n x^n - \sum_{n \ge 0} 3^n x^{n+1}
$$
So sánh hệ số của $(x^n)$:
* Với $(n = 0): (T(0) = 1)$
* Với $(n \ge 1): (T(n) = 3^n - 3^{n-1} = 2 \cdot 3^{n-1})$

Kết luận: $$T(n) = 2 \cdot 3^{n-1} \quad (n \ge 1)$$
Độ phức tạp thời gian:
$$\boxed{T(n) = \Theta(3^n)}$$


