# Báo cáo cá nhân — Nguyễn Văn Nhất — 2A202603278

Dữ liệu: 12 ảnh người COCO val2017 (Lin et al., 2014) và 8 ảnh chân dung Wikimedia Commons, chỉ sử dụng trong lớp.

## 0. Thông tin học viên

- Họ tên: Nguyễn Văn Nhất
- MSSV: 2A202603278
- Email: nhatnvedelz@gmail.com
- Link repository: https://github.com/Edelzz/K5-L2B-Day04-NguyenVanNhat-2A202603278-KeypointPose.git
- Phiên bản CVAT: 2.74.1
- Máy: Windows, RAM 16 GB, CVAT chế độ đầy đủ
- Bộ ảnh (`src/exports/assignment.json` do `lab.py setup` tạo): có
- Giờ bắt đầu: 16h30
- Giờ kết thúc: 18h10 

## 1. Kiểm tra label (CP0)

| Label | Kiểu | Số điểm | Tên điểm đúng bảng của lab? | Đúng thứ tự? | Số cạnh |
|---|---|---:|---|---|---:|
| `person` | Skeleton | 17 | nose, left_eye, right_eye, left_ear, right_ear, left_shoulder, right_shoulder, left_elbow, right_elbow, left_wrist, right_wrist, left_hip, right_hip, left_knee, right_knee, left_ankle, right_ankle| đúng | 19 |
| `face` | Skeleton | 13 | left_eye_outer, left_eye_inner, left_eye_upper, left_eye_lower, right_eye_outer, right_eye_inner, right_eye_upper, right_eye_lower, nose_tip, mouth_left, mouth_right, lip_upper, lip_lower | đúng | 13 |

Mẫu `person` dựng theo người quay mặt về camera (các điểm `left_*` nằm bên phải khung mẫu)? Nằm bên phải

Cách đổi cờ một điểm trên CVAT 2.74.1 (theo hướng dẫn bài lab): rê chuột vào đúng keypoint, nhấn `Q` để đánh dấu `occluded`, hoặc `O` để đánh dấu `outside`; không dùng `H`.

## 2. Số lượng đã gán và thời gian (CP1, CP2)

| Nhóm ảnh | Số ảnh | Số skeleton đã gán | Số người dưới 60 px (không gán) | Số poster / gương / màn hình bỏ qua | Thời gian (phút) |
|---|---:|---:|---:|---:|---:|
| `easy` | 5 |  |  |  |  |
| `occluded` | 3 |  | |   |
| `back` | 2 | |  |  |  |
| `small` | 1 | |  |  |  |
| `crowd` | 1 |  |  |  |  |
| `faces` | 8 | **8** | — |  |  |

**Tổng kiểm chứng từ hai file export:** 12 ảnh người với **18 skeleton `person`** và 8 ảnh mặt với **8 skeleton `face`**. Không thể xác định ảnh thuộc nhóm `easy/occluded/back/small/crowd` chỉ từ tên file COCO trong export; cần `assignment.json` hoặc bảng phân nhóm của lab để điền chính xác.

- Số ảnh người đã xong ở mốc phút 105: ** / 10**.
- Thời gian thực tế (phút): CP1 **** · CP2 **** · CP3 ****.
- Ảnh tốn thời gian nhất và lý do: ****.

## 3. Bảng ca khó (CP1, CP2)

Bảng sau để ghi các quyết định thực tế; không suy diễn cờ hoặc lý do từ dữ liệu JSON nếu không có ảnh đối chiếu.

| Ảnh | Người / mặt | Điểm | Cờ đã chọn | Phân vân giữa | Lý do chọn |
|---|---|---|---:|---|---|
| |  |  |  | `v=1` / `v=0`  |



## 4. Bảng tự review (CP3)


| Ảnh | Người / mặt | Điểm | Mã lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|---|
|  | person |  |  |  |  |
|  | person |  |  |  |  |
|  | person |  |  |  |  |
|  | person |  |  |  |  |
|  | person |  |  |  |  |
|  | face |  |  |  |  |
|  | face |  |  |  |  |
| | face |  |  | |  |

Mã hợp lệ: `lr_swap`, `vis_flag`, `position`, `missing`, `extra`, `ok`.

| `lr_swap` | `vis_flag` | `position` | `missing` | `extra` | `ok` |
|---:|---:|---:|---:|---:|---:|
| | |  | |  |  |

Điểm còn phân vân giữa `v=1` và `v=0`: 

## 5. Kiểm file xuất và kết quả tự kiểm (CP4)

Đã đọc trực tiếp `annotations/person_keypoints_default.json` bên trong cả hai ZIP và kiểm tra cấu trúc, cờ visibility, `num_keypoints`.

| File | Người / mặt kiểm (ảnh, thứ tự) | Số phần tử `keypoints` | Điểm `outside` ra `v=0`, `occluded` ra `v=1`? | `num_keypoints` khớp? |
|---|---|---:|---|---|
| `NguyenVanNhat_persons.zip` | `000000311300.jpg`, người thứ 1 theo thứ tự annotation | 51 (17 × 3) | Có: 2 điểm `v=0`, 6 điểm `v=1` | Có: 15 |
| `NguyenVanNhat_persons.zip` | `000000381889.jpg`, người thứ 1 theo thứ tự annotation | 51 (17 × 3) | Có: 7 điểm `v=0`, 2 điểm `v=1` | Có: 10 |
| `NguyenVanNhat_faces.zip` | `face_301643.jpg`, mặt thứ 1 | 39 (13 × 3) | Có: 0 điểm `v=0`, 8 điểm `v=1` | Có: 13 |

Sau khi xuất, các điểm được đánh dấu `occluded` xuất ra **`v=1`**, các điểm `outside` xuất ra **`v=0`**. Trong hai ZIP được kiểm tra, **20/20 điểm `outside` vẫn mang tọa độ cũ/khác `(0,0)`**, không phải `(0,0)`.

**Tổng kiểm tra toàn bộ export:**

| Nhóm | Ảnh | Skeleton | Keypoint `v=2` | `v=1` | `v=0` | `num_keypoints` không khớp |
|---|---:|---:|---:|---:|---:|---:|
| Person | 12 | 18 | 225 | 61 | 20 | 0 |
| Face | 8 | 8 | 95 | 9 | 0 | 0 |
| **Tổng** | **20** | **26** | **320** | **70** | **20** | **0** |

**Ghi chú:** `num_keypoints` được kiểm tra bằng số keypoint có `v > 0`; không có annotation nào sai quy tắc này. Các thống kê trên không chứng minh rằng tọa độ giải phẫu hoặc hướng trái/phải đều chính xác.

Hai job đã chuyển sang `completed` trên CVAT? Đã complete

Dán phần **TÓM TẮT** in ra từ `src/check_submission.py`:

```text
----- TÓM TẮT (dán vào báo cáo mục 5) -----
- File person: NguyenVanNhat_persons.zip
  Số ảnh: 12 · số skeleton `person`: 18 · mỗi annotation 51 số
  Skeleton theo ảnh: 000000091637=2, 000000156069=1, 000000162046=1, 000000213933=1, 000000241837=1, 000000253584=1, 000000294329=1, 000000311300=2, 000000381889=3, 000000391222=2, 000000516902=1, 000000571665=2
  Cờ v: v=2 225 (74%) · v=1 61 (20%) · v=0 20 (7%)
  num_keypoints trung bình: 15.9
- File face: NguyenVanNhat_faces.zip
  Số ảnh: 8 · số skeleton `face`: 8 · mỗi annotation 39 số
  Skeleton theo ảnh: face_137371=1, face_145751=1, face_264124=1, face_301643=1, face_3348=1, face_345145=1, face_490361=1, face_575921=1
  Cờ v: v=2 95 (91%) · v=1 9 (9%) · v=0 0 (0%)
  num_keypoints trung bình: 13.0
- Ghi chú: 20 điểm v = 0 vẫn mang tọa độ cũ (CVAT 2.x xuất như vậy; chuẩn COCO ghi 0, 0). Không phải lỗi: điểm v = 0 bị bỏ qua khi huấn luyện và khi chấm.
- Số [LỖI]: 0 · số [CẢNH BÁO]: 1
Kết quả: ĐẠT (đọc lại từng cảnh báo ở trên)
```

**Kết quả chạy `src/check_submission.py`: ĐẠT — 0 lỗi, 1 cảnh báo.**

**Cảnh báo còn giữ nguyên:** 20 keypoint có `v=0` vẫn giữ tọa độ cũ thay vì `(0, 0)`. Theo thông báo của checker, đây không phải lỗi chặn nộp vì các điểm `v=0` bị bỏ qua khi huấn luyện và đánh giá. Cần đảm bảo pipeline sử dụng cờ visibility thay vì chỉ đọc tọa độ.

## 6. Ảnh chụp màn hình

1. Label `person` trong label constructor (đủ 17 điểm có tên):

   [Lable Person] ("...\report\individual\Lable Person.png")

2. Một người quay lưng đã gán, cờ đã đặt:

   [Người quay lưng]("...\report\individual\NguoiQuayLung.png"image.png)

3. Một khuôn mặt đã gán 13 điểm, phóng to vùng mắt:

   [Khuôn mặt phóng to]("...\report\individual\KhuonMatPhongTo.png")

4. Một đoạn JSON xuất của một người:

   [JSON export](images/4_json_export.png)



Nguồn ảnh: COCO val2017 / Wikimedia Commons.

## 7. Tự đánh giá

1. **Lỗi mắc nhiều nhất và cách tránh: Không có

2. **Đề xuất bổ sung guideline:** Nên bổ sung ví dụ so sánh `v=1` (điểm bị che nhưng có thể suy luận đáng tin cậy) với `v=0` (ngoài ảnh hoặc không đủ cơ sở xác định), đặc biệt ở người quay lưng hoặc che khuất chéo. 
3. **Nhãn ảnh hưởng model thế nào:

## 8. Khó khăn và lỗi kỹ thuật

- Môi trường thực hiện: Windows, RAM 16 GB, CVAT local 2.74.1 (theo thông tin học viên).
- Khó khăn nghiệp vụ có thể gặp: phân biệt trái/phải khi người quay lưng, xử lý khớp bị che và đặt chính xác điểm trên mắt/miệng.

## Bonus (nếu làm)

### B1 — 3 ảnh người khó thêm


| Ảnh | Số skeleton | Số người dưới 60 px | Ca khó nhất |
|---|---:|---:|---|
|  | | | |
|  | | | |
|  | | | |

```text

```

### B2 — 5 ảnh khuôn mặt đen trắng / hồng ngoại

 Ảnh không màu có thể làm giảm tín hiệu màu giúp phân biệt da, mí mắt, môi và vật che. Kính râm trên ảnh hồng ngoại không mặc nhiên là `v=1`: phải căn cứ khả năng nhìn thấy điểm mắt trong chính ảnh và quy tắc visibility của lab; nếu không thể suy luận đủ tin cậy thì cân nhắc `v=0`.

### B3 — Model so với nhãn của tôi (không tính điểm)

- Demo đã dùng:
- Ảnh đã thử

1. Model có trả điểm cho khớp bị che hoặc ngoài ảnh không, confidence thế nào?
2. Với người quay lưng, model có đổi trái/phải không? 
3. Bộ điểm model có giống 17 điểm COCO không?

## 9. Tài liệu tham khảo và công cụ AI đã dùng

- Lin, T.-Y. và cộng sự (2014). *Microsoft COCO: Common Objects in Context*. https://arxiv.org/abs/1405.0312
- CVAT Documentation: https://docs.cvat.ai/
- COCO Keypoints annotation format (cấu trúc trong hai file ZIP xuất từ CVAT).
- Nguồn ảnh: COCO val2017 và Wikimedia Commons, theo mô tả bài lab.
- Công cụ: CVAT 2.74.1; ChatGPT (OpenAI) hỗ trợ đọc file ZIP, kiểm tra thống kê JSON và soạn báo cáo.
