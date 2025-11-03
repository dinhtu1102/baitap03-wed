# Nguyễn Đình Tú k225480106067 lớp k58.ktp
# baitap03-wed
bai tap 03
Bài tập 3   : môn Phát triển ứng dụng trên nền web
Giảng viên  : Đỗ Duy Cốp
Lớp học phần: 58KTPM
Ngày giao   : 2025-10-24 13:50
Hạn nộp     : 2025-11-05 00:00
--------------------------------------------------
Yêu cầu     : LẬP TRÌNH ỨNG DỤNG WEB trên nền linux
1. Cài đặt môi trường linux: SV chọn 1 trong các phương án
 - enable wsl: cài đặt docker desktop
 - enable wsl: cài đặt ubuntu
 - sử dụng Hyper-V: cài đặt ubuntu
 - sử dụng VMware : cài đặt ubuntu
 - sử dụng Virtual Box: cài đặt ubuntu
2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
   mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)
4. Lập trình web frontend+backend:
 SV chọn 1 trong các web sau:
 4.1 Web thương mại điện tử
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - Có tính năng liệt kê các sản phẩm bán chạy ra trang chủ
 - Có tính năng liệt kê các nhóm sản phẩm
 - Có tính năng liệt kê sản phẩm theo nhóm
 - Có tính năng tìm kiếm sản phẩm
 - Có tính năng chọn sản phẩm (đưa sản phẩm vào giỏ hàng, thay đổi số lượng sản phẩm trong giỏ, cập nhật tổng tiền)
 - Có tính năng đặt hàng, nhập thông tin giao hàng => được 1 đơn hàng.
 - Có tính năng dành cho admin: Thống kê xem có bao nhiêu đơn hàng, call để xác nhận và cập nhật thông tin đơn hàng. chuyển cho bộ phận đóng gói, gửi bưu điện, cập nhật mã COD, tình trạng giao hàng, huỷ hàng,...
 - Có tính năng dành cho admin: biểu đồ thống kê số lượng mặt hàng bán được trong từng ngày. (sử dụng grafana)
 - backend: sử dụng nodered xử lý request gửi lên từ javascript, phản hồi về json.
 4.2 Web IOT: Giám sát dữ liệu IOT.
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - hiển thị giá trị mới nhất của các thông số đang giám sát, khi click vào thì hiển thị đồ thị lịch sử quá trình thay đổi (gọi grafana iframe để hiển thị)
 - backend: Sử dụng nodered để đọc dữ liệu từ các cảm biến (có thể dùng api online để lấy dữ liệu theo giời gian thực), 
   nodered sẽ lưu dữ liệu mới nhất (dạng update) vào cơ sở dữ liệu mariadb (sử dụng phpmyadmin để tạp table và quản trị lần đầu)
   nodered sẽ lưu dữ liệu (insert) vào influxdb để lưu giá trị lịch sử, để cho grafana dùng để hiển thị biểu đồ.
5. Nginx làm web-server
 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)

Yêu cầu sinh viên lưu code trên github
có file readme.md có hình ảnh + text: ghi lại nhật ký quá trình làm bài.

CÁCH ĐÁNH GIÁ:
1. Cài đặt được môi trường: 1đ
2. Cài đặt được các docker container với cấu hình phù hợp: 1đ
3. Web chạy được, giao diện phù hợp, chạy trên web sever nginx: 2đ
4. nodered api trả về json, test được: 2đ
5. front-end có js gọi được api nodered, nhận về json, hiển thị được kết quả từ json này. 2đ
6. Bài làm có dấu ấn, giải thích rõ ràng, hiểu vấn đề: 2đ

-------- BÀI LÀM-----------

Yêu cầu     : LẬP TRÌNH ỨNG DỤNG WEB trên nền linux
1. Cài đặt môi trường linux: SV chọn 1 trong các phương án
mới đầu kích hoạt WSL và cài Ubuntu bằng lệnh này trong CMD : wsl --install
Kiểm tra trong Command Prompt
      wsl -l -v
Nếu không thấy dòng như:
      Ubuntu-22.04    Running    2
thì cần phải cài :
      wsl --install -d Ubuntu-22.04
Kiểm tra Docker hoạt động trong WSL
      docker --version
      docker run hello-world
Nếu thấy:
     Hello from Docker!
→ Docker Desktop đã hoạt động hoàn toàn.
 - enable wsl: cài đặt docker desktop
   tìm đường dẫn này để tải desktop Download for Windows – AMD64
 https://www.docker.com/products/docker-desktop/
 sau khi cài đặt destop thì nó có giao diện này:
 <img width="1255" height="962" alt="{FF05BC6C-8D57-4B84-A2E4-D32C8B3D0CA6}" src="https://github.com/user-attachments/assets/217bfae6-561c-4baa-909c-dd83ff85e903" />
cho thấy Docker Desktop của bạn đã bật WSL integration với Ubuntu-22.04, và Engine đang chạy 

2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
   → Docker Desktop đã hoạt động hoàn toàn.
 - enable wsl: cài đặt docker desktop
   tìm đường dẫn này để tải desktop Download for Windows – AMD64
 https://www.docker.com/products/docker-desktop/
 <img width="1255" height="962" alt="{FF05BC6C-8D57-4B84-A2E4-D32C8B3D0CA6}" src="https://github.com/user-attachments/assets/217bfae6-561c-4baa-909c-dd83ff85e903" />
 sau khi cài về cần đăng nhập và được giao diện như này
  sau khi cài được ubuntu thiwf nó
<img width="1580" height="888" alt="{E8937925-BBC3-4BA7-97F2-4D34CDC4276D}" src="https://github.com/user-attachments/assets/0e905cc8-c8c7-479b-ae7e-0aa315c41628" />
nếu chưua cài ubuntu thì nó sẽ ko có trong dosktop 
cho thấy Docker Desktop của bạn đã bật WSL integration với Ubuntu-22.04, và Engine đang chạy 

3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
<img width="976" height="223" alt="{44329A0C-2E8D-40C1-BF52-BDF111CBE456}" src="https://github.com/user-attachments/assets/e5433db9-a4fd-49c6-a218-280eab6570d7" />
tạo file:
<img width="1007" height="66" alt="{2E57125B-E9BC-454F-A024-C731BBB610C0}" src="https://github.com/user-attachments/assets/628fe1f3-6c46-452f-b5d7-9786ed9103d9" />
   mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)
   <img width="583" height="799" alt="{D31C8637-13FC-4912-851F-AD901D04D7B0}" src="https://github.com/user-attachments/assets/5f7e9fc1-fffd-4d69-8f36-634223caae9d" />
   <img width="962" height="386" alt="{82A25E31-19A6-4B2D-B4FE-1AFC4C90B113}" src="https://github.com/user-attachments/assets/f8850e52-f197-4d1c-b75d-8c3b16ad08d0" />
 <img width="1099" height="278" alt="{009EE016-5F8A-41AE-ADA7-7BB9430F676F}" src="https://github.com/user-attachments/assets/c589c348-1a93-4126-acb9-ca87475fe7ff" />
4. Lập trình web frontend+backend:
 SV chọn 1 trong các web sau:
 4.2 Web IOT: Giám sát dữ liệu IOT.
 Tạo bảng MariaDB (qua phpMyAdmin hoặc CLI)
   ![Uploading {69A6D222-05E1-48B5-A41D-247AFCE7B44C}.png…]()
 Node-RED — flow & API (các bước và function code)
    Menu → Manage Palette → Install:
    ![Uploading {21668756-B970-4F28-880F-8C4B48759375}.png…]()
    node-red-node-mysql
    ![Uploading {21ED8BF4-6549-4280-8CB5-C926E32F37AE}.png…]()
   Mở database iotdb
   Tạo bảng users và sensors
   CREATE TABLE IF NOT EXISTS users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(100) NOT NULL UNIQUE,
  password_hash CHAR(64) NOT NULL, -- SHA-256 hex
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS sensors (
  id INT AUTO_INCREMENT PRIMARY KEY,
  sensor_key VARCHAR(100) UNIQUE, -- ví dụ 'temp_1'
  sensor_name VARCHAR(100),
  latest_value DOUBLE,
  updated_at DATETIME
);
![Uploading {3BD6F745-C52E-4082-ADA3-C7C3CB22729A}.png…]()

node-red-contrib-influxdb (hoặc node-red-node-influxdb tùy version)
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - hiển thị giá trị mới nhất của các thông số đang giám sát, khi click vào thì hiển thị đồ thị lịch sử quá trình thay đổi (gọi grafana iframe để hiển thị)
 - backend: Sử dụng nodered để đọc dữ liệu từ các cảm biến (có thể dùng api online để lấy dữ liệu theo giời gian thực), 
   nodered sẽ lưu dữ liệu mới nhất (dạng update) vào cơ sở dữ liệu mariadb (sử dụng phpmyadmin để tạp table và quản trị lần đầu)
   nodered sẽ lưu dữ liệu (insert) vào influxdb để lưu giá trị lịch sử, để cho grafana dùng để hiển thị biểu đồ.
5. Nginx làm web-server
 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)

Yêu cầu sinh viên lưu code trên github
có file readme.md có hình ảnh + text: ghi lại nhật ký quá trình làm bài.

CÁCH ĐÁNH GIÁ:
1. Cài đặt được môi trường: 1đ
2. Cài đặt được các docker container với cấu hình phù hợp: 1đ
3. Web chạy được, giao diện phù hợp, chạy trên web sever nginx: 2đ
4. nodered api trả về json, test được: 2đ
5. front-end có js gọi được api nodered, nhận về json, hiển thị được kết quả từ json này. 2đ
6. Bài làm có dấu ấn, giải thích rõ ràng, hiểu vấn đề: 2đ
