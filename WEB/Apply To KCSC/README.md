# Apply To KCSC 
BÀI NÀY CHO MÌNH NỘP CV LÊN KCSC -> mình hâm mộ clb đã lâu , nên nếu admin thấy dòng này thì có thể chiếu cố em với :))) , em hứa sẽ học tập tốt để đưa Việt Nam sánh vai các cường quốc năm châu  :>>>

Giao diện bài này : 
![Alt text](image.png)
điều mình chú ý là có chỗ upload file cv :>>  ( sơ hở là mình muốn up shell code )

![Alt text](image-1.png)

Ban đầu hãy làm dùng như người dùng bình thường :> 
mình điền bình thường , tuy nhiên file mình tets gửi là file docx
và mình nhận được thông báo ! 

![Alt text](image-2.png)

theo kinh nghiệm chơi ctf 1 tháng cuả mình thì thấy filter như này thì cứ vào burp suite xem test xem nó có gửi request đi không , filter ở client hay server ! 
ném vào repeater chúng ta cùng test :>

![Alt text](image-3.png)

vẫn có request đi , và đây là filter từ server 
mình thử up 1 file pdf chuẩn chỉ ! 

![Alt text](image-4.png)

và ok mình đã biết nó được move vào trong thư mục uploads/your_file
mình đưa request sang repeater 

![Alt text](image-5.png)

đuổi extension file thành .php 
và nó vẫn success -> suy ra server filter qua $_FILE['file']['type']
chính là header này 

![Alt text](image-6.png)

giờ chỉ cần sửa content của file thành payload shell code php rồi up lên ! 
payload :
```
<?php system($_GET['cmd']); ?>
```
![Alt text](image-7.png)
và mình đã chạy được shell code trên hệ thống -> giờ chỉ tìm flag thôi 
có quá trình file nên mình không biết nó nằm chỗ nào -> mình dùng grep thử tìm folder 
cú pháp như sau :
```
grep -r "chuỗi_cần_tìm" /đường/dẫn/thư/mục
```
payload của mình :
![Alt text](image-8.png)
# FLAG 
```
KCSC{W3lc0m3_T0_KCSC_2023____}
```
