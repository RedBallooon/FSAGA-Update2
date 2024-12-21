# Tối Ưu Hóa Lịch Học Với Thuật Toán Flamingo Search

Dự án này nhằm tối ưu hóa lịch học cho trường học hoặc đại học bằng cách sử dụng **Flamingo Search Algorithm** (FSA). Chương trình tạo ra một lịch học ban đầu dựa trên các lớp học, giảng viên, phòng học và thời gian có sẵn, sau đó cải thiện lịch học này thông qua tối ưu hóa để giảm thiểu các xung đột (như xung đột về phòng học hoặc giảng viên).

## Mục Lục
1. [Cách Hoạt Động](#cách-hoạt-động)
2. [Hướng Dẫn Sử Dụng](#hướng-dẫn-sử-dụng)
3. [Yêu Cầu Hệ Thống](#yêu-cầu-hệ-thống)



## Cách Hoạt Động

### 1. **Tải Dữ Liệu Đầu Vào**:
Chương trình tải các dữ liệu về các lớp học, giảng viên, phòng học và thời gian từ các tệp CSV.

### 2. **Tạo Lịch Học Ban Đầu**:
Chương trình tạo ra một lịch học ngẫu nhiên trong đó không có xung đột giữa các lớp học, phòng học và giảng viên. Mỗi lớp học sẽ được gán ngẫu nhiên một phòng học, một giảng viên, một ngày trong tuần và một khung giờ học.

### 3. **Thuật Toán Flamingo Search**:
Thuật toán **Flamingo Search Algorithm (FSA)** được sử dụng để tối ưu hóa lịch học ban đầu. Thuật toán này tìm kiếm giải pháp tối ưu bằng cách cân bằng giữa việc khám phá không gian giải pháp (exploration) và khai thác (exploitation), đảm bảo giải pháp vừa đa dạng vừa tối ưu.

### 4. **Tính Toán Ngày Bắt Đầu và Kết Thúc**:
Chương trình tính toán ngày bắt đầu và kết thúc của mỗi lớp học dựa trên loại phòng học (Giảng dạy lý thuyết - LT, Thực hành - TH). Mỗi phòng LT có thời gian học kéo dài 15 tuần, trong khi TH bắt đầu muộn hơn và kéo dài 10 tuần.

### 5. **Xuất Lịch Học Cuối Cùng**:
Lịch học đã được tối ưu hóa sẽ được lưu vào một tệp CSV, trong đó bao gồm thông tin về các lớp học, phòng học, giảng viên và thời gian học.

## Hướng Dẫn Sử Dụng

### Bước 1: Chuẩn Bị Các Tệp Dữ Liệu Đầu Vào

Bạn cần có bốn tệp CSV sau đây:

1. **classes.csv**: Chứa thông tin về các lớp học.
   - Cột: `class_id`, `course_id`, `class_name`
   
2. **instructors.csv**: Chứa thông tin về các giảng viên.
   - Cột: `instructor_id`, `fullname`, `email`
   
3. **rooms.csv**: Chứa thông tin về các phòng học.
   - Cột: `room_id`, `name`, `type` (LT hoặc TH), `capacity`
   
4. **timeslots.csv**: Chứa thông tin về các khung giờ.
   - Cột: `TietTrongKhungGio`, `start_time`, `end_time`

### Bước 2: Chạy Chương Trình

1. Clone repository này hoặc tải mã nguồn về máy tính của bạn.
2. Đặt các tệp dữ liệu đầu vào vào cùng thư mục với mã nguồn.
3. Mở terminal hoặc command prompt và di chuyển đến thư mục chứa mã nguồn.
4. Chạy chương trình:
   ```bash
   python fixed_timtable.py
5. Sau khi chương trình chạy, bạn sẽ được yêu cầu nhập ngày bắt đầu của học kỳ theo định dạng YYYY-MM-DD. Ví dụ:
   ```bash
   Vui lòng nhập ngày bắt đầu (YYYY-MM-DD): 2024-01-01

### Bước 3: Kiểm Tra Kết Quả
Sau khi chương trình chạy xong, lịch học tối ưu sẽ được lưu vào một tệp CSV có tên `schedule.csv`.

### Bước 4: Tùy Chỉnh Hoặc Thay Đổi Tham Số
Bạn có thể điều chỉnh các tham số của Flamingo Search Algorithm (ví dụ: kích thước quần thể, tỷ lệ đột biến, số thế hệ) để tinh chỉnh quá trình tối ưu hóa.

## Yêu Cầu Hệ Thống

Chương trình yêu cầu Python 3.x trở lên và các thư viện sau:

1. pandas
2. random
3. csv
4. math
5. datetime

Để cài đặt các thư viện yêu cầu, bạn chỉ cần sử dụng file `requirements.txt`. Chạy lệnh sau trong terminal hoặc command prompt:

```bash
pip install -r requirements.txt

