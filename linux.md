---------------------------------------FILE----------------------------------
- Kernel buffer: Khi read/write file, thay vi ghi truc tiep vao file trong o cung(ton time), se copy vao mot buffer trong kernel. Sau do co kernel thread thu thap va ghi buffer do vao o cung, roi lam sach buffer de tai su dung.
+ file bao gồm 2 phần: dâta và metadata(owner,quyền truy cập file, kích thước, số hardlink đến file,...)
# Có 2 cách đồng bộ thủ công dữ liệu giữa kernel buffer và ổ cứng:
1Synchronized I/O data integrity chỉ yêu cầu nội dung data của file được đồng bộ giữa tiến trình và file
2Synchronized I/O file integrity yêu cầu tất cả nội dung của file bao gồm data và metadata phải được đồng bộ giữa tiến trình gọi và ổ cứng
	`sync(), fsync(), fdatasync(): đồng bộ file ở kernel buffer xuông ổ cứng
	`select(): theo dõi nhiều mô tả file, trả về fd của file sẵn sàng
	`poll() tuong tu select, khac cach truyen mo ta file. poll co hieu nang cao hon. Giả sử nếu bạn chỉ muốn theo dõi mô tả file fd là 1000 			thì kernel vẫn phải quét 1001 mô tả file (từ 0 đến 1000) để xem mô tả file nào được theo dõi (1001 poll routine). Với poll() 			thì khác, bạn chỉ cần truyền cấu trúc với chính xác mô tả file fd 1000 kèm với sự kiện quan tâm tương ứng xuống kernel, do vậy 			kernel sẽ gọi 1 poll routine để kiểm tra duy nhất mô tả file 1000.


--------------------------------------PROCESS----------------------------------
- Chương trình (program) là một file chạy được (executable) chứa các chỉ lệnh (instruction) được viết để thực thi một công việc nào đó trên máy tính
+tiến trình (process) là một phiên bản đang chạy của một chương trình. Tiến trình được gọi là thực thể chủ động (active entity) để phân biệt với chương trình, vì nó sẽ được copy từ ổ cứng sang bộ nhớ RAM để chạy trên hệ điều hành máy tính 
# Cấu trúc bộ nhớ của tiến trình:
					Heap
				
					Stack

					Uninitialized data segment(bss)

					Initialized data

					Text code

-Text code: Chứa các chỉ lệnh ngôn ngữ máy (machine-language instruction) của chương trình mà tiến trình đó chạy. Text segment chính là các chỉ lệnh được biên dịch từ source code của lập trình viên cho chương trình đó. Nội dung của phân vùng này không thay đổi trong suốt quá trình process tồn tại nên được kernel thiết lập chế độ read-only để bảo vệ khỏi sự truy cập vô tình hay cố ý của người dùng. Như đã nói ở trên, vì nhiều tiến trình có thể chạy một chương trình nên text segment cũng được thiết lập sharable để các tiến trình có thể sử dụng chung để tiết kiệm tài nguyên.
+Initialized data segment(bss): Vùng này chứa các biến toàn cục (global) và biến static mà đã được khởi tạo từ code của chương trình. Giá trị của các biến này được đọc từ các file thực thi khi chương trình được tải vào RAM
#Uninitialized data segment: Còn được gọi là vùng bss segment. Segment này chứa các biến toàn cục và static mà 'chưa' được khởi tạo từ source code. Ví dụ khi lập trình viên khai báo biến tĩnh “static var;”, biến var sẽ được chứa ở vùng này và được khởi tạo giá trị 0, khi một chương trình được lưu trữ vào ổ cứng, không cần thiết phải cấp phát tài nguyên cho uninitialized data segment; thay vào đó chương trình chỉ cần nhớ vị trí và kích thước biến được yêu cầu cho vùng này, các biến này sẽ được cấp phát run time khi chương trình được tải vào RAM.
-Stack segment: Chứa stack frame của tiến trình.y. Tạm thời hiểu là khi 1 hàm được gọi, một stack frame sẽ được cấp phát cho hàm đó (các biến được khai báo trong hàm, các đối số truyền vào hay giá trị return) và sẽ bị thu hồi khi hàm đó kết thúc. Vì vậy, stack segment có thể giãn ra hoặc co lại khi tiến trình cấp phát/thu hồi các stack frame.
 Khi một hàm được gọi, một stack frame của hàm đó được cấp phát và push vào stack; và stack frame này sẽ được thu hồi khi hàm đó return.
Mỗi stack frame chứa các thông tin sau:
1.Đối số (argument) của hàm và các biến cục bộ (local variable): Các biến này còn được gọi là biến tự động (automatic variable) vì chúng sẽ tự động được tạo ra khi hàm được gọi và tự động biến mất khi hàm đó return (vì stack frame cũng biến mất).
2.Call linkage information: Các hàm khi chạy sẽ sử dụng các thanh ghi của CPU, ví dụ như thanh ghi program counter (pc) lưu chỉ lệnh tiếp theo được thực thi. Mỗi lần một hàm (ví dụ hàm X) gọi hàm khác (ví dụ hàm Y), giá trị các thanh ghi mà hàm X đang dùng sẽ được lưu vào stack frame của hàm Y; và sau khi hàm Y return, các giá trị thanh ghi này sẽ được phục hồi cho hàm X tiếp tục chạy.
+Heap segment: Là vùng bộ nhớ lưu các biến được cấp phát động (dynamic allocate) tại thời điểm run time. Tương tự như stack segment, heap segment cũng có thể giãn ra hoặc co vào khi một biến được cấp phát hoặc free.
#Typically two processes communicate with each other on a single system through one of the following inter process communication techniques.

Pipes
Message queues
Shared memory

	`fork(): Tạo ra 1 bản sao cho bộ nhớ hiện tại của process
	`exec(): Tạo process mới tại điểm bắt đầu tiến trình
	`wait(): Block process cho đến khi 1 trong các process con kết thúc
	`system(): Cho thực hiện một command line trong C





--------------------------------------------------------------------THREAD--------------------------------------------------------------------------------
- Thread là một cơ chế cho phép một ứng dụng thực thi đồng thời nhiều công việc (multi-task)
+ Thread là một thành phần của tiến trình, một tiến trình có thể chứa một hoặc nhiều thread
#Các thread trong tiến trình chia sẻ các vùng nhớ toàn cục (global memory) của tiến trình bao gồm initialized data, uninitialized data và vùng nhớ heap
Một thread đang thực thi có thể được kết thúc bằng một trong các cách sau:
1.Hàm bắt đầu của thread thực thi câu lệnh return
2.Một hàm bất kỳ trong thread gọi hàm pthread_exit(), chúng ta sẽ nói về hàm này ở dưới đây
3.Thread bị hủy bỏ bằng hàm pthread_cancel()
4.Một thread bất kỳ của tiến trình gọi hàm exit() hoặc thread chính của tiến trình (hàm main()) gọi return. Cả 2 cách này đều có tác dụng kết thúc tiến trình đang chạy và tất nhiên cả các thread của tiến trình đó.
-một thread được tạo ra cũng giống như một tiến trình con, cần phải được theo dõi trạng thái và thu hồi tài nguyên khi kết thúc, tránh việc tạo ra zombie thread gây lãng phí tài nguyên của tiến trình
+Trong Linux, một pthread khi được tạo ra sẽ mặc định là joinable thread. Do đó, thread sau khi kết thúc sẽ được “join” để lấy được trạng thái kết thúc và thu hồi tài nguyên của nó.
#Một thread được thiết lập là detached thread khi lập trình viên không cần quan tâm đến trạng thái kết thúc của nó. Khác với joinable thread, kernel sẽ tự động thu hồi tài nguyên của detached thread khi nó kết thúc.
-#Thuật ngữ critical section (vùng trọng yếu) dùng để chỉ đoạn code mà truy cập vào tài nguyên toàn cục (global resource); đoạn code này nên được chạy hết từ đầu đến cuối bởi mỗi thread thay vì bị ngắt khi có một thread khác xen vào đọc hoặc thay đổi các biến toàn cục trong đó.Như vậy, critical section nên được bảo vệ để khi các thread đồng thời chạy vào, nó phải chờ cho đến khi thread đang chạy thực thi xong và ra khỏi thì mới được chạy vào. Việc này gọi là đồng bộ thread (thread synchronization)
1.Kỹ thuật mutual exclusion (gọi tắt là mutex) dùng để bảo vệ tài nguyên chia sẻ (shared variable) mà chủ yếu là biến chia sẻ (shared variable) giữa các thread. Mỗi vùng critical section sẽ được bảo vệ trong phòng và có một cái khóa ở cửa, một thread trước khi chạy vào critical section sẽ khóa lại rồi vào làm những gì mình muốn làm; sau khi xong việc nó sẽ mở khóa để cho các thread khác truy cập. Các thread khác nếu thấy cửa đang khóa thì phải chờ (đi vào trạng thái blocked) cho đến khi thread trước mở khóa; sau đó nó tiếp tục khóa lại rồi chạy vào critical section và mở khóa ra sau khi xong việc.
- Trạng thái một thread khóa một mutex mà rơi vào trạng thái chờ không thể giải thoát được gọi là deadlock. Có 2 trường hợp:Thread A khóa một mutex mà chính nó trước đó đã bị khóa bởi chính nó hoặc Thread A khóa Mutex1 và vào critical section, sau đó cố gắng khóa một Mutex2 mà thread B đang giữ. Trong khi đó, thread B đang khóa Mutex2 và lại cố gắng khóa Mutex1 ở trong critical section.

	`pthread_create():tao ra thread moi
	`pthread_exit():
	`pthread_join() sẽ block chương trình và chờ cho thread với ID truyen vao kết thúc
	`pthread_detach(), chuyển thread thành detached thread
	`pthread_mutex_lock, pthread_mutex_unlock



-------------------------------------------------------SOCKET----------------------------------------------------

			Application layer

			Transport layer

			Internet layer

			Network Interface layer

+ Có 4 lớp trong mô hình TCP
1.Lơp truy nhập mạng: bao gồm các thiết bị giao tiếp mạng và các chương trình cung cấp các thông tin cần thiết để có thể hoạt động, truy nhập đường truyền vật lý qua các thiết bị giao tiếp mạng đó. Các chức năng trình diễn trong tầng này bao gồm đóng gói gói thông tin IP thành các "Frame" được truyền dẫn trên mạng và chuyển địa chỉ IP thành địa chỉ vật lý sử dụng bởi mạng máy tính.
2.Lơps Internet: Mục đích của lớp Internet là chọn lấy một đường dẫn tốt nhất xuyên qua mạng cho các gói di chuyển tới đích. Các giao thức của tầng này bao gồm : IP ( Internet Protocol) , ICMP ( Internet Control Message Protocol) , IGMP ( Internet Group Message Protocol ). Giao thức chính hoạt động tại lớp này là Internet Protocol (IP). Sự xác định đường dẫn tốt nhất và chuyển mạch gói diễn ra tại lớp này. IP thực hiện các hoạt động sau: Định nghĩa một gói là một lược đồ đánh địa chỉ.->Trung chuyển số liệu giữa lớp Internet và lớp truy nhập mạng.->Định tuyến chuyển các gói đến host ở xa.
3.  Tầng giao vận phụ trách luồng dữ liệu giữa 2 trạm thực hiện các ứng dụng của tầng trên, tầng này có 2 giao thức chính là TCP ( Transmisson Control Protocol) và UDP ( User Datagram Protocol ). Cả hai giao thức đều chuyển giao thông tin giữa tầng ứng dụng và tầng Internet
4. Tầng ứng dụng là tầng trên của mô hình TCP/IP bao gồm các tiến trình và các ứng dụng cung cấp cho người sử dụng để truy cập mạng. Có rất nhiều ứng dụng được cung cấp trong tầng này , mà phổ biến là Telnet: sử dụng trong việc truy cập mạng từ xa, FTP ( File Transport Protocol ) dịch vụ truyền tệp tin


-Socket là một điểm cuối (end-point) của liên kết giao tiếp hai chiều (two-way communication) giữa hai chương trình chạy trên mạng. Nghĩa là một socket được sử dụng để cho phép 1 process nói chuyện với 1 process khác.
1.Stream sockets: Dựa trên giao thức TCP (Tranmission Control Protocol), là giao thức hướng luồng (stream oriented). Việc truyền dữ liệu chỉ thực hiện giữa 2 tiến trình đã thiết lập kết nối. Giao thức này đảm bảo dữ liệu được truyền đến nơi nhận một cách đáng tin cậy, đúng thứ tự nhờ vào cơ chế quản lý luồng lưu thông trên mạng và cơ chế chống tắc nghẽn. Dùng cho mạng WAN, tốc độ thấp
2.Datagram sockets: Dựa trên giao thức UDP (User Datagram Protocol), là giao thức hướng thông điệp (message oriented). Việc truyền dữ liệu không yêu cầu có sự thiết lập kết nối giữa tiến quá trình. Ngược lại với giao thức TCP thì dữ liệu được truyền theo giao thức UDP không được tin cậy, có thế không đúng trình tự và lặp lại. Tuy nhiên vì nó không yêu cầu thiết lập kết nối không phải có những cơ chế phức tạp nên tốc độ nhanh…ứng dụng cho các ứng dụng truyền dữ liệu nhanh như chat, game….. Dùng cho majng LAN, Tốc độ truyền cao, VolP truyền tốt qua UDP

+TCP Server –
+using create(), Create TCP socket.
+using bind(), Bind the socket to server address.
+using listen(), put the server socket in a passive mode, where it waits for the client to approach the server to make a connection
+using accept(), At this point, connection is established between client and server, and they are ready to transfer data.
+Go back to Step 3.
+TCP Client –
+Create TCP socket.
+connect newly created client socket to server.

UDP Server:
Create UDP socket.
Bind the socket to server address.
Wait until datagram packet arrives from client.
Process the datagram packet and send a reply to client.
Go back to Step 3.
UDP Client:
Create UDP socket.
Send message to server.
Wait until response from server is recieved.
Process reply and go back to step 2, if necessary.
Close socket descriptor and exit.
-UDP header: gồm UDP header và UDP data. UDP header đơn giản bao gồm 8 byte(source port, destination port, length, checksum) trong khi TCP header 20-60byte


	`socket()
	`bind
	`listen()
	`accept()
	`connect()


------------------------------------------------------------SCTP----------------------------------------------------------------
- Stream Control Transmission Protocol - Giao thức truyền vận điều khiển dòng
+ SCTP có nhiều điểm tương đồng với TCP. Cả hai đều là các giao thức vận chuyển tin cậy dựa trên IP, áphân phối gói theo trình tự và kiểm soát tắc nghẽn theo biến đổi tốc độ. TCP có checksum 16 bit (RFC 1071) thì SCTP có CRC 32 bit (RFC 4960)
+ Khác: Tuy nhiên, SCTP cung cấp một số chức năng không có trong TCP như: SCTP được định hướng theo message trong khi TCP được định hướng theo luồng, SCTP có thể xử lý nhiều luồng đồng thời và luồng đa kênh trong đó TCP chỉ có thể xử lý một luồng dữ liệu trên mỗi kết nối. SCTP cho phép dữ liệu được chuyển thành nhiều luồng độc lập, do đó, nếu mất dữ liệu trong một luồng, việc truyền dữ liệu sẽ không ảnh hưởng đối với các luồng khác. Tính năng kiểm soát kết nối, nhận biết luồng của SCTP là một trong những tính năng đáng chú ý nhất của nó. 
#SCTP cũng có nhiều tính năng tương tự như UDP. Cả hai đều hỗ trợ vận chuyển không xác thực và truyền tin ngoài gói. SCTP có tiêu đề 12 byte so với tiêu đề 8 byte của UDP. SCTP có tính năng phát hiện kết nối, qua đó phát hiện các gói bị mất và trùng lặp.
Đặc trưng SCTP:
# Multi-homing: Máy chủ có nhiều giao diện mạng và do đó có nhiều địa chỉ IP có thể xử lý. SCTP theo dõi các đường dẫn, khi phát hiện đường dẫn này có lỗi sẽ gửi dữ liệu qua đường truyền khác thay thế (failover). Failover cũng có thể được sử dụng để duy trì kết nối ứng dụng mạng. Ví dụ, hãy xem xét một máy tính xách tay bao gồm giao diện 802.11 không dây và giao diện Ethernet. Khi máy tính xách tay ở trong trạm kết nối, giao diện Ethernet tốc độ cao hơn sẽ được ưu tiên (trong SCTP, được gọi là địa chỉ chính); nhưng khi mất kết nối này (loại bỏ khỏi trạm nối), các kết nối sẽ chuyển đổi với giao diện không dây. Khi trở về trạm nối, kết nối Ethernet sẽ được phát hiện và giao tiếp được tiếp tục qua giao diện này. Đây là một cơ chế mạnh mẽ để cung cấp tính sẵn sàng cao và tăng độ tin cậy.
#Multi-streaming: SCTP cũng giống như TCP ngoại trừ khả năng SCTP hoõ trợ đa luồng trong 1 kết nối. Mỗi luồng được cung cấp một số luồng được mã hóa bên trong các gói SCTP chảy qua liên kết. Đa luồng rất quan trọng vì một luồng bị chặn (ví dụ: một luồng đang chờ truyền lại dẫn đến việc mất gói) không ảnh hưởng đến các luồng khác trong một liên kết. Vấn đề này thường được gọi là chặn đầu dòng. TCP dễ bị chặn như vậy




-------------------------------------------------------------MEMORY----------------------------------------------------------------------
- Linux sử dụng cơ chế quản lý bộ nhớ ảo (virtual memory managemment). Kỹ thuật này khai thác đặc điểm chung của các chương trình là tham chiếu vùng (locality ò referene):
+ Spactial locality: chương trình có xu hướng tham chiếu đến địa chỉ bộ nhớ gần với phân vùng bộ nhớ nó đang truy cập
+ Temporal locality: chương trình có xu hướng truy cập một vùng nhớ trong thời điểm rất gần nhau
# Một bộ nhớ ảo chia không gian bộ nhớ tiến trình ra nhiều đoạn nhỏ có kích thước cố định là các trang (page). RAM cũng chia làm nhiều đoạn nhỏ cùng kích thước là page frame. Taị mỗi thời điểm, process chỉ cần tải 1 vài trang vào trong frame để chay, các trang chưa sử dujgn để ở phân vùng swap và tải khi cần
- Kernel tạo ra bảng page table cho mỗi tiến trình. Mỗi entry của page table ứng với 1 trang cuar bộ nhớ ảo cho phép chỉ ra vị trí của trang đó nằm ở đâu trong RAM
+ Demand paging: Là kỹ thuật xây dựng các bảng paging table và tải các page tiến trình theo nhu cầu. Nếu process truy cập vào phần page chưa có trong RAM hoặc chưa được dựng bảng paging table thì CPU sinh ra page fault( tạm dừng thực thi cho đén khi kernel hoàn tất tải bộ nhớ nó đang cần vào RAM). Trong thời gian đó, để tối ưu xử lý, CPU thực hiện process khác đang chờ đã có bộ nhớ cần thiết trong RAM và quay lại thực thi tiến trình cũ từ chính page fault
#Cấp phát bộ nhớ trên Heap: Dùng brk, sbrk, malloc, calloc,..Thay đổi kích thước phân vùng heap bằng cách tăng giảm giá trị program break. Sau khi program break tăng, process có thể truy cập vào vùng nhớ mới được cấp phát, nhưng đấy chỉ là trên không gian địa chỉ ảo. Địa chỉ vật lý sẽ tự độgn cấp phát khi process truy cập lần đầu vào chúng.
- Cấp phát trên Stack: Dùng alloca. Do cấp phát ở stack nên tự thu hồi.

+ Memory mapping là kỹ thuật tạo ra vùng nhớ ánh xạ trên không gian bộ nhớ ảo cảu tiến trình. Vùng nhớ này có thể ánh xạ đến một file hoặc không file nào, có thể đặt private hoạc shared
# Dùng system call mmap() để thực hiệm memory mapping. Vùng nhớ ánh xạ có thể chia sẻ giữa các process (cùng trỏ đến vùng nhớ giống nhau trên RAM. Khi 2 hoạc nhiều tiến trình chia sẻ vungf nhớ, sự thay đổi có thể được nhìn thấy tùy thuộc vào vung mapping là private  hay shared.
- Các bước tạo ra file mapping
- 1.Lấy giá trị fd file cần map, dùng systemcall open()
- 2.Truyền fd vào đối số của mmap()
- Sau 2 bước này, mmap() sẽ ánh xạ nội dung file vào địa chỉ bộ nhớ ảo cảu tiến trình gọi
+ Private file mapping: nếu truyền cờ MAP_PRIVATE, vùng nhớ mapping thiết lập ché độ private. Sau khởi tạo vungf nhớ mapping được khởi tạo ở vùng nhớ tương ứng trong file. Nhiều tiến trình có thể cùng map đến file. Kernel dùng kỹ thuật copy-on-write, nếu một process thay đổi vùng nhớ map đến file, kernel tạo ra vung nhớ riêng biệt cho tiến trình đó, sự thay đổi sẽ không thay dổi nội dung file trong vung nhớ tiến trình đó.
#Shared file mapping: truyền cờ MAP_SHARED. Nếu 1 process thay đổi vùng nhớ này, các tiến trình khác sẽ nhìn thấy sự thay dổi. Shared file ứng dụng trong 2 trường hợp:
#1.Memory-mapped IO: Nội dung của file được tải vào 1 vùng nhớ trong bộ nhớ ảo của process, chỉ cần thay đổi nội dung vùng nhớ thì sẽ thay đổi nội dung file (Dùng thay thế cho read(), write()). Tối ưu hiệu năng, tieét kiệm bộ nhớ  hơn read(), write() thông thường vì dùng read, write phải copy 2 lần giữa RAM và bộ nhớ đệm kernel, bộ nhớ đệm kernel và bộ nhớ đệm user. mmap() sẽ loại bỏ bước 2, copy thẳng giữa RAM và user 
#2.IPC 

