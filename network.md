# OSI
1. Tầng vật lý (physical)
* Cung cấp giao thức truyền thông từng bit từ máy này sang máy khác qua đường truyền vật lý
* Mã hóa tín hiệu bit và định thời giao truyền
* Mô hình vật lý của mạng(BUS/STAR/RING)
* **Các thiết bị: Reapeater, HUB, Bridge, tranceiver**

2. Tầng liên kết dữ liệu (datalink)

* Cung cấp giao thức truyền thông theo khung trong cùng 1 mạng
* Mô tả cấu trúc khung
* Định nghĩa địa chỉ trạm của 1 máy trên mạng
* Phương pháp truy cập mạng (VD ethernet dùng CSMA/CD, mạng token ring dùng token pssing)
* Kiểm soát lỗi, luồng dữ liệu(ví dụ dung mã dò CRC)
* Cung cấp các dịch vụ truyền thông
** Dịch vụ phi liên kết: 2 bên ko cần thiết lập kết nối. Nhanh, chi phí thấp nhưng ko tin cậy
** Dịch vụ hướng liên kết: bên phải thiết lập kết nối, chi phí cao do có kiểm soát lỗi và luồng, đảm bảo tin cậy, ko mất dữ liệu
** Dịch vuj phi liên kết có báo nhận
* **Các thiết bị: LAN card, switch, bridge**
