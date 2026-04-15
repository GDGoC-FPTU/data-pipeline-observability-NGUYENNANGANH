[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572374&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** 2A202600184
**Name:** Nguyen Nang Anh
**Email:** 26ai.anhnn@vinuni.edu.vn

---

## Mo ta

Bai lab ngay 10 xay dung mot ETL (Extract - Transform - Load) pipeline hoan chinh de xu ly du lieu san pham tu file JSON. Pipeline thuc hien cac buoc: doc du lieu, kiem tra chat luong (loai bo gia am va category rong), chuan hoa du lieu (Title Case, gia giam 10%), va luu ket qua ra CSV. Ngoai ra, bai lab con thuc hien stress test de so sanh hieu qua cua AI Agent khi su dung du lieu sach vs du lieu "rac", qua do chung minh tam quan trong cua data quality trong cac he thong AI.

---

## Cach chay (How to Run)

### Prerequisites

Cai dat cac thu vien can thiet:

```bash
pip install pandas pytest
```

### Chay ETL Pipeline

```bash
python solution.py
```

Sau khi chay, file `processed_data.csv` se duoc tao ra voi 3 records hop le (2 records bi loai: 1 gia am, 1 category rong).

### Chay Agent Simulation (Stress Test)

Buoc 1: Tao file du lieu rac

```bash
python generate_garbage.py
```

Buoc 2: Chay agent simulation de so sanh ket qua

```bash
python agent_simulation.py
```

Agent se cho ket qua khac nhau ro ret giua clean data va garbage data.

### Chay Tests

```bash
pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script (extract, validate, transform, load)
├── raw_data.json            # Du lieu dau vao (5 records, co ca record loi)
├── processed_data.csv       # Output cua pipeline (3 records hop le)
├── garbage_data.csv         # Du lieu rac de stress test
├── generate_garbage.py      # Script tao du lieu rac
├── agent_simulation.py      # Demo Agent so sanh clean vs garbage data
├── experiment_report.md     # Bao cao thi nghiem stress test
└── README.md                # File nay
```

---

## Ket qua

- **Tong so records doc vao:** 5
- **Records hop le (valid):** 3 (Laptop, Chair, Monitor)
- **Records bi loai (dropped):** 2
  - Mystery Box (price = -10, gia am)
  - Phone (category = "", rong)
- **Stress Test:** Agent cho ket qua chinh xac voi clean data (Laptop $1200), nhung tra ve ket qua vo nghia voi garbage data (Nuclear Reactor $999,999) do outlier cuc doan.
