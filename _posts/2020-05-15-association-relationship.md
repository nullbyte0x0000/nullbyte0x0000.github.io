---
layout: post
title: Association - Quan hệ liên hệ/hợp tác
subtitle: Hủy đối tượng này không ảnh hưởng tới đối tượng khác
tags: [Association, UML, C++]
categories: [Design Pattern]
---

## Quan hệ Association

| Kí hiệu |
| :-----: |
| ![Association](/img/2020_05_15/Association1.png?raw=true) |

Quan hệ Association (liên hệ/hợp tác) là quan hệ giữa hai lớp có liên quan gì đó với nhau mà việc hủy lớp này không ảnh hưởng tới lớp khác.

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
* **ClassA** có biến thành viên là chính là **ClassA**
* **ClassA** có biến thành viên là **ClassB**
* **ClassA** chứa một tập các đối tượng của **ClassB**

### Trường hợp ClassA có biến thành viên là ClassA

![association](/img/2020_05_15/Association3.png?raw=true){: .center-block :}

```cpp
class Person
{
public:
	explicit Person(const string& name);
	//lấy người vợ hoặc chồng
	Person spouse() const;
	void setSpouse(const Person& p);
    
private:
	string mName;
	//Người vợ hoặc chồng
	Person mSpouse; //Quan hệ association
};
```

### Trường hợp ClassA có biến thành viên là ClassB

![association](/img/2020_05_15/Association4.png?raw=true){: .center-block :}

```cpp
class Address
{
};

class Person
{
public:
	explicit Person(const string& name);
	Address address() const;
	void setAddress(const Address& address);
	
private:
	string mName;
	Address mAddress;
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
	Address homeAddress() const;
	Address officeAddress() const;
	void setHomeAddress(const Address& address);
	void setOfficeAddress(const Address& address);
	
private:
	string mName;
	Address mHomeAddress; //Quan hệ association
	Address mOfficeAddress; //Quan hệ association
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
	void addStudent(const Student& student);
	
private:
	string mName;
	vector<Student> mStudents; //Quan hệ association
};
```

Hoặc chi tiết hơn nữa sẽ như thế này:

![association](/img/2020_05_15/Association7.png?raw=true){: .center-block :}

```cpp
#include <iostream>
#include <utility>
#include <vector>
#include <string>
#include <utility>

using namespace std;

class Teacher;

class Student
{
public:
	explicit Student(string name)
		: mName(std::move(name))
	{
	}

	string name() const
	{
		return mName;
	}

	void addTeacher(const Teacher& teacher)
	{
		mTeachers.push_back(teacher);
	}

	friend ostream& operator<< (ostream& out, const Student& student);

private:
	string mName;
	vector<Teacher> mTeachers;
};

class Teacher
{
public:
	explicit Teacher(string name)
		: mName(std::move(name))
	{
	}

	string name() const
	{
		return mName;
	}

	void addStudent(Student& student)
	{
		mStudents.push_back(student);
		student.addTeacher(*this);
	}

	friend ostream& operator<< (ostream& out, const Teacher& teacher)
	{
		out << "Teacher: " << teacher.name() << endl;
			cout << "  students {" << endl;
		for (const Student& student : teacher.mStudents)
			out << "    " << student.name() << endl;
		out << "  }" << endl;
		return out;
	}

private:
	string mName;
	vector<Student> mStudents; //Quan hệ association
};

ostream& operator<<(ostream& out, const Student& student)
{
	out << "Student: " << student.name() << endl;
	cout << "  teachers {" << endl;
	for (const Teacher& teacher : student.mTeachers)
		out << "    " << teacher.name() << endl;
	out << "  }" << endl;
	return out;
}

int main(int argc, char* argv[])
{
	Student student1("Lan");
	Student student2("Mai");
	Student student3("Hoa");

	Teacher teacher1("Hung");
	teacher1.addStudent(student1);
	teacher1.addStudent(student2);

	Teacher teacher2("Truong");
	teacher2.addStudent(student1);
	teacher2.addStudent(student3);

	cout << teacher1 << endl;
	cout << teacher2 << endl;
	cout << student1 << endl;
	cout << student2 << endl;
	cout << student3 << endl;

	return 0;
}
```

Kết quả chúng ta nhận được như sau:

```console
Teacher: Hung
  students {
     Lan
     Mai
  }

Teacher: Truong
  students {
     Lan
     Hoa
  }

Student: Lan
  teachers {
     Hung
     Truong
  }

Student: Mai
  teachers {
    Hung
  }

Student: Hoa
  teachers {
     Truong
  }
```