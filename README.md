# 📚 FULL LÝ THUYẾT IP — TRỌN BỘ 7 CHƯƠNG
*(Chương 04 & 05 mình đã gửi đầy đủ ở tin trước → tin này bổ sung **Chương 01, 02, 03, 06, 07** để bạn có trọn bộ tài liệu ôn thi)*

---

# 🖥️ CHƯƠNG 01 — COMPUTER & PROGRAMMING BASICS

## 1.1. Architecture of a Computer (Kiến trúc máy tính)

### A. Mô hình Von Neumann (1945) — nền tảng của mọi máy tính hiện đại

```
        ┌─────────────────────────────────────────┐
        │                  CPU                    │
        │   ┌──────────┐        ┌─────────────┐   │
        │   │ CU       │        │ ALU         │   │
        │   │ Control  │        │ Arithmetic  │   │
        │   │ Unit     │        │ Logic Unit  │   │
        │   └──────────┘        └─────────────┘   │
        │        ┌───────────────────┐            │
        │        │ Registers (thanh ghi)│         │
        │        └───────────────────┘            │
        └──────────────────┬──────────────────────┘
                           │ BUS (Data / Address / Control)
        ┌──────────────────┼──────────────────┐
        │                  │                  │
   ┌────▼─────┐      ┌─────▼──────┐    ┌──────▼──────┐
   │ MEMORY   │      │ INPUT      │    │ OUTPUT      │
   │ RAM/ROM  │      │键盘/鼠标    │    │ 屏幕/打印机  │
   └──────────┘      └────────────┘    └─────────────┘
```

| Bộ phận | Tên đầy đủ | Chức năng |
|---|---|---|
| **CPU** | Central Processing Unit | "bộ não", xử lý lệnh |
| **ALU** | Arithmetic Logic Unit | tính toán số học (+ − × ÷) & logic (AND, OR, NOT) |
| **CU** | Control Unit | điều phối, giải mã lệnh, phát tín hiệu điều khiển |
| **Registers** | thanh ghi | bộ nhớ siêu nhanh **trong** CPU (PC, IR, ACC) |
| **RAM** | Random Access Memory | bộ nhớ chính, **mất dữ liệu khi tắt máy** (volatile) |
| **ROM** | Read Only Memory | chứa firmware/BIOS, **không mất** (non-volatile) |
| **HDD/SSD** | Secondary storage | lưu trữ lâu dài |
| **Bus** | hệ thống bus | Data bus (dữ liệu), Address bus (địa chỉ), Control bus (tín hiệu) |

**Đặc trưng Von Neumann:** chương trình và dữ liệu ** lưu chung một bộ nhớ** → CPU đọc lệnh như đọc dữ liệu.

### B. Chu kỳ Fetch – Decode – Execute (câu hỏi lý thuyết cực hay ra)

```
1. FETCH   : CU lấy lệnh từ RAM theo địa chỉ trong PC (Program Counter)
2. DECODE  : CU giải mã lệnh → hiểu phải làm gì
3. EXECUTE : ALU tính toán / truy cập bộ nhớ / ghi kết quả
4. STORE   : ghi kết quả về thanh ghi hoặc RAM (write-back)
   → PC tăng lên, quay lại bước 1
```

### C. Phân cấp bộ nhớ (Memory Hierarchy) — nhanh ↓, đắt ↓, dung lượng ↑

```
Registers  (~1 ns,   vài chục byte)     ← nhanh nhất
Cache L1/L2/L3 (~ns,  MB)
RAM        (~100 ns,  GB)
SSD/HDD    (~µs–ms,   TB)               ← chậm nhất
```

### D. Đơn vị & hệ đếm

| Đơn vị | Giá trị |
|---|---|
| 1 bit | 0 hoặc 1 |
| 1 byte | 8 bit |
| 1 KB | 1024 byte = 2¹⁰ |
| 1 MB | 1024 KB = 2²⁰ |
| 1 GB | 1024 MB = 2³⁰ |
| 1 TB | 1024 GB = 2⁴⁰ |

```python
bin(25)   # '0b11001'   nhị phân
oct(25)   # '0o31'      bát phân
hex(25)   # '0x19'      thập lục phân
int('11001', 2)   # 25  ← đổi về thập phân
```
> 25₁₀ = 11001₂ = 31₈ = 19₁₆

### E. Hardware vs Software

- **Hardware**: vật lý (CPU, RAM, mainboard, SSD)
- **Software**: System software (OS: Windows/Linux/macOS, driver) + Application software (Python, Word, QGIS)
- **OS làm gì?** quản lý tiến trình, bộ nhớ, file system, thiết bị I/O; làm cầu nối app ↔ hardware

---

## 1.2. Programming Languages (Ngôn ngữ lập trình)

### A. Các thế hệ

| Thế hệ | Tên | Ví dụ | Đặc điểm |
|---|---|---|---|
| **1GL** | Machine language | `10110000 01100001` | nhị phân, máy hiểu trực tiếp |
| **2GL** | Assembly | `MOV AL, 61h` | ký hiệu mnemonic, phụ thuộc CPU |
| **3GL** | High-level | **Python**, C, C++, Java, JS | gần ngôn ngữ tự nhiên |
| **4GL** | Very high-level | SQL, MATLAB, R | khai báo "muốn gì", không cần "làm thế nào" |
| **5GL** | Logic/AI | Prolog, Mercury | giải bài toán bằng ràng buộc |

### B. Compiler vs Interpreter (⭐ câu hỏi thi số 1 chương này)

| | **Compiler** (biên dịch) | **Interpreter** (thông dịch) |
|---|---|---|
| Cách chạy | dịch **toàn bộ** source → file máy **1 lần** | dịch & chạy **từng dòng** |
| Tốc độ chạy | nhanh | chậm hơn |
| Phát hiện lỗi | khi biên dịch, báo nhiều lỗi 1 lúc | dừng ngay dòng lỗi |
| Phân phối | file .exe (không cần source) | cần source + interpreter |
| Ngôn ngữ | C, C++, Go, Rust | **Python**, JS, PHP, Ruby |
| Di động | phải build lại cho mỗi OS | chạy mọi nơi có interpreter |

> **Python thực tế là hybrid**: `.py` → biên dịch thành **bytecode** `.pyc` → **PVM** (Python Virtual Machine) thông dịch bytecode. Java cũng vậy (`.java` → `.class` → JVM).

### C. Phân loại theo kiểu dữ liệu

| Tiêu chí | Static (tĩnh) | Dynamic (động) |
|---|---|---|
| Khai báo kiểu | bắt buộc, lúc compile | không cần, lúc runtime |
| Ví dụ | `int x = 5;` (C/Java) | `x = 5` (Python) |

| | Strong typing | Weak typing |
|---|---|---|
| Ép kiểu ngầm | hạn chế, báo lỗi | tự do, dễ lỗi lạ |
| Ví dụ | **Python**, Java | JavaScript (`"5"+3="53"`) |

> **Python = high-level + interpreted + dynamically typed + strongly typed + multi-paradigm + general-purpose.** Học thuộc câu này.
> ```python
> "5" + 3   # ❌ TypeError → chứng minh Python STRONGLY typed
> ```

### D. Programming paradigms (mô hình lập trình)

| Paradigm | Tư tưởng | Ngôn ngữ |
|---|---|---|
| Procedural | chia thành hàm/thủ tục, chạy tuần tự | C, Pascal |
| **Object-Oriented** | mọi thứ là object (data + method) | Java, C++, **Python** |
| Functional | hàm thuần, bất biến, không side-effect | Haskell, Lisp |
| Declarative | khai báo kết quả mong muốn | SQL, Prolog |
| Scripting | viết nhanh, tự động hóa | **Python**, Bash |

---

## 1.3. Program = Objects + Operations ⭐

> **Niklaus Wirth (1976): "Algorithms + Data Structures = Programs"**
> Diễn đạt trong slide của bạn: **Program = Objects (dữ liệu) + Operations (thao tác)**

### A. Objects = DỮ LIỆU

Trong Python, **mọi thứ đều là object** (số, chuỗi, hàm, lớp, module). Mỗi object có **3 thuộc tính**:

| Thuộc tính | Ý nghĩa | Lệnh kiểm tra |
|---|---|---|
| **Identity** | địa chỉ ô nhớ, không đổi suốt đời | `id(x)` |
| **Type** | kiểu, quyết định phép toán hợp lệ | `type(x)` |
| **Value** | giá trị đang chứa | `print(x)` |

```python
x = 5
print(id(x), type(x), x)   # 1407... <class 'int'> 5
```

Phân loại object:
- **Constant / literal**: `5`, `3.14`, `"abc"`, `True`
- **Variable**: `x`, `name`, `data`
- **Data structure**: `list`, `dict`, `DataFrame`
- **Function / class / module** cũng là object!

### B. Operations = THAO TÁC

| Loại | Ví dụ |
|---|---|
| Arithmetic | `+ - * / // % **` |
| Comparison | `== != > <` |
| Logical | `and or not` |
| Assignment | `= += *=` |
| Function call | `len(x)`, `math.sqrt(x)` |
| Method call | `s.upper()`, `a.append(1)` |
| Indexing / slicing | `a[0]`, `s[1:3]` |
| Control | `if`, `for`, `while` |

### C. Mổ xẻ một chương trình

```python
import math                 # ← import module (object)
r = 5                       # ← OBJECT: biến r, value 5, type int
area = math.pi * r ** 2     # ← OPERATIONS: ** , * , gọi math.pi
print(f"S = {area:.2f}")    # ← OPERATION: gọi hàm print
```

**Bậc thang cấu thành chương trình:**
```
Ký tự → Token (từ khóa, tên, số, toán tử)
      → Expression (biểu thức: có giá trị)   vd: 2 + 3*4
      → Statement (câu lệnh: thực thi)       vd: x = 2 + 3*4
      → Block (khối, cùng indent)
      → Function / Class
      → Module (.py)
      → Package (thư mục có __init__.py)
      → Program / Application
```

> **Expression vs Statement** là câu hỏi lý thuyết hay bị hỏi:
> - Expression **luôn trả về giá trị** → `3+4`, `len(a)`, `x>5`
> - Statement **thực hiện hành động** → `x = 5`, `if`, `for`, `return`

---

## 1.4. Programming Applications

| Lĩnh vực | Ứng dụng | Thư viện Python |
|---|---|---|
| Web | backend, API | Django, Flask, **FastAPI** |
| **Data Science** | phân tích, thống kê | **NumPy, Pandas, Matplotlib** |
| AI / ML | dự đoán, nhận dạng | Scikit-learn, TensorFlow, PyTorch |
| **GIS / Remote Sensing** | bản đồ, ảnh vệ tinh | **GeoPandas, Rasterio, Shapely** |
| Automation | script, cào dữ liệu | Selenium, Requests, BeautifulSoup |
| Desktop GUI | phần mềm máy tính | Tkinter, PyQt |
| Game | game 2D | Pygame |
| DevOps / Cloud | triển khai | Docker SDK, Boto3 (AWS) |
| Scientific | mô phỏng | SciPy, SymPy |

---

# 🧩 CHƯƠNG 02 — BASIC CONCEPTS & DATA FORMS

## 2.1. Structure of a Computer Program

### A. Mô hình IPO — mọi chương trình đều theo khung này

```
INPUT  ──►  PROCESS  ──►  OUTPUT
(nhập)      (xử lý)       (xuất)
   ↑            ↑            ↑
input()      tính toán    print()
file, DB     if/for/while  file, chart, API
```

### B. Bộ khung chuẩn của một file Python (⭐ viết bài thi nên theo mẫu này)

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Tên chương trình : Quản lý điểm sinh viên
Tác giả          : Nguyễn Thanh Thiên - 2511166073
Mô tả            : Nhập, thống kê và xếp loại điểm
"""

# 1. IMPORT THƯ VIỆN
import math
import statistics as st

# 2. HẰNG SỐ (quy ước VIẾT HOA)
PI = 3.14159
MAX_STUDENT = 100

# 3. ĐỊNH NGHĨA HÀM
def nhap_diem():
    """Nhập danh sách điểm từ bàn phím."""
    return list(map(float, input("Nhập điểm: ").split()))

def xep_loai(d):
    if d >= 8.5: return "A"
    elif d >= 7: return "B"
    elif d >= 5: return "C"
    return "D"

# 4. HÀM MAIN
def main():
    diem = nhap_diem()
    print("ĐTB:", st.mean(diem))
    for d in diem:
        print(d, "→", xep_loai(d))

# 5. ĐIỂM VÀO CHƯƠNG TRÌNH
if __name__ == "__main__":
    main()
```

**`if __name__ == "__main__":` nghĩa là gì?**
- Chạy trực tiếp file → `__name__ == "__main__"` → khối này chạy
- File được `import` bởi file khác → `__name__ == "tên_module"` → khối này **không** chạy
- 👉 Giúp file vừa chạy độc lập, vừa làm thư viện tái sử dụng được.

### C. Quy tắc cú pháp Python

| Quy tắc | Chi tiết |
|---|---|
| **Indentation** | 4 space, thay cho `{ }` của C/Java — **bắt buộc** |
| Dấu `:` | kết thúc dòng mở khối: `if`, `for`, `while`, `def`, `class`, `try` |
| Comment | `#` một dòng; `"""..."""` docstring |
| Case-sensitive | `Name` ≠ `name` |
| Không `;` | mỗi lệnh 1 dòng (hoặc dùng `;` nhưng không khuyến khích) |
| Xuống dòng dài | trong `( )`, `[ ]`, `{ }` hoặc dùng `\` |
| Nhiều lệnh 1 dòng | `a = 1; b = 2` (hạn chế) |

---

## 2.2. Python for Data Analysis

**Pipeline 5 bước chuẩn:**
```
1. LOAD     : đọc dữ liệu  (pd.read_csv, rasterio.open)
2. CLEAN    : xử lý thiếu/sai (dropna, fillna, drop_duplicates)
3. TRANSFORM: biến đổi, tính cột mới, groupby, merge
4. ANALYZE  : thống kê, mô hình, tương quan
5. VISUALIZE: biểu đồ, bản đồ (matplotlib, folium)
```

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("diem.csv")            # 1. LOAD
df = df.dropna()                        # 2. CLEAN
df["dtb"] = df[["toan","ly","hoa"]].mean(axis=1)   # 3. TRANSFORM
print(df.groupby("lop")["dtb"].mean())  # 4. ANALYZE
df["dtb"].hist(bins=10)                 # 5. VISUALIZE
plt.xlabel("Điểm"); plt.ylabel("Số SV"); plt.show()
```

**Bộ 3 quyền lực:** `NumPy` (số học mảng) → `Pandas` (bảng dữ liệu) → `Matplotlib` (vẽ).

---

## 2.3. Data Types and Computation ⭐⭐ (phần trọng tâm nhất chương 2)

### A. Bảng kiểu dữ liệu dựng sẵn (built-in) — HỌC THUỘC

| Nhóm | Kiểu | Ví dụ | Mutable? | Hashable? |
|---|---|---|---|---|
| Số nguyên | `int` | `5`, `-3`, `0xFF` | ❌ | ✅ |
| Số thực | `float` | `3.14`, `1e-3` | ❌ | ✅ |
| Logic | `bool` | `True`, `False` | ❌ | ✅ |
| Số phức | `complex` | `3+4j` | ❌ | ✅ |
| Chuỗi | `str` | `"abc"` | ❌ | ✅ |
| Danh sách | `list` | `[1,2,3]` | ✅ | ❌ |
| Bộ | `tuple` | `(1,2)` | ❌ | ✅* |
| Từ điển | `dict` | `{"a":1}` | ✅ | ❌ |
| Tập hợp | `set` | `{1,2,3}` | ✅ | ❌ |
| Tập bất biến | `frozenset` | `frozenset({1,2})` | ❌ | ✅ |
| Rỗng | `NoneType` | `None` | ❌ | ✅ |
| Nhị phân | `bytes` | `b"abc"` | ❌ | ✅ |

\* tuple hash được **nếu mọi phần tử bên trong hash được**.
> **Quy tắc vàng:** *Immutable → hashable → làm key dict / phần tử set được.* Mutable thì không.

```python
d = {(1,2): "tọa độ"}   # ✅
d = {[1,2]: "tọa độ"}   # ❌ TypeError: unhashable type: 'list'
```

### B. Kiểm tra & chuyển kiểu

```python
type(5)                 # <class 'int'>
isinstance(5, int)      # True  ← khuyên dùng (nhận cả lớp con)
isinstance(5, (int,float))  # True

int("42")     # 42
int(3.99)     # 3      ← CẮT PHẦN THẬP PHÂN, không làm tròn!
int(-3.99)    # -3     ← cắt về phía 0
int("3.5")    # ❌ ValueError → phải float("3.5") rồi int()
float("3.5")  # 3.5
str(42)       # "42"
bool("")      # False
bool("False") # ⚠ True! chuỗi không rỗng luôn True
list("abc")   # ['a','b','c']
tuple([1,2])  # (1,2)
set([1,1,2])  # {1,2}  ← khử trùng
dict([("a",1)])  # {'a': 1}
```

**Ép kiểu ngầm (implicit) vs tường minh (explicit):**
```python
3 + 4.5      # 7.5  ← Python tự nâng int → float (implicit)
"3" + 4      # ❌ lỗi → phải int("3") + 4 (explicit)
True + True  # 2    ← bool là con của int
```

### C. Số học & các bẫy tính toán

```python
7 / 2      # 3.5    ← / LUÔN ra float
7 // 2     # 3      ← chia lấy nguyên, LÀM TRÒN XUỐNG (floor)
-7 // 2    # -4     ← ⚠ không phải -3! floor về -∞
7 % 3      # 1
-7 % 3     # 2      ← ⚠ dấu theo SỐ CHIA (Python khác C)
2 ** 10    # 1024
2 ** 0.5   # 1.414...
divmod(7,3)  # (2, 1) = (thương, dư)
pow(2,10,1000)  # 24  ← (2**10) % 1000, nhanh hơn
abs(-5); round(3.14159, 2)   # 5 ; 3.14
```

**⚠ Bẫy float (IEEE 754 double, 64-bit, ~15–17 chữ số có nghĩa):**
```python
0.1 + 0.2 == 0.3          # False! (0.30000000000000004)
abs(0.1+0.2 - 0.3) < 1e-9 # True ← ✅ cách so sánh đúng

round(2.5)   # 2  ← ⚠ BANKER'S ROUNDING: làm tròn về số CHẴN gần nhất
round(3.5)   # 4
round(0.5)   # 0

import math
math.isclose(0.1+0.2, 0.3)   # True ← cách chuẩn

from decimal import Decimal
Decimal("0.1") + Decimal("0.2")   # Decimal('0.3') ← dùng cho TIỀN
```

**int của Python không giới hạn** (arbitrary precision): `2**1000` tính được bình thường.

### D. Bảng toán tử đầy đủ + thứ tự ưu tiên

| Ưu tiên (cao→thấp) | Toán tử | Ghi chú |
|---|---|---|
| 1 | `( )` | ngoặc |
| 2 | `**` | **kết hợp PHẢI**: `2**3**2 = 2**9 = 512` |
| 3 | `+x  -x  ~x` | một ngôi; `-2**2 = -4` |
| 4 | `*  /  //  %` | |
| 5 | `+  -` | |
| 6 | `<<  >>` | dịch bit |
| 7 | `&` → `^` → `\|` | bit AND, XOR, OR |
| 8 | `== != > < >= <= in not in is is not` | so sánh, **cho phép chuỗi**: `18 <= age < 25` |
| 9 | `not` | |
| 10 | `and` | short-circuit |
| 11 | `or` | short-circuit |
| 12 | `= += -= ...` | gán (thấp nhất) |

### E. Module `math` cần thuộc

```python
import math
math.pi, math.e, math.inf, math.nan
math.sqrt(x); math.pow(x,y)
math.ceil(3.2)   # 4  ← trần
math.floor(3.8)  # 3  ← sàn
math.trunc(3.8)  # 3  ← cắt
math.fabs(-3)    # 3.0
math.factorial(5)  # 120
math.gcd(12,18)    # 6
math.log(x); math.log10(x); math.log(x, 2)
math.exp(x)
math.sin/cos/tan(x)      # ⚠ x tính bằng RADIAN
math.radians(90)         # 1.5708
math.degrees(math.pi)    # 180
math.hypot(3,4)          # 5.0 ← cạnh huyền
```

### F. Nhập / Xuất

```python
n = int(input("n = "))                       # input luôn trả STR
a, b = map(int, input().split())             # nhập 2 số 1 dòng
arr = list(map(float, input().split()))      # nhập dãy

print("a", "b", sep="-", end="!\n")          # a-b!
print(f"{3.14159:.2f} | {'An':>10} | {1234567:,}")
print("%.2f" % 3.14159)                      # kiểu cũ
print("{:.2f}".format(3.14159))
```

---

## 2.4. Python Libraries for Programming

### A. Ba tầng thư viện

| Tầng | Cài đặt | Ví dụ |
|---|---|---|
| **Built-in** | sẵn trong ngôn ngữ | `print, len, range, sum, abs` |
| **Standard Library** | sẵn theo Python, cần `import` | `math, random, os, datetime` |
| **Third-party** | `pip install` | `numpy, pandas, matplotlib` |

### B. Các cách import

```python
import math                    # math.sqrt(2)
import math as m               # m.sqrt(2)
from math import sqrt, pi      # sqrt(2)
from math import *             # ⚠ tránh: ô nhiễm namespace
```

### C. Standard Library phải biết

| Module | Công dụng | Hàm hay dùng |
|---|---|---|
| `math` | toán học | sqrt, ceil, floor, factorial, gcd |
| `random` | ngẫu nhiên | random, randint, choice, shuffle, sample, seed |
| `statistics` | thống kê | mean, median, mode, stdev, variance |
| `datetime` | ngày giờ | date, datetime, timedelta, strftime |
| `time` | thời gian | time, sleep, perf_counter |
| `os` / `pathlib` | hệ thống, file | listdir, getcwd, path.join |
| `sys` | hệ thống Python | argv, exit, getsizeof, getrefcount |
| `json` | đọc/ghi JSON | load, loads, dump, dumps |
| `csv` | đọc/ghi CSV | reader, DictReader |
| `re` | biểu thức chính quy | search, findall, sub, match |
| `collections` | cấu trúc dữ liệu | Counter, defaultdict, deque, namedtuple |
| `itertools` | tổ hợp | permutations, combinations, product |
| `functools` | hàm bậc cao | reduce, lru_cache, partial |

### D. Third-party theo ngành

```bash
pip install numpy pandas matplotlib scipy scikit-learn geopandas rasterio
pip list                 # xem đã cài
pip freeze > requirements.txt
python -m venv venv      # tạo môi trường ảo (nên làm!)
```

---

## 2.5. Examples Using Libraries

**VD1 — Thống kê mô tả**
```python
import statistics as st
a = [7, 8, 6, 9, 8, 7, 10]
print(f"Mean={st.mean(a):.2f} Median={st.median(a)} Mode={st.mode(a)}")
print(f"SD={st.stdev(a):.2f} Var={st.variance(a):.2f}")
```

**VD2 — Mô phỏng Monte Carlo ước lượng π** *(hợp gu xác suất của bạn)*
```python
import random
random.seed(42)                 # cố định để tái lập kết quả
N, inside = 1_000_000, 0
for _ in range(N):
    x, y = random.random(), random.random()
    if x*x + y*y <= 1: inside += 1
print("π ≈", 4 * inside / N)    # ≈ 3.1415
```

**VD3 — Mô phỏng tung xúc xắc (kiểm chứng xác suất)**
```python
from collections import Counter
c = Counter(sum(random.randint(1,6) for _ in range(2)) for _ in range(100000))
for s in range(2, 13):
    print(f"{s:2d}: {c[s]/100000:.4f}  (lý thuyết 7 = 0.1667)")
```

**VD4 — Ngày giờ**
```python
from datetime import date, datetime, timedelta
today = date.today()
birth = date(2006, 5, 20)
print("Tuổi:", (today - birth).days // 365)
print("Sau 30 ngày:", today + timedelta(days=30))
print(datetime.now().strftime("%d/%m/%Y %H:%M:%S"))
```

**VD5 — File JSON**
```python
import json
data = {"ten": "Thiên", "diem": [8, 9, 7]}
with open("sv.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)
with open("sv.json", encoding="utf-8") as f:
    d = json.load(f)
```

**VD6 — Đếm & tổ hợp**
```python
from collections import Counter
from itertools import combinations, permutations
print(Counter("nguyen thanh thien"))
print(list(combinations([1,2,3], 2)))   # [(1,2),(1,3),(2,3)]
```

---

# 🔤 CHƯƠNG 03 — VARIABLE & FUNCTION

## 3.1. Variables — cấu trúc biến

### A. Mô hình biến trong Python (⭐ khác C/Java — cực quan trọng)

```
C/Java:   biến = CÁI HỘP chứa giá trị
          x ┌─────┐
            │  5  │
            └─────┘

Python:   biến = NHÃN DÁN (reference) trỏ tới object trong bộ nhớ
          x ──────► [ object: type=int, value=5, id=0x7f... ]
          y ──────►  (cùng object nếu y = x)
```

**Một biến gồm 4 thành phần:** `Name` + `Type` + `Value` + `Address(id)`

```python
x = 5
print(id(x))        # địa chỉ
x = "hello"         # ✅ hợp lệ: DYNAMIC TYPING — nhãn dán sang object khác
```

### B. Quy tắc đặt tên

**Bắt buộc (vi phạm = SyntaxError):**
1. Chỉ gồm chữ cái, số, `_`
2. **Không bắt đầu bằng số** (`2diem` ❌)
3. Không trùng **từ khóa** (`if`, `for`, `class`, `import`, `None`, `True`...)
4. Phân biệt Hoa/thường
5. Không dấu cách, không dấu tiếng Việt có dấu (nên tránh)

```python
import keyword
print(keyword.kwlist)   # xem 35 từ khóa
```

**Quy ước PEP 8 (nên theo):**
| Đối tượng | Quy ước | Ví dụ |
|---|---|---|
| biến, hàm | `snake_case` | `diem_tb`, `tinh_tong` |
| hằng số | `UPPER_SNAKE` | `MAX_SIZE`, `PI` |
| lớp | `PascalCase` | `SinhVien` |
| "nội bộ" | `_ten` | `_helper` |
| name mangling | `__ten` | `__private` |

### C. Các phép gán

```python
x = 5                    # gán đơn
a = b = c = 0            # gán dây chuyền (⚠ cùng object!)
x, y = 1, 2              # gán bộ (tuple unpacking)
x, y = y, x              # HOÁN VỊ không cần biến tạm
first, *rest = [1,2,3]   # first=1, rest=[2,3]
x += 1                   # gán kết hợp
x: int = 5               # type hint (chỉ gợi ý, KHÔNG ép buộc)
del x                    # xóa nhãn
```

### D. Bộ nhớ & đếm tham chiếu

```python
import sys
a = [1,2,3]
print(sys.getrefcount(a))   # số tham chiếu (có +1 do tham số tạm)
b = a                       # +1
del b                       # -1
# Khi refcount = 0 → Garbage Collector tự giải phóng
print(sys.getsizeof(a))     # byte chiếm dụng
```

---

## 3.2. Local vs Global Variable — Quy tắc LEGB ⭐⭐

### A. Bốn tầng scope

```
L — Local      : trong hàm đang chạy
E — Enclosing  : trong hàm bao ngoài (hàm lồng)
G — Global     : cấp module (ngoài mọi hàm)
B — Built-in   : sẵn có (len, print, sum...)
```
**Tra cứu tên: L → E → G → B**, tìm thấy ở đâu dừng ở đó.

### B. Ví dụ minh họa đầy đủ

```python
x = "global"            # G

def outer():
    x = "enclosing"     # E
    def inner():
        x = "local"     # L
        print(x)        # local
    inner()
    print(x)            # enclosing

outer()
print(x)                # global
```

### C. Đọc được nhưng KHÔNG ghi được

```python
count = 0
def tang():
    print(count)     # ✅ ĐỌC biến global — OK
    # count += 1     # ❌ UnboundLocalError!
tang()
```
> **Vì sao lỗi?** Trong hàm có lệnh **gán** `count = ...` → Python coi `count` là **biến local** ngay từ đầu → đọc trước khi gán → lỗi.

### D. `global` và `nonlocal`

```python
count = 0
def tang():
    global count      # khai báo: dùng biến GLOBAL
    count += 1        # ✅
tang(); print(count)  # 1

def outer():
    n = 0
    def inner():
        nonlocal n    # khai báo: dùng biến ENCLOSING
        n += 1
    inner(); print(n) # 1
outer()
```

| Từ khóa | Trỏ tới tầng | Dùng khi |
|---|---|---|
| `global` | G (module) | cần **ghi** biến toàn cục |
| `nonlocal` | E (hàm ngoài) | closure, hàm lồng cần ghi |
| (không gì) | L | mặc định, an toàn nhất |

### E. So sánh & lời khuyên

| | Local | Global |
|---|---|---|
| Khai báo | trong hàm | ngoài mọi hàm |
| Sống | khi hàm chạy → hết | suốt chương trình |
| Truy cập | chỉ trong hàm | mọi nơi |
| An toàn | ✅ cao | ❌ dễ bị sửa ngoài ý muốn |

> **Best practice:** hạn chế global. Truyền dữ liệu qua **tham số**, nhận kết quả qua **return**. Chương trình dễ test, dễ debug hơn nhiều.

**⚠ Bẫy shadowing:**
```python
list = [1,2,3]     # ❌ đè mất built-in list()
list("abc")        # TypeError: 'list' object is not callable
```

---

## 3.3. Parameters & Arguments ⭐

### A. Phân biệt

- **Parameter (tham số hình thức)**: tên trong **định nghĩa** hàm → `def f(a, b)`
- **Argument (đối số thực sự)**: giá trị thật khi **gọi** hàm → `f(3, 5)`

### B. Năm loại tham số — HỌC THUỘC THỨ TỰ

```python
def f(a, /, b, c=10, *args, d, e=20, **kwargs):
#     ①    ②  ③     ④     ⑤  ⑤      ⑥
```
| # | Loại | Cú pháp | Ý nghĩa |
|---|---|---|---|
| ① | Positional-only | trước `/` | **bắt buộc** truyền theo vị trí |
| ② | Positional-or-keyword | bình thường | cả hai cách |
| ③ | Default | `c=10` | có giá trị mặc định |
| ④ | `*args` | gom vị trí dư | nhận **tuple** |
| ⑤ | Keyword-only | sau `*` | **bắt buộc** gọi bằng tên |
| ⑥ | `**kwargs` | gom keyword dư | nhận **dict** |

```python
def demo(a, b=2, *args, c, **kwargs):
    print(a, b, args, c, kwargs)

demo(1, 2, 3, 4, c=5, d=6, e=7)
# 1 2 (3, 4) 5 {'d': 6, 'e': 7}
```

**Ứng dụng thực tế:**
```python
def tong(*so):                 # nhận bao nhiêu số cũng được
    return sum(so)
tong(1,2,3,4)                  # 10

def tao_sv(**info):
    return info
tao_sv(ten="Thiên", mssv="2511166073", lop="CA3")

# UNPACKING khi gọi
def dientich(a, b): return a*b
size = (3, 4);  print(dientich(*size))     # 12
cfg = {"a":3, "b":4}; print(dientich(**cfg))  # 12
```

### C. ⚠ Bẫy tham số mặc định MUTABLE (câu thi kinh điển)

```python
def them(x, a=[]):        # ❌ NGUY HIỂM
    a.append(x); return a
print(them(1))   # [1]
print(them(2))   # [1, 2]  ← KHÔNG phải [2]!

def them(x, a=None):      # ✅ CHUẨN
    if a is None: a = []
    a.append(x); return a
```
> **Lý do:** giá trị mặc định được tạo **1 lần duy nhất lúc định nghĩa hàm**, không phải mỗi lần gọi.

### D. Cơ chế truyền tham số: **Pass by Object Reference**

Python **không** phải pass-by-value, cũng **không** phải pass-by-reference thuần — mà là **pass by assignment / object reference**.

```python
def doi_so(x):
    x = 100               # gán lại → trỏ object MỚI
a = 5; doi_so(a); print(a)     # 5  ← KHÔNG đổi (int immutable)

def doi_list(lst):
    lst.append(4)         # SỬA TẠI CHỖ object
b = [1,2,3]; doi_list(b); print(b)   # [1,2,3,4] ← CÓ đổi!

def thay_list(lst):
    lst = [9,9]           # gán lại nhãn → không ảnh hưởng ngoài
c = [1,2]; thay_list(c); print(c)    # [1,2] ← không đổi
```

**Kết luận vàng:**
> Truyền **immutable** (int, float, str, tuple) → hàm **không** làm đổi biến ngoài.
> Truyền **mutable** (list, dict, set) → hàm **có thể** làm đổi nếu **sửa tại chỗ**; nhưng **gán lại** thì không.

---

## 3.4. Functions — cấu trúc & phân loại

### A. Cấu trúc đầy đủ

```python
def ten_ham(tham_so: kieu = mac_dinh) -> kieu_tra_ve:
    """Docstring: mô tả hàm làm gì, tham số, kết quả."""
    than_ham
    return gia_tri        # có thể thiếu → trả None
```

```python
def bmi(can_nang: float, chieu_cao: float) -> float:
    """Tính chỉ số BMI.
    Args: can_nang (kg), chieu_cao (m)
    Returns: float — chỉ số BMI
    """
    return can_nang / chieu_cao ** 2

print(bmi.__doc__)     # xem docstring
help(bmi)
```

### B. `return` — 4 điều phải nhớ

```python
def f(): pass
print(f())                    # None ← hàm không return trả None

def g(): return               # cũng None
def h(): return 1, 2, 3       # trả TUPLE (đa giá trị)
a, b, c = h()                 # unpack

def k():
    return                    # return sớm = thoát hàm ngay
    print("không chạy tới")
```

### C. Phân loại hàm

| Loại | Ví dụ |
|---|---|
| **Built-in** | `print, len, sum, max, sorted, input, range` |
| **Module function** | `math.sqrt`, `random.randint` |
| **User-defined** | `def tinh_tong():` |
| **Method** (hàm của object) | `s.upper()`, `a.append()` |
| **Lambda** (vô danh) | `lambda x: x**2` |
| **Recursive** (đệ quy) | giai thừa, Fibonacci |
| **Generator** | có `yield` |
| **Higher-order** | nhận/trả về hàm: `map, filter, sorted(key=)` |
| **Decorator** | `@lru_cache`, `@staticmethod` |

### D. Lambda + map / filter / reduce

```python
f = lambda x: x**2
print(f(5))                            # 25

list(map(lambda x: x*2, [1,2,3]))      # [2,4,6]
list(filter(lambda x: x%2==0, range(10)))  # [0,2,4,6,8]

from functools import reduce
reduce(lambda a,b: a*b, [1,2,3,4])     # 24 (giai thừa)

sv.sort(key=lambda s: s[1], reverse=True)
```
> Lambda chỉ chứa **1 biểu thức**, không có `if` khối / `for` / `return`.

### E. Đệ quy (Recursion) — 2 phần bắt buộc

```
1. BASE CASE  (điều kiện dừng)  ← thiếu = RecursionError
2. RECURSIVE CASE (gọi lại chính nó với bài toán NHỎ HƠN)
```

```python
def factorial(n):
    if n <= 1: return 1            # base
    return n * factorial(n-1)      # recursive

def fib(n):
    if n < 2: return n
    return fib(n-1) + fib(n-2)     # ⚠ O(2^n) rất chậm

from functools import lru_cache
@lru_cache(maxsize=None)           # ✅ memoization → O(n)
def fib_fast(n):
    return n if n < 2 else fib_fast(n-1) + fib_fast(n-2)

def gcd(a, b):
    return a if b == 0 else gcd(b, a % b)

def hanoi(n, src, dst, mid):
    if n == 1:
        print(f"Chuyển đĩa 1: {src} → {dst}"); return
    hanoi(n-1, src, mid, dst)
    print(f"Chuyển đĩa {n}: {src} → {dst}")
    hanoi(n-1, mid, dst, src)
hanoi(3, 'A', 'C', 'B')            # 2^3 - 1 = 7 bước
```
> Giới hạn đệ quy mặc định ~1000: `sys.setrecursionlimit(3000)`.

| | Đệ quy | Vòng lặp |
|---|---|---|
| Code | ngắn, đẹp, gần toán học | dài hơn |
| Bộ nhớ | tốn stack, có thể tràn | tiết kiệm |
| Tốc độ | chậm hơn | nhanh hơn |
| Dùng khi | cây, đồ thị, chia để trị | bài toán tuyến tính |

### F. Hàm là "first-class object"

```python
def chao(): return "Hi"
f = chao            # gán hàm cho biến
print(f())          # Hi

def ap_dung(func, x): return func(x)     # nhận hàm làm tham số
print(ap_dung(lambda x: x*3, 5))         # 15

def tao_nhan(n):                          # trả về hàm (closure)
    return lambda x: x * n
nhan3 = tao_nhan(3); print(nhan3(5))     # 15
```

### G. Generator (tiết kiệm bộ nhớ)

```python
def dem(n):
    for i in range(n):
        yield i          # trả từng giá trị, KHÔNG tạo cả list
for x in dem(5): print(x)
# range(), (x*x for x in ...) cũng là lazy
```

---

## 3.5. FULL EXAMPLE — chương trình tổng hợp Chương 2+3+4+5

```python
"""QUẢN LÝ ĐIỂM SINH VIÊN — tổng hợp biến, hàm, list/dict, if/for/while"""
import statistics as st

DIEM_CHUAN = {"A": 8.5, "B": 7.0, "C": 5.0, "D": 0.0}   # global constant

def xep_loai(dtb: float) -> str:
    """Xếp loại theo điểm trung bình."""
    if dtb >= DIEM_CHUAN["A"]: return "A"
    elif dtb >= DIEM_CHUAN["B"]: return "B"
    elif dtb >= DIEM_CHUAN["C"]: return "C"
    return "D"

def nhap_sv() -> dict:
    ten = input("Tên: ").strip().title()
    while True:
        try:
            diem = list(map(float, input("Điểm (cách nhau bởi space): ").split()))
            if diem and all(0 <= d <= 10 for d in diem): break
            print("Điểm phải trong [0,10]!")
        except ValueError:
            print("Nhập số hợp lệ!")
    return {"ten": ten, "diem": diem, "dtb": st.mean(diem)}

def in_bang(ds: list) -> None:
    if not ds:
        print("Danh sách rỗng!"); return
    print(f"{'STT':<5}{'Tên':<22}{'ĐTB':>6}{'Loại':>6}")
    print("-" * 40)
    for i, sv in enumerate(ds, 1):
        print(f"{i:<5}{sv['ten']:<22}{sv['dtb']:>6.2f}{xep_loai(sv['dtb']):>6}")

def thong_ke(ds: list) -> None:
    if not ds: return
    diem = [sv["dtb"] for sv in ds]
    print(f"Sĩ số: {len(ds)} | ĐTB lớp: {st.mean(diem):.2f}")
    print(f"Cao nhất: {max(diem):.2f} | Thấp nhất: {min(diem):.2f}")
    gioi = sum(1 for d in diem if d >= 8)
    print(f"SV giỏi: {gioi} ({gioi/len(ds)*100:.1f}%)")

def main():
    ds = []
    while True:
        print("\n1.Thêm  2.In bảng  3.Thống kê  4.Sắp xếp  0.Thoát")
        c = input("Chọn: ").strip()
        if c == "1": ds.append(nhap_sv())
        elif c == "2": in_bang(ds)
        elif c == "3": thong_ke(ds)
        elif c == "4":
            ds.sort(key=lambda s: -s["dtb"]); print("Đã sắp xếp giảm dần!")
        elif c == "0": print("Tạm biệt!"); break
        else: print("Lựa chọn không hợp lệ!")

if __name__ == "__main__":
    main()
```

---

# 🔗 CHƯƠNG 06 — POINTER AND APPLICATIONS

## 4.1. What are Pointers and Indexes?

| Khái niệm | Định nghĩa | Ngôn ngữ |
|---|---|---|
| **Pointer** | biến lưu **ĐỊA CHỈ Ô NHỚ** của biến khác | C, C++ |
| **Reference** | tên/bí danh trỏ tới object | **Python**, Java |
| **Index** | **vị trí logic** của phần tử trong dãy (0-based) | mọi ngôn ngữ |

**Trong C (để hiểu bản chất):**
```c
int x = 5;
int *p = &x;    // p lưu ĐỊA CHỈ của x  (& = address-of)
printf("%d", *p);  // 5  (* = dereference: lấy giá trị tại địa chỉ)
*p = 10;           // x cũng thành 10
p++;               // pointer arithmetic — Python KHÔNG có
```

**Trong Python:**
```python
a = [1,2,3]
print(a[0])       # INDEX  → phần tử vị trí 0
print(id(a))      # "địa chỉ" của object (CPython)
b = a             # REFERENCE → b là "con trỏ" thứ 2 tới cùng object
```

---

## 4.2. Pointers ARE used in Python? — Câu trả lời chuẩn thi

> ✅ **CÓ, nhưng NGẦM ẨN (implicitly).** Python không có con trỏ tường minh như C, nhưng **mọi biến đều là tham chiếu (reference) — bản chất là con trỏ tới `PyObject` trong bộ nhớ**.

**Python KHÔNG có:**
- ❌ Khai báo con trỏ `int *p`
- ❌ Toán tử `&` (lấy địa chỉ) và `*` (dereference)
- ❌ Pointer arithmetic (`p++`, `p+1`)
- ❌ Con trỏ NULL, con trỏ hàm tường minh
- ❌ Quản lý `malloc/free` thủ công

**Python CÓ (cơ chế tương đương):**

| Cơ chế | Lệnh | Ý nghĩa |
|---|---|---|
| Lấy "địa chỉ" | `id(x)` | định danh object (CPython = địa chỉ) |
| So sánh địa chỉ | `x is y` | cùng object? |
| So sánh giá trị | `x == y` | cùng giá trị? |
| Đếm tham chiếu | `sys.getrefcount(x)` | bao nhiêu "con trỏ" đang trỏ tới |
| Aliasing | `b = a` | 2 tên, 1 object |
| Copy | `copy.copy` / `deepcopy` | tạo object độc lập |
| Con trỏ thật | `ctypes` | gọi C, can thiệp bộ nhớ |

---

## 4.3. Uses of the Pointer in Python

### A. `is` vs `==` (⭐ bẫy thi số 1 chương 6)

```python
a = [1,2,3]
b = [1,2,3]
c = a
print(a == b)   # True  ← cùng GIÁ TRỊ
print(a is b)   # False ← KHÁC object
print(a is c)   # True  ← cùng object (alias)
print(id(a) == id(c))   # True
```
> **Quy tắc:** dùng `is` **chỉ** với `None`, `True`, `False`. Còn lại dùng `==`.
> ```python
> if x is None:   # ✅ chuẩn PEP8
> if x == None:   # ⚠ không khuyến khích
> ```

### B. Aliasing — nhiều "con trỏ" cùng object

```python
a = [1,2,3]; b = a
b.append(4)
print(a)            # [1,2,3,4] ← a đổi theo!
print(id(a)==id(b)) # True
```

### C. Copy: 3 mức

```python
import copy
a = [[1,2],[3,4]]

b = a                    # 1. ALIAS — chung mọi thứ
c = a.copy()             # 2. SHALLOW — list ngoài mới, list trong chung
d = copy.deepcopy(a)     # 3. DEEP — độc lập hoàn toàn

c[0][0] = 99
print(a)   # [[99,2],[3,4]] ← vẫn bị
print(d)   # [[1,2],[3,4]]  ← an toàn
```
Các cách shallow copy list: `a[:]`, `list(a)`, `a.copy()`, `copy.copy(a)`.

### D. Mutable/Immutable quyết định hành vi "con trỏ"

```python
def f(x): x += 1
a = 10; f(a); print(a)   # 10 ← int immutable, += tạo object mới

def g(x): x += [4]
b = [1,2]; g(b); print(b)  # [1,2,4] ← list mutable, sửa tại chỗ

# ⚠ Phân biệt với list:
t = (1,2); t += (3,)     # tạo tuple MỚI, id đổi
l = [1,2]; l += [3]      # SỬA TẠI CHỖ, id KHÔNG đổi (tương đương extend)
```

### E. Object interning / caching (hiện tượng lạ hay bị hỏi)

```python
a = 256; b = 256; print(a is b)   # True  ← CPython cache int -5..256
a = 257; b = 257; print(a is b)   # False (trong REPL)
s1 = "hello"; s2 = "hello"; print(s1 is s2)   # True ← string interning
s3 = "hello world!"; s4 = "hello world!"      # có thể False
```
> ⚠ Đây là **tối ưu của CPython**, không phải chuẩn ngôn ngữ → **đừng bao giờ dựa vào `is` để so sánh số/chuỗi**.

### F. Refcount & Garbage Collection

```python
import sys
a = [1,2,3]
print(sys.getrefcount(a))   # 2 (a + tham số tạm)
b = a; print(sys.getrefcount(a))   # 3
del b; print(sys.getrefcount(a))   # 2
# refcount → 0 thì giải phóng; vòng tham chiếu thì GC chu kỳ xử lý
```

### G. Con trỏ "thật" với ctypes (nâng cao, biết để trả lời)

```python
import ctypes
x = ctypes.c_int(5)
p = ctypes.pointer(x)         # con trỏ thật
print(p.contents.value)       # 5 ← dereference
p.contents.value = 99
print(x.value)                # 99
```

### H. Ứng dụng thực tế của cơ chế reference

| Ứng dụng | Lợi ích |
|---|---|
| Truyền list/dict vào hàm | không phải copy dữ liệu lớn → nhanh, tiết kiệm RAM |
| Cấu trúc liên kết (linked list, tree, graph) | node trỏ tới node khác |
| Cache / memoization | nhiều nơi dùng chung 1 object |
| Chia sẻ trạng thái giữa module | singleton |
| NumPy view | slice không copy → xử lý ảnh GB cực nhanh |

---

## 4.4. Multiple Pointers Approach ⭐ (Kỹ thuật HAI CON TRỎ)

> Đây là phần **thực chiến** của chương 6: dùng 2 (hoặc nhiều) **chỉ số/reference** chạy trên mảng để giải bài toán **O(n)** thay vì O(n²).

### Pattern 1 — Two pointers ngược chiều (Opposite ends)

**Đảo mảng tại chỗ:**
```python
def reverse(a):
    l, r = 0, len(a)-1
    while l < r:
        a[l], a[r] = a[r], a[l]
        l += 1; r -= 1
    return a
```

**Kiểm tra palindrome:**
```python
def is_pal(s):
    s = "".join(s.lower().split())
    l, r = 0, len(s)-1
    while l < r:
        if s[l] != s[r]: return False
        l += 1; r -= 1
    return True
```

**Two Sum trên mảng ĐÃ SẮP XẾP — O(n):**
```python
def two_sum(a, target):
    l, r = 0, len(a)-1
    while l < r:
        s = a[l] + a[r]
        if s == target: return (l, r)
        elif s < target: l += 1     # cần lớn hơn → dịch trái
        else: r -= 1                # cần nhỏ hơn → dịch phải
    return None
```

### Pattern 2 — Fast & Slow (rùa và thỏ)

**Dời số 0 về cuối, giữ thứ tự:**
```python
def move_zeros(a):
    slow = 0
    for fast in range(len(a)):
        if a[fast] != 0:
            a[slow], a[fast] = a[fast], a[slow]
            slow += 1
    return a
```

**Xóa trùng trên mảng đã sắp xếp:**
```python
def remove_dup(a):
    if not a: return 0
    slow = 0
    for fast in range(1, len(a)):
        if a[fast] != a[slow]:
            slow += 1; a[slow] = a[fast]
    return slow + 1
```

**Floyd's cycle detection — phát hiện chu trình:**
```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next          # đi 1 bước
        fast = fast.next.next     # đi 2 bước
        if slow is fast: return True    # ⭐ dùng IS, không dùng ==
    return False
```

### Pattern 3 — Sliding Window (cửa sổ trượt)

**Tổng lớn nhất của k phần tử liên tiếp — O(n):**
```python
def max_sum_k(a, k):
    s = sum(a[:k]); best = s
    for i in range(k, len(a)):
        s += a[i] - a[i-k]        # thêm phải, bớt trái
        best = max(best, s)
    return best
```

### Pattern 4 — Merge hai con trỏ (như merge sort)

```python
def merge(A, B):
    i = j = 0; out = []
    while i < len(A) and j < len(B):
        if A[i] <= B[j]: out.append(A[i]); i += 1
        else:            out.append(B[j]); j += 1
    out.extend(A[i:]); out.extend(B[j:])
    return out
```

### Pattern 5 — Nhiều reference cùng lúc (aliasing có chủ đích)

```python
# Hoán vị 3 biến không cần biến tạm
a, b, c = c, a, b

# Node liên kết: nhiều "con trỏ" tới cùng object
class Node:
    def __init__(self, val): self.val = val; self.next = None
n1, n2, n3 = Node(1), Node(2), Node(3)
n1.next = n2; n2.next = n3     # ← con trỏ liên kết
head = n1
while head: print(head.val); head = head.next
```

**Bảng độ phức tạp:**
| Bài toán | Brute force | Two pointers |
|---|---|---|
| Two sum (sorted) | O(n²) | **O(n)** |
| Đảo mảng | O(n) + O(n) RAM | **O(n) + O(1) RAM** |
| Max sum k | O(n·k) | **O(n)** |
| Xóa trùng | O(n²) | **O(n)** |

---

# 🧠 CHƯƠNG 07 — ALGORITHM & APPLICATION PROGRAMMING

## 5.1. What is an Algorithm? Thinking in Algorithms

### A. Định nghĩa

> **Algorithm (thuật toán)** = dãy **hữu hạn** các bước **xác định, rõ ràng**, biến **input** thành **output** mong muốn.

### B. 5 tính chất bắt buộc (⭐ câu lý thuyết kinh điển)

| # | Tính chất | Nghĩa |
|---|---|---|
| 1 | **Input** | có 0 hoặc nhiều đầu vào |
| 2 | **Output** | có **ít nhất 1** đầu ra |
| 3 | **Definiteness** (tính xác định) | mỗi bước rõ ràng, không mơ hồ |
| 4 | **Finiteness** (tính hữu hạn) | **phải dừng** sau hữu hạn bước |
| 5 | **Effectiveness** (tính hiệu quả/khả thi) | mỗi bước thực hiện được trong thời gian hữu hạn |

*(+ Correctness: đúng với mọi input hợp lệ; + Generality: áp dụng cho cả họ bài toán)*

### C. 3 cách biểu diễn thuật toán

**① Ngôn ngữ tự nhiên**
```
B1. Nhập a, b
B2. Nếu b = 0 thì UCLN = a, kết thúc
B3. Ngược lại: a ← b, b ← a mod b, quay lại B2
```

**② Lưu đồ (Flowchart) — ký hiệu phải thuộc:**
| Hình | Tên | Ý nghĩa |
|---|---|---|
| ⬭ Oval | Terminator | Start / End |
| ▱ Parallelogram | Input/Output | Nhập / Xuất |
| ▭ Rectangle | Process | Xử lý, gán |
| ◇ Diamond | Decision | Rẽ nhánh (Đúng/Sai) |
| → Arrow | Flow line | Hướng đi |
| ⬡ Hexagon | Preparation | Vòng lặp for |

**③ Giả mã (Pseudocode)**
```
ALGORITHM Max(A, n)
  max ← A[0]
  FOR i ← 1 TO n-1 DO
     IF A[i] > max THEN max ← A[i]
  RETURN max
```

### D. Computational Thinking — 4 bước tư duy thuật toán

```
1. DECOMPOSITION  (phân rã)   : chia bài toán lớn → bài toán nhỏ
2. PATTERN RECOGNITION (nhận mẫu): tìm điểm lặp lại, tương tự bài đã biết
3. ABSTRACTION    (trừu tượng): bỏ chi tiết thừa, giữ cái cốt lõi
4. ALGORITHM DESIGN (thiết kế): viết các bước giải quyết
```

**Ví dụ áp dụng — "Tính điểm trung bình lớp và xếp loại":**
- Decomposition: nhập → tính ĐTB → xếp loại → in
- Pattern: ĐTB = accumulator (tổng/đếm); xếp loại = if-elif
- Abstraction: mỗi SV chỉ cần `(tên, [điểm])`, bỏ qua tuổi, quê
- Algorithm: for duyệt list → sum/len → if-elif → print

### E. Đánh giá thuật toán

| Tiêu chí | Đo bằng |
|---|---|
| **Correctness** | đúng mọi input (test biên!) |
| **Time complexity** | Big-O số phép toán |
| **Space complexity** | Big-O bộ nhớ thêm |
| Readability | dễ đọc, dễ bảo trì |

---

## 5.2. Data Structures & Algorithms

### A. Mối quan hệ (nhắc lại Wirth)

> **Program = Data Structures + Algorithms**
> Cấu trúc dữ liệu = **cách tổ chức** dữ liệu; Thuật toán = **cách xử lý**. Chọn CTDL đúng → thuật toán đơn giản & nhanh.

### B. Bảng cấu trúc dữ liệu & độ phức tạp

| CTDL | Truy cập | Tìm | Chèn | Xóa | Dùng khi |
|---|---|---|---|---|---|
| **Array/List** | O(1) | O(n) | O(n)* | O(n) | dãy có thứ tự, index |
| **Linked List** | O(n) | O(n) | O(1) | O(1) | chèn/xóa nhiều |
| **Stack** (LIFO) | — | O(n) | O(1) | O(1) | undo, đệ quy, DFS |
| **Queue** (FIFO) | — | O(n) | O(1) | O(1) | hàng đợi, BFS |
| **Hash table (dict/set)** | — | **O(1)** | O(1) | O(1) | tra cứu nhanh, đếm |
| **Binary Search Tree** | O(log n) | O(log n) | O(log n) | O(log n) | dữ liệu có thứ tự động |
| **Heap** | O(1) min/max | O(n) | O(log n) | O(log n) | top-k, Dijkstra |
| **Graph** | — | O(V+E) | O(1) | O(1) | mạng lưới, bản đồ |

\* chèn cuối list là O(1) amortized.

### C. Big-O — bảng xếp hạng tốc độ

```
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)
tốt ──────────────────────────────────────────────────► tệ
```

| Big-O | Tên | Ví dụ |
|---|---|---|
| O(1) | hằng số | `a[0]`, `dict[key]`, `append` |
| O(log n) | logarit | binary search |
| O(n) | tuyến tính | duyệt list, linear search |
| O(n log n) | tuyến tính-log | merge sort, quick sort (TB), `sorted()` |
| O(n²) | bậc hai | bubble/selection/insertion sort, 2 for lồng |
| O(2ⁿ) | hàm mũ | fib đệ quy ngây thơ, tập con |
| O(n!) | giai thừa | hoán vị, brute-force TSP |

**Cách đếm nhanh:**
```python
for i in range(n):          # n lần
    for j in range(n):      # × n lần
        ...                 # → O(n²)

for i in range(n): ...      # O(n)
for j in range(n): ...      # O(n)  ← 2 vòng NỐI TIẾP → O(2n) = O(n)

while n > 1: n //= 2        # mỗi lần giảm nửa → O(log n)
```
> Quy tắc: **bỏ hằng số** (O(3n) → O(n)), **giữ bậc cao nhất** (O(n²+n) → O(n²)).

### D. Cài đặt các CTDL bằng Python

```python
# STACK — LIFO (vào sau ra trước)
stack = []
stack.append(1); stack.append(2)   # push
top = stack.pop()                  # pop → 2
# Ứng dụng: kiểm tra ngoặc hợp lệ, undo, DFS

# QUEUE — FIFO (vào trước ra trước)
from collections import deque
q = deque()
q.append(1); q.append(2)           # enqueue
first = q.popleft()                # dequeue → 1  (O(1), list.pop(0) là O(n)!)

# HASH TABLE — dict/set
d = {"a": 1}                       # O(1) lookup
count = {}
for x in a: count[x] = count.get(x, 0) + 1

# TREE
class TreeNode:
    def __init__(self, v): self.v = v; self.left = self.right = None

# GRAPH — danh sách kề
G = {"A": ["B","C"], "B": ["D"], "C": ["D"], "D": []}
```

**Ứng dụng Stack — kiểm tra ngoặc:**
```python
def valid_brackets(s):
    st, pair = [], {')':'(', ']':'[', '}':'{'}
    for c in s:
        if c in "([{": st.append(c)
        elif c in ")]}":
            if not st or st.pop() != pair[c]: return False
    return not st
```

### E. Các chiến lược thuật toán (Algorithm Paradigms)

| Chiến lược | Tư tưởng | Ví dụ |
|---|---|---|
| **Brute force** (vét cạn) | thử mọi khả năng | dò mật khẩu, tìm cặp O(n²) |
| **Divide & Conquer** (chia để trị) | chia nhỏ → giải → gộp | merge sort, quick sort, binary search |
| **Greedy** (tham lam) | chọn tốt nhất **tại mỗi bước** | đổi tiền, chọn công việc, Dijkstra |
| **Dynamic Programming** (QHĐ) | lưu kết quả bài toán con, tránh tính lại | fib memo, balo, LCS, đường đi ngắn nhất |
| **Backtracking** (quay lui) | thử → sai → lùi lại | 8 quân hậu, sudoku, mê cung |
| **Recursion** | gọi lại chính nó | cây, tháp Hà Nội |
| **Two pointers / Sliding window** | nhiều con trỏ trên mảng | xem Chương 6 |

**Greedy — đổi tiền:**
```python
def doi_tien(amount, coins=[500,200,100,50,20,10,5,1]):
    res = {}
    for c in coins:
        if amount >= c:
            res[c] = amount // c
            amount %= c
    return res
print(doi_tien(1275))
```

**Dynamic Programming — fib O(n):**
```python
def fib_dp(n):
    dp = [0, 1] + [0]*(n-1)
    for i in range(2, n+1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n]
```

### F. Thuật toán sắp xếp — Merge & Quick (Divide & Conquer)

```python
def merge_sort(a):
    if len(a) <= 1: return a
    mid = len(a)//2
    L, R = merge_sort(a[:mid]), merge_sort(a[mid:])
    out, i, j = [], 0, 0
    while i < len(L) and j < len(R):
        if L[i] <= R[j]: out.append(L[i]); i += 1
        else:            out.append(R[j]); j += 1
    return out + L[i:] + R[j:]
# O(n log n) mọi trường hợp, cần O(n) RAM, ỔN ĐỊNH (stable)

def quick_sort(a):
    if len(a) <= 1: return a
    pivot = a[len(a)//2]
    left  = [x for x in a if x < pivot]
    mid   = [x for x in a if x == pivot]
    right = [x for x in a if x > pivot]
    return quick_sort(left) + mid + quick_sort(right)
# O(n log n) trung bình, O(n²) xấu nhất
```

| Thuật toán | Best | Average | Worst | Space | Stable |
|---|---|---|---|---|---|
| Bubble | O(n) | O(n²) | O(n²) | O(1) | ✅ |
| Selection | O(n²) | O(n²) | O(n²) | O(1) | ❌ |
| Insertion | O(n) | O(n²) | O(n²) | O(1) | ✅ |
| **Merge** | O(n log n) | O(n log n) | O(n log n) | O(n) | ✅ |
| **Quick** | O(n log n) | O(n log n) | O(n²) | O(log n) | ❌ |
| Python `sorted()` (Timsort) | O(n) | O(n log n) | O(n log n) | O(n) | ✅ |

### G. Thuật toán trên đồ thị (liên hệ GIS của bạn 🗺️)

```python
# BFS — duyệt theo chiều rộng (tìm đường đi ÍT CẠNH NHẤT)
from collections import deque
def bfs(G, start):
    visited, q, order = {start}, deque([start]), []
    while q:
        u = q.popleft(); order.append(u)
        for v in G[u]:
            if v not in visited:
                visited.add(v); q.append(v)
    return order

# DFS — duyệt theo chiều sâu
def dfs(G, u, visited=None):
    if visited is None: visited = set()
    visited.add(u)
    for v in G[u]:
        if v not in visited: dfs(G, v, visited)
    return visited

# DIJKSTRA — đường đi ngắn nhất có trọng số (⭐ nền tảng routing GIS)
import heapq
def dijkstra(G, src):
    dist = {v: float('inf') for v in G}
    dist[src] = 0
    pq = [(0, src)]
    while pq:
        d, u = heapq.heappop(pq)
        if d > dist[u]: continue
        for v, w in G[u]:
            if d + w < dist[v]:
                dist[v] = d + w
                heapq.heappush(pq, (dist[v], v))
    return dist

G = {"A":[("B",4),("C",1)], "B":[("D",1)], "C":[("B",2),("D",5)], "D":[]}
print(dijkstra(G, "A"))   # {'A':0, 'B':3, 'C':1, 'D':4}
```

---

## 5.3. Applications (Ứng dụng thuật toán)

| Bài toán thực tế | Thuật toán | CTDL |
|---|---|---|
| Tìm đường Google Maps / OSRM | **Dijkstra, A\*** | Graph + Heap |
| Gợi ý bạn bè Facebook | BFS, community detection | Graph |
| Tìm kiếm văn bản | KMP, Rabin-Karp | String |
| Nén file ZIP / PNG | Huffman, LZW | Tree |
| Mã hóa RSA | Euclid, lũy thừa modulo | Number theory |
| Xếp lịch, phân công | Greedy, backtracking | Interval |
| **Phân vùng lưu vực (D8)** | DFS/queue trên raster | Array 2D |
| **Flood mapping từ ảnh vệ tinh** | Ngưỡng + connected components | Tensor + Stack |
| **Nội suy IDW / Kriging** | Khoảng cách + trọng số | KD-Tree |
| ML dự đoán | Gradient descent | Matrix/Tensor |
| Autocomplete | Trie | Tree |
| Xếp hạng trang web | PageRank | Graph |

---

# 📝 PRACTICE TỔNG HỢP (Chương 1–3, 6–7)

## 🟢 Lý thuyết — tự trả lời được là đạt

1. Kể 4 thành phần mô hình Von Neumann + chức năng.
2. Trình bày chu kỳ Fetch–Decode–Execute.
3. Compiler khác Interpreter ở 4 điểm nào? Python thuộc loại nào?
4. Vì sao nói Python "dynamically typed nhưng strongly typed"?
5. Giải thích "Program = Objects + Operations" bằng ví dụ 3 dòng code.
6. Expression khác Statement thế nào? Cho ví dụ.
7. Kể 8 kiểu dữ liệu built-in, chỉ rõ mutable/immutable.
8. Vì sao `0.1 + 0.2 != 0.3`? Cách so sánh đúng?
9. `-7 // 2` và `-7 % 2` bằng bao nhiêu? Giải thích.
10. `if __name__ == "__main__":` để làm gì?
11. Phân biệt parameter và argument. Kể 5 loại tham số.
12. Quy tắc LEGB là gì? Khi nào dùng `global`, `nonlocal`?
13. Vì sao `def f(a=[])` nguy hiểm? Sửa thế nào?
14. Python truyền tham số theo cơ chế nào? Cho ví dụ list và int.
15. Hàm không có `return` trả về gì?
16. Hai thành phần bắt buộc của đệ quy?
17. Python có con trỏ không? Trả lời đầy đủ.
18. `is` khác `==` thế nào? Khi nào dùng `is`?
19. Shallow copy khác deep copy ra sao?
20. Kể 5 tính chất của thuật toán.
21. Sắp xếp: O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ).
22. Vì sao `deque.popleft()` nhanh hơn `list.pop(0)`?
23. Kỹ thuật two pointers giải Two Sum trên mảng sắp xếp thế nào?
24. Merge sort vs Quick sort: độ phức tạp và tính ổn định.
25. Program = Data Structures + Algorithms — giải thích.

## 🟡 Code cơ bản

**C1.** Hàm kiểm tra số hoàn hảo (tổng ước thực sự = chính nó, VD 6 = 1+2+3).
```python
def perfect(n):
    return n > 1 and sum(i for i in range(1, n//2+1) if n % i == 0) == n
```

**C2.** Hàm chuyển °C ↔ °F ↔ K, có tham số mặc định.
```python
def doi_nhiet(x, don_vi="C", sang="F"):
    c = x if don_vi=="C" else (x-32)*5/9 if don_vi=="F" else x-273.15
    return c*9/5+32 if sang=="F" else c+273.15 if sang=="K" else c
```

**C3.** Hàm nhận `*args` trả về (min, max, mean, stdev).

**C4.** Đệ quy tính tổng chữ số: `s(n) = n%10 + s(n//10)`, base `n==0`.

**C5.** Chứng minh aliasing: viết hàm sửa list và hàm không sửa được int.

**C6.** Dùng `Counter` đếm tần suất và in top-3 phần tử.

## 🔴 Code tổng hợp

**C7.** Cài Stack bằng class, dùng kiểm tra chuỗi ngoặc hợp lệ.

**C8.** Cài Two Sum bằng 2 cách: brute force O(n²) và two pointers O(n), đo thời gian bằng `time.perf_counter()` với n = 10.000.
```python
import time
t0 = time.perf_counter(); two_sum(a, target)
print(f"{time.perf_counter()-t0:.6f}s")
```

**C9.** Viết merge sort + đếm số lần so sánh, so sánh với bubble sort.

**C10.** Mô phỏng Monte Carlo tính xác suất ít nhất 1 mặt 6 khi tung 3 xúc xắc (lý thuyết = 1 − (5/6)³ ≈ 0.4213).

**C11.** Xây graph thành phố, chạy Dijkstra tìm đường ngắn nhất, in đường đi (lưu thêm `prev`).

**C12.** Chương trình hoàn chỉnh: đọc file CSV điểm → làm sạch → tính ĐTB → xếp loại → sắp xếp → vẽ histogram → ghi JSON. *(Tổng hợp cả 7 chương — rất hợp để làm đồ án cuối kỳ.)*

---

# 🗺️ BẢN ĐỒ ÔN THI — DẠNG ĐỀ → CHƯƠNG → CÔNG CỤ

| Đề bài xuất hiện chữ… | Chương | Dùng ngay |
|---|---|---|
| "CPU / ALU / bộ nhớ / chu kỳ lệnh" | 1 | Von Neumann + Fetch-Decode-Execute |
| "biên dịch vs thông dịch" | 1 | bảng so sánh |
| "kiểu dữ liệu / đổi kiểu / làm tròn" | 2 | bảng type + bẫy float |
| "thư viện / import / pip" | 2 | bảng standard library |
| "tham số / đối số / mặc định" | 3 | 5 loại tham số |
| "biến cục bộ / toàn cục" | 3 | LEGB + global/nonlocal |
| "viết hàm / đệ quy" | 3 | def + base case |
| "list / chuỗi / tuple / slicing" | 4 | bảng method + `[::-1]` |
| "ma trận / vector / tensor / axis" | 4 | list lồng / NumPy |
| "vòng lặp / điều kiện / menu" | 5 | for / while / if-elif |
| "id / is / copy / alias" | 6 | reference + deepcopy |
| "hai con trỏ / tối ưu O(n)" | 6 | two pointers patterns |
| "độ phức tạp / Big-O / sắp xếp" | 7 | bảng Big-O |
| "ngăn xếp / hàng đợi / đồ thị" | 7 | list / deque / dict |

---

# 📅 LỘ TRÌNH 7 TUẦN (khớp đúng slide của thầy)

| Tuần | Chương | Việc phải làm | Sản phẩm |
|---|---|---|---|
| 1 | 01 | Vẽ lại sơ đồ Von Neumann từ trí nhớ; thuộc bảng compiler/interpreter | 1 trang A4 lý thuyết |
| 2–3 | 02 | Thuộc bảng data type; viết 10 chương trình IPO nhỏ; thử pandas | `basics.py` |
| 4–5 | 03 | Viết 15 hàm; thử nghiệm global/nonlocal; 5 bài đệ quy | `functions.py` |
| 6 | 04 | 20 bài list/str/tuple + 10 bài ma trận | `sequences.py` |
| 7 | 05 | 20 bài vòng lặp + vẽ hình + menu | `loops.py` |
| 8 | 06 | Chứng minh aliasing bằng `id()`; cài 5 pattern two pointers | `pointers.py` |
| 9 | 07 | Cài stack/queue/BFS/Dijkstra + 5 sort; đo thời gian | `algorithms.py` |

---

## ⚡ 10 SỰ THẬT QUYẾT ĐỊNH ĐIỂM SỐ

1. `input()` **luôn** trả `str` → phải ép kiểu.
2. `/` ra float, `//` làm tròn **xuống**, `%` theo dấu **số chia**.
3. Immutable: `int, float, str, tuple, bool, frozenset` → hashable → làm key dict được.
4. `b = a` là **alias**, không phải copy.
5. `[[0]*n]*m` là **bẫy** ma trận.
6. Hàm không `return` → `None`.
7. Mặc định mutable `def f(a=[])` → **bẫy tích lũy**.
8. `is` so **địa chỉ**, `==` so **giá trị**; chỉ dùng `is` với `None`.
9. `for...else` / `while...else`: else chạy khi **không bị break**.
10. `sorted()` trả list mới (O(n log n)), `list.sort()` trả `None`.

---

Thiên ơi, giờ bạn đã có **trọn bộ 7 chương** (tin trước: Ch04–05, tin này: Ch01–03, 06–07). Bộ này đủ để xử lý mọi dạng đề thầy ra.

Muốn mình làm tiếp cái nào?
1. 📄 **Gói file `.py` chạy được** — mỗi chương 1 file, có `assert` tự kiểm tra để bạn vừa học vừa test
2. 📝 **Đề mô phỏng thi cuối kỳ 90 phút** (trắc nghiệm lý thuyết 20 câu + tự luận code 4 câu) rồi mình chấm chi tiết
3. 🎯 **Bộ 100 câu hỏi lý thuyết có đáp án** để học thuộc nhanh trước thi
4. 🗺️ **Đồ án cuối kỳ theo ngành GIS** — dùng trọn 7 chương để làm công cụ phân tích điểm/bản đồ, vừa nộp bài vừa bỏ vào portfolio du học
