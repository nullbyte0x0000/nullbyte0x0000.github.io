---
layout: post
title: Mẫu Decorator C++
subtitle: Mở rộng một chức năng
tags: [Design Pattern, Decorator Pattern, C++]
---

Mẫu Decorator (mẫu trang trí) là mẫu được dùng khi bạn muốn mở rộng một chức năng mà không muốn sửa nó ở lớp cơ sở. Yếu quyết của mẫu này là: “Đóng cho việc sửa đổi, mở cho việc mở rộng”. Với mẫu Decorator, các chức năng của lớp cơ sở sẽ được giữ nguyên, không thay đổi. Bạn mở rộng nó bằng cách tạo một lớp Wrapper để bọc lấy nó. Trong Wrapper bạn sẽ gọi chức năng của lớp cơ sở và sau đó thêm vào thứ bạn muốn bổ sung.

+![wrapper](https://github.com/bachns/bachns.github.io/blob/master/img/wrapper.png?raw=true){: .center-block :}

**Ví dụ:** Chúng ta phải xây dựng hai class Desktop và Laptop. Yêu cầu hai class này phải có các phương thức ***description()*** để mô tả và ***cost()*** để tính giá tiền. Như vậy, ta sẽ tạo một interface Computer chung cho cả hai lớp, đương nhiên các phương thức trong interface là ***description()*** và ***cost()***.

Yêu cầu đặt ra tiếp, các đối tượng Desktop, Laptop có thể có hoặc không các thiết bị đi kèm như Monitor, Scanner… Khi gắn thêm các thiết bị này thì Destop và Laptop phải có mô tả và giá tiền khác. Vẫn là tên các phương thức ***description()*** và ***cost()*** đó, nhưng nội dung của bọn nó phải được thay đổi khi gắn thêm Monitor hoặc Scanner.

Vậy làm sao để thay đổi, mở rộng ***description()*** và ***cost()*** mà không làm thay đổi các class Desktop và Laptop. Mẫu Decorator sẽ giải quyết vấn đề này.

+![Decorator Pattern](https://github.com/bachns/bachns.github.io/blob/master/img/decorator-pattern.png?raw=true){: .center-block :}

Trong đó:
* Computer: là Interface chung
* Desktop, Laptop: là các lớp hiện thực của Interface Computer
* ComponentDecorator: là Abstract class, cùng triển khai Interface Computer như Desktop và Laptop
* Monitor, Scanner: là các lớp hiện thực của ComponentDecorator. Việc tính tiền, trang trí cụ thể như thế nào sẽ được thực hiện ở đây

```cpp

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
