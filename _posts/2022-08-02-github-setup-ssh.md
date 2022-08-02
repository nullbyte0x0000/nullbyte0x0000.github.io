---
layout: post
title: Kết nối tới github bằng ssh
subtitle: Đã xưa rồi username/password
tags: [ssh, github]
categories: [Programming]
---

# Kết nối tới github bằng ssh

## Kiểm tra cặp khoá

Kiểm tra xem liệu máy đã có cặp khoá hay chưa? Nếu chưa có ta sẽ thực hiện tạo mới cặp khoá, nếu đã có ta sẽ bổ sung public key lên tài khoản github.

    ls -al ~/.ssh

## Tạo cặp khoá

Vì lý do bảo mật github không còn hỗ trợ khoá DSA, và hạn chế sử dụng khoá RSA nên ta sẽ sử dụng khoá EdDSA.

    ssh-keygen -t ed25519 -C "bachns@outlook.com"

Ta cũng nên nhập mật khẩu để bảo vệ khoá. Cặp khoá tạo ra sẽ được lưu mặc định trong thư mục `~/.ssh` với tên khoá riêng là `id_ed25519` và khoá công khai là `id_ed25519.pub`.

## Thêm khoá vào ssh-agent

Chạy ssh-agent ở background:

    eval "$(ssh-agent -s)"

Tạo tệp tin `~/.ssh/config` với nội dung như sau:

    Host *
    AddKeysToAgent yes
    UseKeychain yes
    IdentityFile ~/.ssh/id_ed25519

Thêm khoá vào `ssh-agent`:

    ssh-add -K ~/.ssh/id_ed25519

## Thiết lập SSH cho tài khoản

Copy nội dung khoá công khai vào trong bộ đêm clipboard bằng lệnh:

    pbcopy < ~/.ssh/id_ed25519.pub

Đăng nhập vào tài khoản github, tiếp đó truy cập `https://github.com/settings/keys` để thiết lập khoá. Nhấn `New SSH key`, nhập tiêu đề và paste nội dung đã copy trước đó và mục `Key`, sau cùng nhấn `Add SSH key`.

## Thử kết nối tới github

Ta sử dụng lệnh sau để kiểm tra kết nối tới github:

    ssh -T git@github.com

## Địa chỉ truy cập tới repository qua ssh

Thay vì sử dụng địa chỉ `https://github.com/<username>/repository.git` hãy sử dụng địa chỉ mới như dưới đây:

    git@github.com:<username>/<repository>.git
