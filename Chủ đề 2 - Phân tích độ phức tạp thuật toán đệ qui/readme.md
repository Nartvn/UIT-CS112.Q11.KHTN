# Chủ đề 2 - Phân tích độ phức tạp thuật toán đệ qui

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

Công thức truy hồi: 

$$
f(0) = 1
$$

$$
f(n)=f(n−1)+1
$$

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

**a. Trường hợp cơ sở**

* **n = 1:**
  $( T(1) = 2 )$ vì 1 chiếc bánh có 2 mặt, mỗi mặt cần 1 phút → mất 2 phút.
* **n = 2:**
  $( T(2) = 2 )$, tương tự như trường hợp $( n = 1 )$, ta có thể đặt cả 2 chiếc bánh lên chảo nấu cùng lúc.

**Trường hợp n > 2**

Ta có thể chọn 2 cái, nấu chín cả 2 mặt (mất 2 phút) và đệ quy tính toán cho ( n - 2 ) cái còn lại.

$$
\Rightarrow T(n) = T(n - 2) + 2 \quad \text{với } T(1) = T(2) = 2
$$

** Giải hệ thức truy hồi**

Dùng **phương pháp thế**:

$$
\begin{aligned} T(n) &= T(n - 2) + 2 \ &= T(n - 4) + 4 \
&= \dots \
&= T(\text{cơ sở}) + \frac{n}{2} \times 2 \quad (\text{cơ sở } = 1 \text{ hoặc } 2)
\end{aligned}
$$

* Với **n chẵn**, cơ sở = 2:
  $
  T(n) = 2 + \frac{n - 2}{2} \times 2 = n
  $
* Với **n lẻ**, cơ sở = 1:
  $T(n) = 2 + \frac{n - 1}{2} \times 2 = n + 1$

➡️ **Kết luận:** $( T(n) = O(n) )$

**b. Nhận xét**

* Thuật toán trên **“tuần tự hóa” quá mức** quy trình: luôn chọn nấu chín hoàn chỉnh 2 bánh rồi mới chuyển sang các bánh tiếp theo → **không tận dụng tối ưu thời gian**.

#### Ví dụ:

Giả sử có **3 chiếc bánh** $( C_1, C_2, C_3 )$

* Theo đệ quy ở trên:

  * Mất 2 phút cho $( C_1, C_2 )$
  * Mất thêm 2 phút cho $( C_3 )$
    → **Tổng cộng: 4 phút**

* Tuy nhiên, nếu **tận dụng nấu xen kẽ các mặt**, ta làm như sau:

| Phút | Mặt được nấu                         |
| ---- | ------------------------------------ |
| 1    | Mặt 1 của $( C_1 )$, mặt 1 của $( C_2 )$ |
| 2    | Mặt 2 của $( C_1 )$, mặt 1 của $( C_3 )$ |
| 3    | Mặt 2 của $( C_2 )$, mặt 2 của $( C_3 )$ |

→ **Tổng thời gian chỉ 3 phút**

➡️ Thuật toán đệ quy ban đầu không tận dụng được tính chất có thể **nấu xen kẽ** để giảm thời gian chết.

**c. Ý tưởng tối ưu**

Tận dụng tính chất: mỗi phút chảo có thể nấu chín **2 mặt của 2 bánh bất kỳ**.

* Có **n chiếc bánh**, tức là **2n mặt** cần nấu.
* Mỗi phút nấu được **2 mặt bất kỳ**.
* Do đó, cần ít nhất: $\frac{2n}{2} = n \text{ phút}$
* Sau ( n ) phút, toàn bộ công việc hoàn thành → **thuật toán tối ưu tuyệt đối**.

**Demo (giả mã):**

```python
for minute in range(0, n):
    cook(2_sides_not_yet_cooked)
```


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
 $G(x) - T(0) = G(x) - 1$

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

$$
G(x) \left( 1 - \frac{2x}{1 - x} \right) = 1
$$

$$
G(x) \frac{1 - 3x}{1 - x} = 1
$$

$$
\Rightarrow \boxed{G(x) = \frac{1 - x}{1 - 3x}}
$$

**Bước 5**. Khai triển chuỗi

$$
\frac{1 - x}{1 - 3x} = \frac{1}{1 - 3x} - \frac{x}{1 - 3x}
= \sum_{n \ge 0} 3^n x^n - \sum_{n \ge 0} 3^n x^{n+1}
$$

So sánh hệ số của $(x^n)$:
* Với $(n = 0): (T(0) = 1)$
* Với $(n \ge 1): (T(n) = 3^n - 3^{n-1} = 2 \cdot 3^{n-1})$

Kết luận: $$T(n) = 2 \cdot 3^{n-1} \quad (n \ge 1)$$
Độ phức tạp thời gian:
$$\boxed{T(n) = \Theta(3^n)}$$


