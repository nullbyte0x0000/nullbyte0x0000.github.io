---
layout: post
title: Association - Quan hệ hợp tác
subtitle: Hủy đối tượng này không ảnh hưởng tới đối tượng khác
tags: [Design Pattern, C++]
categories: [Design Pattern]
---

## Association

Quan hệ Association (hợp tác) là quan hệ giữa hai lớp có liên quan gì đó với nhau mà việc hủy lớp này không ảnh hưởng tới lớp khác.

Ví dụ quan hệ giữa:

* Sinh Viên - Lớp Học
* Giáo Viên - Bộ Môn
* v.v.

Khi một đối tượng ***sinhvien*** nào đó bị hủy sẽ không ảnh hưởng gì tới đối tượng ***lophoc***. Tương tự, nếu một đối tượng ***lophoc*** bị hủy thì cũng chẳng ảnh hưởng gì tới đối tượng ***sinhvien***.

Quan hệ Association thường được sử dụng khi một lớp nào đó có biến thành viên là con trỏ của một lớp khác.

Kí hiệu của quan hệ Association là một đường nét liền, có thể có mũi tên hoặc không, thường có nhãn và bản số đi kèm để giải thích rõ hơn về quan hệ. Trường hợp vẽ quan hệ Association có mũi tên khi muốn thể hiện rõ chiều của quan hệ.

Quay lại với ví dụ trên, chúng ta sẽ có biểu đồ quan hệ Association như sau:

| Association không có mũi tên |
| :--------------------------: |
| ![Association](/img/2020_05_15/Association1.png?raw=true) |

Mọi thứ đến đây là khá ổn rồi. Có điều chúng ta tham lam và muốn thể hiện rõ hơn nữa. Ta sẽ sử dụng association có mũi tên, nhãn và bản số để làm điều này.

Hai cách dưới đây là như nhau, chú ý nhãn thay đổi để phù hợp với chiều của mũi tên.

| Association có mũi tên |
| :--------------------------: |
| ![Association](/img/2020_05_15/Association2.png?raw=true) |
| ![Association](/img/2020_05_15/Association3.png?raw=true) |

Tuyệt vời! Vậy là mọi thứ đã rõ ràng. Từ biểu đồ ta có thể dễ dàng phát biểu:

* Nhiều **Sinh Viên** thuộc một **Lớp Học**; Nhiều **Giáo Viên** thuộc một **Bộ Môn**

hoặc

* Một **Lớp Học** có nhiều **Sinh Viên**; Một **Bộ Môn** có nhiều **Giáo Viên**

```cpp
// Giáo viên
class GiaoVien
{
}

// Bộ môn
class BoMon
{
public:
    void add(GiaoVien* gv);
    void remove(GiaoVien* gv);

private:
    std::vector<GiaoVien*> mDanhSachGiaoVien;
}

```
