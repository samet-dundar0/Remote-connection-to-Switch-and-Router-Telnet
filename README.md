Cisco Packet Tracer: Switch ve Router Uzaktan Erişim (Telnet) Yapılandırması



Bu proje, bir ağ topolojisindeki ağ cihazlarına (Switch ve Router) Telnet protokolü kullanılarak uzaktan nasıl bağlanılacağını ve bu cihazların yönetimsel olarak nasıl yapılandırılacağını göstermektedir.



Proje Amacı: Ağ yöneticilerinin cihazların yanına gitmeden, ağ üzerindeki herhangi bir bilgisayardan konsol bağlantısı gibi cihaz yönetimi yapabilmesini sağlayan \*\*VTY (Virtual TYpe)\*\* hatlarının yapılandırılmasını simüle etmektir.





1\. Switch Uzaktan Erişim

Switchler doğrudan IP almadığı için yönetimsel bir arayüze ihtiyaç duyar

VLAN 1 Arayüzü: interface vlan 1 komutu ile bir IP adresi ve subnet mask atandı.

VTY Hatları: line vty 0 4 komutu ile 5 eşzamanlı bağlantı için izin verildi.

Şifreleme: password ve login komutları ile erişim güvenliği sağlandı.



Switch için komutlar: 

Switch>en

Switch#conf ter

Switch(config)#interface vlan 1

Switch(config-if)#ip address 192.168.1.1 255.255.255.0

Switch(config-if)#no sh

Switch(config-if)#line vty 0 4

Switch(config-line)#password 12345

Switch(config-line)#login

Switch(config-line)#exit









2\. Router Uzaktan Erişim

Router'da doğrudan fiziksel arayüzler üzerinden erişim sağlanır:

\- \*\*Interface Yapılandırması:\*\* İlgili GigabitEthernet veya FastEthernet portlarına IP atandı ve `no shutdown` ile aktif edildi.

\- \*\*Güvenlik:\*\* Telnet erişimi için VTY şifresi ve ayrıcalıklı mod (Privileged EXEC) için `enable password` ataması yapıldı.



Router için komutlar:
------------------------



Router>en

Router#conf ter

Router(config)#interface gig0/0

Router(config-if)#ip address 192.168.1.1 255.255.255.0

Router(config-if)#no sh



Router(config-if)#interface gig1/0

Router(config-if)#ip address 192.168.2.1 255.255.255.0

Router(config-if)#no sh



Router(config-if)#interface gig2/0

Router(config-if)#ip address 192.168.3.1 255.255.255.0

Router(config-if)#no sh



Router(config-if)#interface gig3/0

Router(config-if)#ip address 192.168.4.1 255.255.255.0

Router(config-if)#no sh

Router(config-if)#exit



Router(config)#enable password 12345

Router(config)#line vty 0 4

Router(config-line)#password 12345

Router(config-line)#login

Router(config-line)#exit







