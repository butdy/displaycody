################################################################################
   DISPLAY AUTOPLAY FULLSCREEN VIDEO DI RASPBERRY PAKAI KODI
     membuat tampilan full screen dari player codi di raspberry
     menggunakan python yang mengimport modul dari xmbc
     letakkan file ada autoexec.py di /home/pi/.kodi/userdata/
     sesuaikan lokasi playlist dengan yang ada di dalam file autoexec.py
     source ide dari mr febry
################################################################################

Setting ukuran display
sudo nano /boot/config.txt
tambahkan berikut :
hdmi_group=1 
#untuk nilai 0 , auto detect dari EDID
#untuk nilai 1 , CEA (Consumer Electronics Association, biasanya TV / display)
#untuk nilai 2 , DMT(Display Monitor Timings, yang biasanya di pakai untuk monitor)
hdmi_mode=81 #16=1080p, 81=1366x768
#https://www.raspberrypi.org/documentation/configuration/config-txt/video.md

syarat agar bisa berjalan dengan baik :
1. terinstall raspbian
2. terinstall kodi player
sudo apt install kodi kodi-peripheral-joystick kodi-pvr-iptvsimple kodi-inputstream-adaptive kodi-inputstream-rtmp
3. sudah create playlist / bisa menggunakan komputer lain atau menggunakan kodi untuk create playlist
cek contoh playlist puter.m3u
4. create playlist dari kodi kemungkinan mapping path lokasi penyimpanan yang 
   tidak pas karena permission folder by kodi tetapi bisa di cari dengan 
   menggunakan perintah find / -iname namaplaylist.*  
5. create autoplay video saat menjalankan kodi
/home/pi/.kodi/userdata/autoexec.py
chmod +x /home/pi/.kodi/userdata/autoexec.py
6. create service agar kodi jalan setelah raspberry restart , boot awal
  copi file kodi.service ke dalam folder /lib/systemd/system/
  systemctl enable kodi
 sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
 tambahkan pada baris paling atas
 @kodi
