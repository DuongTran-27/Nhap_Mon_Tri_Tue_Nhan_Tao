##README - Bài toán N quân hậu
Giới thiệu
File TH_2.ipynb là notebook Jupyter dùng để giải bài toán N quân hậu bằng thuật toán quay lui (Backtracking). Bài toán đặt ra là: với một bàn cờ kích thước N x N, làm sao để đặt N quân hậu sao cho không có hai quân nào tấn công nhau (khác hàng, cột, và đường chéo).

Nội dung chính
Chương trình gồm các phần chính sau:

Hàm is_valid_state(state, N): Kiểm tra xem trạng thái hiện tại đã đủ N quân hậu hay chưa.

Hàm get_candidates(state, N): Trả về danh sách các cột có thể đặt quân hậu tiếp theo mà không bị tấn công.

Hàm search(state, solutions, N): Áp dụng thuật toán quay lui để tìm các lời giải hợp lệ.

Hàm solve(N): Gọi hàm search và trả về toàn bộ lời giải.

Hàm main:

Nhập vào số quân hậu N.

Tìm tất cả lời giải với solve(N).

In ra tổng số lời giải tìm được.

Lấy ngẫu nhiên 2 lời giải và in ra dưới dạng tọa độ (row, col).

Cách sử dụng
Mở file TH_2.ipynb trong môi trường Jupyter Notebook hoặc Google Colab.

Chạy từng ô theo thứ tự từ trên xuống.

Khi được yêu cầu, nhập giá trị N (số quân hậu).

Xem kết quả in ra bao gồm số lời giải và tọa độ 2 lời giải ngẫu nhiên.
