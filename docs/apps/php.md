# PHP

Běh PHP aplikací je u nás stejně flexibilní jako u jiných technologí, ale PHP se z principu nasazuje o něco snadněji. Podporujeme širokou škálu verzí PHP od 5.4 po ty nejnovější, vždy se skokem v minoritní verzi, takže:

* PHP 5.4
* PHP 5.5
* PHP 5.6
* PHP 5.x

Když se objeví nová verze, během pár týdnů ji přidáme. Aktualizujeme image vždy na nejnovější sub minor verzi. Minoritní verze budou k dispozici vždy, i po skončení jejich oficiální podpory. Na končící podporu se vás budeme snažit upozorňovat a dostanete prostor pro vyřešení ať už přechodem na novější verzi nebo setrváním u již nepodporované verze.

Aktuálně Roští používá *mod_php* ve webovém serveru Apache. Každá aplikace má vlastní Apache a to nám umožňuje vám dát například APC cache. Máme plány na přechod na *Nginx* a *php-fpm*, ale aktuálně to pro nás není priorita.

## Změna verze

Mezi verzemi PHP lze snadno přepínat. U vytvořené aplikace stačí změnit image na jinou verzi PHP a kliknout na uložit. Na pozadí se znovu vytvoří kontejner, připojí se do něj vaše data a během minuty přejdete na nové PHP. Stejně tak se můžete vrátit zpět.

## php.ini

Nastavení PHP, v souboru *php.ini*, můžete libovolně měnit. Soubor se nachází v */srv/conf/php.ini*. Jedná se o symlink do */etc/php5/conf.d/99-custom.ini*, takže výchozím stavem je */etc/php5/apache2/php.ini* a ve vašem */srv/conf/php.ini* stačí uvést hodnoty, které chcete mít proti výchozímu stavu jiné. Díky tomu můžeme měnit verze PHP a konfigurace zůstane ve většině případů kompatibilní.

Po změně *php.ini* je potřeba restartovat Apache, to se provádí přes supervisor pomocí:

```shell
supervisorctl restart app
```

## Supervisor

Pro kompletní informace o supervisoru se prosím podívejte na [stránku dokumentace](../tools/supervisor.md), kterou věnujeme právě jemu.

Apache běží pod daemonem *supervisord*, jehož nastavení je možné ovlivnit v */srv/conf/supervisor.d*. Pro PHP je zde menší význam než u jiných technologií, ale do supervisoru můžete dát i další skripty běžící na pozadí. Tato možnost je určena pro zkušenější uživatele a případné využití je třeba konzultovat s [dokumentací supervisoru](http://supervisord.org/). Můžete se obrátit i na naši technickou podporu.

## Hledání problémů

Všechny informace o běhu vaší aplikace najdete v */srv/logs*. Běh aplikace můžete ovlivnit v mnoha směrech a tak by nemělo být složité problém nalézt. Pokud si ale nebudete vědět rady, napište nám na podporu a určitě nějaké řešení vymyslíme.

## Aktualizace/změna obrazu

V administraci je možné změnit obraz s verzí PHP. Na rozdíl od jiných jazyků, PHP obrazy nevyžadují žádné další kroky od uživatele a je možné s verzemi cestovat na novější i starší. Po změně obrazu se celý kontejner restartuje a jediné, na co si musíte dát pozor, je kompatibilita vašeho kódu s novým PHP.

