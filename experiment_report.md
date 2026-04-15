# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600184
**Name:** Nguyen Nang Anh
**Email:** 26ai.anhnn@vinuni.edu.vn
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | "Based on my data, the best choice is Laptop at $1200." | 9 | Ket qua chinh xac, Laptop la san pham electronics gia cao nhat hop le |
| Garbage Data (`garbage_data.csv`) | "Based on my data, the best choice is Nuclear Reactor at $999999." | 1 | Ket qua sai, Agent bi anh huong boi outlier cuc doan trong du lieu rac |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung bo du lieu sach (clean data) da qua xu ly ETL, Agent cho ket qua chinh xac va co y nghia thuc te. Laptop duoc chon vi day la san pham electronics co gia hop le cao nhat. Tuy nhien, khi su dung garbage data, Agent tra ve ket qua hoan toan sai lech va khong co y nghia thuc te.

Co ba van de chinh trong garbage data anh huong den Agent. Thu nhat, co mot extreme outlier la "Nuclear Reactor" voi gia $999,999 - day la gia tri bat thuong khong phan anh thuc te thi truong. Vi Agent tim san pham co gia cao nhat trong danh muc electronics, no bi "danh lua" boi gia tri nay. Thu hai, garbage data co duplicate ID (ca hai record id=1 cho Laptop va Banana), gay ra tinh trang du lieu khong nhat quan. Thu ba, co cac gia tri null va wrong data types (price = "ten dollars") co the gay ra loi khi xu ly.

Day la minh chung ro rang cho thay rang chat luong du lieu dau vao (data quality) anh huong truc tiep va manh me den ket qua cua AI Agent. Mot mo hinh AI du thong minh den dau cung se cho ket qua sai neu du lieu no dua vao bi "rac" (garbage in, garbage out). Vi vay, buoc validate va clean du lieu trong ETL pipeline la vo cung quan trong truoc khi dua du lieu vao bat ky he thong AI nao.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y hoan toan.

Du lieu chat luong cao quan trong hon mot prompt duoc viet tot. Trong thi nghiem nay, du Agent va query hoan toan giong nhau, ket qua tro nen vo nghia khi du lieu dau vao chua cac van de nhu outlier, null values, va duplicate records. ETL pipeline voi buoc validate nghiem ngat chinh la nen tang de bat ky ung dung AI nao hoat dong dung dan va dang tin cay.
