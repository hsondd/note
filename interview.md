-------------------------------------------------------------CPP--------------------------------------------------------------------
- Namespace là một cơ chế trong C++, cho phép ta nhóm các thực thể (class, object, function…) có liên quan thành từng nhóm khác nhau theo tên, mà theo đó tên của mọi thực thể trong mỗi namespace đều được gắn thêm tên của namespace đó như tiền tố.
2. Từ khóa volatile làm gì
Việc khai báo biến có thuộc tính volatile là rất cần thiết nhằm tránh các lỗi phát sinh ngoài ý muốn khi tính năng optimization của compiler được bật. Volatile để chỉ một biến có thể bị thay đổi giá trị một cách "bất thường". Có nghĩa là giá trị của biến có thể bị thay đổi mà không được báo trước
3.Phân biệt Syntax-error, Runtime-error and Logical-error?
Syntax-error: Lỗi cú pháp được phát hiện ngay khi biên dịch chương trình. Trình biên dịch sẽ thông báo lỗi tại cửa sổ Output
Runtime-error: Chương trình đã được biên dịch thành công, gặp lỗi khi chạy chương trình do đầu vào hoặc đầu ra có giá trị không mong muốn
Logical-error: Chương trình đã được biên dịch và chạy không gặp lỗi Runtime-error. Nhưng kết quả đầu ra không đúng theo yêu cầu do logic xử lý bài toán bị sai.
4. Phân biệt biến Local, Global, Extern, Static và Const
- Biến global
Là biến được khai báo bên ngoài tất cả các hàm và có giá trị với tất cả các hàm trong chương trình. Tức là các hàm trong chương trình có thể sử dụng biến global để tính toán.
Biến global tồn tại đến khi nào chương trình kết thúc.
Có thể định nghĩa 1 biến global trong 1 file (.c/.cpp/.h) và truy cập biến này từ 1 file (.c/.cpp/.h) khác. Để làm điều này, biến phải được khai báo ở cả 2 file và từ khóa extern được thêm trong lần khai báo thứ 2.
- Biến local 
Biến local là xuất hiện trong phạm vi cụ thể.
Biến local chỉ tồn tại trong hàm mà biến được khai báo
Đôi khi, biến local được gọi là biến tự động (auto) bởi vì các biến được tự động sinh ra khi hàm được thực hiện và sẽ tự động biến mất khi kết thúc hàm.
Từ khóa auto được sử dụng để ám chỉ biến cục bộ.
-Biến static
Biến static có thể là global hoặc local. Cả hai đều được khai báo với từ khóa static đi kèm.
Biến local static là biến có thể duy trì giá trị từ lần gọi hàm thứ nhất đến các lần gọi hàm tiếp theo. Biến local static tồn tại đến khi chương trình kết thúc.
Khi tạo 1 biến local static trong hàm, chúng ta nên khởi tạo giá trị cho chúng. Nếu không giá trị biến được gán mặc định bằng 0.
Biến global static là biến global mà chỉ có thể truy cập từ file (.c/.cpp) mà biến đó được định nghĩa.
- Biến const
Trong ngôn ngữ C, tiền xử lý #define được sử dụng để tạo biến với giá trị là hằng số.
Trong ngôn ngữ C++, xuất hiện một số vấn đề: khi sử dụng #define, tiền xử lí sẽ nhảy thẳng vào source code và thay thế biến bằng giá trị đã định nghĩa. Vì biến #define chỉ tồn tại bên trong file mà nó được định nghĩa, có thể xảy ra trường hợp định nghĩa tên biến giống nhưng khác về giá trị.
Định nghĩa biến hằng trong C++, chủng ta nên sử dụng từ khóa const đi kèm.
Khi sử dụng từ khóa const, phải khởi tạo giá trị ban đầu cho biến
5. Truyền tham trị và tham biến cho hàm
-Khi truyền đối số kiểu tham trị, chương trình biên dịch sẽ copy giá trị của đối số để gán cho tham số của hàm (không tác động trực tiếp đến biến số truyền vào).
- Phương pháp truyền tham biến là cách truyền địa chỉ của đối số cho các tham số tương ứng của hàm được gọi. Với cách truyền tham biến, giá trị của đối số truyền vào có thể bị thay đổi bởi việc gọi hàm.
Truyền tham biến chia ra thành 2 loại : truyền con trỏ (dùng trong C và C++) , truyền tham chiếu (chỉ dùng trong C++)
6. Sự khác nhau giữa const char* s và char* const s?
- Hằng con trỏ – Constant pointer: <Kiểu dữ liệu> * const <Tên con trỏ> = <Địa chỉ khởi tạo> ;
Cần gán ngay giá trị địa chỉ khởi tạo cho hằng con trỏ tại câu lệnh khai báo ban đầu.
Không thể thay đổi địa chỉ đã được khởi gán cho hằng con trỏ ( sẽ gây ra lỗi).
Có thể thay đổi giá trị tại địa chỉ đã khởi gián ban đầu
- Con trỏ hằng- pointer to constant: const <Kiểu dữ liệu> * <Tên con trỏ>;
Không được phép dùng trực tiếp con trỏ hằng để thay đổi giá trị tại vùng nhớ mà con trỏ hằng đang trỏ đến.
Con trỏ hằng có thể thể thay đổi địa chỉ trỏ tới (hay nói cách khác: nó có thể trỏ đến các ô nhớ khác nhau).
7. Con trỏ void là gì:
Nó có thể lưu trữ địa chỉ của mọi kiểu biến dữ liệu
Ta không thể sử dụng trực tiếp dữ liệu mà con trỏ void trỏ tới bằng toán tử (*), mà cần biến đổi con trỏ (void*) sang thành kiểu dữ liệu tương ứng.
8.Kich thước của con trỏ là gì?
Tùy thuộc vào hệ điều hành là 64bit hay 32 bit mà con trỏ có kích thước khác nhau

9. Sự khác nhau giữa const và volatite?
-Biến volatile là rất cần thiết để tránh những lỗi sai khó phát hiện do tính năng optimization của compiler. Trong thực tế, có 3 loại biến mà giá trị có thể bị thay đổi như vậy:Memory-mapped peripheral registers (thanh ghi ngoại vi có ánh xạ đến ô nhớ); Biến toàn cục được truy xuất từ các tiến trình con xử lý ngắt (interrupt service routine); Biến toàn cục được truy xuất từ nhiều tác vụ trong một ứng dụng đa luồng.

- Const được sử dụng để định nghĩa một hằng số trong chương trình.

10. Tại sao nên gán NULL cho con trỏ sau khi giải phóng vùng nhớ?
NULL tương đương với 0

Một con trỏ mới tạo ra trỏ “linh tinh” vào một vùng nhớ nào đấy. Gán con trỏ bằng NULL để đảm bảo nó trỏ về 0. Dù 0 cũng là một vị trí không hợp lệ, nhưng mình sẽ dễ quản lý hơn là khi con trỏ trỏ về một vùng nào đó mình không biết.

11.Sự khác nhau giữa malloc() và new()?
* new la toan tu, malloc la ham
* new có thể dùng gọi hàm khởi tạo còn malloc thì ko
* new có thể override, malloc thì ko;
* new cấp phát từ vùng nhớ trống, malloc cấp phát từ heap
* new trả về kiểu dũ liệu chính xác, malloc chả về (void *), phải ép kiểu
* cáp phát thất bại new xay ra ngoại lê, malloc caasp phát thất bại trả về null

1.  Hàm nội tuyến(inline function) là gì
Khi một hàm được gọi, CPU sẽ lưu địa chỉ bộ nhớ của dòng lệnh hiện tại mà nó đang thực thi (để biết nơi sẽ quay lại sau lời gọi hàm), sao chép các đối số của hàm trên ngăn xếp (stack) và cuối cùng chuyển hướng điều khiển sang hàm đã chỉ định. CPU sau đó thực thi mã bên trong hàm, lưu trữ giá trị trả về của hàm trong một vùng nhớ/thanh ghi và trả lại quyền điều khiển cho vị trí lời gọi hàm. Điều này sẽ tạo ra một lượng chi phí hoạt động nhất định so với việc thực thi mã trực tiếp (không sử dụng hàm).

-  Inline function là một chức năng trong ngôn ngữ lập trình C++. Hàm inline là hàm được định nghĩa bằng từ khóa inline. Hàm inline được sử dụng để yêu cầu trình biên dịch (compiler) thay thế lời gọi hàm bằng toàn bộ mã code của hàm nhằm mục đích giảm thời gian chạy chương trình.

13. Hàm hủy ảo
Khi kế thừa nếu hàm hủy ko phải hàm ảo. Khi gọi hàm hủy, là chỉ hàm phương thức lớp cha được gọi nhưng phương thức của lớp con không được gọi. Dẫn đến mất mát bộ nhớ. Còn nếu dùng hàm hủy ảo phương thức hủy của lớp con được gọi trước sau đó mới gọi phương thức hủy lớp cha, đúng như chúng ta mong muốn. Tránh được tình trạng mất bộ nhớ.

18. Virtual function
* Virtual Function là để khai báo một function ở class cha (base class) mà sau đó các class kế thừa (derived class) có thể override function đó
* Hàm ảo là một loại hàm đặc biệt, khi được gọi, sẽ tự động hiểu và chọn đúng đối tượng gốc để gọi đúng hàm của đối tượng đó giữa lớp cơ sở và lớp dẫn xuất. Khả năng này được gọi là đa hình. Hàm dẫn xuất được coi là khớp với lớp cơ sở nếu nó có cùng tên, loại tham số (cho dù đó là const) và kiểu trả về của hàm trong lớp cơ sở. Các hàm như vậy được gọi là ghi đè(overriding).
* Virtual functions cannot be static
* A virtual function can be a friend function of another class
* They are always defined in the base class and overridden in a derived class. It is not mandatory for the derived class to override
* *override*, ý nghĩa của từ khóa này sẽ giúp ta kiểm soát việc một hàm có thật sự là override một phương thức của lớp mà nó đang kế thừa hay không, nếu không tồn tại phương thức mà nó đang "nghĩ" rằng nó đang override tại lớp mà nó kế thừa thì trình biên dịch sẽ báo lỗi khi biên dịch
* *final* Virtual function được đánh dấu là final sẽ không cho phép override ở lớp dẫn suất. Nếu lớp dẫn suất vẫn override thì trình biên dịch sẽ báo lỗi.

19. Virtual table
* Con trỏ _vptr là con trỏ được tạo ra mỗi khi một đối tượng (class định nghĩa đối tượng này có khai báo virtual function) được tạo ra khai báo.
* Khi một đối tượng được tạo ra, đồng thời con trỏ _vptr cũng sẽ được tạo ra để trỏ đến virtual table của đối tượng đó
* Virtual Table là một bảng tra cứu các phương thức được sử dụng để giải quyết các lệnh gọi hàm trong quá trình late binding. Tất cả những lớp có sử dụng phương thức ảo (hoặc kế thừa từ một lớp có sử dụng phương thức ảo) đều sở hữu Virtual Table. Bảng này thực chất là một mảng tĩnh được trình biên dịch thiết lập trong quá trình biên dịch (compile time). Mỗi một Virtual Table đều có ô chứa cho từng phương thức ảo có thể được truy xuất từ đối tượng của lớp. Mỗi ô chứa trong Virtual Table thực chất là một con trỏ hàm trỏ đến phương thức được kế thừa gần nhất và có thể truy cập từ lớp này.

20. Pure virtual function
* Hàm thuần ảo (hoặc hàm trừu tượng) hoàn toàn không có cơ thể! Một hàm thuần ảo hoạt động như một trình giữ chỗ có nghĩa là nó được định nghĩa lại bởi các lớp dẫn xuất.
* Bất kỳ lớp nào có một hoặc nhiều hàm thuần ảo sẽ trở thành một lớp cơ sở trừu tượng điều đó có nghĩa là nó không thể được khởi tạo
* Bất kỳ lớp dẫn xuất nào cũng phải định nghĩa một thân cho hàm này hoặc lớp dẫn xuất đó cũng sẽ được coi là một lớp cơ sở trừu tượng.


1.   Delegating constructor
2.   No Static member init
3.   Default and Deleted function
4.   Move semantics
5.  Friend
* Nếu một hàm được định nghĩa là một hàm bạn (Friend function) trong C++, thì dữ liệu được bảo vệ (protected) và riêng tư (private) của một lớp có thể được truy cập bằng cách sử dụng hàm.
* Một hàm có thể là bạn của nhiều class cùng một lúc.
* Một lớp bạn (friend class) có thể truy cập cả các thành viên riêng tư và được bảo vệ của lớp mà nó đã được khai báo là friend. Việc biến toàn bộ một lớp trở thành bạn của một lớp khác là hoàn toàn có thể. Điều này cho phép tất cả các thành viên của lớp bạn có thể truy cập tới các thành viên private của lớp khác.

21. Singleton

* Có 2 điểm cần lưu ý ở đây:

Khi class chỉ cần sử dụng 1 và duy nhất 1 instance

Cung cấp một điểm truy cập toàn cục tới instance này thay vì qua constructor

22. Observe pattern

* Observer pattern là một mẫu thiết kế phần mềm mà một đối tượng, gọi là subject, duy trì một danh sách các thành phần phụ thuộc nó, gọi là observer, và thông báo tới chúng một cách tự động về bất cứ thay đổi nào, thường thì bằng cách gọi 1 hàm của chúng.Observer pattern là một mẫu thiết kế phần mềm mà một đối tượng, gọi là subject, duy trì một danh sách các thành phần phụ thuộc nó, gọi là observer, và thông báo tới chúng một cách tự động về bất cứ thay đổi nào, thường thì bằng cách gọi 1 hàm của chúng.

23. Adapter pattern

* Adapter pattern chuyển đổi interface của một class thành interface mà client yêu cầu.
Adapter ở giữa gắn kết các lớp làm việc với nhau dù cho có những interface không tương thích với nhau.


