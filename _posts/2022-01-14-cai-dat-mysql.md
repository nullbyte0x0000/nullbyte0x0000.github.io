---
layout: post
title: Cài đặt MySQL trên macOS
subtitle: Đơn giản, nhanh gọn lẹ
tags: [mysql, brew]
categories: [Programming, macOS]
---

Cài đặt bằng brew

    brew install mysql

Chạy hoặc dừng dịch vụ

    mysql.server start
    mysql.server stop

*Khởi động hoặc gỡ khởi động cùng hệ thống (tuỳ chọn)*

    brew services start mysql
    brew services start mysql

Cấu hình bảo mật cho root

    mysql_secure_installation

Thực hiện kết nối tới server

    mysql -u root -p
