# Baitap-1
A. Đăng ký tên miền xịn cho cá nhân:
1.Đăng ký domain xịn (có thể dùng của mắt bão, tên miền *.id.vn đang miễn phí cho mọi công dân việt nam <= 23 tuổi, *.io.vn : giá 30k vnđ/năm)
2.Đăng ký tài khoản cloudflare
3.Thêm domain đã đăng ký vào trong cloudflare : Nhận 2 dòng namespace
4.Nhập 2 dòng namespace của cloudflare vào trong trang quản lý DNS record của tên miền đăng ký (vd trên mắt bão)

1. Domain : Thao04.io.vn
2. <img width="1290" height="892" alt="image" src="https://github.com/user-attachments/assets/b94e23cc-5a49-43cf-98da-c4043e8b504a" />

B. Cài đặt Ubuntu + Docker
1.Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
 - Sử dụng một trong các công cụ để giả lập: HyperV (có sẵn của windows), VirutualBox (Miễn phí), VM_Ware (bản quyền)
 - Download file iso để cài đặt.

  <img width="958" height="927" alt="image" src="https://github.com/user-attachments/assets/361905f1-cd38-4202-abdc-aa1cfd638f86" />

 - Cấu hình mạng trong Ubuntu (và công cụ giả lập) để cho phép truy cập SSH vào Ubuntu từ cmd của windows
Thiết lập SSH trên Ubuntu
<img width="1260" height="884" alt="image" src="https://github.com/user-attachments/assets/8a0f55ad-7bcf-4383-a62f-55983c845826" />

Cấu hình để Windows "nhìn thấy" Ubuntu
<img width="1169" height="755" alt="image" src="https://github.com/user-attachments/assets/cb13ef41-3328-4805-8bbb-7bf8e526c2c0" />

2.Tìm hiểu các lệnh cơ bản của ubuntu
Các lệnh cần tìm hiểu:

-Liệt kê các file trong thư mục: ls
-Tạo thư mục: mkdir nameFolder
-Chuyển thư mục làm việc: cd path

<img width="1111" height="182" alt="image" src="https://github.com/user-attachments/assets/1dae9501-3840-4f48-b2c2-fd1f962f508a" />

-Copy file: cp file_nguồn path/file_đích

<img width="805" height="128" alt="image" src="https://github.com/user-attachments/assets/69692e39-9dc9-49f8-8f1a-bc1c3f12dca8" />

-Thay đổi quyền thao tác file: sudo chmod xxx filename

<img width="783" height="271" alt="image" src="https://github.com/user-attachments/assets/54615de2-9c81-4816-a1cc-af4b79ffa88c" />

-Edit file: sudo nano tenfile
  .CTRL+o : lưu nội dung sau khi edit
  .CTRL+x : thoát edit file

  <img width="1445" height="759" alt="image" src="https://github.com/user-attachments/assets/544ad340-2beb-42d0-8535-38607fcdc4c7" />

-Xem ip của máy ubuntu: ip -4 addr
ip của máy ảo ubuntu: 192.168.1.26/24

<img width="1241" height="189" alt="image" src="https://github.com/user-attachments/assets/b545b3c1-48fb-4637-821c-09c2a7802f7f" />

3.Cài đặt docker cho Ubuntu
4.Kiểm tra phiên bản docker vừa cài đặt, kiểm tra phiên bản của docker compose

<img width="647" height="135" alt="image" src="https://github.com/user-attachments/assets/f0868e18-6db1-4336-9a53-0bbac1447e5f" />

5.Cấu hình để docker chạy mà không cần tiền tố sudo

dùng câu lệnh :  sudo usermod -aG docker $USER

                 newgrp docker
                 
6.Tìm hiểu tập lệnh của docker và docker compose

   1. Nhóm lệnh Docker (Quản lý Container lẻ)
      
Dùng khi bạn muốn chạy nhanh một ứng dụng hoặc kiểm tra hệ thống.

docker ps: Liệt kê các container đang chạy. (Thêm -a để xem cả các cái đã tắt).

docker images: Xem danh sách các Image (bản thiết kế) đang có trong máy.

docker run [tên_image]: Tải và chạy một container từ image.

Ví dụ: docker run -d -p 80:80 nginx (Chạy web server Nginx ngầm và mở cổng 80).

docker stop [ID_hoặc_tên]: Dừng một container đang chạy.

docker rm [ID_hoặc_tên]: Xóa hẳn một container.

docker exec -it [ID] bash: "Chui" vào bên trong container để gõ lệnh trực tiếp (rất hay dùng để debug).

   2. Nhóm lệnh Docker Compose (Quản lý đa dịch vụ)
      
Đây là công cụ cực mạnh cho đồ án. Thay vì gõ từng lệnh docker run, bạn viết tất cả vào file docker-compose.yml rồi chỉ cần 1 lệnh để khởi động toàn bộ (ví dụ: chạy cùng lúc Node-RED, Database, và Backend).

docker compose up -d: Khởi động tất cả các dịch vụ được định nghĩa trong file cấu hình (chạy ngầm).

docker compose down: Dừng và xóa toàn bộ các container, mạng lưới đã tạo từ file compose (giúp máy sạch sẽ).

docker compose logs -f: Xem nhật ký hoạt động của các dịch vụ (để biết tại sao code bị lỗi).

docker compose restart: Khởi động lại các dịch vụ.
7.Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)
