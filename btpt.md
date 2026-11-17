# [Phân tích] So sánh Trade-off các giải pháp ra lệnh cho Kỹ thuật Prompting Nâng cao (Logic & Chuỗi)

## **Bước 1: Hai prompt mẫu**

**Giải pháp 1**

```
Chia bài toán thành các bước nhỏ
Thực hiện lần lượt
Nếu gặp dữ liệu lỗi, hãy thông báo
Xuất kết quả cuối cùng
```

**Giải pháp 2**

```
Thực hiện theo các bước:
1. Kiểm tra và làm sạch dữ liệu
2. Phân tích từng phần
3. Tóm tắt để tránh mất ngữ cảnh
4. Lưu kết quả để khôi phục khi bị gián đoạn
5. Kiểm tra lỗi và xuất JSON hợp lệ
Không tự suy đoán dữ liệu còn thiếu
```

## **Bước 2: Bảng so sánh Trade-off**

| Tiêu chí | Giải pháp 1 | Giải pháp 2 |
| --- | --- | --- |
| Độ dễ hiểu | Cao  | Trung bình |
| Tốn token | Ít | Nhiều |
| Không mất ngữ cảnh | Cơ bản | Tốt |
|Chặn lỗi biên | Trung bình | Tốt |
| Khôi phục khi lỗi  | Thấp | Cao  |

## **Bước 3: Lựa chọn và chạy thử**

Chọn 2 vì kiểm tra dữ liệu kỹ hơn, hạn chế lỗi và có thể tiếp tục khi quy trình bị gián đoạn

**Input:** Khách hàng phản ánh: "Đơn hàng giao chậm 3 ngày, nhân viên không liên lạc"

**Output:**

```
{
  "status": "success",
  "category": "Giao hàng",
  "department": "Vận chuyển",
  "issue": "Giao hàng chậm 3 ngày",
  "priority": "high",
  "errors": []
}
```