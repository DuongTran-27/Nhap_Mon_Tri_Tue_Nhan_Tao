# Bài toán N quân hậu – Thuật toán Quay lui

## Giới thiệu

File `TH_2.ipynb` là một notebook Python giải bài toán **N quân hậu** bằng thuật toán **quay lui (Backtracking)**.  
Bài toán yêu cầu đặt N quân hậu lên bàn cờ kích thước N x N sao cho không có quân hậu nào tấn công nhau (tức là không cùng hàng, cột, hoặc đường chéo).

## Nội dung chính

Chương trình bao gồm các thành phần sau:

- **`is_valid_state(state, N)`**: Kiểm tra xem trạng thái hiện tại có đủ N quân hậu không.
- **`get_candidates(state, N)`**: Tìm các cột an toàn để đặt quân hậu tiếp theo.
- **`search(state, solutions, N)`**: Áp dụng đệ quy và quay lui để tìm tất cả lời giải.
- **`solve(N)`**: Gọi hàm `search` và trả về toàn bộ lời giải.
- **Hàm `main`**:
  - Nhập số quân hậu từ người dùng
  - Gọi hàm `solve` để tìm tất cả lời giải
  - In tổng số lời giải
  - Lấy ngẫu nhiên 2 lời giải và in ra theo dạng tọa độ `(row, col)`

## Cách sử dụng

1. Mở file `TH_2.ipynb` bằng Jupyter Notebook hoặc Google Colab.
2. Chạy từng ô (cell) từ trên xuống.
3. Khi được yêu cầu, nhập vào giá trị `N` là số quân hậu.
4. Chương trình sẽ in ra:
   - Tổng số lời giải tìm được
   - Hai lời giải ngẫu nhiên dưới dạng tọa độ

## Ví dụ kết quả

Nhập vào số quân hậu N = 4

Tổng số lời giải tìm được: 2

Lời giải 1:
Tọa độ các quân hậu: [(0, 1), (1, 3), (2, 0), (3, 2)]

Lời giải 2:
Tọa độ các quân hậu: [(0, 2), (1, 0), (2, 3), (3, 1)]
