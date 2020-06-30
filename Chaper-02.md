# Chapter 02: Sử dụng những công cụ thiết yếu

## I. Các kỹ năng Bash Shell cơ bản

1. Linux Shell cung cấp môi trường để thực thi các câu lệnh một cách chính xác 

2. Có 3 loại câu lệnh có thể thực  thi trên bash shell là

  - Alias: là loại câu lệnh mà người dùng có thể định nghĩa  được. Cú pháp như sau: **alias newcommand ='oldcommand'**

  - Câu lệnh bên trong (internal command) là một phần của bash shell, chúng có sẵn khi shell được load lên và khi thực  thi chúng thì đọc từ ram luôn chứ không đọc từ ổ cứng nên rất nhanh vd: source, cd, fg etc. Để biết nó là câu lệnh internal thì dùng lệnh **type**
  
  - Câu lệnh bên ngoài (External commands) là những câu lệnh tồn tại như một file thực thi bên trong ổ cứng của máy nên chậm hơn so với IC, dùng biến **$Path** để liệt kê các thư mục mà shell sẽ quét tìm file thực thi câu lệnh, thư mục bạn đang ở trong khi thực hiện câu lệnh sẽ không được list ra do đó cần thực bổ xung ./ phía trước câu lệnh. Hầu hết các user đều dùng chung một biến $PATH chỉ trừ root
  
3. Điều hướng đầu vào/đầu ra

 Thông thường các lệnh được nhập từ đầu vào chuẩn (stdin) là bàn phím, sau khi xử lý được đưa ra màn hình monitor là đầu ra chuẩn (stdout) và báo lỗi chuẩn (stderr) tuy nhiên có những lệnh chạy trên nền linux chứ không từ phiên tẻminal hiện tại, do đó chúng không có monitor để gửi stdout và stderr, không có bàn phím để nhập vì vậy chúng ta cần điều hướng cho chúng 
 
**>** là toán tử chuyển hướng đầu ra còn **>>** là nối thêm đầu ra vào một tệp hiện có
**<** loà toán tử chuyển hướng đầu vào
**2>** là toán tử điều hướng báo lỗi chuẩn sang 
...

4. Sử dụng Pipes

pipe là ký hiệu **"|"**, Môt pipe được sử dụng để lấy đầu ra của một câu lệnh và dùng nó để làm đầu vào cho một câu lệnh khác. Ví dụ như ls | les thì danh sách đượhc ls liệu kê ra sẽ được sử  dụng làm đầu vào cho lệnh less kết quả là danh sách được list ra sẽ được biểu diễn theo từng trang 

5. Câu lệnh Lịch Sử

Mặc định thì Bash Shell sẽ giữ 1000 câu lệnh gần nhất mà người dùng gõ vào trong Ram, và khi đóng session thì tất cả thông tin về session như câu lệnh đã được thực thi sẽ được ghi vào file .bash_history và lưu trong thư mục home của người dùng đã mở session đó.Các cách để sử dụng history như sau:
  - lệnh **history** để list các câu lệnh đã được gõ
  - Ctr + R để tìm kiếm các câu lệnh đã từng gõ vào terminal
  - **!number** để thực thi câu lệnh trong lichh sử có số thứ tự là number
  - !sometext để thực hiện ngay lập tức câu lệnh cuối cùng 
  
 6. Bash Shell có khả nănghoàn thiện câu lệnh bằng cách sử dụng phím tab

## II. Sửa file với lệnh Vim

Dùng lệnh vim để sửa file,dùng phím **i** để thêm xoá sửa text, dùng **q!** để kết thúc sửa file mà không lưu lại những điều chỉnh, dùng lệnh **!wq** để kết thúc sửa file và lưu những chỉnh sửa. Ngoài ra còn một số câu lệnh khác trong ảng 2.4

## III. Tìm hiểu môi trường Shell

Môi trường Shell được tạo ra để đảm bảo mọi thứ hoạt động một cách chính xác, nó bao gồm các biến định nghĩa môi trường của người dùng 

 1. Tìm hiêu các biến:  
 
  - Môi trường Shell gồm nhiều biến, là những tên chứa giá trị có thể thay đổi, các biến được set cho mỗi trường cua mỗi user là khác nhau do nhu cầu của mỗi người dùng là khác nhau. Sử dụng lệnh **env** để xem qua một lượt các biến môi trường của một user
  Để định nghĩa biến môi trường thì người ta dùng name = value
  Người ta dùng lệnh **echo** để show giá trị biến
  
 2. Các tệp cấu hình môi trường 
 
 khi người dùng login vào hệ thống thì 4 loại file cấu hình môi trường được tạo ra 
 
 /etc/profile: là file chung được tất cả người dùng login vào hệ thống sử dụng
 /etc/bashrc: là file được xư lý khi một shell con được khởi động
 ~/.bash_profile: trong file này các biến shell login (là shell đầu tiên được mở cho người dùng sau khi người dùng login vào) của người dùng nhất định được định nghĩa
 ~/.bashrc : trong file này thì biến shell con (sau khi người dùn login vào họ được mở login shell, từ đó họ chạy script để tạo ra shell con) của người cụ thể dùng được định nghĩa
 
 3. Sử dụng /etc/motd and /etc/issue
  - những tin nhắn lưu trong /etc/motd có thể được show sau khi người dùng login thành công do đó nó thường được admin dùng để thông báo và lưu ý người dùng 
  - Các message trong /etc/issue được show cho người dùng sau khi họ login, bất kể có thành công hay không
  
  4. Sử dụng Trợ giúp có sẵn để biết cách sử dụng câu lệnh cho đúng 
  
  - Sử dụng --help: dùng sau câu lệnh để biết hướng dẫn sử dụng của câu lệnh đó nhanh nhất có thể 
  - Sử dụng man: cú pháp là **man command** để thể hiện cú pháp dòng lệnh, các tham số
  - Sử dụng info
