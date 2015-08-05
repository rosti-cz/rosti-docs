# Python

Podporujeme Python ve všech jeho nejčastěji používaných verzích. Dokážeme ale zařídit třeba Python 2.6 nebo i 2.5. V takovém případě se na nás obraťte. Nejnovější verze řady 2 a 3 jsou k dispozici standardně.

## Nejkratší cesta k běžící aplikaci

Když vytvoříte aplikaci, na její doméně poběží jednoduchý web se základními informacemi. Vytvořili jsme ho pro vás, abyste měli příklad, od kterého se můžete odrazít. Pro servírování stránek používáme gunicorn a jeho konfiguraci můžete měnit v _/srv/conf/supervisor.d/_. Gunicorn spustí na portu 8000 HTTP server a přes WSGI protokol ho spojí s vaším kódem. Pokud dokážete svoji aplikaci spustit na portu 8000 (jako HTTP server) jiným způsobem, můžete gunicorn úplně vypustit. Pro hlavní funkci je vyžadován pouze protokol (HTTP) a port (8000).

Všechny požadavky na váš web jdou nejdříve na náš load balancer na adrese lb1.rosti.cz. Ten požadavky posílá na server, kde běží vaše aplikace. Na této straně běží Nginx, který už požadavek nasměruje přímo do vaší aplikace. Požadavek tedy dvakrát přeskakuje, než se dostane tam kam má. Oba skoky mají v současné době svůj důvod, ale pracujeme na tom, aby byl pouze jeden.


## Virtualenv

Základním stavebním kamenem Pythonu je virtualenv. Je dostupný pro všechny verze Pythonu na Roští.cz a obsahuje předinstalovaný _pip_. Po přihlášení na SSH je aktivovaný a můžete hned instalovat závislosti vaší aplikací.

Virtualenv se nachází v adresáři _/srv/venv/_ a pokud není, můžete ho aktivovat pomocí:

  source /srv/venv/bin/activate

### Znovuvytvoření virtualenvu

Virtualenv se nedá přesouvat a při změně obrazu, například z Pythonu 2.7 a 3.4 nebo i při změně na jinou minoritní verzi, se může stát, že ho budete muset vygenerovat znovu. Závislosti vaší aplikace byste měli mít vždy někde po ruce, aby se to dalo snadno provést. Běžně bývají součástí zdrojových kódů. Takže když chcete znovuvytvořit virtualenv, použijete následující:

```shell
supervisorctl stop app
rm -rf /srv/venv
virtualenv /srv/venv
source /srv/venv/bin/activate
pip install -r /srv/app/requirements.txt
supervisorctl start app
```

První a poslední příkaz zastaví a spustí vaši aplikaci. Předposlední nainstaluje závislosti uložené v _/srv/app/requirements.txt_ a další příkazy pravděpodobně není třeba další rozebírat.

## Supervisor

Pro kompletní informace o supervisoru se prosím podívejte na [stránku dokumentace](../tools/supervisor.md), kterou věnujeme právě jemu.

Aplikaci je možné restartovat pomocí _supervisorctl_:

```shell
supervisorctl restart app
```

Když spustíte _supervisorctl_ bez parametrů, dostanete jeho konzoli s dalšími parametry. Logy z běhu pythoní aplikace najdete _/srv/logs/_ a konfiguraci supervisoru v _/srv/conf/supervisor.d/_.
