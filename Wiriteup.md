# Time_machine_DigitalDragonsCTF_2023
## Description: Nhóm cảnh sát đã phát hiện ra manh mối phạm tội của John, hãy giúp những chú cần sát đảnh này tìm ra chúng.
- Link: [Time machine](https://drive.google.com/file/d/1rSRcWnyefr6dVf29kP0fctoV27Kw5Vit/view?usp=sharing)
- Format: flag{}

1. Đầu tiên mình thấy đuôi file là .pcapng nên đây là phần mở rộng của .pcap - tệp lưu trữ các gói tin trong mạng máy tính
2. Mình mở Wireshark lên để phân tích, mình thử xem các luồng TCP xem có gì đặc biệt ![](https://github.com/BuiDuyet/Time_machine_DigitalDragonsCTF_2023/blob/main/6.png?raw=true)
 ![](https://github.com/BuiDuyet/Time_machine_DigitalDragonsCTF_2023/blob/main/1.png?raw=true)
Bùm, thấy một đoạn giao tiếp giữa John và server, đọc kỹ sẽ thấy ông Jhon này đã gửi file gì đó đến server
4. Sau đó mình mở phần Export Object ra rồi check từng phần export xem có ra gì không ![](https://github.com/BuiDuyet/Time_machine_DigitalDragonsCTF_2023/blob/main/2.png?raw=true)
Và trong phần FTP-Data quả nhiên có vài file đáng nghi vấn ở đây ![](https://github.com/BuiDuyet/Time_machine_DigitalDragonsCTF_2023/blob/main/3.png?raw=true)
5. Mình Save all về và kiểm tra từng file một, mình kiểm tra file "secret.odt" trước vì thấy secret là đã thấy mùi nghi nghi rồi
6. Mình extract file bằng lệnh *$binwalk -e secret.odt* sau khi kiểm tra và vào đường dẫn */secret/Thumbnails/* mình thấy có một file ảnh .png với nội dung **NOT Here lol**, biêt mình đã bị lừa nên mình tiếp tục soát các file còn lại
7. Tiếp đến kiểm tra *takemehome.jpg* xem có gì đặc biệt không, qua một loạt thử từ exiftool cho đến strings và cả binwalk thì chả thu được cái gì
8. Cay quá nên tiếp tục chuyển sang file *timemachine.apk*, vẫn extract file ra bằng lệnh *binwalk -e timemachine.apk* thu được folder
9. Dựa theo đề thì ông John này đang phạm tội và có vài thông tin kín được truyền đi thông qua app **Time machine** này (bởi đuôi của file này là .apk) mình kiểm tra các folder chứa tài nguyên trước, thường các folder này có tên là */res*, và khi vào folder này mình phát hiện ra phần Date có điểm kỳ lạ ![](https://github.com/BuiDuyet/Time_machine_DigitalDragonsCTF_2023/blob/main/4.png?raw=true)
10. Các folder khác đều đã cũ từ tận 1981 và riêng có một folder mới được update gần đây 2023, nhấp chuột vào và "Ồ" thêm phát nữa, có duy nhất một file "strings.xml" cũng được update gần đây, tiếp cái đà sắp vớ được flag thì mình bật terminal lên và *$strings strings.xml*.
   # VÀ ĐIỀU GÌ ĐẾN CŨNG PHẢI ĐẾN
-    Here is your flaggg !
![](https://github.com/BuiDuyet/Time_machine_DigitalDragonsCTF_2023/blob/main/5.png?raw=true)
- ***ZmxhZ3t5MHVfNHIzXzRfbDMzdF9oNGNrM3J9Cg==***
-    Nhìn cái đuôi "==" là biết ngay kiểu mã hóa Base64
-    Và đây là kết quả: **flag{y0u_4r3_4_l33t_h4ck3r}**


