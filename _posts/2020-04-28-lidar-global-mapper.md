---
layout: post
title: Xử lý dữ liệu Lidar với Global Mapper
subtitle: Phân loại hiển thị và tạo mô hình số độ cao
tags: [Remote sensing, Lidar, Global Mapper]
categories: [Remote Sensing]
---

Với sự phát triển và mức độ phổ biến của dữ liệu LiDAR ngày càng tăng, nhiều công ty phần mềm trong ngành địa không gian đã phát triển và cung cấp các công cụ để xử lý và khai thác loại dữ liệu này. Bài viết này giới thiệu một số tính năng chính của module Lidar của phần mềm Global Mapper để tạo ra mô hình số địa hình và đường bình độ từ dữ liệu LiDAR.

## Tổng quan về LiDAR
LiDAR – Light Detection And Ranging, là công nghệ viễn thám chủ động, hoạt động dựa trên việc phát ra các tia sáng mạnh, tập trung và đo thời gian phản xạ trở lại cảm biến. Thông tin này được sử dụng để xác định các vùng, hoặc khoảng cách đến đối tượng. Bằng cách này LiDAR tương tự như radar, ngoại trừ việc sử dụng xung của ánh sáng laser, trong khi radar lại sử dụng sóng vô tuyến. Tập tọa độ điểm trong không gian ba chiều (ví dụ: x, y, z hoặc kinh, vĩ độ và độ cao) của các đối tượng đích được tính từ: khoảng thời gian khác nhau giữa xung laser phát ra và trả về; góc mà tại đó xung đã được phát ra; và vị trí tuyệt đối của cảm biến.

![lidar](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh1.png?raw=true "Máy bay thực hiện quét laser bề mặt địa hình"){: .center-block :}

LiDAR thường được thu thập từ các thiết bị bay hoặc máy bay, vì ưu điểm là có thể nhanh chóng thu thập được thông tin trên các khu vực rộng lớn. Bên cạnh đó, LiDAR cũng được thu thập từ các máy trạm cố định hoặc di động trên mặt đất. Kỹ thuật thu thập thông tin kiểu này có khả năng tạo ra độ chính xác cao và mật độ điểm đo dày đặc, từ đó thể hiện chi tiết không gian ba chiều của nhiều loại công trình như: đường sắt, cầu treo, các tòa nhà... Việc thu thập dữ liệu độ cao sử dụng LiDAR có nhiều ưu điểm hơn so với hầu hết các kỹ thuật khác. Bởi LiDAR cho phân giải cao (cỡ centimét), xác định được bề mặt địa hình ở ngay cả khi địa hình có rừng và thu thập dữ liệu cả trong điều kiện ban ngày và ban đêm.

Thiết bị LiDAR có thể nhanh chóng đo bề mặt trái đất, ở tốc độ lấy mẫu hơn 150 kilohertz (tức 150.000 xung/giây). Sản phẩm kết quả là một mạng lưới có mật độ dày đặc, được định vị chính xác cao về độ cao – được gọi là đám mây điểm. Các hệ thống LiDAR có thể được sử dụng ở các khu vực ven biển có nước tương đối trong suốt để đo độ cao đáy.

| ![point-cloud1](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh2a.png?raw=true "Đám mây điểm thu thập từ công nghệ LiDAR"){: .center-block :} | ![point-cloud2](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh2b.png?raw=true "Đám mây điểm thu thập từ công nghệ LiDAR"){: .center-block :} |

Khả năng xác định bề mặt địa hình ngay cả khi có cây cối che phủ luôn là một mục tiêu trong viễn thám khi thu thập dữ liệu độ cao từ phía trên bề mặt Trái Đất. Hầu hết các bộ dữ liệu có độ cao, được tạo ra bằng cách sử dụng các công nghệ viễn thám thường không thể xâm nhập qua thực vật, LiDAR cũng không ngoại lệ; tuy nhiên, thường có đủ tập “điểm riêng” trên mặt đất mà LiDAR có thể nhìn thấy thông qua các lỗ hổng hoặc vùng trống trong tán thực vật. Trong điều kiện rừng rậm hoặc các khu vực thực vật có độ che phủ dày đặc thường có ít lỗ hổng và do đó số lượng điểm thu thập nằm trên mặt đất thấp  (nghĩa là tất cả các điểm đều rơi trên cây cối và thảm thực vật giữa tán lá). Vì lý do này, thu thập dữ liệu trong khu vực cây ít lá, tán thực vật thưa là thuận lợi cho việc tính toán bề mặt địa hình ở các khu vực có rừng.

Dữ liệu LiDAR có hai định dạng *.las và *.laz, với định dạng *.laz đã được nén dữ liệu. Hiện nay có nhiều phần mềm cho phép đọc và khai thác định dạng dữ liệu này như: Global Mapper, ENVI, ArcGIS, SAGA-GIS...

## Global Mapper và module Lidar

Global Mapper là một phần mềm xử lý dữ liệu GIS của hãng Blue Marble Geographics, nó dễ dàng sử dụng và hỗ trợ hầu hết các định dạng dữ liệu không gian. Global Mapper rất phù hợp với vai trò là một công cụ xử lý, quản lý dữ liệu không gian độc lập và là một thành phần không thể tách rời của GIS, phần mềm này cần thiết cho bất cứ ai làm việc liên quan đến bản đồ hoặc dữ liệu không gian. Hãng Blue Marble Geographics cũng cung cấp một số module xử lý và các phần mở rộng tùy chọn để tích hợp cho phần mềm Global Mapper như: Lidar, OTF, COAST... Trong đó, module Lidar là module xử lý dữ liệu LiDAR, nó cung cấp nhiều công cụ xử lý dữ liệu tiên tiến, bao gồm phân loại đám mây điểm (Point Cloud) tự động, lọc tách tự động các tòa nhà, cây cối, đường dây điện, xem mặt cắt ngang hoặc trích xuất các đối tượng đường, vùng 3D. Để kiểm tra module này đã được tích hợp hay chưa, trong Global Mapper ta vào Help → Module/Extension License Manager...

![lidar-module](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh3.png?raw=true "Module Lidar trong phần mềm Global Mapper"){: .center-block :}

## Hiển thị dữ liệu LiDAR

Trong phần mềm Global Mapper, ta thực hiện mở dữ liệu định dạng LiDAR (*.las, *.laz) giống như các định dạng khác. Tuy nhiên, với dữ liệu LiDAR sẽ có một hội thoại Lidar Load Options hiện lên để tùy chọn những loại điểm nào sẽ được tải vào phần mềm. Để hiển thị được chi tiết, chúng ta sẽ chọn tất cả.

![load-options](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh4.png?raw=true "Tùy chọn lựa chọn loại điểm"){: .center-block :}

Không giống như các loại dữ liệu khác, việc hiển thị đám mây điểm LiDAR được cấu hình để biểu diễn theo một thành phần nào đó, có thể là độ cao, cường độ phản xạ hoặc loại phân loại... Mặc định, Global Mapper sẽ hiển thị các điểm dựa trên giá trị RGB hoặc màu sắc của chúng nếu có, nếu không các điểm sẽ được hiển thị theo độ cao (Color Lidar by RGB/Elev). Ta có thể thay đổi các thể hiện dữ liệu này tại Lidar Draw Modes ngay trên thanh Lidar Toolbar với một số dạng thể hiện chính sau:

![draw-modes](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh5.png?raw=true "Lidar Draw Modes"){: .center-block :}

Một số chế độ phổ biến khác như:
* Color Lidar by Intensity: Thể hiện cường độ phản xạ của bề mặt tại mỗi điểm, các bề mặt rắn có xu hướng phản xạ với cường độ cao hơn, ví dụ như các tòa nhà. Trong Global Mapper, các điểm tối hơn đại diện cho cường độ phản xạ kém của tín hiệu và các điểm sáng là các bề mặt rắn chắc có cường độ phản xạ tín hiệu mạnh.
* Color by Classification: Thể hiện sự phân loại của tập điểm, mỗi loại điểm sẽ được thể hiện bằng một màu khác nhau.
* Color by Return Number: Thể hiện số lượng tín hiệu phản xạ trở lại từ một tín hiệu phát đi. Cách thể hiện này rất hữu ích khi chúng ta muốn làm rõ thực vật. Vì đối với thực vật sẽ có số lượng tín hiệu phản xạ trả lại nhiều hơn một.

| Color Lidar by RGB/Elev | Color Lidar by Intensity |
| :---------------------: | :----------------------: |
| ![rgb-mode](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh6a.png?raw=true "Color Lidar by RGB/Elev") | ![intensity-mode](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh6b.png?raw=true "Color Lidar by Intensity") |
| Color by Classification | Color by Return Number |
| ![classfification-mode](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh6c.png?raw=true "Color by Classification") | ![returnnumber-modes](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh6d.png?raw=true "Color by Return Number") |

Hiển thị theo dữ liệu độ cao sẽ được Global Mapper thể hiện mặc định bằng màu sắc theo dải màu Atlas, từ màu xanh nước biển đến màu đỏ. Để quan sát tập đám mây điểm này bằng màu tự nhiên, chúng ta sẽ sử dụng thêm một ảnh tại cùng khu vực và tiến hành phủ màu cho chúng. Ta thực hiện mở hình ảnh tại cùng khu vực, tại Lidar Toolbar chọn Lidar Draw Mode là Color Lidar by RGB/Elev và chọn  Apply Color to Lidar Points. Ta có thể chọn chế độ hiển thị 3D để quan sát kết quả.

| Khi chưa phủ ảnh | Sau khi phủ ảnh |
| :--------------: | :-------------: |
| ![befor-apply-color](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh7a.png?raw=true "Khi chưa phủ ảnh") | ![after-apply-color](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh7b.png?raw=true "Sau khi phủ ảnh") |

## Thành lập mô hình số độ cao từ dữ liệu LiDAR

Dữ liệu thực nghiệm là một khu vực thuộc thủ đô Wellington của New Zealand, thu thập năm 2013. Có tạo độ địa lý Đông Bắc – Tây Nam là (41°03’00″S, 175°18’47″E) – (41°05’00″S, 175°21’34”). Dữ liệu này có đến 98,882,697 điểm rời rạc và được phân thành nhiều loại khác nhau. Tuy nhiên, để thành lập mô hình số độ cao (DEM), ta chỉ quan tâm đến các điểm nằm trên mặt đất và lọc bỏ đi các loại điểm khác. Ta sử dụng công cụ  Lidar Filter Setting để thực hiện công việc này, trong hội thoại Lidar Filter Setting chọn bỏ tất cả các loại điểm không cần thiết và chỉ giữ lại loại điểm Ground. Ngoài ra, cũng có thể thực hiện việc lọc bỏ này ngay khi mở dữ liệu.

![lidar-filter](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh8a.png?raw=true "Tùy chọn lọc")

Thực hiện tạo DEM bằng công cụ  Create Elevation Grid trên thanh Analysis Toolbar, hộp thoại Elevation Grid Creation Options sẽ xuất hiện để người sử dụng tùy chỉnh, với dữ liệu LiDAR hộp thoại này có bổ sung thêm hai tùy chọn là Grid Method và Grid Type để tùy chọn các phương pháp tạo DEM như: Triangulation, Minimum Value, Average Value and Maximum Value... Thông thường, phương pháp mặc định và cũng được sử dụng nhiều nhất là Triangulation – phương pháp lưới tam giác; với Vertical Units ta chọn đơn vị METERS. Thời gian tạo mô hình số độ cao bằng dữ liệu LiDAR phụ thuộc chủ yếu vào mức độ chi tiết của đám mây điểm. Sau khi hoàn thành, DEM mặc định cũng được thể hiện bằng dải màu Atlas, nếu muốn phủ màu tự nhiên ta phải lựa chọn ảnh phủ ở chế độ Texture Map.

![grid-creation](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh8b.png?raw=true "Tùy chọn tạo DEM")

Ta cũng có thể nội suy đường bình độ từ dữ liệu DEM, bằng việc sử dụng công cụ  Create Contours, nó phép người sử dụng tạo ra dữ liệu vector các đường bình độ, với nhiều tùy chọn như: khoảng cao đều, đường bình độ con, bình độ cái...

| Mô hình số độ cao | Đường bình độ |
| :---------------: | :-----------: |
| ![DEM](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh9a.png?raw=true "Mô hình số độ cao") | ![contour](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_28/Hinh9b.png?raw=true "Đường bình độ")

## Kết luận
LiDAR là nguồn dữ liệu không gian có độ chính xác cao, việc thu thập và xử lý được thực hiện một cách nhanh chóng. Các quy trình xử lý dữ liệu LiDAR thường ít phụ thuộc vào con người, không giống như các phương pháp đo đạc trực tiếp, đo ảnh, GPS... Vì vậy, LiDAR ngày càng được sử dụng rộng rãi và ứng dụng phổ biến. Với module Lidar có trên phần mềm Global Mapper, việc đọc và hiểu thị dữ liệu LiDAR đã không còn là trở ngại, module này cũng giải quyết trọn vẹn hầu hết các bài toán liên quan đến phân tích dữ liệu 3D, phục vụ công tác khảo sát, thiết kế, điều tra cơ bản.