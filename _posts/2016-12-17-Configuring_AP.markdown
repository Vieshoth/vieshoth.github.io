#### To configure imx6 som as wifi hotspot we need to create two file.
/etc/hostapd.conf - The configuration file
/usr/sbin/hostapd
By default we have both the files in our rootfs.

#### STEP 1: Copy the below content in the configuration file
```
interface=wlan0
driver=nl80211
channel=8
ssid=NEW_AP
max_num_sta=5
hw_mode=g
preamble=1
dtim_period=2
beacon_int=100
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
supported_rates=60 90 120 180 240 360 480 540
basic_rates=60 90 120 180 240
macaddr_acl=0
tx_queue_data3_aifs=7
tx_queue_data3_cwmin=15
tx_queue_data3_cwmax=1023
tx_queue_data3_burst=0
tx_queue_data2_aifs=3
tx_queue_data2_cwmin=15
tx_queue_data2_cwmax=63
tx_queue_data2_burst=0
tx_queue_data1_aifs=1
tx_queue_data1_cwmin=7
tx_queue_data1_cwmax=15
tx_queue_data1_burst=3.0
tx_queue_data0_aifs=1
tx_queue_data0_cwmin=3
tx_queue_data0_cwmax=7
tx_queue_data0_burst=1.5
wme_enabled=1
wme_ac_bk_cwmin=4
wme_ac_bk_cwmax=10
wme_ac_bk_aifs=7
wme_ac_bk_txop_limit=0
wme_ac_bk_acm=0
wme_ac_be_aifs=3
wme_ac_be_cwmin=4
wme_ac_be_cwmax=10
wme_ac_be_txop_limit=0
wme_ac_be_acm=0
wme_ac_vi_aifs=2
wme_ac_vi_cwmin=3
wme_ac_vi_cwmax=4
wme_ac_vi_txop_limit=94
wme_ac_vi_acm=0
wme_ac_vo_aifs=2
wme_ac_vo_cwmin=2
wme_ac_vo_cwmax=3
wme_ac_vo_txop_limit=47
wme_ac_vo_acm=0
auth_algs=3
ieee80211d=0
ieee80211n=1
uapsd_advertisement_enabled=1
wep_rekey_period=0
own_ip_addr=127.0.0.1
wpa_group_rekey=0
wpa_strict_rekey=0
wpa_gmk_rekey=0
wpa_ptk_rekey=0
#ap_table_max_size=255
#ap_table_expiration_time=60
eap_server=1

```




#### STEP 2: Run the hostapd binary configure it as AP
```
hostapd /etc/hostapd.conf -B
```



#### STEP 3: Configure the IP with the command below
```
ifconfig wlan0 <IP ADDRESS> up
```

#### STEP 4: Now you can connect any station with this AP using the SSID.
Since our ssid is "NEW_AP" scan this ssid with the following command from the station side.
```
sudo iw dev wlan0 scan
```
This will list all the available AP with required information.

#### STEP 5: Once the station is connected to AP, assign an IP address.

####STEP 6: Ping and confirm the connection.
```
ping <IP ADDRESS OF THE AP>
```
