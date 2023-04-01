# Tạo UI với Reactstrap 
-   Reactstrap là một thư viện React cung cấp các thành phần giao diện được xây dựng trên Bootstrap 
    -   ``` jsx
        import { Col, Container, Row } from 'reactstrap';
        ```
    -   Container: là một thành phần dùng để tạo một container chứa các thành phần khác trên giao diện. Container thường được sử dụng để giới hạn độ rộng của các thành phần và giúp trang web trông đẹp hơn.

    -   Row: là một thành phần dùng để tạo một hàng chứa các cột trên giao diện. Row thường được sử dụng để căn chỉnh các cột và giúp trang web trông đẹp hơn.

    -   Col: là một thành phần dùng để tạo một cột trên giao diện. Col thường được sử dụng để chứa các thành phần khác như hình ảnh, nội dung, v.v... và giúp trang web trông đẹp hơn.
    -   ``` jsx
        import { Button, Form, FormGroup, Input, Label } from 'reactstrap';
        ```
    -   Button: là thành phần dùng để tạo các nút bấm trên giao diện, có thể tùy chỉnh các thuộc tính như màu sắc, kích thước, v.v...

    -   Form: là thành phần dùng để tạo các biểu mẫu trên giao diện, có thể chứa các thành phần Input và được tùy chỉnh theo ý muốn.

    -   FormGroup: là thành phần dùng để tạo các nhóm các thành phần Form trên giao diện, giúp căn chỉnh các thành phần Form với nhau.

    -   Input: là thành phần dùng để tạo các ô nhập liệu trên giao diện, có thể tạo các loại ô nhập liệu khác nhau như ô nhập văn bản, ô nhập email, ô nhập mật khẩu, v.v...

    -   Label: là thành phần dùng để tạo các nhãn trên giao diện, có thể được sử dụng để liên kết với các thành phần Input và giúp người dùng hiểu rõ hơn về các trường nhập liệu trên giao diện.

-   Ngoài ra để tạo ra một ô chọn từ danh sách các tùy chọn
dùng **Select** trong **react-select**
    -   ```jsx
        const opptions = [
            {value: 1, label: 'Hai'},
            {value: 2, label: 'Minh'},
            {value: 3, label: 'Dung'},
            {value: 4, label: 'Nhat'},
        ];
        <Select
        options={options}
        />
      ```
