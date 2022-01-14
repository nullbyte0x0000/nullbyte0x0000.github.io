---
layout: post
title: Cài đặt MySQL trên Mac OS
subtitle: Đơn giản, nhanh gọn lẹ
tags: [mysql, macos]
categories: [Programming]
---

Ghi lại vài dòng về quá trình cài đặt MySQL trên MacOS. Nó khá là đơn giản, chúng ta chỉ cần sử dụng brew là đã cài đặt được rồi.

1. Cài đặt bằng terminal

    ```text
    brew install mysql
    ```

2. Chạy hoặc dừng dịch vụ

    ```text
    mysql.server start
    mysql.server stop
    ```

    *Khởi động hoặc gỡ khởi động cùng hệ thống (tuỳ chọn)*

    ```text
    brew services start mysql
    brew services start mysql
    ```

3. Cấu hình bảo mật cho root

    ```text
    mysql_secure_installation
    ```

4. Thực hiện kết nối tới server

    ```text
    mysql -u root -p
    ```
