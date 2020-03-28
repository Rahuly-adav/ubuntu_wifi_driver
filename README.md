This technique will help you in installing wifi drivers in ubuntu and improve wifi signal range.

In my case, I am using ubuntu 18.04 and it is my host os. the issue is that it is not showing the nearest wifi devices where as at the same time my mobile phone is connect to those devices, but they are not visible in my laptop. so to resolve this issue i have downloaded "rtlwifi_new-master" and "rtlwifi_new-rock.new_btcoex" from git hub which is also available in my respo. and then install them in my device. it helps me. hope it also help you...
kindly follow the instruction and type command 1 by 1:

First of all check your wlan port:
by command-

            iwconfig
            
In my case the wlan port is "wlp19s0"

then go to the location where you have downloaded the "rtlwifi_new-master" and "rtlwifi_new-rock.new_btcoex"

Then,
            
            cd rtlwifi_new-rock.new_btcoex

Type    

           make
 
 If it shows any error then open the second file "cd rtlwifi_new-master" 

 then type 
 
           make

 then 
 
           sudo make install

 ***Type your ubuntu password***

           sudo modprobe -rv rtl8723be
           sudo modprobe -v rtl8723be ant_sel=2
           sudo ip link set wlp19s0 up
           sudo iw dev wlp19s0 scan


 ***To make this change permenant type***
 			       
           echo "options rtl8723be ant_sel=2" |sudo tee /etc/modprobe.d/50rtl8723be.conf

