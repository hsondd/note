-------------------------------------------------------------CPP--------------------------------------------------------------------
# 1. Namespace
- là một cơ chế trong C++, cho phép ta nhóm các thực thể (class, object, function…) có liên quan thành từng nhóm khác nhau theo tên, mà theo đó tên của mọi thực thể trong mỗi namespace đều được gắn thêm tên của namespace đó như tiền tố.

# 2. Từ khóa volatile làm gì
- Việc khai báo biến có thuộc tính volatile là rất cần thiết nhằm tránh các lỗi phát sinh ngoài ý muốn khi tính năng optimization của compiler được bật. Volatile để chỉ một biến có thể bị thay đổi giá trị một cách "bất thường". Có nghĩa là giá trị của biến có thể bị thay đổi mà không được báo trước


# 3. Phân biệt Syntax-error, Runtime-error and Logical-error?

- Syntax-error: Lỗi cú pháp được phát hiện ngay khi biên dịch chương trình. Trình biên dịch sẽ thông báo lỗi tại cửa sổ Output
- Runtime-error: Chương trình đã được biên dịch thành công, gặp lỗi khi chạy chương trình do đầu vào hoặc đầu ra có giá trị không mong muốn
- Logical-error: Chương trình đã được biên dịch và chạy không gặp lỗi Runtime-error. Nhưng kết quả đầu ra không đúng theo yêu cầu do logic xử lý bài toán bị sai.

# 4. Phân biệt biến Local, Global, Extern, Static và Const
- Biến global
    - Là biến được khai báo bên ngoài tất cả các hàm và có giá trị với tất cả các hàm trong chương trình. Tức là các hàm trong chương trình có thể sử dụng biến global để tính toán.
    - Biến global tồn tại đến khi nào chương trình kết thúc.

    - Có thể định nghĩa 1 biến global trong 1 file (.c/.cpp/.h) và truy cập biến này từ 1 file (.c/.cpp/.h) khác. Để làm điều này, biến phải được khai báo ở cả 2 file và từ khóa extern được thêm trong lần khai báo thứ 2.
- Biến local 
    - Biến local là xuất hiện trong phạm vi cụ thể.
    - Biến local chỉ tồn tại trong hàm mà biến được khai báo
    - Đôi khi, biến local được gọi là biến tự động (auto) bởi vì các biến được tự động sinh ra khi hàm được thực hiện và sẽ tự động biến mất khi kết thúc hàm.
- Từ khóa auto được sử dụng để ám chỉ biến cục bộ.
- Biến static
    - Biến static có thể là global hoặc local. Cả hai đều được khai báo với từ khóa static đi kèm.
    - Biến local static là biến có thể duy trì giá trị từ lần gọi hàm thứ nhất đến các lần gọi hàm tiếp theo. Biến local static tồn tại đến khi chương trình kết thúc.
    - Khi tạo 1 biến local static trong hàm, chúng ta nên khởi tạo giá trị cho chúng. Nếu không giá trị biến được gán mặc định bằng 0.
    - Biến global static là biến global mà chỉ có thể truy cập từ file (.c/.cpp) mà biến đó được định nghĩa.
- Biến const
    - Trong ngôn ngữ C, tiền xử lý #define được sử dụng để tạo biến với giá trị là hằng số.
    - Trong ngôn ngữ C++, xuất hiện một số vấn đề: khi sử dụng #define, tiền xử lí sẽ nhảy thẳng vào source code và thay thế biến bằng giá trị đã định nghĩa. Vì biến #define chỉ tồn tại bên trong file mà nó được định nghĩa, có thể xảy ra trường hợp định nghĩa tên biến giống nhưng khác về giá trị.
    - Định nghĩa biến hằng trong C++, chủng ta nên sử dụng từ khóa const đi kèm.
    - Khi sử dụng từ khóa const, phải khởi tạo giá trị ban đầu cho biến
# 5. Truyền tham trị và tham biến cho hàm
- Khi truyền đối số kiểu tham trị, chương trình biên dịch sẽ copy giá trị của đối số để gán cho tham số của hàm (không tác động trực tiếp đến biến số truyền vào).
- Phương pháp truyền tham biến là cách truyền địa chỉ của đối số cho các tham số tương ứng của hàm được gọi. Với cách truyền tham biến, giá trị của đối số truyền vào có thể bị thay đổi bởi việc gọi hàm.
    - Truyền tham biến chia ra thành 2 loại : truyền con trỏ (dùng trong C và C++) , truyền tham chiếu (chỉ dùng trong C++)

# 6. Sự khác nhau giữa const char* s và char* const s?
- Hằng con trỏ – Constant pointer: <Kiểu dữ liệu> * const <Tên con trỏ> = <Địa chỉ khởi tạo> ;
Cần gán ngay giá trị địa chỉ khởi tạo cho hằng con trỏ tại câu lệnh khai báo ban đầu.
Không thể thay đổi địa chỉ đã được khởi gán cho hằng con trỏ ( sẽ gây ra lỗi).
Có thể thay đổi giá trị tại địa chỉ đã khởi gián ban đầu
- Con trỏ hằng- pointer to constant: const <Kiểu dữ liệu> * <Tên con trỏ>;
Không được phép dùng trực tiếp con trỏ hằng để thay đổi giá trị tại vùng nhớ mà con trỏ hằng đang trỏ đến.
Con trỏ hằng có thể thể thay đổi địa chỉ trỏ tới (hay nói cách khác: nó có thể trỏ đến các ô nhớ khác nhau).

# 7. Con trỏ void là gì:
Nó có thể lưu trữ địa chỉ của mọi kiểu biến dữ liệu
Ta không thể sử dụng trực tiếp dữ liệu mà con trỏ void trỏ tới bằng toán tử (*), mà cần biến đổi con trỏ (void*) sang thành kiểu dữ liệu tương ứng.
# 8.Kich thước của con trỏ là gì?
Tùy thuộc vào hệ điều hành là 64bit hay 32 bit mà con trỏ có kích thước khác nhau

# 9. Sự khác nhau giữa const và volatite?
- Biến volatile là rất cần thiết để tránh những lỗi sai khó phát hiện do tính năng optimization của compiler. Trong thực tế, có 3 loại biến mà giá trị có thể bị thay đổi như vậy: Memory-mapped peripheral registers (thanh ghi ngoại vi có ánh xạ đến ô nhớ); Biến toàn cục được truy xuất từ các tiến trình con xử lý ngắt (interrupt service routine); Biến toàn cục được truy xuất từ nhiều tác vụ trong một ứng dụng đa luồng.

- Const được sử dụng để định nghĩa một hằng số trong chương trình.

# 10. Tại sao nên gán NULL cho con trỏ sau khi giải phóng vùng nhớ?
NULL tương đương với 0

Một con trỏ mới tạo ra trỏ “linh tinh” vào một vùng nhớ nào đấy. Gán con trỏ bằng NULL để đảm bảo nó trỏ về 0. Dù 0 cũng là một vị trí không hợp lệ, nhưng mình sẽ dễ quản lý hơn là khi con trỏ trỏ về một vùng nào đó mình không biết.

# 11.Sự khác nhau giữa malloc() và new()?
* new la toan tu, malloc la ham
* new có thể dùng gọi hàm khởi tạo còn malloc thì ko
* new có thể override, malloc thì ko;
* new cấp phát từ vùng nhớ trống, malloc cấp phát từ heap
* new trả về kiểu dũ liệu chính xác, malloc chả về (void *), phải ép kiểu
* cáp phát thất bại new xay ra ngoại lê, malloc caasp phát thất bại trả về null

# 12.  Hàm nội tuyến(inline function) là gì
Khi một hàm được gọi, CPU sẽ lưu địa chỉ bộ nhớ của dòng lệnh hiện tại mà nó đang thực thi (để biết nơi sẽ quay lại sau lời gọi hàm), sao chép các đối số của hàm trên ngăn xếp (stack) và cuối cùng chuyển hướng điều khiển sang hàm đã chỉ định. CPU sau đó thực thi mã bên trong hàm, lưu trữ giá trị trả về của hàm trong một vùng nhớ/thanh ghi và trả lại quyền điều khiển cho vị trí lời gọi hàm. Điều này sẽ tạo ra một lượng chi phí hoạt động nhất định so với việc thực thi mã trực tiếp (không sử dụng hàm).

-  Inline function là một chức năng trong ngôn ngữ lập trình C++. Hàm inline là hàm được định nghĩa bằng từ khóa inline. Hàm inline được sử dụng để yêu cầu trình biên dịch (compiler) thay thế lời gọi hàm bằng toàn bộ mã code của hàm nhằm mục đích giảm thời gian chạy chương trình.

# 13. Hàm hủy ảo
Khi kế thừa nếu hàm hủy ko phải hàm ảo. Khi gọi hàm hủy, là chỉ hàm phương thức lớp cha được gọi nhưng phương thức của lớp con không được gọi. Dẫn đến mất mát bộ nhớ. Còn nếu dùng hàm hủy ảo phương thức hủy của lớp con được gọi trước sau đó mới gọi phương thức hủy lớp cha, đúng như chúng ta mong muốn. Tránh được tình trạng mất bộ nhớ.

# 13. Virtual function
* Virtual Function là để khai báo một function ở class cha (base class) mà sau đó các class kế thừa (derived class) có thể override function đó
* Hàm ảo là một loại hàm đặc biệt, khi được gọi, sẽ tự động hiểu và chọn đúng đối tượng gốc để gọi đúng hàm của đối tượng đó giữa lớp cơ sở và lớp dẫn xuất. Khả năng này được gọi là đa hình. Hàm dẫn xuất được coi là khớp với lớp cơ sở nếu nó có cùng tên, loại tham số (cho dù đó là const) và kiểu trả về của hàm trong lớp cơ sở. Các hàm như vậy được gọi là ghi đè(overriding).
* Virtual functions cannot be static
* A virtual function can be a friend function of another class
* They are always defined in the base class and overridden in a derived class. It is not mandatory for the derived class to override
* *override*, ý nghĩa của từ khóa này sẽ giúp ta kiểm soát việc một hàm có thật sự là override một phương thức của lớp mà nó đang kế thừa hay không, nếu không tồn tại phương thức mà nó đang "nghĩ" rằng nó đang override tại lớp mà nó kế thừa thì trình biên dịch sẽ báo lỗi khi biên dịch
* *final* Virtual function được đánh dấu là final sẽ không cho phép override ở lớp dẫn suất. Nếu lớp dẫn suất vẫn override thì trình biên dịch sẽ báo lỗi.

# 14. Virtual table
* Con trỏ _vptr là con trỏ được tạo ra mỗi khi một đối tượng (class định nghĩa đối tượng này có khai báo virtual function) được tạo ra khai báo.
* Khi một đối tượng được tạo ra, đồng thời con trỏ _vptr cũng sẽ được tạo ra để trỏ đến virtual table của đối tượng đó
* Virtual Table là một bảng tra cứu các phương thức được sử dụng để giải quyết các lệnh gọi hàm trong quá trình late binding. Tất cả những lớp có sử dụng phương thức ảo (hoặc kế thừa từ một lớp có sử dụng phương thức ảo) đều sở hữu Virtual Table. Bảng này thực chất là một mảng tĩnh được trình biên dịch thiết lập trong quá trình biên dịch (compile time). Mỗi một Virtual Table đều có ô chứa cho từng phương thức ảo có thể được truy xuất từ đối tượng của lớp. Mỗi ô chứa trong Virtual Table thực chất là một con trỏ hàm trỏ đến phương thức được kế thừa gần nhất và có thể truy cập từ lớp này.

# 15. Pure virtual function
* Hàm thuần ảo (hoặc hàm trừu tượng) hoàn toàn không có cơ thể! Một hàm thuần ảo hoạt động như một trình giữ chỗ có nghĩa là nó được định nghĩa lại bởi các lớp dẫn xuất.
* Bất kỳ lớp nào có một hoặc nhiều hàm thuần ảo sẽ trở thành một lớp cơ sở trừu tượng điều đó có nghĩa là nó không thể được khởi tạo
* Bất kỳ lớp dẫn xuất nào cũng phải định nghĩa một thân cho hàm này hoặc lớp dẫn xuất đó cũng sẽ được coi là một lớp cơ sở trừu tượng.


# 16.   Delegating constructor
# 17.   No Static member init
# 18.   Default and Deleted function
# 19.   Move semantics
- Tác dụng
  - Giúp loại bỏ những chi phí vô ích khi thực hiện copy dữ liệu từ đối tượng tạm.
  - Loại bỏ những chi phí "vô hình" khi hàm trả về một đối tượng.
  - Tối ưu hóa việc copy trong một số trường hợp nhất định, khi nắm rõ vòng đời của đối tượng.
  - Giúp chúng ta thực hiện việc "chuyển quyền sở hữu".


- Temporary object
    - Giá trị trung gian trong quá trình tính toán của biểu thức. Ví dụ: int a = 4 + (3 * b);
    Biến trả về từ hàm.
    Ví dụ: std::vector<int> sortedArray = CreateSortedArray(inputedArray);
    - Biến trả về từ hàm.
    Ví dụ: std::vector<int> sortedArray = CreateSortedArray(inputedArray);
    - Biến được khởi tạo nhưng không đặt tên. Trong đoạn code ví dụ sau ta tạo ra đối tượng string để chứa giá trị "stdio.vn" và "www.stdio.vn" nhưng vì không được đặt tên nên 2 đối tượng này là 2 đối tượng tạm.
    if (string("stdio.vn") == string("www.stdio.vn"));

- lvalue and rvalue
    - lvalue là giá trị có thể gán được, còn rvalue là giá trị ta không thể gán được hoặc rvalue chỉ có thể nằm bên phải dấu =
    - Có thể thực hiện lấy địa chỉ của lvalue sử dụng toán tử &, nhưng không thể lấy địa chỉ của rvalue.
    - Các lvalue thường là những biến có tên, các rvalue thường là những biến không có tên.
    - Hầu hết các đối tượng tạm là rvalue, và hầu hết các rvalue là đối tượng tạm.
    - Các đối tượng tạm được tạo ra trong quá trình tính toán biểu thức là rvalue.
    - Khi một hàm trả về giá trị của một biến thì giá trị trả về đó là một rvalue (Vì chương trình phải tạo ra một đối tượng tạm để chứa giá trị của biến mà nó trả về).
    - lvalue reference có thể dùng để tham chiếu đến một lvalue, nhưng không thể dùng để tham chiếu đến một rvalue.
    - Trong C++ lại cho phép dùng const lvalue reference để tham chiếu đến rvalue.
- Copy semantics là thực hiện copy trạng thái (hay dữ liệu) của đối tượng này sang đối tượng khác, sau đó cả 2 đối tượng này sẽ có trạng thái (hay dữ liệu) như nhau.




# 20.  Friend
* Nếu một hàm được định nghĩa là một hàm bạn (Friend function) trong C++, thì dữ liệu được bảo vệ (protected) và riêng tư (private) của một lớp có thể được truy cập bằng cách sử dụng hàm.
* Một hàm có thể là bạn của nhiều class cùng một lúc.
* Một lớp bạn (friend class) có thể truy cập cả các thành viên riêng tư và được bảo vệ của lớp mà nó đã được khai báo là friend. Việc biến toàn bộ một lớp trở thành bạn của một lớp khác là hoàn toàn có thể. Điều này cho phép tất cả các thành viên của lớp bạn có thể truy cập tới các thành viên private của lớp khác.

# 21. Singleton

* Có 2 điểm cần lưu ý ở đây:

Khi class chỉ cần sử dụng 1 và duy nhất 1 instance

Cung cấp một điểm truy cập toàn cục tới instance này thay vì qua constructor

# 22. Observe pattern

* Observer pattern là một mẫu thiết kế phần mềm mà một đối tượng, gọi là subject, duy trì một danh sách các thành phần phụ thuộc nó, gọi là observer, và thông báo tới chúng một cách tự động về bất cứ thay đổi nào, thường thì bằng cách gọi 1 hàm của chúng.Observer pattern là một mẫu thiết kế phần mềm mà một đối tượng, gọi là subject, duy trì một danh sách các thành phần phụ thuộc nó, gọi là observer, và thông báo tới chúng một cách tự động về bất cứ thay đổi nào, thường thì bằng cách gọi 1 hàm của chúng.

# 23. Adapter pattern

* Adapter pattern chuyển đổi interface của một class thành interface mà client yêu cầu.
Adapter ở giữa gắn kết các lớp làm việc với nhau dù cho có những interface không tương thích với nhau.

# 24. Lớp lưu trữ (Storage Class)

* Lớp lưu trữ auto trong C/C++ là lớp lưu trữ mặc định cho tất cả biến cục bộ trong C/C++:
* Lớp lưu trữ register trong C/C++ được sử dụng để định nghĩa các biến cục bộ mà nên được lưu giữ trong một thanh ghi thay vì RAM
* Lớp lưu trữ static trong C/C++ nói với compiler để giữ một biến cục bộ tồn tại trong toàn bộ thời gian sống của chương trình thay vì tạo và hủy biến mỗi lần nó vào và ra khỏi phạm vi biến.
* Lớp lưu trữ extern trong C/C++ được dùng để cung cấp một tham chiếu của một biến toàn cục được nhìn thấy bởi TẤT CẢ các file chương trình. Khi bạn sử dụng 'extern', biến không thể được khởi tạo, khi nó trỏ tới tên biến tại một vị trí lớp lưu trữ mà đã được định nghĩa trước đó
* Lớp lưu trữ mutable trong C/C++ chỉ áp dụng cho các đối tượng class. Nó cho phép một thành viên của một đối tượng để override (ghi đè). Đó là, một thành viên là mutable có thể được sửa đổi bởi một hàm thành viên const.

# 25. Atomic
* std::atomic được gọi là lock-free . Nghĩa là khi dùng atomic thì khỏi cần dùng lock để chia sẻ tài nguyên giữa các thread. Đáng tiếc là atomic cũng chỉ hỗ trợ một số type nhất định ( có thể check bằng atomic::is_lock_free() , và không đảm bảo hỗ trợ giống nhau ở các platform khác nhau, tốt nhất nên check.

# 26. Lock_guard

* std::lock_guard cho phép bạn dùng mutex trong một đoạn code, thay vì phải tự lock và unlock ( đôi khi quên unlock là chương trình đơ luôn) chỉ cần gọi std::lock_guard.
* Theo một số benmarch thì dùng lock_guard sẽ tốn ít CPU hơn dùng lock, unlock của mutex

# 27. std::future 

* std::future là một lớp template và đối tượng của nó lưu trữ giá trị tương lai. Thật vây, một đối tượng std::future lưu trữ bên trong một giá trị sẽ được gán trong tương lai và nó cũng cung cấp một cơ chế để truy cập giá trị đó, tức là sử dụng hàm thành viên get(). Nhưng nếu ai đó cố gắng truy cập giá trị này của tương lai thông qua hàm get() trước khi có sẵn, thì hàm get() sẽ chặn cho đến khi giá trị là khả dụng.

# 28. std::promise 
    
* std::promise cũng là một lớp template và đối tượng của nó hứa sẽ set một giá trị trong tương lai. Mỗi đối tượng std::promise có một đối tượng std::future được liên kết tới, đối tương mà sẽ cho ra giá trị khi nó được set bởi std::promise.

# 29. std :: pack_task

* std :: pack_task <> là một lớp template và đại diện cho task thực thi không đồng bộ. Nó bao gồm:

-  Một thực thể có thể gọi được. Đó có thể là hàm, hàm lambda hoặc đối tượng hàm.
- Một trạng thái chia sẻ lưu trữ giá trị được trả về hoặc ném ngoại lệ bằng cách gọi hàm callback.

# 30. vector

* std::vector cung cấp chức năng mảng động có khả năng tự xử lý việc quản lý bộ nhớ của chính nó. Điều này nghĩa là bạn có thể tạo ra những mảng có độ dài được thiết lập tại runtime (thời điểm chương trình chạy), mà không cần phải cấp phát và giải phóng bộ nhớ một cách rõ ràng/tường minh bằng toán tử new và delete. std::vector tồn tại trong header <vector>.
* Khi một biến vector nằm ngoài phạm vi đoạn comà chương trình đang chạy (goes out of scope), nó sẽ tự động giải phóng những phần bộ nhớ mà nó kiểm soát (nếu cần). Điều này không chỉ tiện dụng (bởi vì bạn không phải tự giải phóng bộ nhớ), mà nó còn giúp ngăn ngừa lỗi rò rỉ bộ nhớ (memory leaks)
* Không giống như mảng động được tích hợp sẵn của C++, cái mà không biết được độ dài của mảng mà nó đang trỏ tới là bao nhiêu, std::vectors tự theo dõi độ dài của chính nó. Chúng ta có thể lấy được độ dài của vector thông qua hàm size():

# 31. set

* Set là container lưu các phần tử duy nhất tuân theo 1 thứ tự đặc biệt. Giá trị của mỗi phần tử luôn là hằng số, (không thể modify được), chỉ có thể insert hoặc remove phần tử khỏi container set.
* Mỗi phần tử trong cùng một std::set là duy nhất (hay unique). Điều này có nghĩa rằng nếu bạn không thể lưu trữ hai phần tử có giá trị như nhau trong cùng một std::set.
* Tất cả các phần trử trong cùng một std::set phải thuộc cùng một kiểu dữ liệu.

# 32. Tại sao dùng con trỏ

- Cần để control thời gian tạo và hủy biến, ví dụ: out of scope nhưng ko huyr biến
- Cần khi allocate bộ nhớ, tránh tràn stack. 
- Dynamic allocation

# 33. Smart Pointer

- Smart pointer là 1 loại dữ liệu mới bổ sung thêm các khả năng regular pointer, kiểm tra truy xuất ngoài vùng được cấp phát, ... Để đạt được điều này, thiết kế C++ đã tạo ra các đối tượng để đóng gói các regular pointer. Để các đối tượng này hành xử như 1 regular pointer thật sự, các toán tử đặc trưng của pointer thông thường như *  và -> đều được override lại trong các đối tượng này. Nhờ vậy mà nó trông rất giống các regular pointer, và có thể sử dụng nó như là 1 regular pointer thật sự. Ngoài ra thì nó còn được định nghĩa để tự động xử lý các vấn đề liên quan đến quản lý bộ nhớ tự động.. nó cung cấp hàm destructor được tự động gọi đến khi đối tượng của class đó đi ra khỏi phạm vi khối lệnh chứa nó. Vậy, nếu chúng ta cấp phát vùng nhớ cho nó trong phần khởi tạo (constructor), vùng nhớ đó sẽ được đảm bảo giải phóng khi đối tượng smart pointer bị hủy.

- Cách mà các smart pointer trong C++ hoạt động để thực hiện tự động quản lý tài nguyên, đều dựa vào khái niệm quyền sở hữu tài nguyên.

- Trong C++ có 3 loại smart pointer chính là:

    - unique_ptr: đại diện cho quyền sở hữu duy nhất, nghĩa là tài nguyên mà unique_ptr quản lý chỉ có thể được sở hữu bởi duy nhất 1 đối tượng.
    - shared_ptr: đại diện cho quyền sở hữu chia sẻ, nghĩa là tài nguyên mà shared_ptr quản lý có thể được sở hữu bởi nhiều đối tượng.
    - weak_ptr: đại diện cho quyền sở hữu yếu, nghĩa là đối tượng nắm trong tay weak_ptr trỏ tới 1 tài nguyên chỉ có quyền được sử dụng tài nguyên đó, chứ không có quyền hủy đi tài nguyên.

- unique_ptr trong C++ đại diện cho quyền sở hữu duy nhất, nghĩa là tài nguyên mà unique_ptr trỏ tới chỉ được sở hữu bởi 1 đối tượng, và trên lý thuyết 1 tài nguyên chỉ được trỏ tới bởi duy nhất 1 unique_ptr. Do đó không thể thực hiện gán thông thường (bằng copy constructor hoặc toán tử copy assignment), phai sử dụng move constructor hoặc toán tử move assignment.
- shared_ptr sẽ đại diện cho quyền sở hữu chia sẻ. Nghĩa là tài nguyên mà shared_ptr trỏ tới là tài nguyên chia sẻ, có thể được sở hữu bởi nhiều đối tượng cùng 1 lúc. Nhờ shared_ptr mà có thể dễ dàng quản lý các tài nguyên được sử dụng bởi nhiều đối tượng 1 cách dễ dàng. Khi sử dụng shared_ptr với các loại tài nguyên này, hoàn toàn không còn cần phải quan tâm việc thu hồi nó.
    - No sử dụng cơ chế reference counting để đảm bảo khi không còn shared_ptr quản lý tài nguyên đó nữa thì tài nguyên sẽ bị thu hồi, và sử dụng biến atomic để bảo đảm thread-safe khi tài nguyên đó được sử dụng bởi các đối tượng nằm ở các thread khác nhau.

- weak_ptr đại diện cho quyền sở hữu yếu, nghĩa là đối tượng sở hữu tài nguyên bằng weak_ptr chỉ có quyền sử dụng chứ không có quyền thu hồi tài nguyên. Nói cách khác, cơ chế reference counting chỉ dựa vào số lượng shared_ptr đang trỏ tới tài nguyên, chứ không quan tâm tới tài nguyên đó đang được trỏ tới bởi bao nhiêu weak_ptr, dù đang có 5 weak_ptr đang trỏ tới tài nguyên đó, nhưng không còn shared_ptr nào trỏ tới nữa thì tài nguyên đó vẫn bị thu hồi.
    - weak_ptr cũng có 1 điểm yếu rất lớn khi sử dụng, mỗi lần sử dụng tài nguyên mà weak_ptr tham chiếu đến, cần phải thực hiện câu lệnh lock() để tạo ra 1 shared_ptr trỏ tới tài nguyên đó

# 34. struct vs class
- Thành viên class mặc định là private, của struct mặc định là public
- Kế thừa struct từ 1 class/struct, mặc định là public. Còn khi kế thừa 1 class, mặc đinh là private
- class có thể null nhưng struct thì ko
- Bộ nhớ struct được allocate trên stack, còn class là trên heap
- Class yêu cầu có hàm tạo hàm hủy, struct thì ko
- class hỗ trợ đa hình

# 35. Pointer vs reference
- con trỏ có thể ko cần giá trị khởi tạo, tham chiếu cần xác định giá trị ngay lúc khởi tạo
- con trỏ có thể trỏ đến null, tham chiếu thì ko
- không thể thay đổi tham chiếu đến 1 biến khác, Con trỏ có thể trỏ đến bất kỳ giá trị nào sau khi khai báo
- con trỏ có thể sử dụng vs các phép toán số học, tham chiếu thì ko