# Nguyễn Đình Tú k225480106067 lớp k58.ktp

# baitap03-wed

- bai tap 03

- Bài tập 3   : môn Phát triển ứng dụng trên nền web

- Giảng viên  : Đỗ Duy Cốp

- Lớp học phần: 58KTP

- Ngày giao   : 2025-10-24 13:50

- Hạn nộp     : 2025-11-06 23:59

--------------------------------------------------

Yêu cầu     : LẬP TRÌNH ỨNG DỤNG WEB trên nền linux

# 1. Cài đặt môi trường linux: SV chọn 1 trong các phương án


Mới đầu kích hoạt WSL và cài Ubuntu bằng lệnh này trong CMD :

      wsl --install

Kiểm tra trong Command Prompt
     
      wsl -l -v
 
Nếu không thấy dòng như:
    
      Ubuntu-22.04    Running    2
  
Thì cần phải cài :
    
      wsl --install -d Ubuntu-22.04
 
 Kiểm tra Docker hoạt động trong WSL
     
      docker --version
     
      docker run hello-world

 Nếu thấy:
    
      Hello from Docker!
    
→ Docker Desktop đã hoạt động hoàn toàn.

# 2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)

 → Docker Desktop đã hoạt động hoàn toàn.

 - enable wsl: cài đặt docker desktop
 
 - Tìm đường dẫn này để tải desktop Download for Windows – AMD64
   
 https://www.docker.com/products/docker-desktop/
 
 <img width="1255" height="962" alt="{FF05BC6C-8D57-4B84-A2E4-D32C8B3D0CA6}" src="https://github.com/user-attachments/assets/217bfae6-561c-4baa-909c-dd83ff85e903" />

 - Sau khi cài về cần đăng nhập và được giao diện như này
  
 - Sau khi cài được ubuntu thiwf nó

<img width="1580" height="888" alt="{E8937925-BBC3-4BA7-97F2-4D34CDC4276D}" src="https://github.com/user-attachments/assets/0e905cc8-c8c7-479b-ae7e-0aa315c41628" />

 - Nếu chưua cài ubuntu thì nó sẽ ko có trong dosktop 
 
 => Cho thấy Docker Desktop của bạn đã bật WSL integration với Ubuntu-22.04, và Engine đang chạy 

# 3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
 
   mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)
 
 - Tạo folder với cấu trúc 
 
   <img width="376" height="279" alt="image" src="https://github.com/user-attachments/assets/8ec11520-2703-465f-840b-770d99b51ded" />
 
 - Bắt đầu cài đặt các docker container:
 
 <img width="1099" height="278" alt="image" src="https://github.com/user-attachments/assets/57dbb2fe-f6ff-439d-ab3b-590c44c77a42" />

 - Terminal chạy và cài đặt containers
 
   <img width="1137" height="922" alt="image" src="https://github.com/user-attachments/assets/aa282e49-9b2b-4d10-a94e-872224964867" />

 => Kết quả trả về dockers
 
   <img width="1597" height="926" alt="image" src="https://github.com/user-attachments/assets/2f4d0f7f-2ec1-48c7-9602-47b37c7cea99" />

# 4. Lập trình web frontend+backend:

 SV chọn 1 trong các web sau:

 4.2 Web IOT: Giám sát dữ liệu IOT.

 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session

   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.

   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.

 - hiển thị giá trị mới nhất của các thông số đang giám sát, khi click vào thì hiển thị đồ thị lịch sử quá trình thay đổi (gọi grafana iframe để hiển thị)

 - backend: Sử dụng nodered để đọc dữ liệu từ các cảm biến (có thể dùng api online để lấy dữ liệu theo giời gian thực), 

   nodered sẽ lưu dữ liệu mới nhất (dạng update) vào cơ sở dữ liệu mariadb (sử dụng phpmyadmin để tạp table và quản trị lần đầu)

    nodered sẽ lưu dữ liệu (insert) vào influxdb để lưu giá trị lịch sử, để cho grafana dùng để hiển thị biểu đồ.

# Bắt đầu tạo schema MariaDB (dùng phpMyAdmin)
   - Đăng nhập phpMyAdmin 

      <img width="1911" height="1080" alt="{B0B21261-13BD-4427-BE3E-B79594FC3E58}" src="https://github.com/user-attachments/assets/0ed2c01e-5a8a-4df2-8abb-59f15f33f8ff" />
     
   - chọn database tu → chạy SQL:
   
   - THÊM BẢNG USERS VÀO DATABASE tu
  
   <img width="1863" height="750" alt="image" src="https://github.com/user-attachments/assets/d5b30ad5-7602-46e4-8399-4b1071a833ed" />
  
   - Kết quả trả về 
  
  <img width="1867" height="363" alt="image" src="https://github.com/user-attachments/assets/857ae885-c50c-47c5-b7ef-de84247a0a9b" />
  
   - Chèn thông tin vào bảng

      <img width="1868" height="382" alt="image" src="https://github.com/user-attachments/assets/207479b2-d64f-47ca-81bf-141e5de09668" />
  
   - kết quả sau khi thực hiện

      <img width="1865" height="351" alt="image" src="https://github.com/user-attachments/assets/43e9a14c-2c06-47e6-ba2c-8eed6df97059" />
   
   - Kiểm tra kết quả
   
     <img width="925" height="267" alt="image" src="https://github.com/user-attachments/assets/79c6485a-31c1-47c4-8064-9a1b16d99704" />
 
   - Đăng nhập nodered

   - Flow nodered login
   
     <img width="1859" height="925" alt="image" src="https://github.com/user-attachments/assets/66de21d2-ef53-48c5-86ab-1fec9b66ea25" />

   - From đăng nhập

      <img width="1864" height="967" alt="image" src="https://github.com/user-attachments/assets/d32a546e-e9bf-458d-8193-dd6a8370cb8c" />
 
   Bảng lưu dữ liệu mới nhất cho sơ đồ 

  <img width="1913" height="738" alt="image" src="https://github.com/user-attachments/assets/abc11e03-464f-4352-9d00-893201253a65" />

  - kết quả đạt dược
  
     <img width="1917" height="324" alt="image" src="https://github.com/user-attachments/assets/9b2187d5-2420-4b74-ae7c-5ba26c952ba2" />

  - Biểu đồ giám sát iot

    <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/33c63cfd-5623-4e20-aad4-d5269aa3c054" />

  - Nodered tổng kết

    <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2f1ff238-9c0b-4699-982a-274b7d81c62b" />

  - Bảng lưu giá trị từ cảm biến

    <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4db558a1-df4c-4441-934c-67fc52d03d48" />

  - ĐƯỜNG DẪN NODEPAD CẤU HÌNH NGHINX ĐỂ CHẠY WEBSITE

    <img width="939" height="582" alt="image" src="https://github.com/user-attachments/assets/ce50cd60-33de-4c99-be10-2b4dfee11096" />

  - cấu hình api cho bài toán

    <img width="1332" height="1026" alt="{B642DA0A-68CE-4A49-839F-36A0E630B303}" src="https://github.com/user-attachments/assets/49321c5f-1c78-44ee-bfaf-5b83a82ae6ea" />

  - SỬA SERVER NAME TRONG NGINX.CONF

    <img width="1151" height="407" alt="image" src="https://github.com/user-attachments/assets/b3b612b9-4ec7-4df7-92bc-704019569420" />

  - Index.html

    <img width="1920" height="1080" alt="{B3C9D06C-E62D-4BFC-AB09-76427E1D8240}" src="https://github.com/user-attachments/assets/b728afab-a744-43d2-813a-da47ba41609b" />

  - Docker-compose.yml
    
    <img width="1920" height="1080" alt="{809A4732-3C81-4D80-828A-C21162061E8A}" src="https://github.com/user-attachments/assets/80ce7808-055f-49a5-b7e1-dbff751ebdf3" />
    
  - Nginx.conf

   <img width="1920" height="1080" alt="{28FB696E-5D1C-4954-8EAF-29C1BA1ED855}" src="https://github.com/user-attachments/assets/0b02bc96-b862-4543-afbf-71cea23741a3" />

=> kết quả cuối cùng đạt được

   <img width="1920" height="1080" alt="{811C52D6-C8AC-40E4-A0AC-A15C5A091B07}" src="https://github.com/user-attachments/assets/a07a5f32-da44-4807-96bd-b59f46c7ecb3" />

# 5. Nginx làm web-server
 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
 - http://nguyendinhtu.com:8081/

  <img width="1920" height="1080" alt="{F02D4115-E4CA-42DE-BAEE-07DB07EA1052}" src="https://github.com/user-attachments/assets/86f59b87-9aac-4ae0-8681-b5eaa1c2d40f" />

 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
 - http://nguyendinhtu:1880/

   <img width="1920" height="1080" alt="{6B7B03A3-58A4-4BDC-A4B1-5BAA24017D49}" src="https://github.com/user-attachments/assets/33b8c53d-9f37-4fba-be65-5fc3252153fb" />

 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)
 - http://nguyendinhtu.com:3001/grafana/login
 
   <img width="1920" height="1080" alt="{83B7A4DB-AE15-4EDA-B7CB-5477DE86765F}" src="https://github.com/user-attachments/assets/1f14e081-74f7-4745-8923-b984c15b3f92" />

Yêu cầu sinh viên lưu code trên github
có file readme.md có hình ảnh + text: ghi lại nhật ký quá trình làm bài.

CÁCH ĐÁNH GIÁ:
1. Cài đặt được môi trường: 1đ
2. Cài đặt được các docker container với cấu hình phù hợp: 1đ
3. Web chạy được, giao diện phù hợp, chạy trên web sever nginx: 2đ
4. nodered api trả về json, test được: 2đ
5. front-end có js gọi được api nodered, nhận về json, hiển thị được kết quả từ json này. 2đ
6. Bài làm có dấu ấn, giải thích rõ ràng, hiểu vấn đề: 2đ


