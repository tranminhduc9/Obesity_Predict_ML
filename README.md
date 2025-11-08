## Tiền xử lý dữ liệu

### 1. Xóa cột không cần thiết
- Xóa cột `id` (không có giá trị cho việc dự đoán)

### 2. Chuẩn hóa Age, Height, Weight
- **Age (Tuổi)**: Làm tròn xuống số nguyên bằng `np.floor()`
- **Height (Chiều cao)**: Làm tròn đến 2 chữ số thập phân
- **Weight (Cân nặng)**: Làm tròn đến 2 chữ số thập phân

### 3. Mã hóa dữ liệu Category
Sử dụng `LabelEncoder` để chuyển đổi các cột category sang số:
- `CAEC` (Consumption of food between meals)
- `CALC` (Consumption of alcohol)
- `MTRANS` (Transportation used)

### 4. Chuẩn hóa dữ liệu nhị phân
Chuyển đổi các giá trị yes/no và Female/Male thành 0/1:
- `Gender`: Female=0, Male=1
- `family_history_with_overweight`: no=0, yes=1
- `FAVC` (Frequent consumption of high caloric food): no=0, yes=1
- `SMOKE`: no=0, yes=1
- `SCC` (Calories consumption monitoring): no=0, yes=1

### 5. Chuẩn hóa nhãn (Label)
- Sử dụng `LabelEncoder` để mã hóa cột `NObeyesdad` (mức độ béo phì) thành các giá trị số


