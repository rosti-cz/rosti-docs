# PHP

Běh PHP aplikací je u nás stejně flexibilní jako u jiných technologí, ale PHP se z principu nasazuje o něco snadněji. Podporujeme širokou škálu verzí PHP od 5.2 po ty nejnovější, vždy se skokem v minoritní verzi, takže:

* PHP 5.2
* PHP 5.3
* PHP 5.4
* PHP 5.5
* PHP 5.6
* PHP 5.x

Když se objeví nová verze, během pár týdnů ji přidáme. Aktualizujeme image vždy na nejnovější sub minor verzi, to znamená, že image PHP 5.4 obsahuje poslední vydanou verzi PHP 5.4.39. Minoritní verze budou k dispozici vždy, i po skončení jejich oficiální podpory. Na končící podporu vás budeme upozorňovat a dostanete prostor pro vyřešení ať už přechodem na novější verzi nebo setrváním u již nepodorované verze.

Aktuálně Roští používá *mod_php* ve webovém serveru Apache. Každá aplikace má vlastní Apache a to nám umožňuje vám dát například APC cache. Máme plány na přechod na *Nginx* a *php-fpm*, ale aktuálně to pro nás není priorita.

## Změna verze

Mezi verzemi PHP lze snadno přepínat. U vytvořené aplikace stačí změnit image na jinou verzi PHP a kliknout na uložit. Na pozadí se znovu vytvoří kontejner, připojí se do něj vaše data a během minuty přejdete na nové PHP. Stejně tak se můžete vrátit zpět.

## php.ini

Nastavení PHP, v souboru *php.ini*, můžete libovolně měnit. Soubor se nachází v */srv/conf/php.ini*. Jedná se o symlink do */etc/php5/conf.d/99-custom.ini*, takže výchozím stavem je */etc/php5/apache2/php.ini* a ve vašem */srv/conf/php.ini* stačí uvést hodnoty, které chcete mít proto výchozímu stavu jiné. Díky tomu můžeme měnit verze PHP a konfigurace zůstane ve většině případů kompatibilní.

Po změně *php.ini* je potřeba restartovat apache, to se provádí přes supervisor pomocí:

```shell
supervisorctl restart php
```

## Supervisor

Apache běží pod daemonem *supervisord*, jehož nastavení je možné ovlivnit v */srv/conf/supervisor.d*. Pro PHP je zde menší význam než u jiných technologií, ale do supervisoru můžete dát i další skripty běžící na pozadí. Tato možnost je určena pro zkušenější uživatele a případné využití je třeba konzultovat s [dokumentací supervisoru](http://supervisord.org/) a můžete se obrátit i na naši technickou podporu.

## Hledání problémů

Všechny informace o běhu vaší aplikace najdete v */srv/logs*. Běh aplikace můžete ovlivnit v mnoha směrech a tak by nemělo být složité problém nalézt. Pokud si ale nebudete vědět rady, napište nám na podporu a určitě nějaké řešení vymyslíme.