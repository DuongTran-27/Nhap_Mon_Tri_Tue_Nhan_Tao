Công nghệ và Thư viện Sử dụng
Ngôn ngữ: Python 3.7 trở lên, chạy trên Jupyter Notebook hoặc Google Colab.

Thư viện chuẩn Python:

collections.deque: Hàng đợi cho BFS, ngăn xếp cho DFS.

collections.defaultdict: Biểu diễn đồ thị có trọng số.

heapq: Hàng đợi ưu tiên (cho các bài toán nâng cao).

time, statistics: Đo thời gian chạy và phân tích hiệu năng.

typing: Chú thích kiểu dữ liệu.

Mermaid trong Markdown: Dùng để vẽ sơ đồ đồ thị minh họa trong notebook.

Chức năng Chính
Notebook triển khai hai thuật toán tìm kiếm cơ bản trên đồ thị vô hướng:

1. BFS (Breadth-First Search)
Duyệt theo chiều rộng (từng tầng).

Sử dụng hàng đợi FIFO.

Hàm bfs(graph, start, goal) trả về đường đi ngắn nhất về số bước trong đồ thị không trọng số.

Hàm bfs_weighted(graph, start, goal) áp dụng cho đồ thị có trọng số nhưng không đảm bảo tối ưu trọng số.

2. DFS (Depth-First Search)
Duyệt theo chiều sâu, ưu tiên đi sâu trước.

Cài đặt bằng đệ quy hoặc ngăn xếp.

Hàm dfs(graph, start, goal) tìm một đường đi bất kỳ từ đỉnh bắt đầu đến đỉnh đích.

dfs_weighted(graph, start, goal) áp dụng trên đồ thị có trọng số (không đảm bảo ngắn nhất).

Cách Chạy Notebook
Mở notebook: Tải file .ipynb và mở bằng Jupyter Notebook hoặc Google Colab.

Chạy lần lượt các ô mã:

Phần lý thuyết: Trình bày khái quát về BFS, DFS, đồ thị trọng số và không trọng số.

Minh họa thủ công: Mô phỏng bước duyệt bằng sơ đồ Mermaid, thể hiện hàng đợi/ngăn xếp và tập visited.

Triển khai mã Python: Định nghĩa hàm và chạy thử trên đồ thị mẫu để kiểm chứng kết quả.

Tương tác: Thay đổi dữ liệu đồ thị, start/goal, chỉnh sửa thuật toán để thử nghiệm thêm (ví dụ: đếm số nút đã thăm, đo thời gian chạy...).

Cấu trúc Dữ liệu Sử dụng
Biểu diễn đồ thị: Dạng dictionary với danh sách kề. Ví dụ: { 'S': ['A', 'B'] }.

Với đồ thị có trọng số: dùng danh sách các cặp (đỉnh_kề, trọng_số).

Hàng đợi (Queue): Dùng deque cho BFS.

Ngăn xếp (Stack): Thường dùng đệ quy cho DFS; hoặc cũng có thể dùng deque.

Tập đã thăm (visited): Được sử dụng để tránh lặp vô hạn, đặc biệt trong đồ thị có chu trình.

Mục Đích và Ứng Dụng
Notebook được thiết kế phục vụ học phần nhập môn Trí tuệ Nhân tạo, giúp người học:

Hiểu và cài đặt thuật toán BFS, DFS trên các loại đồ thị cơ bản.

So sánh đặc điểm của hai thuật toán:

BFS tìm đường đi ngắn nhất về số bước trên đồ thị không trọng số.

DFS phù hợp khi cần khám phá sâu hoặc giải bài toán thử-sai (backtracking).

Nhận ra giới hạn của BFS/DFS trên đồ thị có trọng số, từ đó biết khi nào nên dùng các thuật toán như Dijkstra, A*.

Ứng dụng vào các bài toán như tìm đường đi trong mê cung, lưới, mạng máy tính, và duyệt không gian trạng thái.
