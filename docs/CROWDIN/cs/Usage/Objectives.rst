Cíle
**********

AndroidAPS má sadu Cílů, které musíte dokončit a které vás provedou jeho funkcemi a nastaveními tak, aby pro vás smyčka nebyla nebezpečná.  Zajistí vám, že jste nastavili všechny detaily z dříve uvedených sekcí správně, že rozumíte tomu, co váš systém dělá a proč, a že mu můžete důvěřovat.

Pokud měníte telefon, můžete si `exportovat své nastavení <../Usage/ExportImportSettings.html>`_ a váš postup (již splněné cíle) bude zachován. Kromě vašeho postupu se exportem/importem uloží řada jiných nastavení, například vaše bezpečnostní nastavení jako maximální bolus apod.  Pokud neabsolvujete export/import svých nastavení, pak budete muset začít plnit cíle znovu od začátku.  Je dobrý nápad `zálohovat Vaše nastavení <../Usage/ExportImportSettings.html>`_ často jen tak pro jistotu.
 
Cíl 1: Nastavit vizualizaci a monitoring, analyzovat bazály a poměry
=================================================================================
* Zvolte správný zdroj glykémie pro svou kombinaci zařízení.  Více informací viz `Zdroj glykémií <../Configuration/BG-Source.html>`_.
* Vyberte správnou pumpu na kartě Konfigurace (zvolte Virtuální pumpu, pokud používáte model pumpy bez ovladače v AndroidAPS – pouze pro otevřenou smyčku) a na kartě pumpy ověřte, že váš model pumpy dokáže komunikovat s aplikací AndroidAPS a přenášet do ní svůj stav.  
* Pokud používáte pumpu DanaR, ujistěte se, že jste postupovali podle pokynů v části `Inzulinová pumpa DanaR <../Configuration/DanaR-Insulin-Pump.html>`_ a že je propojená s AndroidAPS.
* Postupujte podle pokynů na stránce `Nightscout <../Installing-AndroidAPS/Nightscout.html>`_ a ověřte, že Nightscout může přijímat a zobrazovat tato data.
* Všimněte si, že adresa URL v NSClientovi musí být ** BEZ /api/v1 /** na konci - viz `Nastavení NSClienta v předvolbách <../Configuration/Preferences.html#ns-client>`_.

*Možná bude nutné počkat na další odečet glykémie, než AndroidAPS změnu zaregistruje.*

Cíl 2: Naučte se ovládat AndroidAPS
============================
* Proveďte několik akcí v AndroidAPS, jak je popsáno v tomto cíli.
* Click on the orange text "Not completed yet" to access the to-dos.
* Odkazy budou poskytnuty jako vodítko pro případ, že dosud nejste obeznámeni se specifickou akcí.

   .. image:: ../images/Objective2_V2_5.png
     :alt: Screenshot cíl 2

Cíl 3: Prokázat své znalosti
=================================
* Pass a multiple-choice exam testing your AndroidAPS knowledge.
* Click on the orange text "Not completed yet" to access the page with the question and answering options.

   .. image:: ../images/Objective3_V2_5.png
     :alt: Screenshot cíl 3

* Links will be provided to guide you in case you are unsure about the correct answers yet.
* Only if you have been closed looping with another system (i.e. OpenAPS, iOS Loop) before and can proof this (i.e. at least 3 months of looping data in Nightscout), you can send an email to `objectives@androidaps.org <mailto:objectives@androidaps.org>`_ with your NS address and request code to bypass the rest of objectives.

Cíl 4: Začít s otevřenou smyčkou
=====================================
* Vyberte možnost Otevřená smyčka buď v Nastavení, nebo stisknutím a podržením tlačítka Smyčka v levém horním rohu hlavní obrazovky.
* Projděte `Nastavení <../Configuration/Preferences.html>`_ pro nastavení.
* Ručně nařiďte alespoň 20 dočasných bazálních dávek, které vám systém navrhuje, a to během 7 dní; zadejte je do své pumpy a potvrďte v AndroidAPS, že jste návrhy přijali.  Ujistěte se, že se tyto údaje zobrazí v AndroidAPS a Nightscoutu.
* Povolte `dočasné cíle <../Usage/temptarget.html>`_ pokud je to nutné. Použijte dočasný cíl Hypoglykémie, abyste systému zabránili v příliš agresivních korekcích, pokud by glykémie po vyřešení hypoglykémie stoupala. 

Cíl 5: Porozumění otevřené smyčce, včetně doporučení pro dočasné bazály
===================================================================================
* Začněte chápat úvahy, které se skrývají za doporučeními dočasných bazálních dávek, tím, že si projdete `logiku <https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/Understand-determine-basal.html>`_ a budete sledovat graf předpovědí na `domovské obrazovce AndroidAPS <../Getting-Started/Screenshots.html#sekce-e>`_/ v Nightscoutu. Také si v aplikaci procházejte výstupy z výpočtů na záložce OpenAPS.
 
Cíl nastavte o něco výše než obvykle, dokud si nebudete jisti správností výpočtů a nastavení.  Systém umožňuje

* dolní cílová hodnota musí být minimálně 4 mmol (72 mg/dl) nebo nejvýše 10 mmol (180 mg/dl) 
* horní cílová hodnota musí být minimálně 5 mmol (90 mg/dl) nebo nejvýše 15 mmol (225 mg/dl)
* dočasný cíl jako jediná hodnota může být kdekoliv mezi 4 až 15 mmol (72 mg/dl až 225 mg/dl)

Cíl je hodnota, o kterou se opírá kalkulace, nikoliv hodnota, na které byste chtěli svou glykémii držet.  Pokud je váš cíl velmi široký (řekněme 3 nebo více mmol široký), často se objeví pouze málo AAPS akcí. To je proto, že predikovaná glykémie bude někde v tomto širokém rozmezí a proto není doporučováno mnoho dočasných bazálů. 

Snažte se tedy experimentováním upravit svůj cíl tak, aby nebyl rozptyl hodnot příliš velký (řekněme 1 mmol nebo méně) a přitom sledujte, jak se mění chování systému.  

Cílový rozsah hodnot v grafu na hlavní obrazovce (zelené linky), ve kterých chcete udržovat svou glykémii, můžete změnit změnou hodnot v části `Nastavení <../Configuration/Preferences.html>`_ > Rozsah pro zobrazení.
 
.. image:: ../images/sign_stop.png
  :alt: Znaménko Stop

Zastavte se zde, pokud používáte otevřenou smyčku s virtuální pumpou – neklikejte na tlačítko Zkontrolovat na konci tohoto cíle.
--------------------------

.. image:: ./images/blank.png
  :alt: prázdný

Cíl 6: Začátek uzavřené smyčky - s pozastavením pumpy při nízké glykémii
================================================================
.. image:: ../images/sign_warning.png
  :alt: Varování
  
U 6. cíle nebude uzavřená smyčka korigovat vysokou glykémii, bude pouze zastavovat před nízkou. Na vysoké glykémie musíte ručně dopíchnout vy sami!
---------------------------

* Vyberte Uzavřená smyčka buď z `Nastavení <../Configuration/Preferences.html>`_, nebo stisknutím a držením tlačítka Otevřená smyčka z levého horního rohu hlavní stránky.
* Nastavte cílový rozsah mírně vyšší, než který je pro vás běžný, jen pro jistotu.
* Sledujte, jak jsou aktivní dočasné bazální dávky buď prohlížením modrého textu bazálu na hlavní stránce anebo v modrém vykreslení bazálů na grafu.
* Ujistěte se, že AndroidAPS je teď nastavený tak, že po dobu 5 dní nemusíte řešit nízké glykémie.  Pokud stále řešíte časté nebo vážné výskyty nízkých glykémií, zvažte úpravu svého DIA, bazálů, citlivosti a sacharidových poměrů.
* You don't have to change your settings. During objective 6 maxIOB setting is internally set to zero automatically. This override will be reversed when moving to objective 7.

*Systém přepíše vaše nastavení maxIOB na nulu, což znamená, že pokud glykémie klesá, může snížit bazál, ale pokud glykémie stoupá, pak zvýší bazál pouze v případě, že IOB je záporný (z předchozího sníženého bazálu nebo zastavené pumpy). Pokud IOB není záporný, vaše bazální dávky zůstanou stejné jako ve vámi zvoleném aktivním profilu.  Bez možnosti zvýšit bazál při srovnání křivky glykémie se vám dočasně může stávat, že po vyřešení hypoglykémie bude následovat přílišný vzestup glykémie.*

Cíl 7: Vyladit uzavřenou smyčku, zvyšovat max IOB nad 0 a postupně snižovat cílovou glykémii
=========================================================
* Zvyšte hodnotu 'Maximální celkový IOB, který OpenAPS nemůže překročit' (v OpenAPS se tento parametr označuje jako 'max-iob') nad 0 po dobu 1 dne. Výchozím doporučením je použít "průměrnou hodnotu bolusu k jídlu + 3× maximální denní bazální dávku" (pro algoritmus SMB) nebo "3× maximální denní bazální dávku" (pro starší algoritmus AMA). Tyto hodnoty byste však měli zvyšovat postupně, dokud neověříte, že jsou nastaveny správně (maximální denní bazální dávka = maximální bazální dávka za hodinu během dne).

  Toto doporučení by mělo být považováno za výchozí bod. Pokud ho nastavíte na 3x a uvidíte kroky, které vás rychle stahují dolů, pak snižte toto číslo. Pokud jste velmi rezistentní na inzulín, pomalu ho zvyšujte.

   .. image:: ../images/MaxDailyBasal2.png
     :alt: max denní bazál

* Až si budete jistí množstvím IOB, které sedí vašemu vzoru smyčky, pak snižte své cílové glykémie na požadovanou úroveň.


Cíl 8: Upravit bazály a poměry, když bude potřeba, a povolit automatickou detekci citlivosti na inzulín
=============================================
* Můžete použít `autotune <https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html>`_ jako kontrolní nástroj, že vaše bazály zůstávají přesné, anebo si udělejte tradiční bazální test.
* Povolte `automatickou detekci citlivosti <../Usage/Open-APS-features.html>`_ po dobu 7 dní a sledujte bílou křivku na grafu hlavní stránce, jak vaše citlivost na inzulín může růst a klesat jako výsledek cvičení nebo hormonů apod., a při tom sledujte na kartě OpenAPS výslednou zprávu, jak podle toho smyčka upravila vaše bazály a/nebo cíle.

*Pokud jste tak dosud neučinili, nezapomeňte zaznamenat své zkušenosti se smyčkou do `tohoto formuláře <http://bit.ly/nowlooping>`_ a označte AndroidAPS jako typ své DIY smyčky.*


Cíl 9: Povolit další funkce oref0 pro běžné používání, jako je AMA (advanced meal assist)
==============================================
* Nyní byste si již měli být jisti tím, jak AndroidAPS funguje a která nastavení jsou pro váš konkrétní diabetes nejlepší
* Následně můžete po dobu 28 snů vyzkoušet další funkce, které nabízejí ještě větší úroveň automatizace, jako je například `advanced meal assist <../Usage/Open-APS-features.html#advanced-meal-assist-ama>`_


Cíl 10: Povolit další funkce oref1 pro běžné používání, jako je SMB (super micro bolus)
===============================================
* Musíte si přečíst `Kapitolu o SMB zde na wiki<../Usage/Open-APS-features.html#super-micro-bolus-smb>`_ a `Kapitolu oref1 v dokumentaci k openAPS <https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html>`_, abyste porozuměli tomu, jak SMB funguje, zejména na čem stojí princip nulových dočasných bazálů.
* Následně byste měli `zvýšit maxIOB <../Usage/Open-APS-features.html#maximum-total-iob-openaps-cant-go-over-openaps-max-iob>`_ tak, aby SMB správně fungovaly. maxIOB nyní zahrnuje veškerý IOB, nejen ten z bazálů. That is, if given a bolus of 8 U for a meal and maxIOB is 7 U, no SMBs will be delivered until IOB drops below 7 U. A good start is maxIOB = average mealbolus + 3x max daily basal (max daily basal = the maximum hourly value in any time segment of the day - see `objective 7 <../Usage/Objectives.html#objective-7-tuning-the-closed-loop-raising-max-iob-above-0-and-gradually-lowering-bg-targets>`_ for an illustration)
* Výchozí hodnota absorpce „min_5m_carbimpact“ se při přechodu z AMA na SMB mění ze 3 na 8. Pokud přecházíte z AMA na SMB, musíte toto nastavení změnit ručně
