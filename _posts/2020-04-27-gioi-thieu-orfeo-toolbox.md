---
layout: post
title: Giới thiệu bộ công cụ Orfeo Toolbox
subtitle: Một thư viện nguồn mở xử lý ảnh viễn thám
tags: [Orfeo Toolbox, Remote sensing, Open Source]
categories: [Remote Sensing]
---

Orfeo ToolBox là một dự án nguồn mở dành cho viễn thám tiên tiến, bao gồm trình xem ảnh nhanh, các ứng dụng xử lý ảnh được truy cập thông qua giao diện của sổ dòng lệnh, Python, QGIS hay các API C++ mạnh mẽ. Bài viết này sẽ trình bày giới thiệu Orfeo ToolBox theo quan viễn thám và công nghệ phần mềm.

![Orfeo Toolbox](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_27/Hinh1.png?raw=true){: .center-block :}

## Mở đầu

Orfeo ToolBox (OTB) là một dự án nguồn mở cho xử lý hình ảnh vệ tinh. Được xây dựng từ cộng đồng địa không gian mã nguồn mở. OTB có khả năng xử lý ảnh quang học độ phân giải cao, ảnh đa phổ, ảnh siêu phổ và ảnh radar với dung lượng ảnh rất lớn, cỡ hàng Terabyte (~1000Gb). Một loạt các ứng dụng phổ biến, có sẵn như: nắn chỉnh hình học, trộn ảnh, phân loại có giám sát và không có giám sát, trích xuất đặc trưng, xử lý ảnh SAR…

OTB hỗ trợ đa nền tảng, trên cả ba nền tảng Windows, Linux và Mac OS. Từ những máy tính xách tay có cấu hình hạn chế đến những máy tính hiệu suất cao đều có thể cài đặt và chạy OTB. Tất cả các thuật toán OTB có thể truy cập từ Monteverdi, QGIS, Python, command-line hoặc C++ API. Trong đó, Monteverdi được cung cấp kèm với các ứng dụng của OTB, đây là một công cụ trực quan dễ sử dụng, được lập trình để khai thác tối đa sức mạnh phần cứng giúp tăng tốc độ kết xuất đồ họa cho ảnh độ phân giải cao. Với Monteverdi, người dùng có được cái nhìn trực quan từ những sản phẩm ảnh thô kích thước lớn và truy cập tất cả các ứng dụng của OTB trong hộp công cụ.

## Giới thiệu chung

Với hơn 15 năm phát triển, Orfeo ToolBox đã phát triển từ một bộ công cụ chỉ chuyên về độ phân giải cao trở thành bộ công cụ viễn thám đa mục đích, đa cảm biến… Nhờ kiến ​​trúc mô-đun, OTB cho khả năng tạo mẫu nhanh và bao trùm đầy đủ các thuật toán xử lý ảnh viễn thám. Từ tiền xử lý đến các phương pháp trích xuất đặc trưng nâng cao, cho phép người dùng đi từ dữ liệu thô đến các sản phẩm có giá trị. Những tính năng tiêu biểu của OTB như:

* Đọc, ghi, chuyển đổi, trích xuất dữ liệu viễn thám.
* Tiền xử lý dữ liệu, như: nắn ảnh trực giao, hiệu chỉnh bức xạ, trộn ảnh.
* Xử lý ảnh thông thường (biến đổi Fourier, biến đổi Wavelet…).
* Trích xuất đặc trưng (hình dạng, kết cấu, chỉ báo bức xạ…).
* Toán tử hình thái học.
* Phân đoạn ảnh, vector hóa kết quả phân đoạn (theo tỉ lệ).
* Phân loại ảnh có giám sát và không có giám sát.
* Phân tích ảnh dựa trên đối tượng.
* Xuất kết quả cho GIS và xuất bản in.

![Edge Detection](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_27/Hinh2.png?raw=true){: .center-block :}

### Kiến trúc phần mềm

Thư viện OTB có phần lõi dựa trên Insight Toolkit (ITK), ITK là một phần mềm nguồn mở trong xử lý ảnh y tế, gồm đăng ký ảnh và phân đoạn ảnh. Vì thế, giống với ITK phong cách thực thi hàm của OTB là kiểu lập trình tổng quát (C++ templates). Điều này không chỉ cho khả năng làm việc với nhiều định dạng ảnh khác nhau (khác về số kênh, loại điểm ảnh…) mà còn cho hiệu suất cao khi thực thi. Thêm nữa, các lỗi của phần mềm cũng được phát hiện ngay tại thời điểm biên dịch thay vì phải chạy phần mềm.

Các thuật toán của OTB bao phủ hầu hết các chức năng cần thiết cho xử lý ảnh viễn thám, từ tiền xử lý đơn giản đến phân tích hiệu suất cao. Mục tiêu mà OTB hướng tới là cung cấp giải pháp đầu-cuối phần mềm miễn phí để khai thác thông tin hình ảnh quan sát trái đất, dựa trên kiến trúc mô-đun và kỹ thuật ống dẫn (pipeline based) của lập trình tổng quát.

Kiến trúc phần mềm của OTB được thiết kế để nó không chỉ hoạt động trên máy tính cá nhân mà còn trên cả những máy tính hiệu năng cao, có quy mô xử lý hàng Terabyte. Điều này đạt được nhờ kiến ​​trúc phần mềm mô-đun, còn được gọi minh họa với tên là “chiếc bánh sandwich OTB”.

![Sandwich OTB](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_27/Hinh3.png?raw=true){: .center-block :}

Các API C++ của OTB sẽ đảm nhận thực thi kỹ thuật ống dẫn. Kỹ thuật này sẽ hỗ trợ xử lý đa luồng, truyền phát thông điệp. Do đó tất cả các ứng dụng và bộ lọc có thể xử lý ảnh với tối đa tài nguyên bộ nhớ và CPU đang có.

### Tái sử dụng mã từ các nguồn mở khác

Xử lý ảnh viễn thám thường cần đến sự kết hợp của các phương pháp chuyên môn hóa có trong các phần mềm chuyên dụng. Ý tưởng của OTB là cung cấp một giao diện chung kết hợp những thư viện phần mềm chuyên dụng này. Vì thế, OTB sử dụng GDAL để đọc các định dạng dữ liệu cả raster và vector; OSSIM cho các mô hình cảm biến hình học; libSVM, OpenCV và Shark cho học máy; và MuParser để phân tích các biểu thức toán học hiệu suất cao. Bảng 1 dưới đây là danh sách các thư viện nguồn mở được sử dụng trong dự án OTB.

| ITK | http://www.itk.org | libKML | github.com/google/libkml |
| GDAL | http://www.gdal.org | libSVM | http://www.csie.ntu.edu.tw/~cjlin |
| OSSIM | http://www.ossim.org | Mapnik | http://www.mapnik.org |
| libgeotiff | trac.osgeo.org/geotiff | MPI | http://www.open-_mpi.org |
| boost | http://www.boost.org | MuParser | http://www.muparser.sourceforge.net |
| openthreads | http://www.openscenegraph.org | MuParserX | muparserx.beltoforion.de |
| tinyXML | http://www.grinninglizard.com/tinyxml | OpenCV | opencv.org |
| 6S | 6s.ltdri.org | OPENGL | http://www.opengl.org |
| Curl | http://www.curl.haxx.se | Qt | http://www.qt.io/developers |
| FFTW | http://www.fftw.org | QWT | qwt.sourceforge.net |
| GLEW | glew.sourceforge.net | Shark | image.diku.dk/shark |
| GLFW | http://www.glfw.org | SiftFast | libsift.sourceforge.net |
| GLUT | http://www.opengl.org | SPTW | github.com/remicres/sptw.git |

### Cộng đồng phát triển và tài liệu

OTB ngay từ đầu được tạo ra bởi sự hợp tác và tham gia đóng góp của cộng đồng. Giống như nhiều dự án nguồn mở khác, có nhiều cách để tham gia mà không yêu cầu khả năng lập trình, như: viết tài liệu, báo cáo lỗi, yêu cầu các tính năng… đều rất có giá trị. Các tài liệu ví dụ luôn là một kênh quan trọng để bấy kì dự án phần mềm nguồn mở nào thu thập đóng góp từ cộng đồng. Tuy nhiên, các tài liệu ví dụ chỉ là một phần của vấn đề, các tài liệu chuyên môn khác cũng quan trọng không kém. OTB cung cấp nhiều loại tài liệu chuyên môn khác nhau, tùy thuộc vào nhu cầu của người dùng:

* Software Guide: Tài liệu hướng dẫn biên dịch OTB, mô tả các thư viện và các đoạn ví dụ code C++… Đây là tài liệu dành cho các lập trình viên.
* The OTB CookBook: Tài liệu hướng dẫn sử dụng và khai thác các ứng dụng của OTB, hướng dẫn sử dụng Monteverdi. Đây là tài liệu dành cho những người sử dụng.
* Tutorials: Tài liệu hướng dẫn chuyên đề dùng cho tập huấn, đào tạo để giải quyết một số bài toán thường gặp.

Đầu năm 2015, OTB đã thành lập một Ủy ban chỉ đạo dự án chính thức (PSC) để chỉ đạo định hướng và hợp tác. PSC là trung tâm liên lạc cho dự án và giải quyết các tranh chấp. Nó cũng thực hiện kêu gọi để thu hút nhiều nhà phát triển hơn, luôn bảo đảm tính mở cho OTB và là một công ty trung lập. PSC của OTB được lấy cảm hứng từ các dự án phần mềm địa không gian nguồn mở đang tồn tại, như: GRASS GIS, QGIS… Năm 2017, OTB đã chính thức trở thành một dự án thành phần của nền tảng OSGeo. Và hiện tại, OTB hàng ngày vẫn liên tục phát triển không ngừng nhờ những đóng góp của cộng đồng mã nguồn mở.

## Monteverdi

Orfeo ToolBox cung cấp Monteverdi là một công cụ để kết xuất đồ họa và xử lý hình ảnh được viết bằng Qt và OpenGL. Với Monteverdi, người dùng có được cái nhìn trực quan từ những sản phẩm ảnh thô kích thước lớn và truy cập tất cả các ứng dụng của OTB trong hộp công cụ. Một số chức năng chính của Monteverdi:

* Hỗ trợ hình học cảm biến (sensor geometry): Xem trực tiếp ảnh thô trong hình học cảm biến. Lấy mẫu lại được xử lý trên card đồ họa (GPU) nhờ ánh xạ kết cấu.
* Điều hướng nhanh và mượt mà trên các bộ dữ liệu lớn bằng GDAL Overviews Capabilities.
* Các công cụ kết xuất đồ họa cục bộ và toàn cục nhanh (ví dụ: tăng cường độ tương phản, hiệu ứng trong suốt, ánh xạ màu…) nhờ sử dụng sức mạnh của OpenGL như kết cấu dấu phẩy động và GLSL.
* Hiển thị đa hình ảnh với khả năng tự động đăng kí tham chiếu khi chúng không cùng hệ tọa độ, hay còn được gọi là khả năng “on-the-fly”

![Monteverdi](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_27/Hinh4.png?raw=true){: .center-block :}

## Các ứng dụng của OTB

Là bộ công cụ hỗ trợ đa nền tảng, OTB cung cấp sẵn hơn 90 ứng dụng. Các ứng dụng đều được viết bằng các thư viện C++, kết hợp thành kỹ thuật ống dẫn mang đến giao diện lập trình rõ ràng, dễ triển khai cho nhiều giải thuật viễn thám phức tạp. Ví dụ, ứng dụng OrthoRectification bao gồm một tập các đường ống như: Đọc dữ liệu, mô hình số độ cao bổ sung, tái chế mẫu, hệ tọa độ đầu ra… Mỗi đường ống thực hiện một chức năng với các tham số có thể điều chỉnh bởi người dùng.

Gần đây, OTB bổ sung một khung ứng dụng mới cho phân loại dựa trên pixel. Bộ ứng dụng mới này lọc cụ thể ra từng bước cần thiết cho quá trình đào tạo máy học, rất phù hợp với mô hình phân loại. Nói cách khác, chúng lấy mẫu từ ảnh tham chiếu sử dụng trong quá trình học, trích xuất các giá trị pixel và huấn luyện các máy phân loại có giám sát (Support Vector Machines, Random Forests…). Bằng cách này, quyền kiểm soát được trao cho người dùng thông qua từng bước khi xây dựng mô hình máy học.

Một đặc điểm quan trọng nữa trong thiết kế các ứng dụng của OTB là không phụ thuộc giao diện người dùng. Điều này cho phép chúng có thể được sử dụng ở nhiều giao diện khác nhau. Hiện tại, các ứng dụng của OTB có thể được truy cập thông qua các nguồn giao diện sau:

* Giao diện cửa sổ dòng lệnh.
* Giao diện đồ họa người dùng (GUI).
* Python để lập trình bậc cao.
* Monteverdi để xử lý tương tác và hiển thị ảnh.
* QGIS thông qua plugin Processing
* Zoo-Project thông qua Web Processing Service.

![QGIS Plugin](https://github.com/bachns/bachns.github.io/blob/master/img/2020_04_27/Hinh5.png?raw=true){: .center-block :}

Dưới đây là ví dụ sử dụng Python để gọi ứng dụng làm mịn ảnh sử dụng giải thuật Mean và giải thuật Gaussian:

```python
from sys import argv
import otbApplication
app = otbApplication.Registry.CreateApplication("Smoothing")
app.SetParameterString("in", argv[1])
for type in ['mean', 'gaussian']:
    app.SetParameterString("type", type)
    app.SetParameterString("out", argv[2] + type + ".tif")
    app.ExecuteAndWriteOutput()
```

Một ví dụ khác sử dụng API C++ để đọc và ghi ảnh:

```cpp
#include "otbImage.h"
#include "otbImageFileReader.h"
#include "otbImageFileWriter.h"
int main(int argc, char* argv[])
{
   using PixelType = unsigned short;
   const unsigned int Dimension = 2;
   using ImageType = otb::Image;
   using ReaderType = otb::ImageFileReader;
   using WriterType = otb::ImageFileWriter;
   ReaderType::Pointer reader = ReaderType::New();
   WriterType::Pointer writer = WriterType::New();
   reader->SetFileName(argv[1]);
   writer->SetFileName(argv[2]);
   writer->SetInput(reader->GetOutput());
   writer->Update();
   return 0;
}
```

## Kết luận

Suốt hơn 15 năm phát triển Orfeo ToolBox đã đi từ một thư viện đơn giản C++ trở thành bộ công cụ đa năng giải quyết hầu hết các nhu cầu xử lý ảnh viễn thám. Orfeo ToolBox hiện là một phần của một số dự án lớn đang hoạt động, và cũng là công cụ được chọn cho xử lý ảnh hàng ngày trong các phòng thí nghiệm. Orfeo ToolBox là một môi trường tuyệt vời để nghiên cứu, lập trình, thử nghiệm các thuật toán và quy trình xử lý ảnh. Khả năng dễ dàng tùy chỉnh, mở rộng linh hoạt và công khai chính là tài sản của Orfeo ToolBox.

Phần mềm liên tục phát triển để tăng cường hiệu suất, cung cấp thêm nhiều thuật toán mới tiên tiến và cho khả năng tương tác tốt nhất giữa chúng. Lộ trình của Orfeo ToolBox là hướng người dùng và PSC đảm bảo rằng tất cả mọi người tham gia sẽ đều nhận được sự quan tâm như nhau. Trong ngắn hạn và trung hạn, các phiên bản tiếp theo OTB sẽ tích hợp tốt hơn các thuật toán phân loại không giám sát, cũng như cải tiến tích hợp của các ứng dụng trong QGIS. Cuối cùng, dự án sẽ tiếp tục cố gắng quan tâm nhiều hơn nữa đến những người đóng góp. Với hơn mười bộ phận hoạt động từ xa đóng góp vào dự án, Orfeo ToolBox đang trên đà phát triển.