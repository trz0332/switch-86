# switch-86

本项目为个人爱好  

+   ## PCB部分
 
*  ###  打板  
pcb文件可以在嘉立创里面打板，控制板好像没办法白嫖，自己想办法   
*  ###  元件焊接  
1、这里有要注意的是，led的焊接。板子上有个箭头，led的绿点需要指向箭头方向  
2、对于2个，4个led灯的这种，在led不需要焊接的地方，有2个短接焊盘。需要焊接上  
3、市电检测部分的元件朝向参照图片


+   ## 固件部分  

*  ###  使用esphome作为固件
1、板子的右下角的按钮是GPIO0，刷固件的时候可以直接按住这个按键进行通电，进入固件下载模式，如果是2开的开关，需要自己想办法短接GPIO0进入固件下载模式
2、6b3r，4b2r，2b1r是正常的开关固件，开关上面3个按钮是情景开关，下面3个按钮默认是控制继电器的。右下角的按钮长按是开关背光灯，同时关闭一次太阳模式，当下次太阳升起或者落下，打开太阳模式.上面的按键是情景模式，有短按，双机，长按3种模式，
3、上面3种开关，有一个switch_qj的实体开关，当打开这个开关的时候，对应的上下2个按钮均可以控制继电器
4、6b1r，4b1r，是情景开关，代表所有开关都是情景模式，有短按，双机，长按3种模式， 其中有个relay_L1_connect的下拉选择菜单的实体，用于把继电器关联到按键上面，可以设置具体某一个按键可以开关继电器，如果一个继电器都不焊接的话。可以将这个设置成为不关联   
5、所有的参数在secrets.yaml里面修改  
mqtt_server_: '10.18.19.1'  #mqtt服务器地址  
mqtt_port_: '1883'  #mqtt服务器端口  
mqtt_user_: 'pi'  #mqtt服务器用户名  
mqtt_password_: 'rarry'  #mqtt服务器密码  
mqtt_prefix_: 'homeassistant'     #mqtt服务自动发现前缀  
latitude_: '22.568017'  #经度  
longitude_: '115.038915'  #维度  
ota_password: 'xxxxxxxx'  #ota密码  
web_user: 'esphome'  #网页用户名  
web_password: 'xxxxxxxx'  #网页密码  
wifi_ssid: 'iot_wl'  # wifi   ssid  
wifi_password: 'xxxxxxxx'  #wifi密码  
ap_ssid: 'esphome'   #wifi的ap模式下ssid  
ap_password: 'xxxxxxxx'  #wifi的ap模式下密码  
wifi_reboot_timeout: 1200s  #wifi断开情况下多久重启  
mqtt_reboot_timeout: 1200s  #mqtt断开情况下多久重启  

如果需要在开关里面自动实现白天关背光灯，晚上开背光灯，需要设置经纬度，用经纬度拾取器读取你自己的gps坐标。然后修改对应参数，也可以刷完固件之后在网页上修改

