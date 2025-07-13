
## Enterprise Network Project #2 VLAN INTER-VLAN 🌐🖧📡⚙️📈
---
### เครดิต
[**Gurutech Networking Training**](https://www.youtube.com/watch?v=T8F5F9Jt8Yk&list=PLvUOx2WG6R7PMM8UhMWevH75QzGyXOv4g)  
---
#🖼️ PREVIEW   
<p align="center">
  <img src="https://github.com/user-attachments/assets/6640206d-fc2c-47ce-8a44-38342455689f" width="600"/>
  <br/>
  <img src="https://github.com/user-attachments/assets/2fcd1cb6-7e94-471b-b371-a269ecf5d6ab" width="600"/>
  <br/> 
</p> 

#📝Assignment 
<p align="center">
  <img src="https://github.com/user-attachments/assets/cbaf2e90-fea4-4825-a23e-717fdba9fc21" width="600"/> <br/>
  <small>แหล่งที่มา:  
  <a href="https://www.youtube.com/watch?v=F_dSpaTMyuA&list=PLvUOx2WG6R7PMM8UhMWevH75QzGyXOv4g" target="_blank" rel="noopener noreferrer">Gurutech Networking Training - YouTube Playlist</a>
  </small>
</p>
<h2>📊 การคำนวณ Subnet</h2>
<p>
Base network: <code>192.168.1.0</code><br>
จำนวน Subnet ที่ต้องการ: <code>3</code><br>
สูตร: <code>No. of Subnets = 2^n</code><br>
2<sup>n</sup> = 3 → n = 2 (ยืม 2 บิต)<br>
Class C เดิม: 255.255.255.0 → 11111111.11111111.11111111.00000000/24<br>
หลังยืม 2 บิต: 255.255.255.192 → 11111111.11111111.11111111.11000000/26<br>
Block size = 64
</p>

<table border="1" cellpadding="6" cellspacing="0">
  <thead>
    <tr>
      <th>Subnet</th>
      <th>ชื่อ Subnet</th>
      <th>Subnet Mask</th>
      <th>Network ID</th>
      <th>ช่วง IP ที่ใช้ได้ (Valid Hosts)</th>
      <th>Broadcast Address</th>
      <th>Access Point SSID / Password</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Admin-Wifi</td>
      <td>255.255.255.192 (/26)</td>
      <td>192.168.1.0</td>
      <td>192.168.1.1 – 192.168.1.62</td>
      <td>192.168.1.63</td>
      <td>Admin-Wifi / Admin@1234</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Finance-Wifi</td>
      <td>255.255.255.192 (/26)</td>
      <td>192.168.1.64</td>
      <td>192.168.1.65 – 192.168.1.126</td>
      <td>192.168.1.127</td>
      <td>Finance-Wifi / Finance@1234</td>
    </tr>
    <tr>
      <td>3</td>
      <td>CS_WIFI</td>
      <td>255.255.255.192 (/26)</td>
      <td>192.168.1.128</td>
      <td>192.168.1.129 – 192.168.1.190</td>
      <td>192.168.1.191</td>
      <td>CS_WIFI / Customer@1234</td>
    </tr>
  </tbody>
</table>
 
#📝Config Accesspoint ทั้ง 3 แผนก
<p align="center">
  <img src="https://github.com/user-attachments/assets/4b81e16b-29e7-4944-a440-6f44b4f70273" width="600"/>
  <br/>
  <img src="https://github.com/user-attachments/assets/5eab0497-0712-4f44-9cd6-95c49e3153e1" width="600"/>
  <br/> 
  <img src="https://github.com/user-attachments/assets/6612902f-215f-478b-9aab-f1f349c8caf8" width="600"/>
  <br/> 
</p> 

#Config Switch VLAN COMMAND การกำหนดให้กับ Port ต่างๆ
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse;">
  <thead>
    <tr>
      <th>คำสั่ง / ข้อความ</th>
      <th>คำอธิบาย / ความหมาย</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Switch&gt; enable</td>
      <td>เข้าสู่โหมด Privileged EXEC เพื่อแก้ไขคำสั่งขั้นสูง</td>
    </tr>
    <tr>
      <td>Switch# conf t</td>
      <td>เข้าสู่โหมด Global Configuration เพื่อแก้ไขการตั้งค่าอุปกรณ์</td>
    </tr>
    <tr>
      <td>Enter configuration commands, one per line. End with CNTL/Z.</td>
      <td>ระบบแจ้งว่าอยู่ในโหมด Config สามารถใส่คำสั่งได้ทีละบรรทัด และจบด้วย Ctrl+Z</td>
    </tr>
    <tr>
      <td>%LINK-3-UPDOWN: Interface FastEthernet0/2, changed state to down</td>
      <td>แจ้งสถานะลิงก์พอร์ต Fa0/2 ตกลง (Down)</td>
    </tr>
    <tr>
      <td>%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/2, changed state to down</td>
      <td>โปรโตคอลบรรทัด (Layer 2) ของพอร์ต Fa0/2 ตกลง (Down)</td>
    </tr>
    <tr>
      <td>%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to up</td>
      <td>แจ้งสถานะลิงก์พอร์ต Fa0/2 กลับขึ้นมา (Up)</td>
    </tr>
    <tr>
      <td>%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/2, changed state to up</td>
      <td>โปรโตคอลบรรทัดของพอร์ต Fa0/2 กลับขึ้นมา (Up)</td>
    </tr>
    <tr>
      <td>Switch(config)# interface range fa0/2-4</td>
      <td>เลือกช่วง interface Fa0/2 ถึง Fa0/4 เพื่อกำหนดค่า</td>
    </tr>
    <tr>
      <td>switchport mode access</td>
      <td>ตั้งพอร์ตเป็น Access Mode (พอร์ตสำหรับอุปกรณ์ปลายทาง เช่น PC)</td>
    </tr>
    <tr>
      <td>switchport access vlan 10<br>% Access VLAN does not exist. Creating vlan 10</td>
      <td>กำหนดพอร์ตเข้า VLAN 10 หาก VLAN 10 ยังไม่มี จะสร้างให้อัตโนมัติ</td>
    </tr>
    <tr>
      <td>interface range fa0/5-7<br>switchport mode access<br>switchport access vlan 20<br>% Access VLAN does not exist. Creating vlan 20</td>
      <td>ตั้งพอร์ต Fa0/5-7 เป็น Access Mode และผูกกับ VLAN 20 พร้อมสร้าง VLAN 20 ถ้ายังไม่มี</td>
    </tr>
    <tr>
      <td>interface range fa0/8-10<br>switchport mode access<br>switchport access vlan 30<br>% Access VLAN does not exist. Creating vlan 30</td>
      <td>ตั้งพอร์ต Fa0/8-10 เป็น Access Mode และผูกกับ VLAN 30 พร้อมสร้าง VLAN 30 ถ้ายังไม่มี</td>
    </tr>
    <tr>
      <td>do wr<br>Building configuration... [OK]</td>
      <td>คำสั่งบันทึกค่า (write memory) ลงใน startup-config สำเร็จ</td>
    </tr>
    <tr>
      <td>show vlan brief</td>
      <td>แสดงรายการ VLAN ทั้งหมด พร้อมสถานะ และพอร์ตที่ถูกกำหนด VLAN</td>
    </tr>
    <tr>
      <td>VLAN 1 default active Fa0/1, Fa0/11-24, Gig0/1-2</td>
      <td>VLAN 1 เป็น default VLAN มีพอร์ตที่ยังไม่ได้กำหนด VLAN อื่นๆ</td>
    </tr>
    <tr>
      <td>VLAN 10 active Fa0/2, Fa0/3, Fa0/4</td>
      <td>VLAN 10 มีพอร์ต Fa0/2-4 ถูกกำหนดให้ใช้งาน VLAN นี้</td>
    </tr>
    <tr>
      <td>VLAN 20 active Fa0/5, Fa0/6, Fa0/7</td>
      <td>VLAN 20 มีพอร์ต Fa0/5-7 ถูกกำหนดให้ใช้งาน VLAN นี้</td>
    </tr>
    <tr>
      <td>VLAN 30 active Fa0/8, Fa0/9, Fa0/10</td>
      <td>VLAN 30 มีพอร์ต Fa0/8-10 ถูกกำหนดให้ใช้งาน VLAN นี้</td>
    </tr>
    <tr>
      <td>VLAN 1002-1005 (fddi, token-ring etc.)</td>
      <td>VLAN พิเศษสำหรับโปรโตคอลเก่าและค่า default ที่มากับระบบ</td>
    </tr>
  </tbody>
</table>

#Config Switch VLAN COMMAND!! การกำหนด Trunk port ที่เชื่อมกับ Router เพื่อทำการ Routing
 
<p align="center">
  <img src="https://github.com/user-attachments/assets/410d6ed9-80de-4823-9432-497bb5da81c8" width="600"/>
  <br/>
</p> 

##Config ROUTER COMMAND!! การ  Config เบื้องต้น Port ที่ใช้งาน
<p>
1. Router-on-a-Stick<br>
เมื่อเราใช้ Router ต่อกับ Switch ผ่าน สาย <code>Trunk</code> เพียงเส้นเดียว เพื่อรองรับหลาย VLAN<br>
เราจะต้องแยกการรับส่งข้อมูลแต่ละ VLAN ให้ Router เข้าใจว่า packet ไหนมาจาก VLAN ไหน<br><br>
2. Sub-interface คืออะไร?<br>
Sub-interface คือการแบ่งพอร์ตจริง (เช่น <code>gigabitEthernet0/0</code>) ออกเป็น “พอร์ตเสมือน” หลายๆ อัน เช่น<br>
<code>gigabitEthernet0/0.10</code> (สำหรับ VLAN 10)<br>
<code>gigabitEthernet0/0.20</code> (สำหรับ VLAN 20)<br>
<code>gigabitEthernet0/0.30</code> (สำหรับ VLAN 30)<br><br>
3. ทำไมต้องใช้ Sub-interface?<br>
เพื่อให้ Router ทำงานแยกกันกับแต่ละ VLAN ได้<br>
แต่ละ Sub-interface จะถูกตั้งค่าให้รองรับ VLAN Tag (โดยใช้ <code>encapsulation dot1Q &lt;VLAN_ID&gt;</code>)<br>
Router จะรับรู้ว่าแพ็กเก็ตนี้มาจาก VLAN ไหน และสามารถกำหนด Gateway IP ของ VLAN นั้นๆ ได้<br><br>

4. หน้าที่หลักของ Sub-interface<br>
เป็นตัวแทน “Gateway” ของแต่ละ VLAN<br>
ใช้สำหรับทำ Inter-VLAN Routing ให้แต่ละ VLAN สื่อสารกันได้
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/106bb5b6-8732-46d1-887f-50074d547c13" width="600"/>
  <br/>
  <img src="https://github.com/user-attachments/assets/f8f1cfa2-63d9-445f-9b0d-bfda51feb552" width="600"/>
  <br/> 
  <img src="https://github.com/user-attachments/assets/4b77ac9d-bb4e-4115-8b62-4c5c45d0d85d" width="600"/>
  <br/> 
</p> 

ช่วยให้ Router แจก IP (DHCP) แยกตาม VLAN ได้<br>
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse;">
  <thead>
    <tr>
      <th>คำสั่ง / ข้อความ</th>
      <th>คำอธิบาย / ความหมาย</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Router&gt; en</td>
      <td>เข้าสู่โหมด Privileged EXEC</td>
    </tr>
    <tr>
      <td>Router# conf t</td>
      <td>เข้าสู่โหมด Configuration เพื่อแก้ไขค่าอุปกรณ์</td>
    </tr>
    <tr>
      <td>interface gigabitEthernet 0/0</td>
      <td>เลือกอินเทอร์เฟซ GigabitEthernet 0/0 เพื่อแก้ไขค่า</td>
    </tr>
    <tr>
      <td>no sh (no shutdown)</td>
      <td>เปิดใช้งานอินเทอร์เฟซ (เปิดพอร์ต)</td>
    </tr>
    <tr>
      <td>%LINK-5-CHANGED และ %LINEPROTO-5-UPDOWN</td>
      <td>แจ้งสถานะลิงก์และโปรโตคอลของอินเทอร์เฟซขึ้น (Up)</td>
    </tr>
    <tr>
      <td>do wr</td>
      <td>บันทึกการตั้งค่าปัจจุบันลงใน startup-config</td>
    </tr>
    <tr>
      <td>interface gigabitEthernet 0/0.10</td>
      <td>สร้าง Sub-interface 0/0.10 สำหรับ VLAN แยก (Dot1Q VLAN 10)</td>
    </tr>
    <tr>
      <td>encapsulation dot1Q 10</td>
      <td>ตั้งค่า Encapsulation เป็น 802.1Q พร้อม VLAN ID 10 (Tagged VLAN)   ( encapsulation = การห่อหุ้ม) </td>
    </tr>
    <tr>
      <td>ip address 192.168.1.1 255.255.255.192</td>
      <td>กำหนด IP Address และ Subnet Mask ให้กับ Sub-interface</td>
    </tr>
    <tr>
      <td>interface gigabitEthernet 0/0.20<br>encapsulation dot1Q 20<br>ip address 192.168.1.65 255.255.255.192</td>
      <td>สร้าง Sub-interface VLAN 20 พร้อม IP Address</td>
    </tr>
    <tr>
      <td>interface gigabitEthernet 0/0.30<br>encapsulation dot1Q 30<br>ip address 192.168.1.129 255.255.255.192</td>
      <td>สร้าง Sub-interface VLAN 30 พร้อม IP Address</td>
    </tr>
    <tr>
      <td>show start</td>
      <td>แสดงค่า configuration ที่บันทึกไว้ใน startup-config</td>
    </tr>
    <tr>
      <td>config output (interface GigabitEthernet0/0 etc.)</td>
      <td>รายละเอียดการตั้งค่าของอินเทอร์เฟซและ Sub-interface พร้อม IP และ VLAN</td>
    </tr>
    <tr>
      <td>interface GigabitEthernet0/1, 0/2<br>no ip address, shutdown</td>
      <td>อินเทอร์เฟซยังไม่กำหนด IP และถูกปิดใช้งาน (shutdown)</td>
    </tr>
  </tbody>
</table>  
##Config ROUTER COMMAND  DHCP !!
<p align="center">
  <img src="https://github.com/user-attachments/assets/175179c0-69ac-419f-8259-3a4dafa37228" width="600"/>
  <br/>
  <img src="https://github.com/user-attachments/assets/bc814911-15b8-47e4-9fb0-c7f8199e9029" width="600"/>
  <br/>  
</p> 
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse;">
  <thead>
    <tr>
      <th>คำสั่ง / ข้อความ</th>
      <th>คำอธิบาย / ความหมาย</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>service dhcp</td>
      <td>เปิดใช้บริการ DHCP บน Router</td>
    </tr>
    <tr>
      <td>interface GigabitEthernet0/0</td>
      <td>เลือกอินเทอร์เฟซ GigabitEthernet 0/0 เพื่อกำหนดค่า</td>
    </tr>
    <tr>
      <td>ip dhcp pool Admin-Pool</td>
      <td>สร้าง DHCP Pool ชื่อ "Admin-Pool"</td>
    </tr>
    <tr>
      <td>network 192.168.1.0 255.255.255.192</td>
      <td>กำหนดช่วง IP ที่ DHCP จะแจกในเครือข่าย 192.168.1.0/26</td>
    </tr>
    <tr>
      <td>default-router 192.168.1.1</td>
      <td>ตั้งค่า Gateway ของ DHCP Pool เป็น 192.168.1.1</td>
    </tr>
    <tr>
      <td>dns-server 192.168.1.1</td>
      <td>ตั้งค่า DNS Server ของ DHCP Pool เป็น 192.168.1.1</td>
    </tr>
    <tr>
      <td>domain-name Admin.com</td>
      <td>กำหนดชื่อโดเมนสำหรับ DHCP Pool</td>
    </tr>
    <tr>
      <td>ip dhcp pool Finance-Pool</td>
      <td>สร้าง DHCP Pool ชื่อ "Finance-Pool"</td>
    </tr>
    <tr>
      <td>network 192.168.1.64 255.255.255.192</td>
      <td>กำหนดช่วง IP ที่ DHCP จะแจกในเครือข่าย 192.168.1.64/26</td>
    </tr>
    <tr>
      <td>default-router 192.168.1.65</td>
      <td>ตั้งค่า Gateway ของ DHCP Pool เป็น 192.168.1.65</td>
    </tr>
    <tr>
      <td>dns-server 192.168.1.65</td>
      <td>ตั้งค่า DNS Server ของ DHCP Pool เป็น 192.168.1.65</td>
    </tr>
    <tr>
      <td>domain-name Finance.com</td>
      <td>กำหนดชื่อโดเมนสำหรับ DHCP Pool</td>
    </tr>
    <tr>
      <td>ip dhcp pool CS-pool</td>
      <td>สร้าง DHCP Pool ชื่อ "CS-pool"</td>
    </tr>
    <tr>
      <td>network 192.168.1.128 255.255.255.192</td>
      <td>กำหนดช่วง IP ที่ DHCP จะแจกในเครือข่าย 192.168.1.128/26 (แก้ไขค่าถูกต้องจากที่ผิด)</td>
    </tr>
    <tr>
      <td>default-router 192.168.1.129</td>
      <td>ตั้งค่า Gateway ของ DHCP Pool เป็น 192.168.1.129</td>
    </tr>
    <tr>
      <td>dns-server 192.168.1.129</td>
      <td>ตั้งค่า DNS Server ของ DHCP Pool เป็น 192.168.1.129</td>
    </tr>
    <tr>
      <td>domain-name CS.com</td>
      <td>กำหนดชื่อโดเมนสำหรับ DHCP Pool</td>
    </tr>
    <tr>
      <td>do wr</td>
      <td>บันทึกการตั้งค่าปัจจุบันลงใน startup-config</td>
    </tr>
    <tr>
      <td>ข้อความแจ้ง "invalid network"</td>
      <td>แจ้งว่า subnet mask หรือ network address ไม่ถูกต้อง ต้องแก้ไขใหม่</td>
    </tr>
  </tbody>
</table>
<footer style="text-align: center; padding: 15px 0; background-color: #f0f0f0; color: #555; font-family: Arial, sans-serif; margin-top: 40px;">
  Notes compiled by Saranphat Treepien
</footer>


