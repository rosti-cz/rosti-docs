## E-mailové schránky

E-mailové schránky na Roští mohou mít kapacitu až 25 GB, neomezený počet e-mailů a je možné je vybírat přes protokol POP a IMAP. Veškerá e-mailová komunikace je spravována servery **mail.rosti.cz** a **smtp.rosti.cz**. Nastavení vašeho klienta by tedy mělo vypadat takto:

|Parametr|Hodnota|Poznámka|
|-|-|-|
|Uživatelské jméno|vas@email.tld|celý váš mail, platí pro SMTP, IMAP i POP|
|Heslo| \*\*\*\*\*|Heslo nastavené v administraci, platí pro SMTP, IMAP i POP. Je nutné ho poslat jako PLAIN, někdy též označeno jako *normální heslo*|
|SMTP server|smtp.rosti.cz|Přihlášení pro SMTP, POP a IMAP je stejné|
|IMAP server|mail.rosti.cz|IMAP podporuje PUSH notifikace (pro váš telefon)|
|POP server|mail.rosti.cz|Zastaralý, doporučujeme nepoužívat|
|Šifrování|*TLS*, někdy též *starttls*|Není povinné, ale doporučujeme zapnout|
|Webový klient|[https://mail.rosti.cz/](https://mail.rosti.cz/) |Aplikace RoundCube|

Když se vás e-mailový klient zeptá, zda chcete použít IMAP či POP, vyberte IMAP. U mobilních telefonů obzvlášť. IMAP čte ze serveru pouze meta informace a zprávy se drží na serveru. Díky tomu můžete spravovat svoji emailovou schránku z webového rozhraní, z desktopového klienta či z mobilního telefonu. IMAP navíc podporuje PUSH notifikace, díky kterým se váš telefon nemusí dotazovat, zda dorazil nový email, ale server telefon sám upozorní, až k tomu dojde - což šetří baterii.

## Webové rozhraní

Základní přístup ke všem schránkám máte přes webové rozhraní na adrese https://mail.rosti.cz/. Čeká tam na vás webový IMAP klient [RoundCube](https://roundcube.net/), přes kterého můžete plnohodnotně spravovat svoji e-mailovou schránku. Je v češtině a používá se velmi podobně jako ostatní emailoví klienti, například jako Seznam.cz.

Pokud potřebujete ze schránky nastavit přesměrování do dalších schránek nebo rozřazovat emaily, dělá se to v Roundcube. Klikněte na *Nastavení->Filtry*. Filtry jsou rozdělené na *Sady filtrů* a jednotlivé filtry. Jako ukázka vám poslouží obrázek níže. **Na Roští nepodporujeme aliasy**, pouze přesměrování přes filtry.

![Filtry v RoundCube](imgs/rc_filtry.png) 

Sady filtrů můžete definovat například pro různé situace, třeba když jedete na dovolenou nebo když chcete přesměrovat poštu na kolegu a pak celé sady najednou povolit či zakázat. Filtry samotné mohou zprávy testovat na odesílatele, příjemce, obsah předmětu nebo i obsah samotné zprávy. Dostupnými akcemi je přesun do složky, vymazání, smazání, odeslání na jinou e-mailovou adresu a další.

