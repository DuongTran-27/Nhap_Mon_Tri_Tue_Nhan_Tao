Phần code của Lab1:Thuật Toán Tìm Kiếm Mù - Nhập Môn Trí Tuệ Nhân Tạo
Bài Tập Lập Trình
1. Viết mã Python để chạy BFS và DFS trên **Đồ thị mẫu 6** và **Đồ thị mẫu 7**. Định nghĩa đồ thị dưới dạng từ điển và thêm chú thích chi tiết.
# Đồ thị 6 BFS
from collections import deque

def bfs_weighted(graph, start, goal):
    queue = deque([(start, [start], 0)])
    visited = set([start])
    
    while queue:
        (node, path, total_weight) = queue.popleft()
        if node == goal:
            return path, total_weight
        for neighbor, weight in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, path + [neighbor], total_weight + weight))
    return None, 0

# Định nghĩa Đồ thị mẫu 6 (có trọng số)
graph6 = {
    'S': [('A', 2), ('C', 5)],
    'A': [('S', 2), ('D', 4), ('B', 3)],
    'B': [('A', 3), ('E', 6)],
    'C': [('S', 5), ('D', 7), ('F', 9)],
    'D': [('A', 4), ('E', 8), ('C', 7)],
    'E': [('B', 6), ('D', 8), ('H', 10)],
    'F': [('C', 9), ('G', 12)],
    'G': [('F', 12), ('H', 15)],
    'H': [('E', 10), ('G', 15)]
}

# Chạy BFS và in kết quả
path, weight = bfs_weighted(graph6, 'S', 'H')
print("Đường đi BFS trên Đồ thị mẫu 6:", path, "Tổng trọng số:", weight)
#DFS đồ thị 6
def dfs_weighted(graph, start, goal, visited=None, path=None, total_weight=0):
    # Khởi tạo tập đã thăm và đường đi nếu chưa có
    if visited is None:
        visited = set()
    if path is None:
        path = [start]
    
    # Thêm nút hiện tại vào tập đã thăm
    visited.add(start)
    # Kiểm tra nếu nút hiện tại là đích
    if start == goal:
        return path, total_weight
    
    # Duyệt qua các nút kề và trọng số tương ứng
    for neighbor, weight in graph[start]:
        # Nếu nút kề chưa được thăm
        if neighbor not in visited:
            # Gọi đệ quy DFS trên nút kề với đường đi và tổng trọng số mới
            new_path, new_weight = dfs_weighted(graph, neighbor, goal, visited, path + [neighbor], total_weight + weight)
            # Nếu tìm thấy đường đi, trả về
            if new_path:
                return new_path, new_weight
    # Trả về None và 0 nếu không tìm thấy đường đi
    return None, 0

# Định nghĩa Đồ thị mẫu 6 (có trọng số)
graph6 = {
    'S': [('A', 2), ('C', 5)],
    'A': [('S', 2), ('D', 4), ('B', 3)],
    'B': [('A', 3), ('E', 6)],
    'C': [('S', 5), ('D', 7), ('F', 9)],
    'D': [('A', 4), ('E', 8), ('C', 7)],
    'E': [('B', 6), ('D', 8), ('H', 10)],
    'F': [('C', 9), ('G', 12)],
    'G': [('F', 12), ('H', 15)],
    'H': [('E', 10), ('G', 15)]
}

# Chạy DFS và in kết quả
path, weight = dfs_weighted(graph6, 'S', 'H')
print("Đường đi DFS trên Đồ thị mẫu 6:", path, "Tổng trọng số:", weight)

2. Sửa mã BFS để lưu và in tất cả các đường đi từ S đến H trên **Đồ thị mẫu 7** (không trọng số). Đảm bảo mã có chú thích đầy đủ.
from collections import deque  # Dùng deque để tạo hàng đợi cho BFS

def bfs(graph, start, goal):
    queue = deque([(start, [start])])  # Hàng đợi lưu (nút hiện tại, đường đi từ start)
    visited = set([start])  # Tập hợp để tránh thăm lại nút đã duyệt

    while queue:
        node, path = queue.popleft()  # Lấy phần tử đầu hàng đợi
        if node == goal:              # Nếu đến đích thì trả về đường đi
            return path
        for neighbor in graph[node]:  # Duyệt các nút kề
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, path + [neighbor]))  # Thêm vào hàng đợi đường đi mới

    return None  # Không tìm thấy đường đi

# Đồ thị mẫu 7 (không trọng số, mật độ cạnh cao)
graph7 = {
    'S': ['A', 'D', 'E'],
    'A': ['B', 'D', 'E'],
    'B': ['C', 'E', 'F'],
    'C': ['F', 'G'],
    'D': ['E'],
    'E': ['F', 'H'],
    'F': ['G', 'H'],
    'G': ['H'],
    'H': []
}

# Chạy BFS từ S đến H
path_bfs = bfs(graph7, 'S', 'H')
print("Đường đi BFS trên Đồ thị mẫu 7:", path_bfs)
def dfs(graph, start, goal, visited=None, path=None):
    if visited is None:
        visited = set()  # Khởi tạo tập đã thăm để tránh lặp vô hạn
    if path is None:
        path = [start]   # Khởi tạo đường đi hiện tại
    
    visited.add(start)    # Đánh dấu nút hiện tại là đã thăm
    
    if start == goal:     # Nếu đã tới đích thì trả về đường đi
        return path

    for neighbor in graph[start]:  # Duyệt các nút kề
        if neighbor not in visited:
            new_path = dfs(graph, neighbor, goal, visited, path + [neighbor])
            if new_path:  # Nếu tìm được đường đi thì trả về
                return new_path

    return None  # Không tìm thấy đường đi nào từ nhánh hiện tại

# Đồ thị mẫu 7 (không trọng số, mật độ cạnh cao)
graph7 = {
    'S': ['A', 'D', 'E'],
    'A': ['B', 'D', 'E'],
    'B': ['C', 'E', 'F'],
    'C': ['F', 'G'],
    'D': ['E'],
    'E': ['F', 'H'],
    'F': ['G', 'H'],
    'G': ['H'],
    'H': []
}

# In kết quả DFS
print("Đường đi DFS trên Đồ thị mẫu 7:", dfs(graph7, 'S', 'H'))

3. Thêm một cạnh mới vào **Đồ thị mẫu 6** (ví dụ: B-H với trọng số 20). Chạy lại BFS và DFS, phân tích sự thay đổi trong đường đi và tổng trọng số.
#Đây là đồ thị 6 khi thêm cạnh B-H có trọng số là 20. BFS:
from collections import deque

def bfs_weighted(graph, start, goal):
    queue = deque([(start, [start], 0)])
    visited = set([start])
    
    while queue:
        (node, path, total_weight) = queue.popleft()
        if node == goal:
            return path, total_weight
        for neighbor, weight in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, path + [neighbor], total_weight + weight))
    return None, 0

# Định nghĩa Đồ thị mẫu 6 (có trọng số)
graph6 = {
    'S': [('A', 2), ('C', 5)],
    'A': [('B', 3), ('D', 4)],
    'B': [('E', 6), ('H', 20)],  # thêm cạnh mới B → H
    'C': [('D', 7), ('F', 9)],
    'D': [('E', 8)],
    'E': [('H', 10)],
    'F': [('G', 12)],
    'G': [('H', 15)],
    'H': []
}
# Chạy BFS và in kết quả
path, weight = bfs_weighted(graph6, 'S', 'H')
print("Đường đi BFS trên Đồ thị mẫu 6:", path, "Tổng trọng số:", weight)
def dfs_weighted(graph, current, goal, visited=None, path=None, cost=0):
    if visited is None:
        visited = set()
    if path is None:
        path = [current]
    if current == goal:
        return path, cost

    visited.add(current)
    for neighbor, weight in graph[current].items():
        if neighbor not in visited:
            result = dfs_weighted(graph, neighbor, goal, visited.copy(), path + [neighbor], cost + weight)
            if result:
                return result
    return None, float('inf')

graph6 = {
    'S': {'A': 2, 'C': 5},
    'A': {'B': 3, 'D': 4},
    'B': {'E': 6, 'H': 20},  # thêm cạnh mới B -> H (20)
    'C': {'D': 7, 'F': 9},
    'D': {'E': 8},
    'E': {'H': 10},
    'F': {'G': 12},
    'G': {'H': 15},
    'H': {}
}


# Chạy DFS
path_dfs, cost_dfs = dfs_weighted(graph6, 'S', 'H')
print("Một đường đi bằng DFS:", path_dfs)
print("Tổng trọng số:", cost_dfs)
Trước khi thêm:
Đường đi ngắn nhất: S → A → B → E → H
Tổng trọng số: 2 + 3 + 6 + 10 = 21

Sau khi thêm B → H (20):
Vẫn đi S → A → B → E → H là ngắn nhất (21).
Đường S → A → B → H có trọng số: 2 + 3 + 20 = 25 → không ngắn hơn.
DFS có thể đi qua cạnh B-H, làm cho đường đi dài hơn.
### Bài Tập Nâng Cao
1. Đo thời gian chạy của BFS và DFS trên **Đồ thị mẫu 6** và **Đồ thị mẫu 7** bằng thư viện `time`. So sánh hiệu suất và thêm chú thích vào mã.
#Đồ thị 6 DFS có thư viện time
def dfs_weighted(graph, start, goal, visited=None, path=None, weight=0):
    if visited is None:
        visited = set()
    if path is None:
        path = [start]
    if start == goal:
        return path, weight
    visited.add(start)
    for neighbor, w in graph[start]:
        if neighbor not in visited:
            result_path, total_weight = dfs_weighted(graph, neighbor, goal, visited.copy(), path + [neighbor], weight + w)
            if result_path:
                return result_path, total_weight
    return None, 0
graph6 = {
    'S': [('A', 2), ('C', 5)],
    'A': [('S', 2), ('D', 4), ('B', 3)],
    'B': [('A', 3), ('E', 6)],
    'C': [('S', 5), ('D', 7), ('F', 9)],
    'D': [('A', 4), ('E', 8), ('C', 7)],
    'E': [('B', 6), ('D', 8), ('H', 10)],
    'F': [('C', 9), ('G', 12)],
    'G': [('F', 12), ('H', 15)],
    'H': [('E', 10), ('G', 15)]
}

start_time = time.time()
path, weight = dfs_weighted(graph6, 'S', 'H')
end_time = time.time()

print("Đường đi:", path)
print("Tổng trọng số:", weight)
print("Thời gian chạy:", end_time - start_time, "giây")
#Đồ thị 6 BFS có thư viện time
import time
from collections import deque

def bfs_weighted(graph, start, goal):
    queue = deque([(start, [start], 0)])
    visited = set([start])
    while queue:
        node, path, total_weight = queue.popleft()
        if node == goal:
            return path, total_weight
        for neighbor, weight in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, path + [neighbor], total_weight + weight))
    return None, 0

graph6 = {
    'S': [('A', 2), ('C', 5)],
    'A': [('S', 2), ('D', 4), ('B', 3)],
    'B': [('A', 3), ('E', 6)],
    'C': [('S', 5), ('D', 7), ('F', 9)],
    'D': [('A', 4), ('E', 8), ('C', 7)],
    'E': [('B', 6), ('D', 8), ('H', 10)],
    'F': [('C', 9), ('G', 12)],
    'G': [('F', 12), ('H', 15)],
    'H': [('E', 10), ('G', 15)]
}

start_time = time.time()
path, weight = bfs_weighted(graph6, 'S', 'H')
end_time = time.time()
#Đồ thị 7 BFS có thư viện time
def bfs_unweighted(graph, start, goal):
    queue = deque([(start, [start])])
    visited = set([start])
    while queue:
        node, path = queue.popleft()
        if node == goal:
            return path
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, path + [neighbor]))
    return None

graph7 = {
    'S': ['A', 'D', 'E'],
    'A': ['B', 'D', 'E'],
    'B': ['C', 'E', 'F'],
    'C': ['F', 'G'],
    'D': ['E'],
    'E': ['F', 'H'],
    'F': ['G', 'H'],
    'G': ['H'],
    'H': []
}

start_time = time.time()
path = bfs_unweighted(graph7, 'S', 'H')
end_time = time.time()
#Đồ thị 7 DFS có thư viện time
def dfs_unweighted(graph, start, goal, visited=None, path=None):
    if visited is None:
        visited = set()
    if path is None:
        path = [start]
    if start == goal:
        return path
    visited.add(start)
    for neighbor in graph[start]:
        if neighbor not in visited:
            result_path = dfs_unweighted(graph, neighbor, goal, visited.copy(), path + [neighbor])
            if result_path:
                return result_path
    return None
graph7 = {
    'S': ['A', 'D', 'E'],
    'A': ['B', 'D', 'E'],
    'B': ['C', 'E', 'F'],
    'C': ['F', 'G'],
    'D': ['E'],
    'E': ['F', 'H'],
    'F': ['G', 'H'],
    'G': ['H'],
    'H': []
}
start_time = time.time()
path = dfs_unweighted(graph7, 'S', 'H')
end_time = time.time()


print("Đường đi:", path)
print("Thời gian chạy:", end_time - start_time, "giây")

print("Đường đi:", path)
print("Thời gian chạy:", end_time - start_time, "giây")

print("Đường đi:", path)
print("Tổng trọng số:", weight)
print("Thời gian chạy:", end_time - start_time, "giây")

2. Thiết kế một đồ thị có trọng số với ít nhất 10 nút và 15 cạnh. Chạy BFS và DFS, phân tích đường đi và tổng trọng số. Đảm bảo mã có chú thích chi tiết.

# Đồ thị có 10 nút: S, A, B, C, D, E, F, G, H, I
# 15 cạnh có trọng số

from collections import deque

# Đồ thị trọng số (10 nút, 15 cạnh)
graph = {
    'S': [('A', 4), ('B', 2)],
    'A': [('S', 4), ('C', 3), ('D', 2)],
    'B': [('S', 2), ('D', 4), ('E', 6)],
    'C': [('A', 3), ('F', 5)],
    'D': [('A', 2), ('B', 4), ('F', 1), ('G', 3)],
    'E': [('B', 6), ('G', 2), ('H', 5)],
    'F': [('C', 5), ('D', 1), ('I', 4)],
    'G': [('D', 3), ('E', 2), ('I', 6)],
    'H': [('E', 5), ('I', 1)],
    'I': [('F', 4), ('G', 6), ('H', 1)]
}

def bfs_weighted(graph, start, goal):
    queue = deque([(start, [start], 0)])
    visited = set([start])

    while queue:
        node, path, total_weight = queue.popleft()
        if node == goal:
            return path, total_weight
        for neighbor, weight in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, path + [neighbor], total_weight + weight))
    return None, 0

# Chạy BFS từ S đến I
path, weight = bfs_weighted(graph, 'S', 'I')
print("BFS - Đường đi từ S đến I:", path)
print("BFS - Tổng trọng số:", weight)
# Đồ thị trọng số (10 nút, 15 cạnh)
graph = {
    'S': [('A', 4), ('B', 2)],
    'A': [('S', 4), ('C', 3), ('D', 2)],
    'B': [('S', 2), ('D', 4), ('E', 6)],
    'C': [('A', 3), ('F', 5)],
    'D': [('A', 2), ('B', 4), ('F', 1), ('G', 3)],
    'E': [('B', 6), ('G', 2), ('H', 5)],
    'F': [('C', 5), ('D', 1), ('I', 4)],
    'G': [('D', 3), ('E', 2), ('I', 6)],
    'H': [('E', 5), ('I', 1)],
    'I': [('F', 4), ('G', 6), ('H', 1)]
}

def dfs_weighted(graph, start, goal, visited=None, path=None, total_weight=0):
    if visited is None:
        visited = set()
    if path is None:
        path = [start]

    visited.add(start)
    if start == goal:
        return path, total_weight

    for neighbor, weight in graph[start]:
        if neighbor not in visited:
            new_path, new_weight = dfs_weighted(
                graph, neighbor, goal, visited, path + [neighbor], total_weight + weight
            )
            if new_path:
                return new_path, new_weight

    return None, 0

# Chạy DFS từ S đến I
path, weight = dfs_weighted(graph, 'S', 'I')
print("DFS - Đường đi từ S đến I:", path)
print("DFS - Tổng trọng số:", weight)
