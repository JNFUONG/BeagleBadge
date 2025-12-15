 cd /sys/class/i2c-dev/i2c-1/device/1-0050




cat eeprom | hexdump -C




echo hh > ./eeprom




dmesg | grep -i eeprom




#### 🎨OSPI Speed Test
##### Read Test
dd if=/dev/mtdblock5 of=/tmp/test_file bs=1M count=10 oflag=direct
##### Write test
dd if=/dev/zero of=/dev/mtdblock5 bs=1M count=10 oflag=direct




#### 🎨GPIO test
./test_gpio.sh 0




./test_gpio.sh 1
















































### Create Service: sudo nano /etc/systemd/system/re_test.service
[Unit]
Description=Hardware Test Suite
After=multi-user.target




[Service]
Type=simple
ExecStart=/home/am62l/re_test
WorkingDirectory=/home/am62l
Restart=no
User=am62l




[Install]
WantedBy=multi-user.target




#### sudo systemctl enable re_test.service    #Enable the service
#### sudo systemctl start re_test.service
