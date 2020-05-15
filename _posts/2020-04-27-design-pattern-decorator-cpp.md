---
layout: post
title: Mẫu Decorator C++
subtitle: Mở rộng chức năng mà không làm thay đổi lớp cơ sở
tags: [Design Pattern, Decorator Pattern, C++]
categories: [Design Pattern]
---

Mẫu Decorator (mẫu trang trí) là mẫu được dùng khi bạn muốn mở rộng một chức năng mà không muốn sửa nó ở lớp cơ sở. Yếu quyết của mẫu này là: “Đóng cho việc sửa đổi, mở cho việc mở rộng”. Với mẫu Decorator, các chức năng của lớp cơ sở sẽ được giữ nguyên, không thay đổi. Bạn mở rộng nó bằng cách tạo một lớp Wrapper để bọc lấy nó. Trong Wrapper bạn sẽ gọi chức năng của lớp cơ sở và sau đó thêm vào thứ bạn muốn bổ sung.

![wrapper](/img/2020_04_27/wrapper.png?raw=true){: .center-block :}

**Ví dụ:** Chúng ta phải xây dựng hai class Desktop và Laptop. Yêu cầu hai class này phải có các phương thức ***description()*** để mô tả và ***cost()*** để tính giá tiền. Như vậy, ta sẽ tạo một interface Computer chung cho cả hai lớp, đương nhiên các phương thức trong interface là ***description()*** và ***cost()***.

Yêu cầu đặt ra tiếp, các đối tượng Desktop, Laptop có thể có hoặc không các thiết bị đi kèm như Monitor, Scanner… Khi gắn thêm các thiết bị này thì Destop và Laptop phải có mô tả và giá tiền khác. Vẫn là tên các phương thức ***description()*** và ***cost()*** đó, nhưng nội dung của bọn nó phải được thay đổi khi gắn thêm Monitor hoặc Scanner.

Vậy làm sao để thay đổi, mở rộng ***description()*** và ***cost()*** mà không làm thay đổi các class Desktop và Laptop. Mẫu Decorator sẽ giải quyết vấn đề này.

![Decorator Pattern](/img/2020_04_27/decorator-pattern.png?raw=true){: .center-block :}

Trong đó:
* Computer: là Interface chung
* Desktop, Laptop: là các lớp hiện thực của Interface Computer
* ComponentDecorator: là Abstract class, cùng triển khai Interface Computer như Desktop và Laptop
* Monitor, Scanner: là các lớp hiện thực của ComponentDecorator. Việc tính tiền, trang trí cụ thể như thế nào sẽ được thực hiện ở đây

```cpp
#include <iostream>

//Interface
class Computer
{
public:
	virtual ~Computer() = default;
	virtual std::string description() = 0;
	virtual int cost() = 0;
};

//Concrete class
class Desktop : public Computer
{
public:
	std::string description() override
	{
		return "Desktop";
	}
	int cost() override
	{
		return 1000;
	}
};

//Abstract class
class ComponentDecorator : public Computer
{
public:
	std::string description() override = 0;
	int cost() override = 0;
	virtual std::string decoration() = 0;
};


class Monitor : public ComponentDecorator
{
public:
	explicit Monitor(Computer* computer)
		: mComputer(computer)
	{
	}
	std::string description() override
	{
		return mComputer->description() + decoration();
	}
	int cost() override
	{
		return mComputer->cost() + 150;
	}
	std::string decoration() override
	{
		return " and a monitor";
	}

private:
	Computer* mComputer;
};

class Scanner : public ComponentDecorator
{
public:
	explicit Scanner(Computer* computer)
		: mComputer(computer){}

	std::string description() override
	{
		return mComputer->description() + decoration();
	}
	int cost() override
	{
		return mComputer->cost() + 450;
	}
	std::string decoration() override
	{
		return " and a scanner";
	}
	
private:
	Computer* mComputer;
};

int main(int argc, char* argv[])
{
	Computer* computer = new Desktop;
	std::cout << "Cost: " << computer->cost() << std::endl;
	std::cout << computer->description() << std::endl;

	computer = new Monitor(computer);
	std::cout << "Cost: " << computer->cost() << std::endl;
	std::cout << computer->description() << std::endl;

	computer = new Scanner(computer);
	std::cout << "Cost: " << computer->cost() << std::endl;
	std::cout << computer->description() << std::endl;
	
	delete computer;
	return 0;
}
```

Kết quả nhận được:

```console
Cost: 1000
Desktop
Cost: 1150
Desktop and a monitor
Cost: 1600
Desktop and a monitor and a scanner
```

Ok, Mọi thứ đã hoạt động tốt. Mỗi khi chúng ta trang trí (mở rộng) vào Computer nó sẽ được mô tả bổ sung và tính thêm tiền. 
