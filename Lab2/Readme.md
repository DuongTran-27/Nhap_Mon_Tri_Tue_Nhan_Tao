BFS-DFS Notebook – Thuật toán Tìm Kiếm theo Chiều Rộng và Chiều Sâu
Giới thiệu
Notebook này triển khai hai thuật toán tìm kiếm phổ biến trên đồ thị: BFS (Breadth-First Search) và DFS (Depth-First Search). Thông qua các ví dụ trực quan và phần thực hành mã Python, người học sẽ nắm rõ cách các thuật toán hoạt động trên đồ thị có trọng số và không trọng số.

Công nghệ & Thư viện Sử dụng
Ngôn ngữ & Môi trường: Python 3.7+, chạy trên Jupyter Notebook hoặc Google Colab

Thư viện chuẩn Python:

collections.deque: hàng đợi cho BFS, ngăn xếp cho DFS

collections.defaultdict: hỗ trợ lưu đồ thị

heapq: dùng cho hàng đợi ưu tiên

time, statistics: đo thời gian thực thi, phân tích hiệu năng

typing: chú thích kiểu dữ liệu

Markdown + Mermaid: hỗ trợ vẽ sơ đồ đồ thị minh họa trực quan

Chức năng Chính
Thuật toán BFS – Breadth First Search
Duyệt đồ thị theo từng tầng

Sử dụng hàng đợi FIFO

Đảm bảo tìm được đường đi ngắn nhất (tính theo số bước) trên đồ thị không trọng số

Hàm sử dụng:

python
Sao chép
Chỉnh sửa
bfs(graph, start, goal)
bfs_weighted(graph, start, goal)
Thuật toán DFS – Depth First Search
Duyệt sâu vào từng nhánh trước khi quay lại

Sử dụng đệ quy (tương đương với ngăn xếp)

Không đảm bảo ngắn nhất

Hàm sử dụng:

python
Sao chép
Chỉnh sửa
dfs(graph, start, goal)
dfs_weighted(graph, start, goal)
Cách Chạy Notebook
Tải file .ipynb về và mở bằng Jupyter Notebook hoặc Google Colab

Chạy tuần tự từng cell theo thứ tự từ trên xuống

Tương tác: sửa cấu trúc đồ thị hoặc điểm bắt đầu / kết thúc để thử nghiệm

Cấu trúc Nội dung Notebook
Phần 1: Lý thuyết về BFS và DFS

Phần 2: Sơ đồ minh họa (dùng Mermaid)

Phần 3: Triển khai Python và chạy thử trên đồ thị mẫu

Phần 4: Bài tập mở rộng như:

Sửa BFS để đếm số nút đã duyệt

Thử nghiệm với đồ thị do người dùng thiết kế

Cấu trúc Dữ liệu
Đồ thị: sử dụng danh sách kề (adjacency list) – dict[str, list[str]]

Hàng đợi (BFS): dùng collections.deque

Ngăn xếp (DFS): dùng đệ quy hoặc deque (append/pop)

Tập đã thăm: dùng set để tránh duyệt lại các đỉnh

So sánh BFS vs DFS
Đặc điểm	BFS	DFS
Chiến lược duyệt	Theo tầng (từ gần đến xa)	Theo chiều sâu từng nhánh
Cấu trúc hỗ trợ	Hàng đợi (Queue)	Đệ quy / Ngăn xếp (Stack)
Tìm đường đi ngắn nhất	Có	Không
Hiệu quả trên đồ thị sâu	Tốn bộ nhớ	Đi sâu nhanh hơn
Hữu ích trong	Tìm đường ngắn, lan truyền, AI	Backtracking, tìm trạng thái

Mục đích Ứng dụng
Giáo dục & Học tập: Dành cho môn học Nhập môn Trí tuệ Nhân tạo hoặc Cấu trúc Dữ liệu & Giải thuật

Thực tiễn:

Tìm đường trong mê cung, bản đồ

Duyệt mạng xã hội, cây phân cấp

Bài toán tìm kiếm trạng thái như giải Sudoku, N quân hậu

