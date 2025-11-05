# bai_so_3
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
   
# cài unbuntu 

<img width="1058" height="552" alt="image" src="https://github.com/user-attachments/assets/8268af5c-582c-457c-8a39-c11d639d54e0" />

chạy lệnh này để cài ubuntu

<img width="486" height="286" alt="image" src="https://github.com/user-attachments/assets/2c7b2a4b-e097-4cef-ade9-19f1c60f203b" />

cài ubuntu thành công

<img width="1073" height="509" alt="image" src="https://github.com/user-attachments/assets/21c45af9-9fc0-4cff-b3bd-8100842e27b2" />

# cài docker desktop

<img width="1155" height="919" alt="image" src="https://github.com/user-attachments/assets/3d61d47f-ea5f-4b08-8f59-f180bef7a012" />

test docker có trong desktop 

docker desktop

<img width="545" height="245" alt="image" src="https://github.com/user-attachments/assets/00e771b2-42ae-43a8-b810-e728db1ccaf5" />

docker chạy hoàn hảo rồi 

<img width="1468" height="677" alt="image" src="https://github.com/user-attachments/assets/cd7617c8-7b3c-4efe-bed3-c355469ecac4" />

# tạo thư mục dự án 

<img width="461" height="90" alt="image" src="https://github.com/user-attachments/assets/32ea9b9e-2020-4898-99b1-a361f5cf9373" />

Tạo file docker-compose.yml

<img width="1485" height="752" alt="image" src="https://github.com/user-attachments/assets/53a02cc8-3f30-44ef-a762-981128a33e51" />

toàn bộ file docker chạy thành công 

<img width="1462" height="581" alt="image" src="https://github.com/user-attachments/assets/d00c8d8f-b4f7-42f4-bdc1-654b2ad665ab" />

<img width="1917" height="612" alt="image" src="https://github.com/user-attachments/assets/fe852676-10ff-466d-82fd-8f9e783ac74f" />

xem danh sách container đang chạy 

<img width="1919" height="335" alt="image" src="https://github.com/user-attachments/assets/46b520da-7e94-4669-8b2c-460719826d41" />

# Hệ thống Iot Giám sát cảm biến nhiệt độ độ ẩm

tạo bảng sensor_data

<img width="1437" height="871" alt="image" src="https://github.com/user-attachments/assets/2fd348b5-500b-48d2-8b81-94391007121f" />

tạo user người đănh nhập 

<img width="826" height="218" alt="image" src="https://github.com/user-attachments/assets/8906611f-a572-4df8-b54e-ebe663f92f95" />

cấu hình nodered

<img width="1240" height="801" alt="image" src="https://github.com/user-attachments/assets/68afd3ad-5946-46c9-a616-914032c0dfe0" />

đầu tiên em dùng inject để dữ liệu cảm biến ảo mỗi 5s

<img width="257" height="134" alt="image" src="https://github.com/user-attachments/assets/3110810f-1594-4d46-83e5-ed1d4ee72a6c" />

sau đó em thêm 1 function tạo dữ liệu cảm biến

<img width="1213" height="526" alt="image" src="https://github.com/user-attachments/assets/b2092b94-8a74-453e-b25f-2ef5389b5bee" />

sau đó lưu dữ liệu vào mariadb 

<img width="668" height="843" alt="image" src="https://github.com/user-attachments/assets/5284387e-afe8-4a4d-a90a-b7e8ab2b67ef" />

đây là phần cấu hình tạo dữ liệu mỗi 5s

<img width="1179" height="199" alt="image" src="https://github.com/user-attachments/assets/405ae863-c233-4189-a697-5b4b73d3541a" />

phần cấu hình truy vấn dữu liệu trả về api 

lấy http in và cấu hình 

<img width="632" height="808" alt="image" src="https://github.com/user-attachments/assets/3ffa9c3a-4167-4f1d-aae0-73ed1526562b" />

truy vấn dữ liệu 

lấy 10 bản ghi mới nhất ở database senser_data

<img width="1418" height="785" alt="image" src="https://github.com/user-attachments/assets/50958850-94e2-499d-a646-b4b1328a6401" />

lấy dữ liệu ở mariadb 

<img width="659" height="815" alt="image" src="https://github.com/user-attachments/assets/4bff6033-149d-4ac6-8682-d9fb38790140" />

thêm function định dạng json 

<img width="1468" height="785" alt="image" src="https://github.com/user-attachments/assets/aede8004-6b1a-4c94-b6bb-9fe2c39d81ec" />

trả về API

<img width="714" height="827" alt="image" src="https://github.com/user-attachments/assets/a702d6e4-63d1-49ad-9989-ae1bffe28c4f" />

sau khi ấn deloy kiểm tra kết quả có đúng không  truy cập http://localhost:1880/api/data

<img width="627" height="983" alt="image" src="https://github.com/user-attachments/assets/4c75ad8b-7208-4ade-885c-cc9c95628d53" />

toàn bộ node red

<img width="1237" height="835" alt="image" src="https://github.com/user-attachments/assets/913780b0-8d2f-4dad-b154-2143260e18c0" />

chưa gọi được API login lên em để login demo 

giao diện login demo 

<img width="497" height="758" alt="image" src="https://github.com/user-attachments/assets/13ce37a8-0cfb-41a4-a2ce-8b6d819fb22a" />

giao diện chính gọi được API dữ liệu 

<img width="1848" height="924" alt="image" src="https://github.com/user-attachments/assets/481d152a-bfea-4419-8989-503868c96add" />

được hiển thị trên thời gian thực 

cấu hình file host đổi thành http://nguyentrungkien.com

<img width="1485" height="653" alt="image" src="https://github.com/user-attachments/assets/b22aafc2-878f-443b-b240-4f78d2a09845" />

cấu hình file host trong ubuntu

<img width="450" height="69" alt="image" src="https://github.com/user-attachments/assets/a16e8cf5-1082-4c4b-9776-add423548c8b" />

<img width="1470" height="751" alt="image" src="https://github.com/user-attachments/assets/f13eadfe-b85f-458e-abe2-60b9c1476902" />












