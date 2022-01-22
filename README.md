HƯỚNG DẪN CÀI ĐẶT MÔI TRƯỜNG PHÁT TRIỂN FIRMWARE THIẾT BỊ FIRE SAFE
 
I.	Cài đặt môi trường cho chip ESP32
1. Cài đặt ubuntu trên windows
- Chạy power shell với quyền admin 
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
- Cài đặt Linux : download trên Windows Store
 
- Khởi chạy và tiến hành update OS
 


•	sudo apt-get update
- Cài đặt các package cần thiết cho SDK
•	sudo apt-get install git wget flex bison gperf python3 python3-pip python3-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0
- Download SDK
•	git clone --recurse-submodule https://YOUR_GIT_TOKEN@github.com/ByTechJSC/fire_safe_esp32_sdk
- Download ESP32 code
git clone -b feature/dev https://YOUR_GIT_TOKEN@github.com/ByTechJSC/FireSafe
- Cài đặt SDK
•	cd /path/to/esp-idf
•	./install.sh
- Export biến mỗi trường
•	Sử dụng branch v4.3.2
•	cd to IDF_PATH
•	. ./export.sh
- Build
•	Sau khi export biến môi trường thì cd /to/project_path
•	idf.py build
•	Kết quả khi build thành công
 
- Flash chương trình
•	Serial port : trong windows serial port là COMx =>> trong ubuntu serial port là /dev/ttySx
•	idf.py -p /dev/ttySx -b 921600 flash
•	Nếu permission denied thì check lại xem port có đang bị mở bởi phần mềm khác không, hoặc cấp quyền sudo chmod 777 /dev/ttySx
- Erase flash
idf.py -p /dev/ttySx -b 921600 erase_flash
- Monitor
idf.py -p /dev/ttySx monitor

- Công cụ nạp ESP32 trên windows : flash download tool
•	https://www.espressif.com/en/support/download/other-tools
•	Địa chỉ nạp chương trình
fire_safe.bin	0x10000
ota_data_initial.bin	0x270000
bootloader.bin	0x1000
partition-table.bin	0x8000

2. Cài đặt môi trường phát triển cho GD32E230
- Cài KeilC
