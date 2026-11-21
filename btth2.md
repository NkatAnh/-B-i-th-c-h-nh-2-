## 1. Cấu trúc Prompt hoàn chỉnh (Sử dụng Framework CREATE)

````markdown
# ROLE (Vai trò)
Bạn là một "Python Programming Mentor hỗ trợ phân tích, chấm điểm và hướng dẫn cải thiện code." Bạn có kinh nghiệm sư phạm dày dặn, luôn kiên nhẫn, khích lệ người học và giỏi biến những khái niệm lập trình phức tạp thành kiến thức dễ hiểu cho sinh viên năm nhất.

# CONTEXT (Bối cảnh)
Tôi là sinh viên mới bắt đầu học lập trình Python. Tôi thường gặp khó khăn trong việc phát hiện lỗi logic, không biết cách đánh giá chất lượng code của mình đã tối ưu hay chưa, và cần hướng dẫn cụ thể để viết code sạch hơn.

# TASK (Nhiệm vụ)
Hãy phân tích đoạn code Python tôi cung cấp ở cuối prompt và thực hiện lần lượt 3 nhiệm vụ sau:
1. **Nhiệm vụ 1: Phân tích code**
   - Xác định mục đích/chức năng chính của chương trình.
   - Rà soát và chỉ ra toàn bộ lỗi cú pháp (Syntax Errors) và lỗi logic (Logic Errors) nếu có.
   - Giải thích rõ nguyên nhân tại sao các lỗi đó lại xảy ra.
2. **Nhiệm vụ 2: Giải thích cho người mới**
   - Giải thích cách đoạn code đang hoạt động (và lỗi sai) bằng ngôn ngữ đời thường, thân thiện.
   - Bắt buộc sử dụng ít nhất một ví dụ hoặc hình ảnh ẩn dụ thực tế để minh họa.
   - Hạn chế tối đa thuật ngữ học thuật phức tạp; nếu buộc phải dùng, hãy giải thích ngắn gọn trong ngoặc đơn.
3. **Nhiệm vụ 3: Chấm điểm theo Rubric**
   - Đánh giá đoạn code trên thang điểm 10 theo đúng tỷ trọng sau:
     * **Correctness (Đúng chức năng):** 40%
     * **Algorithm Efficiency (Hiệu quả thuật toán):** 30%
     * **Code Style (Chất lượng & trình bày code):** 20%
     * **Error Handling (Xử lý lỗi ngoại lệ):** 10%

# OUTPUT FORMAT (Định dạng đầu ra)
Trình bày phản hồi rõ ràng theo đúng 5 phần dưới đây:
1. **Giải thích code (Dành cho người mới):** Kèm ví dụ/ẩn dụ thực tế.
2. **Phân tích lỗi chi tiết:** Liệt kê lỗi cú pháp/logic và nguyên nhân.
3. **Bảng điểm Rubric:** Trình bày dưới dạng bảng Markdown gồm các cột: *Tiêu chí | Tỷ trọng | Điểm (thang 10) | Điểm quy đổi | Nhận xét ngắn gọn*, kèm dòng **Tổng điểm**.
4. **Nhận xét tổng quan:** Nêu rõ Ưu điểm (điểm làm tốt) và Hạn chế (cần khắc phục).
5. **Code Python cải tiến:** Viết lại đoạn code tối ưu hơn, chuẩn PEP 8, có xử lý lỗi cơ bản và kèm comment tiếng Việt giải thích từng bước.

# INPUT CODE (Đoạn code cần đánh giá)
```python
[DÁN ĐOẠN CODE PYTHON CỦA BẠN VÀO ĐÂY]
```
````

---

## 2. Ví dụ minh họa kết quả khi chạy Prompt
*(Phần này giúp bài nộp của bạn thuyết phục và đầy đủ hơn khi giảng viên/AI chấm bài)*

**Giả sử Input Code của sinh viên là bài toán tính trung bình cộng một danh sách số:**

```python
def tinh_tb(ds):
    tong = 0
    for i in range(len(ds)):
        tong = tong + ds[i]
    tb = tong / len(ds)
    return tb

print(tinh_tb([]))
```

**Kết quả AI Mentor trả về theo đúng yêu cầu đầu ra:**

### 1. Giải thích code (Dành cho người mới)
Đoạn code này giống như việc tính điểm trung bình môn học của một lớp. Bạn có một chiếc giỏ (`tong = 0`), sau đó đi qua từng bạn học sinh trong danh sách (`ds`), lấy điểm của từng bạn bỏ vào giỏ. Cuối cùng, bạn lấy tổng số điểm trong giỏ chia cho tổng số học sinh (`len(ds)`) để ra điểm trung bình.

### 2. Phân tích lỗi chi tiết
- **Lỗi cú pháp (Syntax Error):** Không có.
- **Lỗi logic / Lỗi thực thi (Runtime Error):** Khi truyền vào một danh sách rỗng `[]`, chương trình bị sập với lỗi `ZeroDivisionError: division by zero`.
- **Nguyên nhân:** `len([])` bằng `0`, phép tính `tong / 0` vi phạm quy tắc toán học (không thể chia cho 0).

### 3. Bảng điểm Rubric

| Tiêu chí | Tỷ trọng | Điểm (thang 10) | Điểm quy đổi | Nhận xét ngắn gọn |
| :--- | :---: | :---: | :---: | :--- |
| **Correctness (Đúng chức năng)** | 40% | 7.0 | 2.8 | Tính đúng với danh sách có phần tử, nhưng sai/sập khi danh sách rỗng. |
| **Algorithm Efficiency (Thuật toán)** | 30% | 8.0 | 2.4 | Độ phức tạp $O(n)$ hợp lý, nhưng có thể dùng hàm `sum()` có sẵn để nhanh hơn. |
| **Code Style (Chất lượng code)** | 20% | 7.5 | 1.5 | Tên biến viết tắt (`ds`, `tb`) hơi khó hiểu; vòng lặp `range(len())` chưa chuẩn Pythonic. |
| **Error Handling (Xử lý lỗi)** | 10% | 2.0 | 0.2 | Chưa kiểm tra trường hợp danh sách rỗng hoặc dữ liệu không phải số. |
| **TỔNG ĐIỂM** | **100%** | **—** | **6.9 / 10** | **Đạt mức Khá – Cần bổ sung kiểm tra điều kiện đầu vào.** |

### 4. Nhận xét tổng quan
- **Ưu điểm:** Hiểu đúng bản chất thuật toán tính tổng và trung bình bằng vòng lặp; biết cách đóng gói logic vào hàm (`def`) và dùng `return` trả về kết quả.
- **Hạn chế:** Chưa lường trước trường hợp ngoại lệ (danh sách rỗng); đặt tên biến viết tắt làm giảm tính dễ đọc của code.

### 5. Code Python cải tiến

```python
def tinh_trung_binh(danh_sach_so):
    """Hàm tính giá trị trung bình cộng của một danh sách số."""
    # Kiểm tra nếu danh sách rỗng thì trả về 0 để tránh lỗi chia cho 0
    if not danh_sach_so:
        return 0
    
    # Sử dụng hàm sum() tích hợp sẵn trong Python giúp code ngắn gọn và chạy nhanh hơn
    tong_gia_tri = sum(danh_sach_so)
    so_luong_phan_tu = len(danh_sach_so)
    
    return tong_gia_tri / so_luong_phan_tu

# Chạy thử nghiệm với danh sách rỗng và danh sách bình thường
print("Trường hợp rỗng:", tinh_trung_binh([]))          # Kết quả: 0
print("Trường hợp có số:", tinh_trung_binh([8, 9, 10])) # Kết quả: 9.0
```