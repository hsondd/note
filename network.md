# OSI
1. Tầng vật lý (physical)
* Cung cấp giao thức truyền thông từng bit từ máy này sang máy khác qua đường truyền vật lý
* Mã hóa tín hiệu bit và định thời giao truyền
* Mô hình vật lý của mạng(BUS/STAR/RING)
* **Các thiết bị: Reapeater, HUB, Bridge, Cable, NIC, tranceiver**

2. Tầng liên kết dữ liệu (datalink)

* Tiến hành chuyển đổi thông tin dưới dạng chuỗi bit ở mức mạng thành từng đoạn là khung tin (frame). Nhiệm vụ chính của mức này là khởi tạo, tổ chức các khung tin và xử lý thông tin liên quan tới khung tin
* Mô tả cấu trúc khung
* Định nghĩa địa chỉ trạm của 1 máy trên mạng
* Phương pháp truy cập mạng (VD ethernet dùng CSMA/CD, mạng token ring dùng token pssing)
* Kiểm soát lỗi, luồng dữ liệu(ví dụ dung mã dò CRC)
* Cung cấp các dịch vụ truyền thông
** Dịch vụ phi liên kết: 2 bên ko cần thiết lập kết nối. Nhanh, chi phí thấp nhưng ko tin cậy
** Dịch vụ hướng liên kết: bên phải thiết lập kết nối, chi phí cao do có kiểm soát lỗi và luồng, đảm bảo tin cậy, ko mất dữ liệu
** Dịch vuj phi liên kết có báo nhận
* **Các thiết bị: LAN card, switch, bridge**

3. Tầng mạng (network)
* Tầng mạng cung cấp giao thức truyền thông điểm - điểm theo gói giữa 2 máy bất kỳ trên liên mạng (các máy kết hợp với nhau thành 1 mạng lớn hơn)
* Định nghĩa địa chỉ mạng của 1 mạng vật lý. Gán địa chỉ cho các bản tin và chuyển đổi địa chỉ logic hay địa tên thành các địa chỉ vật lý
* 2 chức năng chính là tìm đường (routing) và chuyển chặng. Chỉ ra dữ liệu từ nguồn tới đíhc sẽ đi theo tuyến nào
* KIểm soát luồng dữ liệu, khắc phục sai sót, giúp loại trừ sự tắc nghẽn cũng như điều khiển luồng thông tin
* **Thiết bị: Router**

4. Tầng giao vận
* Tầng giao vận cung câps chức năng cần thiết giữa tầng mạng và tầng trên
* Tầng vậng chuyển là tầng cơ sở mà ở đó 1 máy tính của majgn chia sẻ thông tin vs một máy khác. Tầng vận chuyển đồng nhất mỗi trạm bằng 1 địa chỉ duy nhất và quản lý sư kết nối giữa các trạm
* Tầng vận chuyển chia gói tin lớn thành các gói tin nhỏ hơn trước khi gửi đi. Thông thường gói tin được đánh số và gửi đúng thứ tự

5. Tầng phiên
* Thiết lập các giao dịch giữa các trạm trên mạng
* Một giao dịch phải được thiết lập trước khi dữ liệu được truyền trên mạng
* Tầng phiên đảm bảo cho các giao dịch được thiết lập và duy trì đúng quy định
* Tầng phiên đảm bảo cung cấp cho người sử dụng các chức năng cần thiết để quản trị giao dịch trong ứng dụng của họ:
** Điều phối việc trao đổi dữ liệu giuwaxc các ứng dụng bằng cách thiết lập và giải phóng các phiên giao dịch
** Cung cấp các điểm đồng booj để kiểm sóat việc trao đổi dữ liệu
** Áp đặt các quy tắc cho csac tương tác giữa các ứng dụng của nguời sử dụng
** Cung cáp cơ chế lấy lượt trong quá trình trao đổi dữ liệu
6. Tầng trình diễn
* Cung cấp các giao thức biểu diễn và chuyển đổi dữ liệu giữa các máy trên mạng
** Nén dữ liệu-> dữ liệu nhỏ hơn->truyền nhanh hơn
** mã hóa dữ liệu->bảo mật thông tin
** Chuyển đổi dữ liệu: trên mạng có thể gồm nhiều máy tính có thể có cấu trúc khác nhau->có thể sử dụng các dạng dữ liệu khác nhau, phải chuyển đổi dữ liệu giữa các máy.

7. Tầng ứng dụng
* Cung cấp giao giện người sử dujgn và môi trường OSI
* Cung cấp giao thức cho các dịch vụ và ứng dụng của người dùng trên mạng

# TCP/IP
1. Lớp ứng dụng
* Người dùng thực hiện các chương trình ứng dụng truy cập đến các dịch vụ hiện hữu trên TCP/IP internet. Mỗi ứng dụng tương tác với một trong những protocol ở mức giao vận để gửi hoặc nhận dữ liệu. Chương trình sẽ gửi dữ liệu đi dưới dạng nào đó mà nó yêu cầu với lớp giao vận
2. Lớp giao vận cung cấp phuong tiện liên lạc từ một ứng dụng này đến một ứng dụng khác. Việc thông tin liên lạc đó thường được gọi là end-to-end. Mức chuyên trở có thể điều khiển luồng thông tin. NÓ cũng có thể cung cấp sự giao vận có độ tin cậy, đảm bảo dữ liệu đến nơi không có lỗi và theo đúng thứ tự.
3. Lớp internet: Nhiệm vụ cơ bản là xử lý việc liên lạc của các thiết bị trên mạng. Nó nhận 1 yêu cầu để gửi gói dữ liệu từ lớp cùng vs 1 định danh của máy mà gói dữ liệu phi được gửi đến. Nó đóng segment vào trong packet, điền vào phần đầu packet sau đó sử dụng các giao thức định tuyến để chuyển gói tin tới được đích của nó hoặc trạm kế tiếp. Tại nơi nhận sẽ kiểm tra tính hợp lệ của chúng và sử dụng tiếp các giao thức định tuyến để xử lý gói tin.
4. Lớp giao tiếp mạng có trách nhiệm nhận các IP datagram và truyền chúng trên một mạng nhất định. chia lớp này thành 2 lớp con là:
* lớp vật lý: làm việc vs các thiết bị vật lý, truyền dòng bit 0, 1 từ nới gửi đên nơi nhận
* lớp liên kết dữ liệu: tại đây dữ liệu được tổ chức thành các khung. phần đầu khung chứa địa chỉ và thoogn tin điều khiển, phần cuosi khung để phát hiện lỗi.

# Internet layer protocol
* IP: định dạng ip, định tuyến, điều khiển và xử lý lỗi
* Giao thức bản tin điều khiển liên mạng (ICMP)
* ARP và RARP

1. IP: IP được cấu tạo gồm 2 phần netword id và host id. cấu tao bởi 32 bit và chia làm 4 octet



# Các thiết bị mạng

1. Bộ lặp
Repeater thực hiện chức năng ở tằng vật lý để khuếch đại tin hiệu khi tín hiệu truyền đi xa. Repeater được sử dụng để kết nối các đoạn mạng lại với nhau. Repeater nhận tín hiệu từ 1 đoạn mạng, tái taioj và truyền đến đoạn mạng khác. Nhờ  có bộ lắp mà tín hiệu suy yếu do truyền qua cáp dài có thể trở lại dạng ban đầu và truyền đi xa hơn.
Bô lặp có thể tuyền gói dữ liệu từ phương tiện truyền dẫn này sang phương tiện truyền dẫn khác

2. Hub:
Là 1 thiết bị liên kết mạng được sử dụng rộng rãi. Là thành phần trung tâm trong mạng star. Có 3 loại hub:
* Hub chủ động: Chiếm phần lớn, tái tạo và truyền lại tín hiệu như repeater. Có nhiều cổng nên thỉnh thoảng còn dùng làm bộ lặp đa cổng. Hub chủ động đưa ra tín hiệu mạnh hơn do đó cho phép đoạn cáp dài hơn
* Hub thụ động: Hoạt động như các điểm kết nốt, chúng không tais tạo hoặc khuếch đại tín hiệu
* Hub lai: Các hub thích ứng với nhiều loại cáp khác nhau là hub lai

3. Bridge
Hoạt động ở tầng liên kết dữ liệu. Dùng để kết nối hai hay nhiều đoạn (segment) của mạng LAN khác nhau. Chức năng
* Mở rộng khoảng cách phân đoạn mạng, tắng số lượng máy tính trên mạng
* Lọc gói để gửi, hoặc gửi trả lại
* Phân chia mạng lớn thành 2 mạng nhỏ nhằm cô lập lưu lượng, tăng tốc độ mạng
* Giảm hiện tượng tắc nghecxn do số lượng máy tính vào mjang quá lớn
* Kết nối các phương tiện truyền dẫn khác nhau như cáp xoắn đôi, cáp quang
* Két nối các đoạn mạng sử dụng phương thức truy nhập đưuong truyền khác nhau, chẳng hạn CSMA/CD và chuyển thẻ bài


4. Bộ định tyến(router)
Chức năng của bộ định tuyến
* Chuyển đổi và định tuyến gói dữ liệu qua nhiều mạng dựa trên chỉ phân lớp của mạng, cung cấp các dịch vụ như bảo mật, quản lý lưu thông..
* Phân chia một mạng lớn thành nhiheefu majgn nhỏ và có thể kết nối nhiều đoạn mạng với nhau
* Lọc gói tin và cô lập lưu lượng mạng
* Ngăn chặn tình trạng quarng bá vì chúng ko chuyển tiếp các gói tin quảng bá, cải thieejun việc phân phát dữ liệu
