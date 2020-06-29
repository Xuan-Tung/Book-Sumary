# Chapter 02: Sử dụng những công cụ thiết yếu

## I. Các kỹ năng Bash Shell cơ bản

1. Linux Shell cung cấp môi trường để thực thi các câu lệnh một cách chính xác 

2. Có 3 loại câu lệnh có thể thực  thi trên bash shell là

  - Alias: là loại câu lệnh mà người dùng có thể định nghĩa  được. Cú pháp như sau: **alias newcommand ='oldcommand'**

  - Câu lệnh bên trong (internal command) là một phần của bash shell, chúng có sẵn khi shell được load lên và khi thực  thi chúng thì đọc từ ram luôn chứ không đọc từ ổ cứng nên rất nhanh vd: source, cd, fg etc. Để biết nó là câu lệnh internal thì dùng lệnh **type**
  
  - Câu lệnh bên ngoài (External commands) là những câu lệnh tồn tại như một file thực thi bên trong ổ cứng của máy nên chậm hơn so với IC, dùng biến **$Path** để liệt kê các thư mục mà shell sẽ quét tìm file thực thi câu lệnh, thư mục bạn đang ở trong khi thực hiện câu lệnh sẽ không được list ra do đó cần thực bổ xung ./ phía trước câu lệnh. Hầu hết các user đều dùng chung một biến $PATH chỉ trừ root
  
 
  
  
  
  
