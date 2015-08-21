## SSH přístup

Přístup k aplikaci přes SSH je alfou a omegou Roští. Málo kde ho dostanete a přitom je při vývoji i nasazování tak neocenitelným nástrojem. Podívejte se, co všechno můžete s SSH u své aplikace dělat:

- Přístup k plnohodnotnému shellu (BASH)
- Bezpečný přenos souborů přes SFTP a SCP
- SOCK proxy
- Tunelování TCP portů

## Přístup k plnohodnotnému shellu (BASH)

Shell je základní vlastnost SSH. Z Linuxu a Mac OS X se ke své aplikaci dostanete pomocí *openssh*, z Windows to je [Putty](http://www.putty.org/). Po přípojení dostanete plnou moc nad tím, v čem váš kód běží. Můžete ovlivnit supervisora, proměnné prostředí, používat Midnight Commander, vim, volat svoje vlastní skripty a mnoho dalšího. Pokud zkusíte na Roští toto, jiný hosting už vám vyhovovat nebude.

## Bezpečný přenos souborů přes SFTP a SCP

SSH ale není jen o příkazové řádce. Je to univerzální kanál pro bezpečný přenos dat a jako takový umí i přenášet soubory. Podporu SFTP i SCP. Pomocí SCP se vám bude dobře provádět automatický deployment a SFTP můžete použít stejně jako FTP klienta. Proti FTP je SFTP bezpečnější, používá moderní protokol a nemá problémy s českými znaky. Na Linuxu ho podporuje každá distribuce, na Windows sáhněte po [WinSCP](https://winscp.net/eng/download.php).

## SOCK proxy

SOCK proxy vám umožní dívat se na web z pohledu vaší aplikace. Pokud zavoláte v Linuxu následující:

```bash
ssh app@pluto.rosti.cz -p 10xxx -D 1234
```

Tak se na lokálním portu 1234 otevře SOCK proxy, na kterou můžete nasměrovat svůj prohlížeč. Všechny stránky které budete procházet teď budete procházet skrze vzdálený server stejně jako by to dělala vaše aplikace.

Tuto vlastnost umí na Windows zprostředkovat Putty.

## Tunelování TCP portů

SSH tunely jsou mocným nástrojem, který vám na Roští zpřístupní přístup k databázi.