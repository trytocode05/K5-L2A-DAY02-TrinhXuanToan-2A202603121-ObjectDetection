# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` | Xe con dùng chở người, gồm sedan, SUV, taxi và xe bán tải. | Xe bán tải/cabin nhỏ xếp vào `car`, không phải `truck`. |
| `truck` | Xe tải chở hàng và xe đầu kéo. | Dựa vào kiểu xe tải/đầu kéo; không xếp xe bán tải nhỏ vào lớp này. |
| `bus` | Xe buýt và minibus dùng chở khách. | Phân biệt với van/minivan; không dựa riêng vào kích thước nếu kiểu xe chưa rõ. |
| `van` | Xe van hoặc minivan dùng chở hàng hoặc chở người. | Van không phải xe buýt lớn; không xếp xe con thông thường vào lớp này. |

## Quy tắc chung

- Box bám sát vật thể nghĩa là: ôm sát phần thân xe nhìn thấy được, không lấy thêm nền hay xe bên cạnh; mỗi xe có box riêng.
- Vật thể bị che khuất: gán box quanh phần nhìn thấy nếu vẫn nhận diện được lớp; không đoán phần bị che.
- Vật thể bị cắt bởi rìa ảnh: box dừng đúng tại rìa ảnh; không mở rộng ra ngoài khung hình.
- Vật thể rất nhỏ/mơ hồ: chỉ gán khi phần nhìn thấy đủ để nhận diện chắc lớp. Nếu không chắc, không đoán; ghi lại ảnh và hỏi giảng viên. Không gán người đi bộ, xe đạp, mô tô/xe máy, biển báo hoặc đèn giao thông.

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

> Thay mỗi chỗ `drive_...` bằng tên ảnh gốc trong `dataset/images/train/` sau khi đối chiếu ảnh. Ảnh chụp gửi kèm không hiển thị tên file nên không thể xác định tên thay cho bạn.

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_...` (ảnh gửi kèm 1) | Vật thể nhỏ, mờ; không thấy đủ đặc điểm để phân biệt chắc xe thuộc lớp nào hay vật thể ngoài schema. | Không gán nếu xem ảnh gốc vẫn không nhận diện chắc được; nếu ảnh gốc cho thấy rõ một xe thuộc schema thì gán đúng lớp và box quanh phần nhìn thấy. | Schema chỉ gồm `car`, `truck`, `bus`, `van`; không suy đoán lớp chỉ từ màu sắc hoặc một mảng hình mờ. |
| `drive_...` (ảnh gửi kèm 2) | Vật thể tối, chi tiết thân xe khó thấy; cần kiểm tra ảnh gốc để biết có bị che hoặc cắt khung hay không. | Chỉ gán box phần nhìn thấy nếu ảnh gốc xác nhận đây là xe và đủ dấu hiệu nhận diện lớp; nếu không thì không đoán và hỏi giảng viên. | Xe bị che/cắt vẫn được gán khi nhận diện được lớp, nhưng không suy ra phần khuất hoặc phần ngoài khung. |
| `drive_...` (ảnh gửi kèm 3) | Hai vật thể/xe có vẻ chồng lấn; ảnh cắt nhỏ chưa đủ để kết luận loại xe. | Nếu ảnh gốc xác nhận là hai xe thuộc schema và nhận diện được từng xe, vẽ hai box riêng quanh phần nhìn thấy; không gộp thành một box. Nếu lớp của xe nào không rõ thì không đoán lớp đó. | Mỗi xe là một đối tượng riêng; chỉ gán các lớp trong schema và box không bao gồm xe bên cạnh. |
