# DNS a domény

Roští zatím neregistruje domény, ale postará se o vaše DNS záznamy. Je lepší, pokud nasměrujete vaše domény na naše DNS servery. Můžeme pak editovat DNS záznamy podle toho, jak postupuje vývoj Roští.cz. Neměníme adresy často, ale jednou za pár let musíme.

Až budete registrovat doménu, tak v případě, že se jedná o _.cz_ doménu, nastavte ji *NSSET* na *ROSTICZ*.

V případě, že se jedná o jinou než _.cz_ doménu, nastavte NS servery:

* ns1.rosti.cz
* ns2.rosti.cz

DNS zóny pro vaše domény se vygenerují společně s vytvořením aplikace. Nic víc nemusíte tedy řešit a DNS zónu můžete libovolně editovat z administrace.

# Nastavení pouze A, AAAA a MX zánamů

Když se u nás rozhodnete mít jen jednu subdoménu nebo třeba jen poštovní server, použijte následující hodnoty:

| Typ záznamu | IP adresa            |
|-------------|----------------------|
| A           | 83.167.253.74        |
| AAAA        | 2a01:430:225::18     |
| MX          | mail.rosti.cz        |


<br>
Pokud to je ale jen trochu možné, použijte první možnost - nasměrování NS serverů k nám. Usnadníte sobě i nás řadu problémů.

Registraci domén pro vás připravujeme, máme vybrané API, napsanou část podpory, ale poprosíme vás ještě o strpení.
