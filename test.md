# CVE-2022-21662
- *Version ảnh hưởng*: <5.8.3
- *Mô tả*: lỗi này nằm trong core wordpress, cần quyền thấp(author)

# Chi tiết kỹ thuật
### 1. _truncate_post_slug
- lỗi xảy ra ở hàm `_truncate_post_slug`,khi giá trị slug >length  hàm `urldecode` có chức năng giải mã các url đã bị encode, điều này dẫn tới có thể bypass được cơ chế fillter của wp.
- Ví dụ, nếu nhập `<script>alert(1)</script>` vào giá trị biến thì đầu ra sẽ bị mã hóa thành `alert-1`. Nhưng nếu nhập bằng giá trị `%3Cscript%3E` thì giá trị vẫn được dữ nguyên.
 ![image](https://user-images.githubusercontent.com/22276712/157584963-d402d828-d55e-48c1-85f1-ce69c1ba1e6f.png)
- Ngoài ra hàm `utf8_uri_encode` chỉ có tác dụng mã hóa các đoạn `Unicode`. Ví dụ chuỗi `utf8_uri_encode("<script>alert(1)</script>á")` sẽ thành `<script>alert(1)</script>%c3%a1%3C`
### 2. tìm kiếm hàm gọi  _truncate_post_slug

- Hàm  `_truncate_post_slug` sẽ được gọi tại hàm `wp_unique_post_slug ` 
- ![image](https://user-images.githubusercontent.com/22276712/157613498-7cb8e63c-5d30-4cf4-a9c8-2f33e12e9212.png)
- hàm này được gọi khi có 2 slug trùng nhau
- ![image](https://user-images.githubusercontent.com/22276712/157614478-8bbe06b1-8963-4746-91a2-4c4ef05eb0f7.png)
### Step
1. Đăng nhập với quyền author
2. Tạo POC `%22%3E%3Cscript%3Ealert%28origin%29%3C%2Fscript%3Eaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa`
3. Edit slug của bài viết 1 và bài viết 2 với POC ở bước 2.
4.![image](https://user-images.githubusercontent.com/22276712/157616526-bdceec12-5ba9-4ea5-a1c3-888eaa45ef6a.png)
5. Tải lại trang, XSS sẽ được kích hoạt

### Patch
![image](https://user-images.githubusercontent.com/22276712/157617979-41294182-36a8-4ffe-b88b-c6c559d8f028.png)
