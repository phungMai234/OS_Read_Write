# OS_Read_Write
Bài 4 trang 29
https://courses.uet.vnu.edu.vn/pluginfile.php/138144/mod_resource/content/0/NLH%C4%90H-Bai-4.pdf

Bài toán người đọc – Người viết
! Một tập dữ liệu được chia sẻ đồng thời bởi một số tiến trình
! Người đọc: chỉ đọc dữ liệu, không cập nhật hay thay đổi dữ liệu
! Người viết: đọc và viết dữ liệu
! Cho phép nhiều người cùng đọc dữ liệu một lúc
! Chỉ một người viết được thay đổi dữ liệu
! Dữ liệu chung
! Tập dữ liệu
! Khởi tạo semaphore mutex bằng 1 //Đảm bảo tính loại trừ lẫn nhau khi cập nhật
readcount
! Khởi tạo semaphore wrt bằng 1 //Đảm bảo tính loại trừ lẫn nhau của người viết
! Khởi tạo semaphore biến tự nhiên readcount bằng 0 // Đếm số tiến trình đang đọc
dữ liệu

Tiến trình người viết
 do {
 wait (wrt) ;
 // writing is performed
 signal (wrt) ;
 } while (TRUE); 
 
 Tiến trình người đọc:



do {
 wait (mutex) ; readcount ++ ;
 if (readcount == 1)
 wait (wrt) ;
 signal (mutex);
 // reading is performed
 wait (mutex) ; readcount - - ;
 if (readcount == 0)
 signal (wrt) ;
 signal (mutex) ;
 
