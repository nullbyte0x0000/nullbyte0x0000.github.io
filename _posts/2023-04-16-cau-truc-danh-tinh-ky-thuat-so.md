---
layout: post
title: Cấu trúc danh tính số (Digital ID - Part 3)
subtitle: Định danh kỹ thuật số liệu có hoàn toàn là "màu hồng"?
tags: [digital identity, covid-19]
categories: [Identity]
---


Các hệ thống ID trong lịch sử đã được các chính phủ sử dụng để cung cấp cho các cá nhân bằng chứng nhận dạng chính thức. Các hệ thống này thu thập các thuộc tính nhận dạng — chẳng hạn như tên, địa chỉ, ngày sinh và dấu vân tay — sau đó xác thực chúng để thiết lập danh tính của một cá nhân. Việc xác thực này được ủy nhiệm thông qua các thông tin xác thực như thẻ ID hoặc số định danh duy nhất mà các cá nhân có thể sử dụng làm bằng chứng nhận dạng khi tương tác với các bên tin tưởng như cơ quan chính phủ, tổ chức tài chính hoặc chủ lao động (Ngân hàng Thế giới 2019a).

Như đã trình bày trong chương trước, các quốc gia đang ngày càng triển khai các hệ thống ID kỹ thuật số, hệ thống này tận dụng công nghệ kỹ thuật số trong suốt vòng đời của danh tính để tăng khả năng tiếp cận và đưa vào các dịch vụ dựa trên danh tính; cải thiện thiết kế, vận hành hiệu quả và minh bạch các dịch vụ chính phủ; thúc đẩy tăng trưởng kinh tế mà chưa được khai thác trước đây.

Hệ thống ID kỹ thuật số đang được sử dụng một cách chiến lược để hiện đại hóa các hệ thống dựa trên giấy đang tồn tại. Chúng đặc biệt cần thiết cho các quốc gia chưa có bất kỳ hệ thống ID số nào hoặc chưa đủ tin cậy để vượt ra khỏi các mô hình truyền thống. Các hệ thống ID số này cho phép xác minh kỹ thuật số danh tính của người dân, đảm bảo rằng danh tính kỹ thuật số của họ là tương ứng với danh tính thực tế của họ — khớp với số nhận dạng duy nhất — khi thực hiện một loạt các giao dịch trực tiếp, trực tuyến và từ xa (Sự kiện ID4D của Ngân hàng Thế giới năm 2021).

Một hệ thống ID kỹ thuật số thành công phải có định hướng chiến lược được phát triển đồng hành bởi cả chính phủ và các bên công-tư có liên quan. Tầm nhìn chung này phải hướng dẫn các quyết định liên quan đến cấu trúc và triển khai hệ thống ID kỹ thuật số, cũng bao gồm cả các quyết định chính như mục đích, trường hợp sử dụng và thiết kế. Các quyết định ở những khía cạnh này là chiến lược và đặc biệt quan trọng để đảm bảo rằng thiết kế của hệ thống ID kỹ thuật số sẽ phù hợp với cả lý thuyết và thực tiễn.

# Mục đích của hệ thống nhận dạng


Tất cả các hệ thống nhận dạng đều có mục đích cơ sở hoặc mục đích chức năng (GSMA 2018). Các hệ thống nền tảng được các chính phủ thiết lập và vận hành để cung cấp danh tính cho người dân nói chung như một hàng hóa công cộng có mục đích chung và có thể truy cập được bởi tất cả mọi người, sau đó danh tính sẽ được xác minh thông qua các phương tiện như thẻ căn cước. Với các thông tin xác thực cơ bản này, việc tạo và sử dụng thường được cung cấp kèm theo luật, và được sử dụng trong nhiều loại giao dịch thương mại và chính phủ. Ngược lại, các hệ thống có mục đích chức năng sẽ được xây dựng và vận hành bởi chính phủ hoặc các tổ chức tư nhân để cung cấp danh tính cho một nhóm nhỏ dân số để cung cấp những dịch vụ cụ thể (Ngân hàng Thế giới 2019a).

Một người có thể có nhiều loại ID chức năng cho các trường hợp sử dụng khác nhau, chẳng hạn như xác nhận đủ điều kiện để lái xe ô tô hoặc cung cấp bằng chứng bảo hiểm. Mặc dù trong một số trường hợp, những thứ này có thể được các bên khác tận dụng như một hàng hóa công cộng cho các mục đích xác thực không được hình dung ban đầu, nhưng chúng thường được liên kết về mặt pháp lý hoặc hoạt động với một trường hợp cụ thể và có thể không phục vụ cho việc xác định mục đích chung trong mọi trường hợp. Các hệ thống cơ sở và chức năng cho phép các chính phủ theo đuổi các trường hợp sử dụng khác nhau để phục vụ các bộ phận dân cư khác nhau (GSMA 2018; Ngân hàng Thế giới 2019a)

![image](https://res.craft.do/user/full/f54ccbe8-6757-2937-86c8-2ad3bf690d94/2413D810-4C59-4C9A-A022-2781689D4F4E_2/YmadCBEQGtNyG4yRKBzQb7Ekd9VFhSUqsB8C5bRTXT8z/Screen%20Shot%202022-09-05%20at%2008.34.31.png)
> **RENIEC của Peru đặt ra tiêu chuẩn cho các hệ thống nền tảng**

> ~~Cơ quan Đăng ký định danh và Hộ tịch Quốc gia (RENIEC) là một cơ quan hiến pháp tự trị duy trì cơ quan đăng ký dân sự tập trung của tất cả công dân Peru và phân phối Tài liệu Nhận dạng Quốc gia (DNI), là chứng minh thư cá nhân duy nhất được chính phủ công nhận. Thẻ được sử dụng cho các mục đích dân sự, thương mại, hành chính và tư pháp như bỏ phiếu, truy cập các dịch vụ của Chính phủ điện tử và tham gia vào các dịch vụ tư nhân như ngân hàng và chăm sóc sức khỏe.~~

> ~~Những ID này theo truyền thống dựa trên giấy. Tuy nhiên, hệ thống quốc gia hiện tại này đang đóng vai trò là cơ sở cho thẻ vật lý có chip mật mã (DNI-e) cung cấp chữ ký điện tử, thẻ thông minh và chức năng xác thực sinh trắc học (Reuben và Palacios 2018).~~

> **Giấy phép lái xe do nhà nước cấp của Hoa Kỳ chỉ đạo việc sử dụng rộng rãi các hệ thống chức năng.** 

> Các tiểu bang riêng lẻ của Hoa Kỳ cấp giấy phép lái xe được sử dụng để xác minh tính đủ điều kiện lái xe ô tô của một cá nhân. Những ID này, dựa trên giấy nhưng chuyển dần sang các phiên bản kỹ thuật số, được phân phối cho các cá nhân sau khi họ vượt qua các yêu cầu như bài kiểm tra lái xe. Chúng bao gồm hình ảnh khuôn mặt cũng như dữ liệu sinh trắc học (tức là chiều cao) và nhân khẩu học (tức là tuổi).

> Mặc dù mục đích chính của những ID này là để điều chỉnh việc sử dụng ô tô, chúng cũng được sử dụng để xác minh danh tính chung; ví dụ: người Mỹ sử dụng giấy phép lái xe để chứng minh danh tính của họ khi đi du lịch trong nước và tiến hành xác minh độ tuổi khi mua hàng có giới hạn độ tuổi. Việc sử dụng các ID chức năng làm bằng chứng nhận dạng trên thực tế cho các mục đích sử dụng ngoài phạm vi dự định của chúng là phổ biến ở các quốc gia thiếu hệ thống ID cơ bản (Ngân hàng Thế giới 2019a).


Các hệ thống ID cơ bản và chức năng cùng tạo nên hệ sinh thái rộng lớn cho một quốc gia hoặc khu vực, nơi các hệ thống khác nhau có thể hoạt động riêng biệt hoặc cùng nhau trong nhiều trường hợp sử dụng khác nhau. Ví dụ: DNI hoặc DNI-e của Peru cung cấp cho công dân bằng chứng nhận dạng chính thức có thể được sử dụng trong tất cả các tình huống yêu cầu xác minh danh tính và xác thực; sau đó chính phủ của quốc gia đó sử dụng DNI này để cung cấp các ID chức năng bổ sung (chẳng hạn như giấy phép lái xe) để cung cấp các dịch vụ bổ sung hoặc “ngách” không áp dụng cho toàn bộ dân số. Ở các quốc gia khác, một hoặc một tập hợp các ID chức năng — chẳng hạn như giấy phép lái xe, đăng ký khai sinh hoặc mã số thuế — có thể được chấp nhận rộng rãi trong toàn bộ hệ sinh thái định danh khi không có một ID nền tảng duy nhất.

Do đó, lựa chọn chiến lược đầu tiên nằm ở việc theo đổi hệ thống ID cơ bản hay chức năng. Cuối cùng, một hệ thống nền tảng đảm bảo rằng chính phủ đang ban hành danh tính pháp lý có thể dùng làm cơ sở mạnh mẽ cho các dịch vụ công hoặc tư bổ sung.
> **Hà Lan thiết lập tầm nhìn chiến lược cho cơ sở hạ tầng nền tảng định danh kỹ thuật số**

> Vào đầu năm 2021, Bộ trưởng Nội vụ và Quan hệ Vương quốc Hà Lan, Raymond Knops, đã công bố tầm nhìn của mình đối với chính phủ để tạo điều kiện cho cơ sở hạ tầng định danh kỹ thuật số quốc gia hợp lý và đáng tin cậy, để cả công dân và tổ chức sử dụng. Đất nước hiện có hai hệ thống nhận dạng kỹ thuật số quốc gia tự nguyện khác nhau: DigiD (nhận dạng kỹ thuật số công cộng để công dân tương tác với chính phủ) và eHerkenning (mạng công-tư kết hợp của các tổ chức để cung cấp dịch vụ xác thực).

> Mặc dù tầm nhìn không thiết lập lịch trình thực hiện, nhưng nó tuyên bố rằng tất cả công dân Hà Lan sẽ được chỉ định một danh tính trên nền tảng kỹ thuật số duy nhất (DFI) có chứa dữ liệu nhận dạng đã được xác minh. DFI sẽ được sử dụng để tạo các ID chức năng khác nhau như hộ chiếu và giấy phép lái xe, cũng như tạo điều kiện cho công dân tương tác với các tổ chức công và tư ở cả Hà Lan và trên toàn Liên minh châu Âu. Tầm nhìn chiến lược của DFI là tăng tốc độ đổi mới, giảm rủi ro về quyền riêng tư và bảo mật, trao quyền tự quyết cho các cá nhân đối với dữ liệu cá nhân của họ và cung cấp quyền tự do trong việc lựa chọn các giải pháp thị trường nhận dạng kỹ thuật số


# Thiết kế hệ thống nhận dạng


Việc triển khai cả hai hệ thống ID dựa trên giấy và kỹ thuật số đòi hỏi phải đưa ra một số lựa chọn thiết kế và kỹ thuật xuyên suốt các giai đoạn hình thành, phát triển và hoạt động, điều quan trọng là giúp hệ thống ID đạt được mục đích dự kiến ​​của chúng.

Ví dụ: quản trị viên thiết lập hệ thống ID phải xác định cách thiết lập bằng chứng xác thực danh tính và những giao thức nào cần thiết để xác nhận một người thực sự tương ứng với ID của họ. Tương tự như vậy, họ cũng phải xác định thông tin nào sẽ được thu thập để xác minh danh tính; các tùy chọn khả thi bao gồm thông tin vốn có như thông số sinh trắc học, thông tin tích lũy như sở thích cá nhân hoặc thông tin được chỉ định như số định danh quốc gia.

![image](https://res.craft.do/user/full/f54ccbe8-6757-2937-86c8-2ad3bf690d94/BD8CAD03-7EBC-47E7-B839-7CF75C0D1313_2/3cpbf2MQZihJ6R3Yplf4Zzqg2AUiEMK8vUjhc6iqkIoz/Screen%20Shot%202022-09-05%20at%2009.29.56.png)

Lựa chọn các loại dữ liệu gắn liền với định danh kỹ thuật số là một quyết định chiến lược thứ hai. Một số thuộc tính cho phép các giao dịch cụ thể tốt hơn các thuộc tính khác và các trường hợp sử dụng của hệ thống ảnh hưởng đến việc lựa chọn các thuộc tính (Diễn đàn Kinh tế Thế giới 2016). Bất kể thế nào, các hệ thống nên hướng tới việc giảm thiểu việc thu thập và lưu trữ thuộc tính đến mức tối thiểu cần thiết để xác thực danh tính. Và trên toàn cầu, ngày càng có nhiều quốc gia lựa chọn sinh trắc học để xác thực danh tính cá nhân.

![image](https://res.craft.do/user/full/f54ccbe8-6757-2937-86c8-2ad3bf690d94/DDDD1855-8F7F-4D71-BEFD-F71D6CE9C435_2/VKzcTcJsTqNG9oqH3kIqOwwOu5zmWZFvy76mFAE5gEoz/Screen%20Shot%202022-09-05%20at%2009.36.40.png)
> **Sự phát triển của sinh trắc học tiên tiến**

> Khi các quốc gia cân nhắc các yếu tố thiết kế khác nhau, một lựa chọn ngày càng phổ biến là sử dụng sinh trắc học để xác thực danh tính. Việc sử dụng các thông số này, bao gồm dấu vân tay, quét mống mắt hoặc hình dạng khuôn mặt, mang lại một số lợi ích.

> 1. Chúng là bản chất của từng cá nhân và duy nhất - luôn là thứ quan trọng, nhất là ở các quốc gia có dân số lớn.
> 2. Chúng cung cấp nhiều thuộc tính thay thế, điều quan trọng là bao gồm các cá nhân có thể không có các loại thuộc tính sinh trắc học cụ thể (tức là dấu vân tay, mống mắt, dấu ấn trên khuôn mặt).
> 3. Chúng có chi phí thấp hơn và dễ dàng tích hợp vào cuộc sống hàng ngày, đặc biệt là với sự thâm nhập ngày càng tăng của thiết bị di động, điều này rất quan trọng để tăng tính khả thi và việc sử dụng hệ thống ID kỹ thuật số.
> 4. Chúng không yêu cầu các cá nhân sử dụng hoặc mang theo các thiết bị, thông tin xác thực hoặc token cụ thể có thể bị mất, điều này đặc biệt quan trọng ở các quốc gia có dân số kém giàu có hoặc biến động.
> 5. Chúng không yêu cầu chính phủ triển khai hoặc duy trì các hệ thống phần cứng chuyên dụng và cụ thể, điều này rất quan trọng để tăng tính tiện lợi và tuổi thọ của hệ thống ID kỹ thuật số và tránh bị nhà cung cấp “look-in” (chặn, ngừng cung cấp).
> Tuy nhiên, việc sử dụng sinh trắc học có thể có những hạn chế. Dữ liệu sinh trắc học đã làm tăng rủi ro về quyền riêng tư do tính chất nhạy cảm của nó và mặc dù an toàn hơn một số công nghệ nhận dạng, nhưng dữ liệu sinh trắc học được lưu trữ có thể cần thêm lan can bảo vệ an ninh mạng. Ngoài ra, việc sử dụng thiết bị đặc biệt có thể được yêu cầu để thu thập hoặc đo lường một số thuộc tính sinh trắc học, điều này có thể tạo ra những thách thức về hậu cần và hòa nhập để cung cấp dịch vụ cho tất cả các bộ phận dân cư như những người ở nông thôn hoặc người khuyết tật.

> Hơn nữa, một số cộng đồng có thể không tin tưởng vào việc thu thập dữ liệu sinh trắc học do nhận thấy tiềm năng giám sát hoặc các kỳ thị xã hội hoặc văn hóa. Giống như các lựa chọn thiết kế khác, các chính phủ nên đánh giá tất cả các thuộc tính để xác thực danh tính (bao gồm cả sinh trắc học) và chọn một thuộc tính phù hợp nhất với mục đích của hệ thống cũng như bối cảnh văn hóa và xã hội của họ.


Khi các quốc gia đối mặt với những lựa chọn kỹ thuật và thiết kế riêng lẻ này, họ cũng có thể đánh giá chúng bằng các phương pháp tiếp cận hướng công cụ hay hướng cơ sở hạ tầng. Các phương pháp tiếp cận hướng công cụ được định hướng mạnh theo trường hợp sử dụng cụ thể và phụ thuộc vào các tiêu chuẩn độc quyền hoặc công nghệ độc quyền, trong khi các phương pháp cơ sở hạ tầng tương thích với nhiều trường hợp sử dụng, tận dụng các tiêu chuẩn chung và công nghệ nguồn mở (USAID 2017).

##### Table


Được thiết kế và thực hiện với nhiều bên liên quan 

Có thể sử dụng lại cho các trường hợp sử dụng khác với tài nguyên bổ sung tối thiểu

Sử dụng các nền tảng mã nguồn mở và các tiêu chuẩn mở

Được xây dựng với mục tiêu dài hạn

Mục đích giới hạn trong một sáng kiến duy nhất ​​hoặc trường hợp sử dụng danh tính cụ thể

**Tiếp cận hướng cơ sở hạ tầng**

**Tiếp cận hướng công cụ**

Phụ thuộc vào phần mềm, phần cứng và tiêu chuẩn dữ liệu tùy chỉnh

Thiết kế, thực hiện và phân kỳ theo khung thời gian của dự án

##### Table


(Nam Á)

Hệ thống ID chức năng để theo dõi những người thụ hưởng các dự án dinh dưỡng.

Dựa trên phần mềm độc quyền và mã địa lý không chuẩn.

**ID quốc gia**

(Nigeria)

Nền tảng hệ thống ID quốc gia

Dựa trên các hệ thống độc quyền từ các nhà cung cấp tư nhân hạn chế tái sử dụng

Hệ thống hồ sơ sức khỏe sinh trắc học chức năng để theo dõi sức khỏe bà mẹ

Sử dụng các tiêu chuẩn mở cho nhiều nền tảng kỹ thuật số

Cơ sở dữ liệu ID quốc gia sinh trắc học cơ bản

Sử dụng dữ liệu chung và các tiêu chuẩn kỹ thuật

Sử dụng điện thoại di động và các nhóm tuyển sinh chỉ dành cho phụ nữ để bao gồm những nhóm dân cư khó tiếp cận

**NADRA**

**Simprints**

USAID

Pakistan

**Integrated Nutrition**

Các hệ thống cơ sở và chức năng có thể kết hợp các yếu tố của cả phương pháp tiếp cận công cụ và cơ sở hạ tầng. Tuy nhiên, các phương pháp tiếp cận nằm trong khía cạnh cơ sở hạ tầng có xu hướng đóng góp nhiều hơn cho các quốc gia đang tìm cách tạo ra một hệ thống ID gắn kết và bền vững. Trong khi các phương pháp tiếp cận công cụ phải được đặt vào bối cảnh thích hợp, có thể không hiệu quả, và nó bỏ qua các khía cạnh xã hội, chính trị, kinh tế cần thiết cho sự thành công của hệ thống (USAID 2017).

Các phương pháp tiếp cận công cụ đối với hệ thống ID kỹ thuật số có thể tạo ra những thách thức chẳng hạn như các cơ quan chính phủ có các hệ thống được bảo mật độc quyền và thiếu một nền tảng tin cậy chung cho các bên liên quan cả công cộng và riêng tư trong hệ sinh thái (Sự kiện ID4D của Ngân hàng Thế giới năm 2021). Những thách thức này dẫn đến lãng phí ở quy mô lớn và chi phí cơ hội đáng kể.
> Những cạm bẫy cần tránh khi thiết kế hệ thống ID hướng công nghệ

> • Loại trừ các cộng đồng dễ bị tổn thương như các nhóm dân cư nông thôn, thu nhập thấp, bị thiệt thòi hoặc tàn tật có thể không được tiếp cận với cơ sở hạ tầng đắt tiền hoặc có năng lực thấp hơn để tham gia với các hệ thống công nghệ cao

> • “Look-in” và phụ thuộc vào nhà cung cấp có thể làm giảm tính linh hoạt của hệ thống để phát triển, ngăn chặn việc tái sử dụng và phát triển hệ thống, đồng thời tạo ra chi phí lớn hơn để chuyển đổi giữa các nhà cung cấp hoặc công nghệ độc quyền

> • Bảo trì và nâng cấp hệ thống thường xuyên và cần thiết để giữ cho hệ thống hoạt động và an toàn

> • Sự phân mảnh của hệ thống ID trong cùng một hệ sinh thái nhận dạng do khả năng không tương thích về công nghệ hoặc tiêu chuẩn

> Các chính phủ nên triển khai các hệ thống ID kỹ thuật số không phụ thuộc vào các loại công nghệ cụ thể, được sửa đổi để phù hợp với điều kiện và bối cảnh địa phương, đồng thời tuân thủ các thực tiễn có thể tương tác và các tiêu chuẩn mở về nhận dạng. Những điều kiện này là cần thiết để tạo ra các hệ thống ID động và gắn kết có thể đáp ứng với các công nghệ phát triển nhanh chóng, cũng như ngăn chặn sự phân mảnh thông tin giữa các hệ thống ID khác nhau trong môi trường nhận dạng.


#### Hoạt động của hệ sinh thái nhận dạng kỹ thuật số


Khi các quốc gia triển khai các hệ thống ID kỹ thuật số mới và số hóa các hệ thống giấy tờ kế thừa, hệ sinh thái nhận dạng mà họ vận hành bên trong trở nên phức tạp hơn. Hệ thống ID kỹ thuật số kết hợp nhiều tác nhân hơn với trách nhiệm, quyền lợi và ưu tiên đa dạng hơn so với hệ thống dựa trên giấy tờ truyền thống (Ngân hàng Thế giới 2016).

Sự phức tạp này đã tạo ra các mô hình mới mà các quốc gia, khu vực và các tổ chức tư nhân sử dụng để thiết lập, vận hành và quản lý các hệ thống ID kỹ thuật số. Một số cân nhắc có thể ảnh hưởng đến cách tiếp cận triển khai đã chọn, chẳng hạn như các hệ thống và tác nhân đã có trong hệ sinh thái ID hiện có và nhu cầu của các bên liên quan cụ thể ở quốc gia, khu vực hoặc tổ chức thực hiện. Nó cũng có thể để triển khai các mô hình kết hợp kết hợp các yếu tố của hai hoặc nhiều mô hình (McKinsey Global Institute 2019).

##### Table


Ưu điểm

Nhược điểm

Được sử dụng ở đâu?

Vai trò của khu vực tư

Vai trò của khu vực công

Làm sao để sử dụng tốt nhất

Là cái gì

Mô hình hệ sinh thái tập trung

Một tổ chức công cung cấp hệ thống ID kỹ thuật số tập trung do chính phủ điều hành (Ngân hàng Thế giới 2016), nơi tổ chức này vận hành và quản lý một kho lưu trữ trung tâm danh tính của từng cá nhân. Tổ chức công hoạt động như một nhà cung cấp danh tính bằng cách xác thực danh tính của các cá nhân và cung cấp các thuộc tính cho các bên phụ thuộc.

Hệ thống cung cấp một nguồn sự thật duy nhất để có cái nhìn đầy đủ và chuẩn hóa về danh tính của các cá nhân, cũng như hợp lý hóa quyền truy cập vào các dịch vụ trực tuyến quan trọng của chính phủ.

Mô hình này do chính phủ định hướng, trong đó khu vực công đóng vai trò vừa là cơ quan quản lý hệ sinh thái nhận dạng vừa là nhà cung cấp danh tính bằng cách thiết lập một kho lưu trữ quốc gia tập trung.

Mô hình này không tạo ra vai trò lớn cho khu vực tư nhân trong việc thu thập, xác minh hoặc xác thực danh tính. Tuy nhiên, các công ty có thể hỗ trợ triển khai kỹ thuật hoặc triển khai hệ thống và kho lưu trữ nhận dạng tập trung (tức là cung cấp phần mềm hoặc phần cứng).

Aadhaar (Ấn Độ), NADRA (Pakistan), NIDA (Rwanda), PhilID (Philippines), RENAPER (Argentina), RENIEC (Peru)

• Có thể không tận dụng hoàn toàn kinh nghiệm của các bên thứ ba (tức là các tổ chức tài chính) trong việc quản lý danh tính kỹ thuật số• Yêu cầu sự tham gia mạnh mẽ từ hệ sinh thái cơ quan chính phủ• Tập trung rủi ro và nợ phải trả, tạo ra một điểm thất bại duy nhất

• Cung cấp danh tính pháp lý• Hợp lý hóa việc cung cấp dịch vụ• Thúc đẩy sự hiện diện của chính phủ trên toàn lãnh thổ• Tận dụng các sáng kiến ​​hiện có của chính phủ• Cho phép chính phủ kiểm soát trực tiếp toàn bộ hệ thống• Tạo trải nghiệm và dịch vụ ID nhất quán

_Hết phần 3_
