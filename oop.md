- Object: Đối tượng là một thực thể trong đời thực. Một đối tượng có thuộc tính và phương thức. VD: Con chó có thuộc tính màu, lông, tuổi, giống,..Phương thức: sủa, ăn, tiêu hóa, chạy. Đối tượng là thể hiện của 1 lớp, tát cả các thành viên cua lớp được truy cập thông qua đối tượng
+ Class: Là 1 nhóm của đối tượng. Một class sẽ định nghĩa danh sách những tính chất và phương thức đối tuowjjng trong class sở hữu.
 Trừu tượng(Abstraction): Mục tiêu chính của nó là làm giảm sự phức tạp bằng cách ẩn các chi tiết không liên quan trực tiếp tới người dùng (người dùng ở đây không phải người dùng cuối mà là lập trình viên). Điều đó cho phép người dùng vẫn thực hiện được các công việc cần thiết dựa trên một thực thể trừu tượng được cung cấp mà không cần hiểu hoặc thậm chí không nghĩ về tất cả sự phức tạp ẩn giấu bên trong..Tập trung vào cốt lõi của đối tượng, không quan tâm những thứ ko liên quan. Ví dụ: Khi nói cái quạt chỉ biết là vật làm mát ko biết là quạt cây, quạt treo tường
Dữ liệu (data) và một số hàm (methods) không cần thiết đưa ra bên ngoài sẽ được đưa vào trong class và chỉ định đặc tả truy cập là private (hoặc protected). Các data hoặc methods đó sẽ không thể truy cập từ bên ngoài của class đó. Ở cảnh giới này trừu tượng giúp cho code dễ hiểu hơn vì nó tập trung vào các tính năng / hành động cốt lõi và không tập trung vào các chi tiết nhỏ nhặt. Ngoài ra nó còn giúp chương trình dễ bảo trì, hạn chế lỗi do truy cập data bừa bãi, sai cách. Ở level này có thể coi Abstraction = Encapsulation + Data Hiding
- Tính đóng gói (encapsulation): Tính đóng gói (Encapsulation) chỉ đơn giản là việc kết hợp một bộ các dữ liệu (data) liên quan đến nhau cùng với một bộ các hàm/phương thức (functions/methods) hoạt động trên các dữ liệu đó, “gói” tất cả vào trong một cái gọi là class.  Các thực thể của các class thì được gọi là các đối tượng (objects) trong khi class giống như một công thức được sử dụng để tạo ra các đối tượng đó.
+ Tính thừa kế (inheritance): Ưu điểm của đặc tính kế thừa: sử dụng lại các đoạn code đã có trong chương trình 1 cách hiệu quả. Khi tạo 1 class, thay vì việc viết 1 class mới hoàn toàn, người lập trình viên có thể kế thừa một số thuộc tính và phương thức từ 1 class đã có trong project. Class đã có trước đấy gọi là lớp cơ sở (Base Class), class kế thừa từ Base Class (hay superclass) gọi là lớp dẫn xuất (Derived Class).
 Tính đa hình (polymorphism): Polymorphism có 2 dạng:

Dạng 1 – Compile time Polymorphism: Một class có nhiều hàm cùng tên nhưng khác nhau về số lượng tham số hoặc kiểu dữ liệu của tham số. Khi call hàm cùng tên đó thì trong quá trình biên dịch, compiler sẽ quyết định hàm nào (trong số các hàm cùng tên) sẽ được call dựa trên số lượng tham số và kiểu dữ liệu của tham số truyển vào hàm. Việc định nghĩa các hàm cùng tên được gọi là overloading – nạp chồng hàm.
Dạng 2 – Runtime Polymorphism: Cùng một class có thể cho ra nhiều biến thể, không phải được định nghĩa bởi lớp đó, mà bởi các lớp con của nó. Đây là một phương pháp để định nghĩa lại hành vi của lớp cơ sở mà không phải sửa code (còn gọi là implementation) của lớp cơ sở. Nếu call hàm của đối tượng của lớp dẫn xuất thông qua con trỏ của lớp cơ sở thì việc hàm nào (của lớp cơ sở hay). Runtime Polymorphism được thực hiện bằng phương pháp overriding – ghi đè phương thức.
Ở lớp cha có phương thức là Draw, tùy theo phuong thức lớp con có thể vẽ là hình vuông, hình tròn, hình chữ  nhật.
- Khai bao class:
	class HocSinh{
	    //Khai bao (cai dat) thuoc tinh
	    //Khai bao (cai dat) phuong thuc
	    //Khai bao thuoc tinh, giong khai bao bien
	    //Khai bao phuong thuc giong khai bao ham
	    //private:  chi su dung trong class do thoi
	    //public: the gioi ben ngoai co the su dung
	    //protected:
	private:
	    string HoTen;
	    void xuat();
	public:
	    string DiaChi;
	    void nhap();
	    float tinhDiem();

	};

	int main()
	{
	    HocSinh HS;//cach khoi tao doi tuong tu class
	    HS.DiaChi = "Ha Noi";
	    HS.nhap();//Cach truy cap den thanh phan cua class

	    return 0;
	}
+ Co 2 cach dinh nghia phuong thuc class, Khai bao va dinh nghia trong class, hai bao trong class va dinh nghia ben ngoai. Cu phap: KieuTraVe TenClass::TenPhuongThuc
 Con trỏ this tham chiếu đến đối tượng đang gọi hàm thành phần. . Con trỏ this trong C++ là một từ khóa đề cập đến thể hiện hiện tại của lớp, là một tham số ẩn với tất cả hàm thành viên. Vì thế, bên trong một hàm thành viên, con trỏ this có thể tham chiếu tới đối tượng đang gọi. Cach 1: Trỏ đến thành phần class hiện tại, Cách 2: Trả về object hiện tại
- Đối tượng có thể là tham số truyền vào của phương thức
+ Hàm khởi tạo- Constructor là hàm mặc định được dùng để khởi tạo đối tượng, cùng tên với class, khong co kieu tra ve, va phải trong tầm vực public. Có 3 loại
1Constructor mặc định
2.Constructor có tham số
3.Constructor sao chép
Thuộc tính tĩnh- static data member: 1 bản duy nhất tồn tại trong suốt quá trình chạy của chương trình, dùng chung cho tất cả đối tượng của class, phải định nghĩa bên ngoài clss

- Hàm bạn:
-Hàm bạn trong c++ là hàm tự do, không thuộc lớp. Tuy nhiên hàm bạn trong c++ có quyền truy cập các thành viên private của lớp.
- Một lớp trong c++ có thể có nhiều hàm bạn, và chúng phải nằm bên ngoài class.
-Hàm bạn không thuộc về class của bạn mình (ví dụ: DienTich ko thuộc HinhChuNhat, ko thể gọi DienTich từ HCN được);-
-Thông thường hàm bạn có tham sô truyền vào là một object=>ko biết bạn của ai;
-Hàm bạn không thể truy cập các thuộc tính của hàm bạn mình.
-Hàm bạn khai báo trong public hay private đều được
-Phuowng thức của một class có thể làm bạn của một class khác

+Nap chồng toán tử có 3 cách: member-function, non-member function, friend member function. Member function bị giới hạn tham số truyền vào, dùng non-mem phải dùng getter và setter để truy cập vào thuộc tính private. Dùng friend function linh hoạt hơn.
#Dung getter và setter để lấy dữ liệu private ra sử dụng

-Virtual: thêm trước phương thức
- Chỉ hoạt động thông qua con trỏ
- chỉ cần thêm trước khai báo, không cần them trước định nghĩa
- nếu 1 hàm khai báo là ảo ở lớp cơ sở, nó sẽ ảo ở mọi lớp con
- Tên phương thức ở lớp cơ sở và dẫn xuất phải trung nhau

+ lớp trừu tượng là lớp có ít nhất 1 phương thức thuần ảo, có thuộc tính và phương thức như lớp bình thường
+ phương thức thuần ảo bắt đầu bằng virtual và kết thúc bằng 0. VD: virtual void f() = 0;
+ Không thể tạo đối tượng từ lớp trừu tượng, nhứng có thể tạo con trỏ và tham chiếu
+ Lớp trừu tượng dùng cho mục đích chủ yếu là trỏ đến lớp con (upcasting
+ lớp kế thừa từ lớp thuần ảo cũng phải định nghĩa hàm thuần, nếu không lớp đó cũng thành lớp trừu tượng

-Dùng phương thức ảo khi ở class cha có thông tin tính toán được, nếu ko tính toán mà chỉ tính toán ở các class con, dùng phương thức thuần ảo








# ----------------------Tong ket------------------------------------
0. 4 thuộc tính
* Tính đóng gói (Encapsulation) chỉ đơn giản là việc kết hợp một bộ các dữ liệu (data) liên quan đến nhau cùng với một bộ các hàm/phương thức (functions/methods) hoạt động trên các dữ liệu đó, “gói” tất cả vào trong một cái gọi là class.  Các thực thể của các class thì được gọi là các đối tượng (objects) trong khi class giống như một công thức được sử dụng để tạo ra các đối tượng đó.
* Tính trừu tượng: Mục tiêu chính của nó là làm giảm sự phức tạp bằng cách ẩn các chi tiết không liên quan. Tập trung vào cốt lõi của đối tượng, các data và phương thức không cần thiết sẽ ko public ra bên ngoài class
* Tính kế thừa: Là kỹ thuật cho phép kế thừa lại những tính năng mà một đối tượng khác đã có, giúp tránh việc code lặp dư thừa mà chỉ xử lý công việc tương tự.
* Tính đa hình (polymorphism): Là một đối tượng thuộc các lớp khác nhau có thể hiểu cùng một thông điệp theo cách khác nhau.
1. Con trỏ this
Mỗi đối tượng trong C++ có sự truy cập tới vị trí riêng của nó thông qua một con trỏ quan trọng gọi là con trỏ this. Con trỏ this trong C++ là một từ khóa đề cập đến thể hiện hiện tại của lớp, là một tham số ẩn với tất cả hàm thành viên. Vì thế, bên trong một hàm thành viên, con trỏ this có thể tham chiếu tới đối tượng đang gọi.
Các hàm friend không có con trỏ this, bởi vì friend không phải là các thành viên của một lớp. Chỉ có các hàm thành viên trong C++ là có con trỏ this.

2. Static
* Khi chúng ta khai báo một thành viên của một lớp là static, khi đó dù cho có bao nhiêu đối tượng của lớp được tạo, thì sẽ chỉ có một bản sao của thành viên static.Một thành viên static chỉ cần khởi tạo 1 lần và được chia sẻ cho tất cả đối tượng của lớp. Tất cả dữ liệu static được khởi tạo về 0 khi đối tượng đầu tiên được tạo. Chúng ta không thể khởi tạo thành viên static trong định nghĩa lớp, nhưng nó có thể được định nghĩa bên ngoài lớp đó bởi việc khai báo lại biến static như trong ví dụ sau, sử dụng toán tử phân giải phạm vi :: để nhận diện lớp nào sở hữu nó
Biến static là private, dùng hàm static getter ở tầm vực public để có thể truy cập

* Biến static trong Hàm: Khi một biến được khai báo với từ khóa static, vùng nhớ cho nó tồn tại theo vòng đời của chương trình. Ngay cả khi hàm được gọi nhiều lần, vùng nhớ cho biến static chỉ được cấp nhát một lần và giá trị của biến trong những lần gọi trước đó được lưu lại và được sử dụng để thực hiện thông qua các lượt gọi hàm tiếp theo.
* Các biến static trong class: Vì các biến được khai báo là tĩnh chỉ được khởi tạo một lần khi chúng được cấp phát một địa chỉ trong bộ lưu trữ tĩnh riêng biệt, do đó, các biến tĩnh trong một lớp được chia sẻ bởi các đối tượng. Chúng ta không tạo ra các bản sao cho cùng một biến tĩnh của các đối tượng khác nhau. Cũng vì lý do này mà các biến tĩnh không thể được khởi tạo bằng cách sử dụng các hàm khởi tạo 
Cũng giống như các biến, các đối tượng cũng khi được khai báo là static có thời gian tồn tại bằng với thời gian tồn tại của chương trình. Các hàm static trong class: Giống như các thành viên kiểu static hoặc các biến static bên trong class, các hàm static cũng không phụ thuộc vào đối tượng của class. Cho phép gọi một hàm thành viên static bằng cách sử dụng đối tượng và toán tử "." . Nhưng nên gọi các thành viên static bằng cách sử dụng tên lớp và toán tử phân giải phạm vi. Các hàm thành viên tĩnh chỉ được phép truy cập các thành viên dữ liệu kiểu static hoặc các hàm thành viên static khác, chúng không thể truy cập các thành viên không phải kiểu static của class.


3. Template
“Template” là từ khóa trong C++, chúng ta có thể hiểu rằng là nó một kiểu dữ liệu trừu tượng, đặc trưng cho các kiểu dữ liệu cơ bản. “Template” là từ khóa báo cho trình biên dịch rằng đoạn mã sau đây định nghĩa cho nhiều kiểu dữ liệu và mã nguồn của nó sẽ được compile sinh ra tương ứng cho từng kiểu dữ liệu trong quá trình biên dịch.

Có 2 loại “template” cơ bản:

Function template: là một khuôn mẫu hàm, cho phép định nghĩa các hàm tổng quát thao tác cho nhiều kiểu dữ liệu.
Class template: là một khuôn mẫu lớp, cho phép định nghĩa các lớp tổng quát cho nhiều kiểu dữ liệu.

4. Hàm bạn
Nếu một hàm được định nghĩa là một hàm bạn (Friend function) trong C++, thì dữ liệu được bảo vệ (protected) và riêng tư (private) của một lớp có thể được truy cập bằng cách sử dụng hàm. Hàm bạn phải truy cập dữ liệu thông qua đối tượng vì không phải hàm thành viên.
Một lớp bạn (friend class) có thể truy cập cả các thành viên riêng tư và được bảo vệ của lớp mà nó đã được khai báo là friend.Khi một lớp trở thành một lớp bạn, mọi hàm thành viên của lớp đó đều trở thành hàm bạn.
5. Const vs variable: Không làm thay đổi giá trị biến
*Const vs pointer: 
  * int const *ptr = const int *ptr (Pointer to const): Được phép thay đổi con trỏ ptr, ko được phép thay đổi giá trị trỏ tới
  * int* const ptr (const pointer): không được phép thay đổi con trỏ ptr, được phép thay đổi giá trị nói trỏ tới

* Const vs function: Một hàm nếu muốn truyền tham chiếu đến một hằng const, khi khai báo param cần định nghĩa param được truyền vào là const. Trường hợp cần truyền một const vào một biến tham chiếu của hàm. Nhưng biến không được khai báo const. Sử dụng từ khóa const_cast:
* Const vs class: Khi khai báo một class const: các giá trị của class tại thời điểm khai báo sẽ không bị thay đổi trong quá trình chạy trương trình. Trong trường hợp muốn tạo class kiểu const, nhưng vẫn muốn một số giá trị có thể thay đổi, trong trường hợp này có thể sử dụng từ khóa mutable
Sử dụng "const" với hàm trong class: Khi một hàm được khai báo const tại vị trí sau khi định nghĩa hàm, nó có thể được gọi trên bất kỳ loại đối tượng nào. Các hàm không phải const chỉ có thể được gọi bởi các đối tượng không phải const

6. virtual table
* Con trỏ _vptr là con trỏ được tạo ra mỗi khi một đối tượng (class định nghĩa đối tượng này có khai báo virtual function) được tạo ra khai báo.
* Khi một đối tượng được tạo ra, đồng thời con trỏ _vptr cũng sẽ được tạo ra để trỏ đến virtual table của đối tượng đó
* Virtual Table là một bảng tra cứu các phương thức được sử dụng để giải quyết các lệnh gọi hàm trong quá trình late binding. , tất cả những lớp có sử dụng phương thức ảo (hoặc kế thừa từ một lớp có sử dụng phương thức ảo) đều sở hữu Virtual Table. Bảng này thực chất là một mảng tĩnh được trình biên dịch thiết lập trong quá trình biên dịch (compile time). Mỗi một Virtual Table đều có ô chứa cho từng phương thức ảo có thể được truy xuất từ đối tượng của lớp. Mỗi ô chứa trong Virtual Table thực chất là một con trỏ hàm trỏ đến phương thức được kế thừa gần nhất và có thể truy cập từ lớp này.
* Nếu một hàm được định nghĩa là một hàm bạn (Friend function) trong C++, thì dữ liệu được bảo vệ (protected) và riêng tư (private) của một lớp có thể được truy cập bằng cách sử dụng hàm.
* Một lớp bạn (friend class) có thể truy cập cả các thành viên riêng tư và được bảo vệ của lớp mà nó đã được khai báo là friend.
7. Copy constructor
* Hàm xây dựng sao chép (Copy Constructor) trong C++ là một hàm xây dựng được sử dụng để khai báo và khởi tạo một đối tượng từ một đối tượng khác.
* Trong C++ có hai loại copy được tạo bởi hàm xây dựng đó là:
  * Shallow copy: Hàm xây dựng sao chép mặc định chỉ có thể tạo shallow copy Shallow copy được định nghĩa là quá trình tạo bản sao của một đối tượng bằng cách sao chép dữ liệu của tất cả các biến thành viên
  * Deep copy: Deep copy tự động cấp phát bộ nhớ cho bản sao và sau đó sao chép giá trị thực cho bản sao, cả nguồn và bản sao có vị trí bộ nhớ khác nhau. Theo cách này, cả nguồn và bản sao là khác nhau và sẽ không chia sẻ cùng một vị trí bộ nhớ. Deep copy yêu cầu chúng ta viết hàm xây dựng do người dùng định nghĩa
8. 
* Truyền tham trị
  * Một bản sao giá trị của biến được truyền vào hàm
  * Những thay đổi trong hàm được giới hạn trong hàm, không làm thay đổi giá trị của biến được truyền vào hàm
  * Đối số trong hàm và tham số chính thức được tạo tại hai vị trí bộ nhớ khác nhau
* Truyền tham chiếu:
  *  Một địa chỉ ô nhớ của biến được truyền vào hàm
  * Những thay đổi không chỉ giới hạn trong hàm mà còn làm thay đổi giá trị của biến được truyền vào hàm nếu trong hàm cũng làm thay đổi giá trị biến đó
  * Đối số trong hàm và tham số chính thức được tạo tại cùng một vị trí bộ nhớ

9. Lỗi Segment fault
* Có 5 lỗi phổ biến dẫn đến lỗi “segmentation fault” đó là
  * Dereferencing con trỏ NULL
  * Dereferencing con trỏ chưa được khởi tạo
  * Dereferencing con trỏ đã bị free hoặc delete
  * Ghi giá trị vượt quá giới hạn của mảng
  * Hàm đệ quy sử dụng hết vùng bộ dành cho stack – còn gọi là “stack overflow”

10. Lớp lưu trữ
Có 5 loại:
* register: biến cục bộ mà nên được lưu giữ trong một thanh ghi thay vì RAM
* static
* extern: Lớp lưu trữ extern được dùng phổ biến khi có hai hoặc nhiều file chia sẻ cùng biến hay hàm toàn cục
* auto
* mutable


