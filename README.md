# Tối Ưu Hóa Lịch Học Với Thuật Toán Flamingo Search

Dự án này nhằm tối ưu hóa lịch học cho trường học hoặc đại học bằng cách sử dụng **Flamingo Search Algorithm** (FSA). Chương trình tạo ra một lịch học ban đầu dựa trên các lớp học, giảng viên, phòng học và thời gian có sẵn, sau đó cải thiện lịch học này thông qua tối ưu hóa để giảm thiểu các xung đột (như xung đột về phòng học hoặc giảng viên).

## Mục Lục
1. [Cách Hoạt Động](#cách-hoạt-động)
2. [Hướng Dẫn Sử Dụng](#hướng-dẫn-sử-dụng)
3. [Yêu Cầu Hệ Thống](#yêu-cầu-hệ-thống)



## Cách Hoạt Động

## Các Thành Phần Chính
1. **Lớp `Data`** - Quản lý và tải dữ liệu từ các file CSV (lớp học, giảng viên, phòng học, thời gian học).
2. **Lớp `Solution`** - Đại diện cho một phương án thời khóa biểu và đánh giá độ "fitness" của lịch học.
3. **Hàm `Crossover`** - Kết hợp hai phương án để tạo ra một phương án mới.
4. **Hàm `Mutation`** - Đột biến một phương án để cải thiện kết quả.
5. **Thuật toán Tìm kiếm Flamingo (FSA)** - Thuật toán tối ưu hóa metaheuristic tìm kiếm lịch học tối ưu.
6. **Thêm Ngày vào Thời Khóa Biểu** - Thêm thông tin về ngày bắt đầu và kết thúc cho từng lớp học.
7. **Ghi Thời Khóa Biểu vào File CSV** - Ghi kết quả vào file CSV.

## Các Bước Thực Thi

### 1. **Khởi Tạo Lớp `Data`**
   - **Mục đích:** Tải và lưu trữ dữ liệu từ các file CSV chứa thông tin về các lớp học, giảng viên, phòng học, và thời gian học.
   - **Phương thức:** 
     - `__init__`: Khởi tạo đối tượng `Data`, gọi các phương thức để tải dữ liệu từ các file CSV.
     - `load_csv`: Đọc dữ liệu từ các file CSV và lưu trữ vào các từ điển tương ứng, bao gồm thông tin về lớp học, giảng viên, phòng học, v.v.
     - `load_time_slots`: Tải dữ liệu về các thời gian học từ một file CSV vào một danh sách. Dữ liệu này sẽ được sử dụng để gán thời gian cho các lớp học.

### 2. **Khởi Tạo Lớp `Solution`**
   - **Mục đích:** Đại diện cho một lịch học và đánh giá độ "fitness" của lịch học đó dựa trên các yếu tố như xung đột giữa các lớp học, phòng học, giảng viên, và thời gian học.
   - **Phương thức:**
     - `__init__`: Khởi tạo đối tượng `Solution`, tính toán độ "fitness" ban đầu của lịch học.
     - `generate_initial_schedule`: Tạo lịch học ngẫu nhiên bằng cách gán lớp học, giảng viên, phòng học, và thời gian học.
     - `calculate_fitness`: Đánh giá độ "fitness" của lịch học dựa trên các tiêu chí như xung đột về phòng học, giảng viên và thời gian học. Mức độ "fitness" càng cao, lịch học càng tốt.

### 3. **Crossover (Giao Phối)**
   - **Mục đích:** Kết hợp hai phương án lịch học (từ hai đối tượng `Solution`) để tạo ra một phương án mới, giúp cải thiện lịch học.
   - **Phương thức:** 
     - Chọn một điểm cắt ngẫu nhiên trong lịch học của hai đối tượng và hoán đổi các phần tương ứng của chúng. Quá trình này tạo ra một lịch học mới, kết hợp các yếu tố tốt nhất từ cả hai phương án.

### 4. **Mutation (Đột Biến)**
   - **Mục đích:** Thực hiện đột biến trên một lịch học để cải thiện kết quả, tránh tình trạng quá trình tối ưu hóa bị dừng lại ở các phương án không tối ưu.
   - **Phương thức:** 
     - Đột biến ngẫu nhiên một lớp học trong lịch học, ví dụ thay đổi giảng viên, phòng học, hoặc thời gian học của lớp. Quá trình này tạo ra sự thay đổi nhỏ nhưng có thể giúp cải thiện độ "fitness" của lịch học.

### 5. **Thuật Toán Tìm Kiếm Flamingo (FSA)**
   - **Mục đích:** Thuật toán tối ưu hóa metaheuristic được sử dụng để tìm kiếm lịch học tối ưu trong không gian giải pháp.
   - **Phương thức:** 
     - Khởi tạo dân số ban đầu bằng cách tạo ra nhiều lịch học ngẫu nhiên.
     - Tạo các thế hệ mới bằng cách áp dụng các phép toán `crossover` và `mutation` trên các lịch học.
     - Đánh giá độ "fitness" của mỗi lịch học và lựa chọn các phương án tốt nhất để tạo thế hệ tiếp theo.
     - Lặp lại quá trình này qua nhiều thế hệ cho đến khi tìm được lịch học tối ưu.

### 6. **Thêm Ngày vào Thời Khóa Biểu**
   - **Mục đích:** Thêm thông tin về ngày bắt đầu và ngày kết thúc cho từng lớp học để hoàn thiện thời khóa biểu.
   - **Phương thức:** 
     - Tính toán ngày bắt đầu và kết thúc cho từng lớp học dựa trên thông tin về loại lớp (lý thuyết hay thực hành).
     - Lớp lý thuyết (LT) kéo dài 15 tuần, còn lớp thực hành (TH) kéo dài 10 tuần. Các ngày bắt đầu và kết thúc được gán cho từng lớp học dựa trên các quy định này.

### 7. **Ghi Lịch Học vào File CSV**
   - **Mục đích:** Lưu lịch học cuối cùng vào một file CSV để người dùng có thể dễ dàng tra cứu và sử dụng.
   - **Phương thức:** 
     - Ghi thông tin chi tiết của lịch học như lớp học, phòng học, giảng viên, thời gian học vào một file CSV. Điều này giúp người dùng có thể xem lại thời khóa biểu dễ dàng, đồng thời phục vụ cho các nhu cầu sau này như lưu trữ hoặc in ấn.

### 8. **Xử Lý Lỗi**
   - **Mục đích:** Đảm bảo chương trình hoạt động mượt mà và thông báo lỗi cho người dùng khi có vấn đề xảy ra trong quá trình tải dữ liệu hoặc tạo lịch học.
   - **Phương thức:** 
     - Nếu có lỗi khi tải các file CSV (ví dụ: file không tồn tại hoặc dữ liệu không hợp lệ), chương trình sẽ thông báo lỗi rõ ràng cho người dùng.
     - Các lỗi khi tạo lịch học (ví dụ: xung đột về phòng học, giảng viên, hoặc thời gian học) sẽ được kiểm tra và xử lý tự động để đảm bảo lịch học được tạo ra là hợp lý.


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

