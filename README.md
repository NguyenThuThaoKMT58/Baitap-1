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

. docker ps: Liệt kê các container đang chạy. (Thêm -a để xem cả các cái đã tắt).

. docker images: Xem danh sách các Image (bản thiết kế) đang có trong máy.

. docker run [tên_image]: Tải và chạy một container từ image.

      Ví dụ: docker run -d -p 80:80 nginx (Chạy web server Nginx ngầm và mở cổng 80).

. docker stop [ID_hoặc_tên]: Dừng một container đang chạy.

. docker rm [ID_hoặc_tên]: Xóa hẳn một container.

. docker exec -it [ID] bash: "Chui" vào bên trong container để gõ lệnh trực tiếp (rất hay dùng để debug).

   2. Nhóm lệnh Docker Compose (Quản lý đa dịch vụ)
      
Đây là công cụ cực mạnh cho đồ án. Thay vì gõ từng lệnh docker run, bạn viết tất cả vào file docker-compose.yml rồi chỉ cần 1 lệnh để khởi động toàn bộ (ví dụ: chạy cùng lúc Node-RED, Database, và Backend).

. docker compose up -d: Khởi động tất cả các dịch vụ được định nghĩa trong file cấu hình (chạy ngầm).

. docker compose down: Dừng và xóa toàn bộ các container, mạng lưới đã tạo từ file compose (giúp máy sạch sẽ).

. docker compose logs -f: Xem nhật ký hoạt động của các dịch vụ (để biết tại sao code bị lỗi).

. docker compose restart: Khởi động lại các dịch vụ.

7.Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)

<img width="670" height="277" alt="image" src="https://github.com/user-attachments/assets/7b1dd4d3-dca7-4b77-8b71-90676a8112df" />

C. Cấu hình docker compose:

1.Tạo thư mục: ~/myapp

2.Chuyển vào trong thư mục ~/myapp

3.Tạo thư mục: ./myweb

4.Tạo file ./myweb/index.html (với nội dung là thông tin cá nhân của em)

5.Tạo file docker-compose.yml để nó sẽ có các dịch vụ sau:

   . Khai báo sử dụng nodered/node-red, cổng 1880, dữ liệu nằm tại thư mục ./nodered
   
   . Khai báo sử dụng nginx, cổng 80, cấu hình trong file ./nginx/nginx.conf
   
   . Mount thư mục ./myweb thành thư mục /myweb trong nginx
   
   . Mount file ./nginx/nginx.conf vào file /etc/nginx/nginx.conf trong nginx
   
6.Edit file ./nginx/nginx.conf để:

   . Cấu hình web server cổng 80
   
   . server_name là sub-domain (sub-domain tuỳ ý của em)
   
   . location / trỏ tới root là thư mục /myweb
   
   . location /api dùng proxy_pass trỏ tới 1 (hoặc nhiều) node http_in của nodered
   
7.Edit file ./nodered/settings.js để nodered bắt buộc đăng nhập

  Chạy docker-compose lần đầu để Node-RED tự sinh file cấu hình trong thư mục ./nodered, sau đó mới tiến hành sửa settings.js và restart lại container

-----

Đây là phần tạo và chuyển vào thư mục ~/myapp và tạo thư mục ./myweb, file ./myweb/index.html (với nội dung là thông tin cá nhân của em)

<img width="1311" height="536" alt="image" src="https://github.com/user-attachments/assets/02b97109-a723-4ab2-b371-9b0498d5fe1c" />


. tạo file cấu hình để Nginx biết cách trỏ về web cá nhân và Node-RED:

<img width="936" height="584" alt="image" src="https://github.com/user-attachments/assets/94784c70-1753-4db8-9f0b-fd496f8cbd14" />

. Tạo file Docker Compose 

File này sẽ "kết nối" Node-RED và Nginx lại với nhau:

<img width="821" height="494" alt="image" src="https://github.com/user-attachments/assets/1be01bca-0bc7-43d2-80cd-482dab81033a" />

. Giao diện Web: Truy cập http://192.168.1.26-> Hiện tên Nguyễn Thu Thảo.

<img width="919" height="771" alt="image" src="https://github.com/user-attachments/assets/ffd00e6c-1d0a-4f92-bf56-5c3dfb2a13a3" />

 . location /api dùng proxy_pass trỏ tới 1 (hoặc nhiều) node http_in của nodered

 <img width="931" height="764" alt="image" src="https://github.com/user-attachments/assets/f06c764b-81bd-4744-b615-160388653b44" />

Bước 1: Khởi tạo dữ liệu (Chạy lần đầu) 

     docker compose up -d

Bước 2: Chỉnh sửa file settings.js

     sudo nano ./nodered/settings.js

-Thao tác trong trình soạn thảo:

Nhấn phím Ctrl + W, nhập từ khóa adminAuth rồi nhấn Enter.

Sẽ thấy một khối mã bị khóa bởi các dấu gạch chéo //. Hãy xóa các dấu // đó đi
     
<img width="1026" height="732" alt="image" src="https://github.com/user-attachments/assets/c10f7bd6-0007-43fb-a2e2-ff0275210de0" />

Bước 3: Khởi động lại Container

Để Node-RED nhận cấu hình bảo mật mới, cần khởi động lại dịch vụ:

    docker compose restart nodered

. Quản trị Node-RED: Truy cập http://192.168.1.26:1880 -> Phải hiện bảng Login.

<img width="947" height="929" alt="image" src="https://github.com/user-attachments/assets/6e6d74c6-fbf2-452f-ba6c-b297fc633577" />

D. (Bonus - không bắt buộc)

1.tạo thư mục ./myapi

    mkdir -p ~/myapp/myapi

2.tạo file ./myapi/app.py sử dụng Python + Flask để làm gì đó funny

<img width="915" height="526" alt="image" src="https://github.com/user-attachments/assets/b4182e80-0e6d-4f40-af41-031a69a52554" />

3.tạo file ./myapi/requirements.txt chứa các thư viện mà app.py sử dụng (theo như app.py ví dụ thì requirements.txt chỉ cần có nội dung: flask)

     echo "flask" > ./myapi/requirements.txt
     
4.tạo file ./myapi/Dockerfile để khai báo sử dụng Python 3.9 slim

  -Sử dụng phiên bản Python nhẹ (alpine) để giảm dung lượng image
 FROM python:3.9-slim

 - Thiết lập thư mục làm việc bên trong container
 WORKDIR /app

 - Sao chép file requirements vào và cài đặt thư viện
 COPY requirements.txt .
 RUN pip install --no-cache-dir -r requirements.txt

 - Sao chép toàn bộ mã nguồn vào container
 COPY . .

 - Thông báo container sẽ chạy ở cổng 9630
 EXPOSE 9630

 - Lệnh khởi chạy ứng dụng
 CMD ["python", "app.py"]

        cat <<EOF > ./myapi/Dockerfile
        FROM python:3.9-slim
        WORKDIR /app
        COPY requirements.txt .
        RUN pip install --no-cache-dir -r requirements.txt
        COPY . .
        EXPOSE 9630
        CMD ["python", "app.py"]
        EOF
 
5.Sửa đổi docker-compose để sử dụng myapp (xem phần tham khảo ở dưới)

<img width="816" height="603" alt="image" src="https://github.com/user-attachments/assets/fbd26237-2bfa-403d-95a4-cca2e99feecd" />

6.Sửa đổi nginx/nginx.conf để /api trỏ tới service myapp cổng 9630

<img width="781" height="446" alt="image" src="https://github.com/user-attachments/assets/2a1128bd-e0ed-4339-850a-629cb1693799" />

Kết quả hiển thị : truy cập vào đường dẫn sau:  http://192.168.1.26/api/funny

<img width="950" height="509" alt="image" src="https://github.com/user-attachments/assets/dce25c53-0ae3-4000-a1fc-1bae8cf100ed" />

E. Triển khai (level test) ứng dụng

1.Chuyển vào trong thư mục ~/myapp

           cd ~/myapp
           
2.Gõ lệnh để docker compose chạy: sẽ run tất cả các service khai báo trong file docker-compose.yml
     Lợi ích: Chỉ cần docker-compose up -d là toàn bộ hệ thống (Web + Node-RED + Tunnel) tự chạy,

            docker compose up -d

<img width="785" height="136" alt="image" src="https://github.com/user-attachments/assets/ef35c76e-cda8-418f-b4eb-f9b0364a1f43" />

3.Kiểm tra các container đang chạy trong docker, nếu có cái nào bị restart cần tìm lỗi rồi edit lại docker-compose.yml

gõ lệnh :     docker ps -a      để kiểm tra

<img width="1465" height="192" alt="image" src="https://github.com/user-attachments/assets/70330091-998b-41c8-acf4-1388ba5f47d0" />

=> không có container nào lỗi

4.Kiểm tra kiểm thử các service đang chạy độc lập thông qua ip và port của nó: ví dụ mở trình duyệt ip_ubuntu:1880 để check nodered đã chạy chưa

.Kiểm tra Web cá nhân (Nginx):

       truy cập: http://192.168.1.26

<img width="942" height="624" alt="image" src="https://github.com/user-attachments/assets/d902047b-0b3c-471c-822d-4272cefe8f18" />

.Kiểm tra API Python (Dịch vụ Backend):

       Truy cập: http://192.168.1.26/api/funny

<img width="722" height="314" alt="image" src="https://github.com/user-attachments/assets/8b90318b-a30e-4270-9f8d-e8f3e601373b" />

.Kiểm tra Node-RED (Công cụ lập trình kéo thả):
      Truy cập: http://192.168.1.26:1880

<img width="908" height="775" alt="image" src="https://github.com/user-attachments/assets/fe6825c2-716e-49e3-9d73-dd50704a10ab" />

5.Sử dụng nodered: kéo nodered http_in , http_response, function : để tạo api get đơn giản (dùng cho /api proxy_pass của nginx)

<img width="955" height="764" alt="image" src="https://github.com/user-attachments/assets/e1dd910d-5a64-4d95-a3a0-bc2b7a784ed1" />

6.Sửa file ./myweb/index.html : thêm code html+js để sử dụng được api đã khai báo proxy_pass (thực ra là sử dụng nodered http_in hoặc sử dụng service myapi)

. chạy lệnh này để ghi đè lại file giao diện mới:

<img width="1462" height="624" alt="image" src="https://github.com/user-attachments/assets/2bb60431-384d-4ff1-9afd-3ca6fb9784bd" />

 - Mở trình duyệt trên máy tính (Windows) truy cập: http://192.168.1.26

 => Nhấn nút "Lấy thông điệp từ Backend".

 <img width="960" height="719" alt="image" src="https://github.com/user-attachments/assets/91404a5a-d571-4591-94f3-e612b7e8c15a" />

F. Gỡ lỗi:

1.nếu có lỗi xẩy ra trong quá trình triển khai docker compose up -d

   Kiểm tra nhanh: docker compose ps giúp biết container nào đang chạy xem log, ví dụ: docker logs mynginx docker logs myapi

2.Thêm healthcheck cho myapi trong file docker-compose.yml

      healthcheck:
      
          test: ["CMD", "curl", "-f", "http://localhost:9630"]

 . mở file bằng lệnh nano docker-compose.yml và sửa phần myapi

 <img width="885" height="935" alt="image" src="https://github.com/user-attachments/assets/d5da5d5f-5d8d-4c0e-802f-efa984750a45" />
   
3.giới hạn resource cho một service: (tránh việc 1 service chiếm quá nhiều ram)

      deploy:
      
        resources:
        
          limits:
          
            memory: 512M
            
sử dụng lệnh: docker compose stats để quan sát lượng ram sử dụng bởi mỗi service

<img width="953" height="259" alt="image" src="https://github.com/user-attachments/assets/39e501a3-6bf4-4597-9b5b-b218ff18203f" />

G. Triển khai ứng dụng đến End-user

1.Trong Cloudflare: Tạo tunnel (đường hầm), chọn loại triển khai cho docker

2.Convert lệnh docker run ... sang dạng docker compose

3.Khai báo kết quả convert vào trong file docker-compose.yml

4.Chạy lại docker compose

5.Public ứng dụng bằng cách thêm 1 router trỏ tới container đang chạy trong docker, dữ liệu sẽ đi qua tunnel, url dạng sub-domain

6.Kiểm tra url sub-domain đã hoạt động public cho mọi end-user

Cấu trúc thư mục:

myapp/
├── docker-compose.yml
├── nginx/
│   └── nginx.conf
├── myweb/
│   └── index.html
└── nodered/ (sẽ tự sinh dữ liệu)
│   └── (có nhiều file tự sinh)
│   └── settings.js (file này cần edit để bắt nodered login)

Sơ đồ theo góc nhìn của dev:

graph LR
A(Ubuntu) -- Command basic --> B((Docker compose))
B -- Khai báo --> C((Nodered))
C -- Cấu hình --> E(Yêu cầu đăng nhập) --> Z[end-user]
B -- Khai báo --> D((nginx))
D -- Cấu hình --> F(web+domain) --> Z
B -- Khai báo --> G(myapi)
D -- Cấu hình --> H((API)) --> F
H -- proxy --> G


Sơ đồ theo góc nhìn ngược lại:

G. Câu hỏi về bài làm?
