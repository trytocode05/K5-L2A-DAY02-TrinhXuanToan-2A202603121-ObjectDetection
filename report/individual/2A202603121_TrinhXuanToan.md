# Báo cáo cá nhân — Ngày 2 Object Detection

Các mục còn ghi `[cần điền]` phải được hoàn thiện từ quá trình làm bài thực tế trước khi nộp.

## 1. Thông tin học viên

- Họ tên: Trịnh Xuân Toàn
- MSSV: 2A202603121
- Email: [cần điền]
- Lớp: K5-L2A
- Link repo bài làm: https://github.com/trytocode05/K5-L2A-DAY02-TrinhXuanToan-2A202603121-ObjectDetection
- Link notebook nguồn mở trong Colab: https://colab.research.google.com/github/trytocode05/K5-L2A-DAY02-TrinhXuanToan-2A202603121-ObjectDetection/blob/main/notebooks/day2_annotation_to_yolo.ipynb
- Link Colab đã chạy: [cần điền sau khi chạy và cấp quyền xem]

## 2. Schema và mini guideline

Dẫn tới [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md). [Cần ghi ba ca mơ hồ theo đúng ảnh đã xem và quyết định thực tế; guideline hiện còn tên ảnh `drive_...` chưa hoàn thiện.]

## 3. Annotation và self-QC

- Số file nhãn train: 50/50.
- Kết quả checker và lỗi đã xử lý: `python tools/check_yolo_labels.py` đạt cấu trúc 50/50. Checker không đánh giá nội dung box.
- Danh sách ít nhất 10 ảnh đã rà bằng mắt: [cần điền sau khi tự rà]
- Lỗi bỏ sót/box/class phát hiện khi rà và cách sửa: [cần điền theo quan sát thực tế]
- Commit lưu bản nhãn ban đầu: `07a9a29` (50 file train, đã push lên `origin/main`).

## 4. Gold QC và rework

| Chỉ số | Bộ nhãn hiện tại | Sau sửa nếu có |
|---|---:|---:|
| TP | 518 | [chưa sửa] |
| FP | 579 | [chưa sửa] |
| FN | 135 | [chưa sửa] |
| Precision | 0.4722 | [chưa sửa] |
| Recall | 0.7933 | [chưa sửa] |
| F1 | 0.5920 | [chưa sửa] |
| mean_iou_of_matches | 0.8033 | [chưa sửa] |
| passed | Có với `--min-f1 0.50`; không với mốc 0.80 trong repo | [chưa sửa] |

[Kết quả đánh giá](../../outputs/annotation_evaluation.json) dùng IoU ghép box 0.50, ngưỡng F1 0.50 theo thông tin học viên cung cấp, và ngưỡng mean IoU 0.70. README/RUBRIC của repo vẫn ghi F1 0.80; cần ghi nguồn thông báo đổi ngưỡng nếu giảng viên xác nhận. Chưa có rework. FP/FN chưa đủ để kết luận nguyên nhân của từng box.

## 5. Kết quả YOLO

- Runtime: T4 GPU đã chọn trên Colab; log train ghi `device: 0`. Phiên bản Ultralytics và Torch: [cần điền từ cell Colab nếu có].
- Tham số train trong `args.yaml`: `yolo26n.pt`, `epochs=50`, `imgsz=640`, `batch=-1`, `seed=20260909`; khớp notebook.
- Đường dẫn best checkpoint trong phiên chạy: `/content/Day2-Lab/outputs/yolo26_runs/vehicle_annotation/weights/best.pt` (không commit checkpoint).

| Chỉ số trên 10 ảnh eval | Giá trị |
|---|---:|
| Precision | 0.5105 |
| Recall | 0.3567 |
| mAP50 | 0.3956 |
| mAP50–95 | 0.2170 |

Kết quả được lấy từ `model_eval_metrics.json` trong `day2_colab_outputs.zip`. Có đủ 10 ảnh dự đoán trong [eval_predictions/visuals](assets/eval_predictions/visuals/drive_051.jpg), [log train](assets/yolo26_runs/vehicle_annotation/results.csv) và [confusion matrix eval](assets/yolo26_runs/vehicle_eval/confusion_matrix.png). [Cần tự xem một ảnh, chỉ ra vật thể cụ thể và phân tích đúng/sai theo quan sát.]

Trả lời bốn câu hỏi cuối notebook:

1. Lớp nào recall thấp nhất? Ảnh nào minh họa?
2. Nếu mAP50 cao nhưng mAP50–95 thấp, cần kiểm điều gì trên box?
3. Lỗi class nào có thể liên quan guideline? Dữ kiện nào hỗ trợ nhận xét?
4. Vì sao không dùng 10 ảnh eval để train? Vai trò validation của chúng trong notebook là gì?

## 6. Khó khăn và cách xử lý

| Bước/thời điểm | Lỗi quan sát | Cách đã thử | Kết quả/còn thiếu |
|---|---|---|---|
| Colab | [cần điền nếu gặp lỗi thực tế] | [cần điền] | [cần điền] |

## 7. Tự đánh giá theo rubric

Đã có 50 nhãn đúng cấu trúc, kết quả gold QC và kết quả Colab trên 10 ảnh eval. Còn thiếu xác nhận self-QC bằng mắt, ba ca mơ hồ có ID ảnh, link Colab đã chạy và phân tích model cá nhân. [Cần đối chiếu lại sau khi hoàn tất.]

## 8. Công cụ AI và tài liệu tham khảo

- Codex: hỗ trợ chạy checker, evaluator, tạo commit, chuẩn bị báo cáo từ số liệu thực tế. [Học viên ghi phần đã tự kiểm tra và các công cụ khác đã sử dụng.]
- Tài liệu: README, GUIDE, CHECKPOINTS, RUBRIC và SUBMISSION trong repo bài học.
