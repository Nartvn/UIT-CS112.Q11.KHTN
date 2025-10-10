# CS112 - Chủ đề 2 - Phân tích độ phức tạp thời gian của đệ quy
Link drive Slide + BTVN + Quiz: https://drive.google.com/drive/folders/1IuP9MwowUDMST8vLPuAkoKHCV9SJwEW_?usp=sharing

# Mở đầu
- **Đệ quy là gì?**
- **So sánh: đệ quy vs vòng lặp**


# Quy trình chung để phân tích thời gian của đệ quy
- Xác định tham số kích thước input
- Xác định phép toán cơ bản của thuật toán
- Với các input có cùng độ lớn thì số lần thực hiện phép toán có thay đổi dựa theo input không. Nếu có, cần phân tích riêng ba trường hợp: tốt nhất, trung bình và xấu nhất.
- Thiết lập công thức truy hồi và trường hợp cơ sở cho hàm $M(i)$,  với $M(i)$ là độ phức tạp thời gian để tính toán ra hàm $F(i)$.
- Giải phương trình truy hồi 


# Phân tích đệ quy (Cách giải hệ thức truy hồi)
- Phương pháp thế (Substitution Method) (tiến + lùi)
- Phương pháp cây đệ qui (Recurrence Tree Method) 
- Phương pháp Master Theorem
- Phương pháp hệ thức truy hồi bậc hai với hệ số hằng  
- Phương pháp hàm sinh



# **Bài tập về nhà**:

**BÀI 1**:
Cho một ma trận vô hạn ô vuông màu trắng. Bắt đầu với một ô vuông bị tô đen ở giữa ma trận, với mỗi một đơn vị thời gian nó sẽ tự loan màu sang các ô khác theo 4 hướng Đông-Tây-Nam-Bắc, hỏi sau $n$ đơn vị thời gian thì có bao nhiêu ô bị loan màu. 

Hãy giải bài toán bằng thuật toán đệ quy.

Tìm ra công thức truy hồi thời gian và giải công thức truy hồi đó để tìm được độ phức tạp thuật toán.

---

**BÀI 2**: 
Một đầu bếp cần nấu n chiếc hamburger trên một chiếc chảo nhỏ có sức chứa tối đa 2 chiếc cùng lúc. Mỗi chiếc hamburger cần được nấu cả hai mặt, và thời gian để nấu một mặt (cho 1 hoặc 2 chiếc) là 1 phút.

Một thuật toán đệ quy được đề xuất như sau:
Trường hợp cơ sở (n ≤ 2): Nếu có 1 hoặc 2 chiếc, nấu tuần tự 2 mặt của chúng.
Đệ quy (n > 2): Chọn 2 chiếc bất kỳ, nấu cả 2 mặt của chúng. Sau đó, giải quyết bài toán còn lại cho n - 2 chiếc.


Yêu cầu:
- a. Xây dựng và giải hệ thức truy hồi:
Thiết lập và giải hệ thức truy hồi T(n) để xác định tổng thời gian nấu n chiếc hamburger theo thuật toán đã cho.
- b. Phân tích tính tối ưu của thuật toán:
Giải thích tại sao thuật toán đệ quy trên không phải là chiến lược tối ưu để giảm thiểu tổng thời gian nấu.
- c. Đề xuất thuật toán tối ưu:
Xây dựng một thuật toán khác để hoàn thành công việc trong thời gian ngắn nhất có thể và chứng minh tính hiệu quả của nó.

---
**BÀI 3**: Cho đoạn code
```python=
def countPairs(n):
    if n <= 1:
        return 1
    total = 0
    for i in range(n):
        total += countPairs(i) * countPairs(n - 1 - i)
    return total
```
Hãy phân tích độ phức tap thời gian thuật toán theo quy trình chung. 


