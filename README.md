 ![image](https://hackmd.io/_uploads/HykU6jwa0.png)

-	Sau khi tải về ta được 1 file pcapng.Bật wireshark lên ta thấy rất nhiều kết nối TCP:
 ![image](https://hackmd.io/_uploads/SkzvpoPT0.png)

-	Chọn 1 gói TCP bất kỳ sau đó chọn follow -> TCP stream đến stream thứ 2 ta được flag đang bị reverse:
 ![image](https://hackmd.io/_uploads/S1EOpov60.png)

-	Dùng tool và lấy lá cờ :
 ![image](https://hackmd.io/_uploads/HyxcFTiwaC.png)

-	Flag: KCSC{s1mplY_Str1ng_R3v3rseD}

 ![image](https://hackmd.io/_uploads/r1Qjaowa0.png)

-	Tên đề bài gợi ý là một thông tin liên quan đến đăng nhập.
-	Lướt xuống 1 đoạn thì mình có thấy file lsass.DMP. Lsass.exe đóng vai trò quan trọng trong việc kiểm tra và xử lý các yêu cầu đăng nhập và xác thực từ các dịch vụ khác trong hệ thống.Có thể trích xuất thông tin từ lsass.exe để lấy cắp thông tin xác thực, đặc biệt là mật khẩu (thường được thực hiện qua các công cụ như Mimikatz).Vì ở đây đề bài cho file ở dạng .DMP nên không thể dùng công cụ Mimikatz, mình có đọc trên google và tìm được bài viết này: https://05t3.github.io/posts/DCTF/ Ở đây họ hướng dẫn sử dụng 1 công cụ là pypykatz:
 ![image](https://hackmd.io/_uploads/rkvp6sDpR.png)
![image](https://hackmd.io/_uploads/HyI0piDaC.png)

 
-	Thực hiện và lấy được hàm băm NTLM của 1 user tên là nex0:
![image](https://hackmd.io/_uploads/Hkxx0jv6R.png)

 
-	Đến đây có nhiều cách để crack mật khẩu mình lên web https://hashes.com/en/tools/hash_identifier crack cho nhanh:
 ![image](https://hackmd.io/_uploads/BJrbAoDT0.png)

-	Flag: KCSC{FrostBite}
 ![image](https://hackmd.io/_uploads/Hk4f0sva0.png)

-	Bài này đề cho 1 ảnh png, mình nghĩ ngay đến stego:
 ![image](https://hackmd.io/_uploads/BkPQAjPaA.png)

-	Sử dụng tool stego online mình thấy ngay flag:
 
 ![image](https://hackmd.io/_uploads/HJE4CsDpR.png)

 
![image](https://hackmd.io/_uploads/HyVrCiDa0.png)

-	Đề bài cho 1 folder là dữ liệu của người dùng admin và dựa vào gợi ý có lẽ là tìm 1 tệp vừa bị người dùng xóa:
 
![image](https://hackmd.io/_uploads/ryDPRsDTA.png)
![image](https://hackmd.io/_uploads/H1Md0oDTC.png)

 
-	Mình nghĩ ngay đến việc đưa folder lên autopsy để phân tích:
 ![image](https://hackmd.io/_uploads/HJlKCiPpC.png)

-	Vào web downloads thấy 1 tệp được tải về nhưng check trong folder này không có nữa nên mình nghĩ tệp bị xóa có lẽ là tệp này:
 ![image](https://hackmd.io/_uploads/Hkd5Rjv60.png)

-	Mình cố gắng truy cập URL để lấy file nhưng không được: 
 
![image](https://hackmd.io/_uploads/Byq6Ciw6A.png)


-	Check cache mình thấy vẫn còn 1 file được bảo vệ bởi mật khẩu:
 ![image](https://hackmd.io/_uploads/HynRCjPT0.png)

-	Thực hiện export file và đưa vào Kali để thực hiện phân tích:
 ![image](https://hackmd.io/_uploads/SJqJJnDpC.png)

-	Là 1 file zip được bảo vệ bởi mật khẩu.Mình sẽ thực hiện zip2john để crack mật khẩu:
 ![image](https://hackmd.io/_uploads/SkSekhPaA.png)


-	Lấy được ngay mật khẩu là benjamin.Giải nén file zip ta được 1 hình ảnh chứa flag:
 ![image](https://hackmd.io/_uploads/HJpGJnDTC.png)

![image](https://hackmd.io/_uploads/rJj_J2PpR.png)


-	Tải về thấy 1 file Ѕuѕpiciouѕ.ad1 mình đưa vào FTK Imager để phân tích:

![image](https://hackmd.io/_uploads/BJdty3DpC.png)
![image](https://hackmd.io/_uploads/ryO91nvaA.png)

 
-	Mình tìm được bài viết về các vị trí phổ biến thường nằm của mã độc qua link: https://sec.vnpt.vn/2022/06/windows-forensic-malware-persistence/ 
 ![image](https://hackmd.io/_uploads/HJ_3khPaR.png)



-	Thực hiện kiểm tra Autostart Registry key qua các path xem thế nào:
 ![image](https://hackmd.io/_uploads/BJSp1hv6R.png)

-	Thực hiện kiểm tra các file khả nghi nằm trong các path trên mình tìm được mã độc tại đây:
DAT\Software\Microsoft\Windows\CurrentVersion\Run
![image](https://hackmd.io/_uploads/SySCJ3waR.png)
![image](https://hackmd.io/_uploads/r1r1ehvp0.png)

 
 
-	Vậy là ta đã có hàm băm của mã độc là 6f56399aec2db382190593623d200fe24069ef629a07990897e6945e3c758cca
-	Tiếp tục tìm phần còn lại của flag.Mình check log evtx thì thấy:
 ![image](https://hackmd.io/_uploads/BJfge2w6A.png)

-	Thực hiện decode ta được ngay phần đầu của flag:
 ![image](https://hackmd.io/_uploads/B1jee3DpA.png)
![image](https://hackmd.io/_uploads/HJIbg3vTC.png)

 
-	Đề bài cho 1 file pcapng.Bật wireshark lên ta thấy rất nhiều kết nối ICMP giữa máy chủ và máy của hacker:
 ![image](https://hackmd.io/_uploads/SJtMenwa0.png)

-	Mình có tìm được video này liên quan đến Digging for a hidden flag inside eavesdrop Pings (an ICMP pcap): https://www.youtube.com/watch?v=KzUgRVirmpg
 ![image](https://hackmd.io/_uploads/B1L7lhwaC.png)


-	Thực hiện tra trên google và hỏi chatGPT mình tìm được đoạn code:
 ![image](https://hackmd.io/_uploads/rk44x2DpA.png)
-	Chạy file mình tìm được flag:
 ![image](https://hackmd.io/_uploads/BJd8ehvT0.png)

-	Flag: KCSC{~(^._.)=^._.^=(._.^)~}
![image](https://hackmd.io/_uploads/rkXvghP6R.png)
 
-	Tiếp tục mở file Challenge.pcapng và flow TCP stream ta thu thập được 1 file key.txt và 4 chuỗi:
![image](https://hackmd.io/_uploads/rkV_xhv6C.png)
![image](https://hackmd.io/_uploads/S1q_lhDTA.png)
![image](https://hackmd.io/_uploads/HJWFghPTA.png)
 
 
 
-	Trông có vẻ giống mã Base64 nhưng không phải.Sau một hồi tìm hiểu mình tìm được đây là mã hóa Fernet.Thực hiện code và lấy flag:
 ![image](https://hackmd.io/_uploads/r1gqgnPp0.png)
![image](https://hackmd.io/_uploads/Bytcl2vT0.png)

 
-	Flag: KCSC{Y0u_Kn0w_F__E__R__N__E__T!!}








