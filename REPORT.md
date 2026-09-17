# Mẫu tham khảo để điền REPORT.md

**Cách dùng:** Bản cần nộp đã có sẵn ở [`REPORT.md`](../REPORT.md) trong thư mục gốc của fork; mở file đó và điền vào chỗ `…`. File này giải thích từng mục và có ví dụ để tham khảo khi bạn bị kẹt. Giữ nguyên bốn mục và bảng để coach đọc bài nhanh; **không chép ví dụ thành câu trả lời của mình**.

- Mã học viên theo lớp: 2A202602159
- Ngày / CVAT local: 17/09/2026
- Công cụ đã dùng: Brush / Polygon / Intelligent Scissors / gợi ý tự động có sẵn / khác: …

Mã học viên là mã lớp cấp, không cần ghi họ tên trong bản nộp nếu kênh lớp đã nhận diện bạn. Ở dòng công cụ, giữ lại những công cụ bạn thật sự dùng; không có SAM cũng hoàn toàn bình thường.

## 1. Bài đã nộp

**Bạn cần điền gì?** “File ZIP đúng tên” là tên file bạn đã tải từ CVAT rồi đặt lại, ví dụ `easy_semantic.zip`. “Hoàn thành mấy ảnh” là số ảnh bạn đã vẽ và Save, không phải số ảnh có trong task. Chưa làm hoặc export lỗi thì ghi `chưa có`, đừng ghi tên một ZIP rỗng. Cột điểm là **điểm tối đa của task**, không phải điểm tự chấm.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Không tự điền điểm nếu chưa có phản hồi từ người chấm. Nếu export lỗi, ghi task, trạng thái Save và thông báo đã gửi coach.

Ví dụ cách ghi lỗi export: “`cp3_thin`: đã Save 1/1 ảnh, CVAT không hiện Segmentation mask 1.1 lúc 14:10, đã báo coach”. Bạn vẫn ghi đúng tình trạng, không tự đổi format.

## 2. Một quyết định trước khi dùng gợi ý

**Mục này hỏi cách bạn tự ra quyết định.** Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi mở bất kỳ đề xuất tự động nào cho object đó. “Vị trí” chỉ cần mô tả đủ để tìm lại, chẳng hạn “xe bên trái, nửa dưới ảnh”; nếu nhớ tên file JPG thì ghi luôn. “Quy tắc biên” nghĩa là lý do bạn dừng mask ở đâu, nhất là mép ảnh hoặc vật che. Không cần ảnh chụp riêng nếu lớp không yêu cầu.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: 
    Ảnh Medium 2 – ảnh đường phố có xe buýt màu đỏ ở giữa ảnh; object đầu tiên là xe buýt ở trung tâm, phía dưới tòa nhà.
- Class và quy tắc tôi dùng để chọn biên: 
    Class: bus. Tôi vẽ polygon theo đường bao bên ngoài của thân xe buýt, bao gồm phần thân nhìn thấy và không lấy phần nền đường, người đi bộ hoặc tòa nhà phía sau. Các vùng bị che bởi người hoặc phương tiện khác chỉ được label theo phần quan sát rõ ràng, không tự đoán phần bị che.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: 
    Với các xe có hình dạng rõ, vùng gợi ý tương đối sát thân xe nhưng có thể tràn sang mặt đường ở phần bánh xe. Tôi giữ phần mask đúng, xóa vùng tràn ra đường và chỉnh lại vertex quanh bánh xe, kính và nóc xe. Lý do là biên của instance phải thuộc về đúng object, không bao gồm nền hoặc object lân cận.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.
    Tôi tự vẽ polygon bằng cách đặt các điểm tại các góc và đường cong chính của object, sau đó zoom để kiểm tra các cạnh nhỏ.

Ví dụ cách giải thích, không phải đáp án cho ảnh của bạn: “Tôi chỉ vẽ phần thân xe còn nhìn thấy; phần sau cột bị che nên không đoán đường biên phía sau.” Nếu công cụ đưa vùng tràn ra nền, hãy ghi đã xóa vùng nào và vì sao. “Gợi ý đúng” cũng cần nói bạn đã kiểm điều gì rồi mới giữ.

## 3. Một lỗi tôi tìm thấy và sửa

**Chọn một lỗi có thật trong bài của bạn**, không cần lỗi lớn nhất. Một dòng tốt có thể là: “Tại `cp2_slice`, hai xe cùng lớp bị gộp thành một mask; nhìn thấy khe giữa hai xe; tôi tách thành hai object, Save và export lại.” Nếu chưa sửa được do công cụ lỗi, nói rõ đã thử gì và cần coach hỗ trợ gì; đừng ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: medium_instance – ảnh Medium 1, khu vực giữa ảnh có nhiều xe máy và một người đi bộ.
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: Gộp–tách instance và biên.
- Bằng chứng tôi nhìn thấy: Hai xe máy cùng class motorcycle nằm gần nhau, phần bánh xe và tay lái gần chạm nhau. Polygon ban đầu bao phủ cả hai xe thành một shape, đồng thời ăn sang một phần người đi bộ phía sau.
- Quy tắc và hành động sửa: Tôi xóa polygon gộp, tạo hai polygon riêng cho từng xe máy. Với mỗi polygon, tôi chỉ giữ phần thuộc về xe tương ứng; vùng bị che bởi xe khác hoặc người đi bộ không được tự vẽ đoán. Tôi cũng chỉnh lại các điểm quanh bánh xe, tay lái và phần đuôi xe để không ăn sang nền.
- Sau sửa đã Save và export lại chưa? Đã Save annotation và export lại file medium_instance.zip. Trước khi nộp cần mở lại file ZIP để kiểm tra đúng format COCO 1.0 và đúng số lượng annotation.

**Nếu đã xem điểm tự đánh giá trên GitHub Actions hoặc chạy scorer:** ghi một kết quả liên quan lỗi bạn vừa sửa, chẳng hạn “`easy_semantic`: per-class IoU của `sidewalk` tăng sau khi tôi sửa ranh bó vỉa, Save và export lại”; nếu chưa có điểm, ghi “chưa có”. Xem [hướng dẫn xem Summary hoặc chạy dự phòng](../docs/SELF_SCORING.md). Kết quả ba tier là tổng **/82**, không tự điền PASS, top 3 hoặc bonus. Đừng đưa ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

**“Ca” là một vùng cụ thể khiến bạn phải dừng lại và chọn cách hiểu**, không nhất thiết là ba lỗi. Với mỗi dòng, ghi vị trí, hai khả năng bạn đã cân nhắc, dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi quyết định của bạn. Nếu quy tắc chưa đủ rõ, viết một câu hỏi mà coach có thể trả lời. Ví dụ: “mép bó vỉa trong `cp4_curb`: road hay sidewalk? Tôi chọn sidewalk vì phần nền nâng cao; xin xác nhận ranh tại chỗ màu giống mặt đường.” Ba dòng có thể đến từ ba task khác nhau.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| Easy 1 – đường cao tốc, vùng nền màu xám bên trái và mặt đường | Có thể là road hoặc sidewalk/curb | Vùng này nằm ngoài làn xe, có mép phân cách rõ và màu sắc khác mặt đường chính. | Chọn class theo schema được cấp; nếu schema chỉ có road, gán vào road khi vùng đó thuộc phần mặt đường giao thông. Cần coach xác nhận nếu có class sidewalk hoặc curb. |
| Hard 1 – ảnh có nhiều xe máy, người đi bộ ở giữa đường | Người đi bộ có thể bị gán thiếu phần chân hoặc bị gộp với nền; xe máy có thể bị gộp do chồng lấn | Người và xe có đường biên riêng ở phần nhìn thấy; phần bị che không nên tự đoán. | Tách người và từng xe máy thành các instance/segment riêng. Chỉ label phần nhìn thấy, không mở rộng polygon vào vùng bị che. |
| Medium 3 – ảnh khu dân cư, xe đỗ gần lề đường và bóng đổ | Bóng đổ có thể bị hiểu nhầm là một phần của xe; vùng giữa xe và nền có thể bị gộp | Bóng không có đường biên vật thể và không có cấu trúc thân xe/bánh xe. Khoảng trống giữa xe và mặt đường phải giữ là nền. | Chỉ vẽ phần thân xe thật; bỏ bóng đổ và không nối polygon qua khoảng trống dưới gầm xe. |
