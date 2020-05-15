---
layout: post
title: Association - Quan hệ hợp tác
subtitle: Hủy đối tượng này không ảnh hưởng tới đối tượng khác
tags: [Association, UML, C++]
categories: [Design Pattern]
---

## Quan hệ Association

| Kí hiệu |
| :-----: |
| ![Association](/img/2020_05_15/Association1.png?raw=true) |

Quan hệ Association (hợp tác) là quan hệ giữa hai lớp có liên quan gì đó với nhau mà việc hủy lớp này không ảnh hưởng tới lớp khác.

Ví dụ quan hệ giữa:

* Học sinh - Giáo viên
* Nhân viên - Phòng ban
* Con người - Địa chỉ
* Vợ - Chồng
* v.v.

![Association](/img/2020_05_15/Association2.png?raw=true){: .center-block :}

Khi một đối tượng ***hocsinh*** bị hủy sẽ không ảnh hưởng gì tới đối tượng ***giaovien***. Tương tự, nếu một đối tượng ***giaovien*** bị hủy thì cũng không ảnh hưởng gì tới đối tượng ***hocsinh***...

Kí hiệu của quan hệ Association là một đường nét liền, có thể vẽ hình mũi tên hoặc không, thường có nhãn và bản số đi kèm để giải thích rõ hơn về quan hệ. Trường hợp vẽ quan hệ Association hình mũi tên là muốn thể hiện rõ chiều của quan hệ.

***Chú ý:*** Association sử dụng mũi tên gai, đừng nhầm lẫn nó với mũi tên đầu tam giác.

Quan hệ Association được sử dụng khi:
* **ClassA** có biến thành viên là chính là con trỏ **ClassA**
* **ClassA** có biến thành viên là con trỏ **ClassB**
* **ClassA** chứa một tập các đối tượng của **ClassB**

### Trường hợp ClassA có biến thành viên là con trỏ ClassA

![association](/img/2020_05_15/Association3.png?raw=true){: .center-block :}

```cpp
class Person
{
public:
	explicit Person(const string& name);
	//lấy con trỏ người vợ hoặc chồng
	Person* spouse() const;
	void setSpouse(Person* p);
    
private:
	string mName;
	//Người vợ hoặc chồng
	Person* mSpouse; //Quan hệ association
};
```

### Trường hợp ClassA có biến thành viên là con trỏ ClassB

![association](/img/2020_05_15/Association4.png?raw=true){: .center-block :}

```cpp
class Address
{
};

class Person
{
public:
	explicit Person(const string& name);
	Address* address() const;
	void setAddress(Address* address);
	
private:
	string mName;
	Address* mAddress = nullptr;
};
```

Khi có hai địa chỉ, một địa chỉ nhà, một địa chỉ cơ quan:

![association](/img/2020_05_15/Association5.png?raw=true){: .center-block :}

```cpp
class Address
{
};

class Person
{
public:
	explicit Person(const string& name);
	Address* homeAddress() const;
	Address* officeAddress() const;
	void setHomeAddress(Address* address);
	void setOfficeAddress(Address* address);
	
private:
	string mName;
	Address* mHomeAddress = nullptr; //Quan hệ association
	Address* mOfficeAddress = nullptr; //Quan hệ association
};
```

### Trường hợp ClassA chứa một tập các đối tượng của ClassB

![association](/img/2020_05_15/Association6.png?raw=true){: .center-block :}

```cpp
class Student
{
public:
	explicit Student(const string& name);
	
private:
	string mName;
};

class Teacher
{
public:
	explicit Teacher(const string& name);
	void add(Student* student);
	void remove(Student* student);
	
private:
	string mName;
	vector<Student*> mStudents; //Quan hệ association
};
```

