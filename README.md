# **BÀI THỰC HÀNH 5: PHÂN LOẠI PHẢN HỒI CỦA KHÁCH HÀNG**

## **PHẦN 1. XÂY DỰNG PROMPT ZERO-SHOT**

### **1.1. Prompt Zero-shot theo CREATE**

```
[C - Context]
Bạn là chuyên viên phân tích phản hồi khách hàng của cửa hàng TechShop, chuyên kinh doanh đồ công nghệ trên Facebook.

[R - Request]
Phân loại 5 phản hồi khách hàng thành 3 nhãn:
- Tích cực.
- Tiêu cực.
- Yêu cầu hỗ trợ.

[E - Explanation]
Quy tắc phân loại:
- Tích cực: Khách hàng hài lòng, khen ngợi.
- Tiêu cực: Khách hàng phàn nàn, không hài lòng.
- Yêu cầu hỗ trợ: Khách hàng cần giải quyết một vấn đề cụ thể.

Không suy diễn thông tin ngoài phản hồi. Nếu khách hàng đưa ra yêu cầu giải quyết cụ thể, ưu tiên nhãn Yêu cầu hỗ trợ.

[A - Action]
1. Đọc và phân tích từng phản hồi.
2. Xác định nhãn phân loại phù hợp.
3. Giải thích ngắn gọn lý do.
4. Tổng hợp kết quả thành bảng.

Dữ liệu:
1. "Sản phẩm đẹp, giao hàng nhanh, rất hài lòng."
2. "Tôi đã đặt hàng 5 ngày nhưng chưa nhận được."
3. "Tai nghe không kết nối được Bluetooth."
4. "Nhân viên tư vấn rất nhiệt tình."
5. "Tôi muốn hoàn tiền vì sản phẩm bị lỗi."

[T - Tone]
Sử dụng văn phong khách quan, chuyên nghiệp, ngắn gọn và dễ hiểu.

[E - Extras]
- Xuất kết quả dưới dạng bảng Markdown.
- Gồm 4 cột: STT, Phản hồi, Nhãn phân loại, Lý do.
- Sau bảng có phần so sánh ngắn gọn Zero-shot và Few-shot.
- Chỉ xuất kết quả, không giải thích thêm.
```

### **1.2. Kết quả Zero-shot**

| STT | Phản hồi                                     | Nhãn phân loại | Lý do                                          |
| --- | -------------------------------------------- | -------------- | ---------------------------------------------- |
| 1   | Sản phẩm đẹp, giao hàng nhanh, rất hài lòng. | Tích cực       | Khách hàng hài lòng với sản phẩm và giao hàng. |
| 2   | Tôi đã đặt hàng 5 ngày nhưng chưa nhận được. | Tiêu cực       | Khách hàng phàn nàn về giao hàng chậm.         |
| 3   | Tai nghe không kết nối được Bluetooth.       | Yêu cầu hỗ trợ | Khách hàng gặp lỗi kỹ thuật.                   |
| 4   | Nhân viên tư vấn rất nhiệt tình.             | Tích cực       | Khách hàng khen ngợi nhân viên.                |
| 5   | Tôi muốn hoàn tiền vì sản phẩm bị lỗi.       | Yêu cầu hỗ trợ | Khách hàng yêu cầu hoàn tiền do sản phẩm lỗi.  |

## **PHẦN 2. XÂY DỰNG PROMPT FEW-SHOT**

### **2.1. Prompt Few-shot theo CREATE**

```
[C - Context]
Bạn là chuyên viên phân tích phản hồi khách hàng của cửa hàng TechShop, chuyên kinh doanh đồ công nghệ trên Facebook.

[R - Request]
Phân loại phản hồi khách hàng thành 3 nhãn:
- Tích cực.
- Tiêu cực.
- Yêu cầu hỗ trợ.

[E - Explanation]
Quy tắc phân loại:
- Tích cực: Khách hàng hài lòng, khen ngợi.
- Tiêu cực: Khách hàng phàn nàn, không hài lòng.
- Yêu cầu hỗ trợ: Khách hàng cần giải quyết một vấn đề cụ thể.

Ví dụ mẫu:

Ví dụ 1:
Phản hồi: "Sản phẩm sử dụng rất tốt."
Nhãn: Tích cực.
Lý do: Khách hàng hài lòng với sản phẩm.

Ví dụ 2:
Phản hồi: "Giao hàng quá chậm, tôi rất thất vọng."
Nhãn: Tiêu cực.
Lý do: Khách hàng không hài lòng về giao hàng.

Ví dụ 3:
Phản hồi: "Điện thoại không bật nguồn được, shop hỗ trợ tôi."
Nhãn: Yêu cầu hỗ trợ.
Lý do: Khách hàng gặp lỗi và cần được hỗ trợ.

Không suy diễn thông tin ngoài dữ liệu. Nếu khách hàng đưa ra yêu cầu giải quyết cụ thể, ưu tiên nhãn Yêu cầu hỗ trợ.

[A - Action]
1. Đọc và phân tích 5 phản hồi.
2. Đối chiếu với các ví dụ mẫu.
3. Xác định nhãn phù hợp.
4. Giải thích lý do phân loại.
5. Tổng hợp kết quả thành bảng.

Dữ liệu:
1. "Sản phẩm đẹp, giao hàng nhanh, rất hài lòng."
2. "Tôi đã đặt hàng 5 ngày nhưng chưa nhận được."
3. "Tai nghe không kết nối được Bluetooth."
4. "Nhân viên tư vấn rất nhiệt tình."
5. "Tôi muốn hoàn tiền vì sản phẩm bị lỗi."

[T - Tone]
Sử dụng văn phong khách quan, chuyên nghiệp, ngắn gọn và dễ hiểu.

[E - Extras]
- Xuất kết quả dưới dạng bảng Markdown.
- Gồm 4 cột: STT, Phản hồi, Nhãn phân loại, Lý do.
- Sau bảng có phần so sánh ngắn gọn Zero-shot và Few-shot.
- Chỉ xuất kết quả, không giải thích thêm.
```

### **2.2. Kết quả Few-shot**

| STT | Phản hồi                                     | Nhãn phân loại | Lý do                                          |
| --- | -------------------------------------------- | -------------- | ---------------------------------------------- |
| 1   | Sản phẩm đẹp, giao hàng nhanh, rất hài lòng. | Tích cực       | Khách hàng hài lòng với sản phẩm và giao hàng. |
| 2   | Tôi đã đặt hàng 5 ngày nhưng chưa nhận được. | Tiêu cực       | Khách hàng phàn nàn về giao hàng chậm.         |
| 3   | Tai nghe không kết nối được Bluetooth.       | Yêu cầu hỗ trợ | Khách hàng gặp sự cố kỹ thuật.                 |
| 4   | Nhân viên tư vấn rất nhiệt tình.             | Tích cực       | Khách hàng đánh giá tốt nhân viên.             |
| 5   | Tôi muốn hoàn tiền vì sản phẩm bị lỗi.       | Yêu cầu hỗ trợ | Khách hàng cần giải quyết yêu cầu hoàn tiền.   |

## **PHẦN 3. SO SÁNH KẾT QUẢ**

### **3.1. Bảng so sánh**

| Tiêu chí       | Zero-shot          | Few-shot                   |
| -------------- | ------------------ | -------------------------- |
| Ví dụ mẫu      | Không có           | Có 3 ví dụ                 |
| Cách phân loại | Dựa vào hướng dẫn  | Dựa vào hướng dẫn và ví dụ |
| Độ chính xác   | Phân loại đúng 5/5 | Phân loại đúng 5/5         |
| Tính nhất quán | Tốt                | Tốt, có ví dụ đối chiếu    |
| Độ phức tạp    | Đơn giản           | Cần chuẩn bị ví dụ         |

### **3.2. Nhận xét và kết luận**

- Zero-shot giúp phân loại nhanh, không cần chuẩn bị ví dụ mẫu.
- Few-shot có ví dụ minh họa nên giúp AI hiểu rõ hơn cách phân biệt các nhãn.
- Cả hai phương pháp đều cho kết quả giống nhau trong bài thực hành này.

**Kết luận:** Few-shot phù hợp hơn khi phân loại phản hồi có nội dung phức tạp vì các ví dụ mẫu giúp AI phân loại nhất quán hơn.
### **3.3. Kết luận**

Qua bài thực hành, cả Zero-shot và Few-shot đều có thể sử dụng để phân loại phản hồi khách hàng. Tuy nhiên, Few-shot phù hợp hơn với bài toán này vì có ví dụ minh họa cụ thể, giúp AI hiểu rõ quy tắc phân loại và đưa ra kết quả nhất quán hơn.

**Lựa chọn:** Nên sử dụng Few-shot khi triển khai phân loại phản hồi khách hàng thực tế, đặc biệt khi cần phân biệt rõ giữa phản hồi tiêu cực và yêu cầu hỗ trợ.
