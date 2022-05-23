---
layout: post
title: Hướng dẫn cơ bản về Networking trong docker
subtitle: Cách để kết nối các container lại với nhau
tags: [docker, networking, container]
categories: [docker]
---

![](/img/2022_05_18/docker.png?raw=true "Docker")

Như chúng ta đã biết, các container là hoàn toàn độc lập với nhau, chúng không thể giao tiếp với các container khác. Vậy nếu muốn các container giao tiếp với nhau thì phải thế nào? Trong bài này tôi sẽ giới thiệu cách sử dụng networking để kết nối các container lại với nhau.

## Chuẩn bị 

Để thực hiện bài lab này, chúng ta cần có các container. Do vậy, tôi sẽ sử dụng alpine image làm nguyên liệu để chạy thành các container. Nếu bạn chưa biết thì Alpine Linux là một hệ điều hành nhân linux siêu nhỏ gọn, image của nó chỉ 5 Mb thôi nhé. Ta sẽ tải alpine image từ docker hub.

```
docker pull alpine
```

## Khám phá mạng bridge

### 1. Xem các mạng đang có

Để xem danh sách các mạng đang có, ta sử dụng lệnh sau:
```
docker network ls
```

Mặc định sẽ có 3 mạng *bridge*, *host*, và *none*. Bài này chúng ta chỉ quan tâm đến mạng *bridge* thôi, hai mạng *host* và *none* được sử dụng nâng cao, sẽ giới thiệu sau. 

### 2. Chạy các container

Chúng ta sẽ chạy hai container alpine và đặt tên chúng lần lượt là alpine1 và alpine2 bằng các lệnh sau: 

```
docker run -it -d --name alpine1 alpine ash
docker run -it -d --name alpine2 alpine ash
```

Trong đó: *-it* để đưa câu lệnh muốn thực thi vào cho container, ở đây chúng ta đã đưa vào câu lệnh: ash (ở cuối), đây là bash của Alpine Linux. *-d* để container chạy ở chế độ background, *--name alpine1* và *--name alpine2* là đặt tên cho container. *alpine* là tên image chúng ta sử dụng, image này đã được tải từ docker hub ở phần trên. *ash* là lệnh chúng ta muốn container thực thi.

Xem các container đang chạy, chúng ta sẽ nhìn thấy hai container là alpine1 và alpine2.

```
docker container ls
```

### 3. Xem thông tin về mạng 
Mặc định, khi chạy các container mà không chỉ định rõ mạng liên kết (không có --network) thì sẽ được kết nối vào mạng *bridge*. Do đó, hai lệnh chạy container ở trên sẽ đặt các container này vào mạng *bridge*. Chúng ta có thể xem thông tin về mạng *bridge* bằng câu lệnh dưới. 

```
docker network inspect bridge
```

Chú ý trong phần "Containers" ta sẽ thấy danh sách các container đang kết nối vào mạng này, cùng các thông tin như: Tên, địa chỉ MAC, địa chỉ IP. Hãy nhớ địa chỉ IP của hai container alpine1 và alpine2.

### 4. Vào trong container 

Các container đang được chạy nền, để vào các container này ta sử dụng lệnh **docker attach**. Ta thực hiện vào container alpine1:

```
docker attach alpine1
```

Lúc này, terminal của chúng ta sẽ xuất hiện "**/ #**" để chỉ báo rằng, ta đang ở trong container, và ta hoàn toàn có thể gõ các lệnh ở đây. Tôi sẽ xem địa chỉ IP của container này

```
ip addr show
```

Nhìn vào eth0 interface, ta sẽ thấy địa chỉ ip giống như khi xem trong mục "Containers" của mạng *bridge*. 

Khi hai container ở trên cùng một mạng, chúng hoàn toàn có thể liên lạc được với nhau. Ta có thể sử dụng lệnh ping để kiểm tra. Ta sử dụng thêm đối số "-c" để giới hạn chỉ gửi 4 gói tin.

*Lưu ý: Địa chi ip container của bạn có thể khác.*

```
ping 172.17.0.3 -c 4
```

Từ kết quả của lệnh ping cho thấy hai container đã thông nhau, bạn có thể thực hiện điều tương tự, từ alpine2 ping sang alpine1. 

Để đi ra khởi container mà không dừng nó lại, ta nhấn tổ hợp phím **Ctrl + pq**. Lúc này container vẫn tiếp tục chạy ở nền.

## Khám phá mạng bridge tự tạo

Ở phần trên chúng ta đang để các container mặc định kết nối vào mạng *bridge*. Vấn đề sẽ xuất hiện khi có nhiều container cùng kết nối vào mạng *bridge* này mà chúng ta lại muốn gom nhóm, tách riêng chúng ra thì phải làm sao? Khi đó chúng ta sẽ sử dụng mạng bridge tự tạo (user-defined bridge).

### 1. Tạo mạng user-defined bridge

Chúng ta sẽ tạo một mạng có tên là: *bachns-network*

```
docker network create --driver bridge bachns-network
```

### 2. Xem các mạng đang có

```
docker network ls
```

Ta sẽ nhìn thấy mạng *bachns-network* vừa tạo. Tương tự, ta cũng có thể xem thông tin về mạng này

```
docker network inspect bachns-network
```

Trong phần "Config" ta sẽ thấy có một giải mạng mới, khác với giải mạng **bridge**. 

### 3. Kết nối các container tới mạng user-defined bridge

Chúng ta thực hiện chạy hai container alpine rồi đặt tên chúng là alpine3 và alpine4, nhưng lần này ta sẽ chỉ định rõ mạng mà hai container này kết nối vào cụ thể là mạng *bachns-network* vừa tạo.

```
docker run --network bachns-network -it -d --name alpine3 alpine ash
docker run --network bachns-network -it -d --name alpine4 alpine ash
```

Xem lại thông tin về mạng bachns-network, ta sẽ nhìn thấy có hai container alpine3 và alpine4 đang ở trên nó. Hãy nhớ địa chỉ IP của hai container này.

```
docker network inspect bachns-network
```

### 4. Vào trong container

Tương tự như phần trên, ta sẽ vào trong một container của mạng *bachns-network*. Ở đây ta sẽ vào container alpine3

```
docker attach alpine3
```

Giờ ta thử ping sang alpine4.

```
ping 172.19.0.3 -c 4
```
Ta thấy lệnh ping đã thành công, hai container này thông nhau bởi chúng nằm trên cùng một mạng *bachns-network*.

Tiếp theo, ta thử ping sang alpine1 và alpine2. 

```
ping 172.17.0.2
ping 172.17.0.3
```

Từ kết quả có thể thấy, từ alpine3 ta không thể ping sang alpine1 và alpine2 được, vì chúng nằm ở mạng khác. Đương nhiên, alpine4 cũng không thể ping sang alpine1 và alpine2 (bạn có thể thử).

## Kết luận

Như vậy, trong bài này chúng ta đã biết: Chỉ những container trên cùng một mạng mới giao tiếp được với nhau. Biết cách tạo một mạng mới và kết nối các container vào một mạng.