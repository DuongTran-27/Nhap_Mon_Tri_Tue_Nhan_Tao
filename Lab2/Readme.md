# BFS-DFS Notebook – Thuật toán Tìm kiếm theo Chiều Rộng và Chiều Sâu

## Giới thiệu

Notebook này triển khai hai thuật toán tìm kiếm phổ biến trên đồ thị:

- **BFS** (Breadth-First Search – Tìm kiếm theo chiều rộng)
- **DFS** (Depth-First Search – Tìm kiếm theo chiều sâu)

Thông qua các ví dụ trực quan và phần thực hành mã Python, người học sẽ nắm được cách hoạt động của các thuật toán trên đồ thị có trọng số và không trọng số.

## Công nghệ & Thư viện Sử dụng

**Ngôn ngữ & Môi trường:**  
- Python 3.7 trở lên  
- Jupyter Notebook hoặc Google Colab

**Thư viện sử dụng:**
- `collections.deque`: hàng đợi cho BFS, ngăn xếp cho DFS
- `collections.defaultdict`: lưu trữ danh sách kề của đồ thị
- `heapq`: hỗ trợ hàng đợi ưu tiên (mở rộng)
- `time`, `statistics`: đo thời gian và phân tích hiệu suất
- `typing`: chú thích kiểu dữ liệu
- `Markdown + Mermaid`: vẽ sơ đồ đồ thị minh họa trực quan

## Chức năng Chính

### Thuật toán BFS – Breadth-First Search
- Duyệt đồ thị theo từng tầng (từ đỉnh gần đến xa)
- Sử dụng hàng đợi FIFO
- Tìm được đường đi ngắn nhất (tính theo số bước) trên đồ thị không trọng số

**Hàm:**
bfs(graph, start, goal)
bfs_weighted(graph, start, goal)
Thuật toán DFS – Depth-First Search
Duyệt sâu từng nhánh trước khi quay lại

Sử dụng đệ quy (hoặc ngăn xếp)

Không đảm bảo đường đi ngắn nhất

Hàm:

python
Sao chép
Chỉnh sửa
dfs(graph, start, goal)
dfs_weighted(graph, start, goal)
