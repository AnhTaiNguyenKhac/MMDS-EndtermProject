# MMDS-EndtermProject

### Product rating data set: ratings2k.csv


The first line is the header.
- index: row index
- user: user ID
- item: product ID
- rating: rating (0.0-5.0)

2365 remaining lines are data samples.

### 1) Câu 1: Dimensionality Reduction – SVD
Cài đặt câu này trong Task01.ipynb. 

Biểu diễn mỗi người dùng (user) trong tập dữ liệu đã cho dưới dạng sparse vector chứa các
ratings.

Sử dụng module của PySpark, ví dụ RowMatrix, để tìm ra 32 nội dung (concepts) có cường
độ lớn nhất trong tập dữ liệu dựa trên thuật toán SVD.

Mỗi concept được gán một số hiệu trong đoạn [0, 31].

Tìm ra concept ID cho từng người (user) và sản phẩm (item). Kết quả bước này được lưu
thành hai data frame: df_concept_user và df_concept_item.

Tính tỷ trọng của từng concept dựa trên số người dùng (user) và dựa trên số sản phẩm (item).
Kết quả lưu thành data frame df_concept_portion.

Tìm ra embedding cho từng người dùng (user) (sử dụng U, Σ, V) và lưu kết quả thành data
frame df_embedding_user để sử dụng cho các câu sau.

### 2) Câu 2: Clustering – CURE
Cài đặt câu này trong Task02.ipynb.

Sử dụng PySpark để cài đặt thuậ toán Clustering Using Representatives (CURE) nhằm phân
cụm user embeddings từ Task 01 (df_embedding_user).

Cài đặt một lớp đối tượng cho thuật toán trên và thực nghiệm với số lượng
điểm representatives trong đoạn [3, 8]. Với từng giá trị, tính trung bình khoảng cách từ mỗi
điểm dữ liệu đến điểm representative gần nhất (trong cluster của nó) và vẽ biểu đồ cột để
minh hoạ kết quả.

### 3) Câu 3: Recommender Systems - Collaborative Filtering
Cài đặt câu này trong Task03.ipynb.

Tạo một lớp đối tượng để cài đặt thuật toán Colaborative Filtering nhằm gợi ý sản phẩm
(item) cho người dùng (user) trong tập dữ liệu đã cho (rating2k.csv). Lưu ý rằng mỗi người
dùng (user) được biểu diễn dưới dạng sparse vector chứa các ratings.

- Phương thức khởi tạo nhận vào giá trị N (số lượng người dùng “tương tự” trong thuật
toán) và tập dữ liệu dưới dạng data frame (PySpark).
- Phương thức predict() nhận vào một người dùng (sparse vector chứa ratings) và số
lượng sản phẩm gợi ý mong muốn. Hàm trả về một data frame (PySpark) chứa các sản
phẩm được gợi ý cho người dùng theo thứ tự giảm dần độ “yêu thích”.
