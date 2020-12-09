---
layout: post
title: Chiết xuất đối tượng vector từ dữ liệu raster bằng phần mềm Global Mapper
subtitle: Quá trình vector hóa, số hóa
tags: [Raster to vector, Simplify, Smooth, Global Mapper]
categories: [Remote Sensing]
---

## Mở đầu

Cả dữ liệu raster và vector đều đóng vai trò quan trọng trong nghiên cứu, quản lý, khai thác và thành lập bản đồ. Dữ liệu raster thường được biết đến như ảnh hàng không, ảnh vệ tinh; là kiểu dữ liệu bao gồm các ô có kích thước và khoảng cách đều nhau đại diện cho một bề mặt liên tục. Và dữ liệu vector là cấu trúc gồm các điểm, đường hoặc đa giác đại diện các thực thể riêng biệt trên bề mặt trái đất. Đa số các tác vụ bản đồ chỉ có thể thực hiện trên hoặc dữ liệu vector hoặc dữ liệu raster, do đó luôn có sự chuyển đổi qua lại giữa hai loại dữ liệu này. Quá trình chuyển đổi từ loại dữ liệu này sang loại khác luôn là một quá trình tốn nhiều công sức. Nhất là quá trình chuyển dữ liệu từ raster sang vector (quá trình số hóa, vector hóa). Hiện nay, Global Mapper đã cung cấp một số công cụ xử lý dữ liệu giúp giải quyết vấn đề trên. Bài viết này, tác giả sẽ trình bày quy trình để chiết xuất các đối tượng vector từ dữ liệu raster.

## Phần mềm Global Mapper

Global Mapper là một phần mềm xử lý dữ liệu GIS của hãng Blue Marble Geographics, nó dễ dàng sử dụng và hỗ trợ hầu hết các định dạng dữ liệu không gian. Global Mapper rất phù hợp với vai trò là một công cụ xử lý, quản lý dữ liệu không gian độc lập và là một thành phần không thể tách rời của GIS, phần mềm này cần thiết cho bất cứ ai làm việc liên quan đến bản đồ hoặc dữ liệu không gian.

Các công cụ vector hóa lần đầu tiên xuất hiện trên Global Mapper từ phiên bản v.16. Kể từ đó trở đi công cụ này liên tục được cải tiến và mở rộng thêm nhiều tùy chọn ở mỗi lần phát hành phiên bản sau đó.

## Bảng ánh xạ và khoảng mờ màu sắc

Quá trình chiết xuất hoạt động bằng cách chọn các đối tượng có cùng màu sắc hoặc có màu sắc tương tự nhau thỏa mãn một ngưỡng khoảng mờ. Khoảng mờ của hai màu là khoảng cách Euclid của các thành phần màu. Ví dụ, khoảng mờ màu sắc của hai màu <img src="https://render.githubusercontent.com/render/math?math=(R_0, G_0, B_0)"/> và <img src="https://render.githubusercontent.com/render/math?math=(R_1, G_1, B_1)"/> là:

<img src="https://render.githubusercontent.com/render/math?math=\theta = \sqrt{(R_1 - R_0)^2 %2b (G_1 - G_0)^2 %2b (B_1 - B_0)^2}"/>

Khi <img src="https://render.githubusercontent.com/render/math?math=\theta \le \theta_0"/> nào đó thì hai màu được coi là tương tự nhau.

Một số dữ liệu ảnh sử dụng kỹ thuật bảng ánh xạ màu. Thay vì phải sử dụng 3 kênh ảnh để mỗi pixel đều có 3 thành phần màu R, G, B thì kỹ thuật này chỉ sử dụng một kênh ảnh, mỗi pixel chỉ chứa một giá trị chỉ báo, giá trị này sau khi tra bảng ánh xạ màu sẽ biết được màu tương ứng.

Để biết một ảnh có sử dụng bảng ánh xạ màu hay không, trong Global Mapper từ **Control Center (Alt+C)** ta nhấp đúp chuột vào raster layer để mở hộp thoại **Raster Options**, nếu có xuất hiện tab **Palette** thì ảnh có bảng ánh xạ màu.

| Có bảng ánh xạ màu | Không có bảng ánh xạ màu |
| :----------------: | :----------------------: |
| ![Palette](/img/2020_12_06/Hinh1a.png?raw=true "Có bảng ánh xạ màu") | ![BandSetup](/img/2020_12_06/Hinh1b.png?raw=true "Không có bảng ánh xạ màu") |

Thông thường các ảnh sản phẩm bản đồ (ảnh bản đồ) là những ảnh có bảng ánh xạ màu, trong khi những ảnh chụp hàng không và ảnh vệ tinh thường không có.

## Chiết xuất đối tượng

![](/img/2020_12_06/Hinh2.png?raw=true "Quá trình chiết xuất")

Từ thanh menu của phần mềm, ta chọn **Layer/Create Area Features from Equal Values**. Hộp thoại **Setup Equal-Value Area Creation** sẽ xuất hiện, đây là hộp thoại cho chúng ta tùy chọn các tham số: màu sắc của đối tượng cần chiết xuất, loại vùng chiết xuất, giới hạn vùng chiết xuất, ngưỡng mờ màu... Lựa chọn **Only Create Areas for Selected Colors** để chỉ chiết xuất đối tượng với màu chỉ định. Nếu ảnh có sử dụng bảng ánh xạ màu, Global Mapper sẽ hiện hộp thoại **Transparent Color** để người sử dụng chọn, đây là những màu mà các đối tượng trên ảnh đang sử dụng. Nếu không, phần mềm sẽ yêu cầu người dùng nhập giá trị màu trong hộp thoại **Color**.

Để biết giá trị màu sắc của đối tượng, ta sử dụng công cụ **Feature Info Tool (Alt+P)** hoặc xem trên thanh trạng thái góc dưới bên trái khi đưa con trỏ chuột vào đối tượng.

| Hộp thoại Setup Equal-Value Area Creation | Hộp thoại Transparent Color |
| :----------------: | :----------------------: |
|![](/img/2020_12_06/Hinh3a.png?raw=true "Hộp thoại Setup Equal-Value Area Creation")|![](/img/2020_12_06/Hinh3b.png?raw=true "Hộp thoại Transparent Color")<br/>![](/img/2020_12_06/Hinh3c.png?raw=true "Hộp thoại Color")|

Tham số ngưỡng mờ màu sắc được đặt trong mục Setup Allowed Color Fuzziness/Maximum Match Distance. Global Mapper cho phép đặt ngưỡng này trong khoảng [0, 256], đây là khoảng giá trị đã được chuẩn hóa. Trường hợp ảnh sử dụng bảng ánh xạ sẽ không có khoảng mờ màu của cùng một loại đối tượng và ngưỡng khoảng cách mờ sẽ là 0. Với trường hợp ảnh không có bảng ánh xạ màu như ảnh hàng không, các đối tượng sẽ không có màu sắc duy nhất, luôn tồn tại một khoảng mờ màu sắc của cùng một loại đối tượng, do đó ta sẽ nhập một ngưỡng mờ khác 0.

Kết quả chiết xuất đường giao thông từ ảnh bản đồ: Chỉ báo màu Pal Idx 3 – RGB(203, 0, 23), ngưỡng mờ màu 0.

| Ảnh bản đồ | Kết quả |
| :--------: | :----: |
| ![](/img/2020_12_06/Hinh4a.png?raw=true "Ảnh bản đồ") | ![Vector](/img/2020_12_06/Hinh4b.png?raw=true "Kết quả chiết xuất ảnh bản đồ") |

Kết quả chiết xuất vùng hồ nước từ ảnh hàng không: Giá trị màu RGB(71, 116, 96), ngưỡng mờ màu 20.

| Ảnh hàng không | Kết quả |
| :----: | :----: |
| ![](/img/2020_12_06/Hinh4c.png?raw=true "Ảnh hàng không") | ![Vector](/img/2020_12_06/Hinh4d.png?raw=true "Kết quả chiết xuất ảnh hàng không") |

## Làm mịn cạnh
Cấu trúc dữ liệu raster là cấu trúc gồm các ô có kích thước và khoảng cách đều nhau. Dẫn đến các đối tượng thu được từ quá trình chiết xuất luôn có cạnh (hay đường biên) là những đường vuông gấp khúc và điều này là không thẩm mĩ. Do vậy, chúng ta cần làm mịn các đường gấp khúc này, để vừa thẩm mĩ mà vẫn đảm bảo độ chính xác. Công đoạn làm mịn cạnh được thực hiện thông qua hai giai đoạn: Đơn giản hóa và làm trơn. 

Để thực hiện đơn giản hóa ta chọn **Edit/Select All Features with Digitizer Tool** để chọn tất cả các đối tượng. Sau đó sử dụng công cụ đơn giản hóa bằng cách bật công cụ **Digitizer Tool (Alt + D)**, nhấp chuột phải chọn **Move/Reshape Feature(s)/SIMPLIFY - Simplify (Reduce) Vertices of Selected Line/ Area Feature(s)**. Nhập tham số khoảng cách vào ô **Horizontal** trong hộp thoại **Enter Simplification Threshold**.

| Hộp thoại Enter Simplification Threshold |
| :--------------------------------------: |
| ![](/img/2020_12_06/Hinh5.png?raw=true "Hộp thoại Enter Simplification Threshold") |

Sau khi đã đơn giản hóa các cạnh, ta sẽ thực hiện làm trơn các cạnh này. Để thực hiện làm trơn ta cũng chọn tất cả các đối tượng, sau đó bật công cụ Digitizer Tool, nhấp chuột phải chọn Move/Reshape Feature(s)/ Smooth Selected Line/ Area Feature(s).

Kết quả của quá trình làm mịn cạnh qua từng bước được thể hiện trong bảng dưới:

| Ban đầu | Đơn giản hóa |
| :-----: | :----: |
| ![](/img/2020_12_06/Bang1a.png?raw=true "Ban đầu") | ![](/img/2020_12_06/Bang1b.png?raw=true "Kết quả đơn giản hóa") |

| Làm trơn cạnh | Kết của cuối cùng |
| :-----------: | :---------------: |
| ![](/img/2020_12_06/Bang1c.png?raw=true "Làm trơn cạnh") | ![](/img/2020_12_06/Bang1d.png?raw=true "Kết quả cuối cùng") |

Một kết quả khác tại những nơi có độ cong lớn.

| Ban đầu | Kết quả cuối cùng |
| :-----: | :---------------: |
| ![](/img/2020_12_06/Bang2a.png?raw=true "Ban đầu") | ![](/img/2020_12_06/Bang2b.png?raw=true "Kết quả cuối cùng") |

## Kết luận

Với sự phát triển của khoa học công nghệ, các phần mềm ngày càng trở nên ưu việt và mạnh mẽ. Phần mềm Global Mapper đã không chỉ cung cấp công cụ chiết xuất đối tượng mà còn trang bị cho người dùng rất nhiều công cụ bổ sung như: Đơn giản hóa, nội suy đỉnh, làm trơn cạnh... giúp tăng hiệu quả và chất lượng của quá trình chiết xuất. Có thể thấy rằng công đoạn số hóa, chiết xuất đối tượng vector từ dữ liệu raster phần nào đó đã được các phần mềm thực hiện tự động. Tuy vậy, các phần mềm vẫn chưa thể thay thế hoàn toàn được con người, chúng chỉ là các công cụ hỗ trợ và tự động ở một vài công đoạn.
