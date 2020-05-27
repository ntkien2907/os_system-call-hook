# SYSTEM CALL VÀ HOOK TRONG LINUX

## SYSTEM CALL
* B1: Tới folder chứa các file test là **run_pnametoid.c** và **run_pidtoname.c**
* B2: Biên dịch file test
        
        gcc <tên file test> -o <tên chương trình>
* B3: Tại folder chứa chương trình

        ./<tên chương trình>

**pnametoid**: Nhập tên process, trả về id (nếu có) hoặc trả về -1 (nếu không tìm thấy)

**pidtoname**: Nhập id của process, tên process được lưu trong buffer

## HOOK
### Bắt đầu
* Tại folder chứa file hook.c, tạo module hook.ko

        make all
* Biên dịch test.c

        gcc test.c -o user_test
##### Terminal 1:
* Đưa module vào kernel

       sudo insmod hook.ko
* Chạy file
       
       ./user_test
##### Terminal 2:
* Xóa dmesg cũ

       sudo dmesg -C
* Mở dmesg mới

       dmesg
### Kết thúc
* Gỡ module khỏi kernel

       sudo rmmod hook
* Xóa các file tạo ra trong quá trình compile

        make clean
