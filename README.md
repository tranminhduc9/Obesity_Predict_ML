## Tiền xử lý dữ liệu

### 1. Xóa cột không cần thiết
- Xóa cột `id` (không có giá trị cho việc dự đoán)

### 2. Chuẩn hóa Age, Height, Weight
- **Age (Tuổi)**: Làm tròn xuống số nguyên bằng `np.floor()`
- **Height (Chiều cao)**: Làm tròn đến 2 chữ số thập phân
- **Weight (Cân nặng)**: Làm tròn đến 2 chữ số thập phân

### 3. Mã hóa dữ liệu Category

#### 3.1. Ordinal Encoding (CAEC, CALC)
Mã hóa thứ tự theo mức độ tăng dần:
- **CAEC** (Consumption of food between meals): no=0, Sometimes=1, Frequently=2, Always=3
- **CALC** (Consumption of alcohol): no=0, Sometimes=1, Frequently=2

#### 3.2. One-Hot Encoding (MTRANS)
Tạo các cột nhị phân (0/1):
- `MTRANS_Automobile`
- `MTRANS_Bike`
- `MTRANS_Motorbike`
- `MTRANS_Public_Transportation`
- `MTRANS_Walking`

Sau khi mã hóa, cột `MTRANS` gốc được xóa để tránh dư thừa.

### 4. Chuẩn hóa dữ liệu nhị phân
Chuyển đổi các giá trị yes/no và Female/Male thành 0/1:
- `Gender`: Female=0, Male=1
- `family_history_with_overweight`: no=0, yes=1
- `FAVC` (Frequent consumption of high caloric food): no=0, yes=1
- `SMOKE`: no=0, yes=1
- `SCC` (Calories consumption monitoring): no=0, yes=1

### 5. Chuẩn hóa nhãn (Label)
- Sử dụng `LabelEncoder` để mã hóa cột `NObeyesdad` (mức độ béo phì) thành các giá trị số

## Phân tích và Trực quan hóa

### 1. Phân bố dữ liệu
- **Nhãn**: Phân bố cân bằng giữa 7 loại béo phì (10-20% mỗi loại)
- **Biến liên tục**: Age lệch phải (tập trung ở nhóm trẻ), Height và Weight phân bố chuẩn
- **Biến category**: Gender cân bằng, MTRANS tập trung ở phương tiện công cộng

### 2. Biểu đồ
- Histogram cho các biến liên tục
- Pie chart (donut) cho các biến category
- Phân biệt màu sắc theo nhãn

## Giảm chiều dữ liệu

### 1. PCA (Principal Component Analysis)
- Giảm từ 8 chiều (biến liên tục) xuống 4 chiều
- Phương pháp unsupervised (không dùng nhãn)
- Giữ lại phương sai tổng thể của dữ liệu
- **Ưu điểm**: Giảm nhiễu, loại bỏ đa cộng tuyến
- **Nhược điểm**: Các lớp vẫn chồng lấn, không tối ưu cho phân loại

### 2. LDA (Linear Discriminant Analysis)
- Giảm từ 8 chiều (biến liên tục) xuống 4 chiều
- Phương pháp supervised (sử dụng nhãn)
- Tối đa hóa khả năng phân biệt giữa các lớp
- **Ưu điểm**: Tách biệt các lớp rõ ràng, tối ưu cho phân loại
- **Nhược điểm**: Cần có nhãn, giả định phân phối chuẩn

### 3. Kết luận
- **LDA phù hợp hơn** cho bài toán phân loại béo phì vì tách biệt các lớp tốt hơn


