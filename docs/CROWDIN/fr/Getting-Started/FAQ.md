# Foire Aux Questions (FAQ)

Comment ajouter des questions à la FAQ : suivez ces [instructions](../make-a-PR.md)

# Généralités

## Puis-je télécharger le fichier d'installation d'AndroidAPS ?

Non. Il n'y a pas de fichier apk téléchargeable pour AndroidAPS. Vous devez le [générer](../Installing-AndroidAPS/Building-APK.md) vous-même. En voici la raison :

AndroidAPS est utilisé pour contrôler votre pompe et injecter de l'insuline. Selon la réglementation actuelle, en Europe, tous les systèmes de classe IIa ou IIb, sont des dispositifs médicaux qui nécessitent une approbation réglementaire (un marquage CE) qui nécessitent diverses études et approbations. La distribution d'un dispositif non homologué est illégal. Des réglementations similaires existent dans d'autres parties du monde.

Ce règlement n'est pas limité aux ventes (dans le sens d'obtenir de l'argent pour quelque chose), mais s'applique à n'importe quel moyen de distribution (même en accès gratuit). Construire vous même un appareil médical est la seule façon de ne pas être touché par ces règlements.

C'est pourquoi les apk ne sont pas disponibles.

## Comment faire pour commencer ?

Tout d'abord, vous devez **obtenir des composants matériels de la boucle** :

* Une [pompe à insuline prise en charge](Pump-Choices.md), 
* un [smartphone Android](Phones.md) (l'iOS d'Apple n'est pas pris en charge par AndroidAPS - vous pouvez vérifier [iOS Loop](https://loopkit.github.io/loopdocs/)), et 
* un système de [Mesure de Glycémie en Continu (MGC)](../Configuration/BG-Source.rst). 

Deuxièmement, vous devez **configurer votre matériel**. Voir [exemple de configuration avec le tutoriel étape par étape](Sample-Setup.md).

Troisièmement, vous devez **configurer vos composants logiciels** : AndroidAPS et la source MGC/MGF.

Quatrièmement, vous devez apprendre et **comprendre le fonctionnement de référence OpenAPS pour vérifier vos paramètres de traitement**. Le principe fondateur de boucle fermée est que votre débit de basal et vos ratios Glucides/Insuline (G/I) et Sensibilité à l'Insuline (SI) sont bien déterminés. Toutes les recommandations supposent que vos besoins en basal sont satisfaits et que les pics ou les creux que vous voyez sont le résultat d'autres facteurs qui nécessitent par conséquent des ajustements (exercices, stress, etc.). Les ajustements que la boucle fermée peut effectuer ont été limités pour des raisons de sécurité (voir Débit Basal Temporaire maximum autorisé dans [Conception de référence OpenAPS](https://openaps.org/reference-design/)), ce qui signifie que vous ne devez pas perdre du dosage autorisé pour corriger un débit de basal erroné. Si par exemple vous êtes souvent bas à l'approche d'un repas, il est probable que vos débits de basal nécessitent un ajustement. Vous pouvez utiliser [autotune](http://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html#phase-c-running-autotune-for-suggested-adjustments-without-an-openaps-rig) pour analyser un grand nombre de données pour voir comment les débit de basal et/ou la SI doivent être ajustés, et aussi si le ratio G/I doit être modifié. Vous pouvez aussi tester et configurer vos débits de basal [à l'ancienne](http://integrateddiabetes.com/basal-testing/).

## Quels sont les aspects pratiques de la boucle ?

### Protection par mot de passe

Si vous ne voulez pas que vos préférences soient facilement modifiées, vous pouvez protéger le menu Préférences par un mot de passe en sélectionnant dans les préférences "Mot de passe pour paramètres" et en tapant le mot de passe choisi. La prochaine fois que vous allez dans le menu Préférences, il demandera ce mot de passe avant d'aller plus loin. Si plus tard vous souhaitez supprimer l'option de mot de passe, allez dans "Mot de passe pour paramètres" et de supprimez le texte.

### Montres connectées Android Wear

Si vous envisagez d'utiliser l'application Android Wear pour créer un bolus ou modifier des paramètres à partir de votre montre connectée, vous devez vous assurer que les notifications d'AndroidAPS ne sont pas bloquées. La confirmation de l'action se fait par notification.

### Débrancher la pompe

Si vous débranchez votre pompe pour une douche / bain / piscine / sport etc., vous devez informer AndroidAPS qu'aucune insuline n'est délivrée pour avoir l'IA correcte.

* Appuyez longuement sur le bouton "Boucle fermée" (qui sera appelé "Boucle Ouverte" si vous n'êtes pas en boucle fermée en ce moment) sur le dessus de l'écran d'accueil. 
* Sélectionnez **'Déconnecter la pompe X min (ou h)'**
* Cela réglera votre débit de basal à zéro pour cette période.
* La durée minimale d'une déconnexion est liée à la durée minimale des DBT pouvant être définies sur la pompe. Donc, si vous souhaitez vous déconnecter pendant une période plus courte, vous devez utiliser le temps de déconnexion le plus court disponible pour votre pompe et vous reconnecter manuellement comme décrit ci-dessous.
* Le bouton 'Boucle fermée' (ou 'Boucle ouverte') va basculer en rouge et être renommé 'Déconnecté (xx m)' affichant le temps de déconnexion restant.
* AAPS reconnectera automatiquement la pompe après la durée choisie et votre boucle fermée recommencera.
    
    ![Débrancher la pompe](../images/PumpDisconnect.png)

* Si la durée sélectionnée était trop longue, vous pouvez vous rebrancher manuellement.

* Appuyez longuement sur le bouton rouge "Déconnecté (x min)'.
* Sélectionnez 'Rebrancher la pompe'.
    
    ![Rebrancher la pompe](../images/PumpReconnect.png)

### Recommandations non seulement basées sur une seule lecture MGC

Pour plus de sécurité, les recommandations faites ne sont pas basées sur une unique lecture MGC, mais sur le delta moyen. Par conséquent, si vous manquez quelques données, cela peut prendre un certain temps après la lecture de nouvelles données avant qu'AndroidAPS n'active à nouveau la boucle fermée.

### Autres lectures

Il y a plusieurs blogs avec de bons conseils pour vous aider à comprendre les aspects pratiques de la boucle :

* [Réglage fin des Paramètres](http://seemycgm.com/2017/10/29/fine-tuning-settings/) Voir ma MGC
* [Pourquoi la DAI est importante](http://seemycgm.com/2017/08/09/why-dia-matters/) Voir ma MGC
* [Limiter les pics de repas](https://diyps.org/2016/07/11/picture-this-how-to-do-eating-soon-mode/) #DIYPS
* [Hormones et autosens](http://seemycgm.com/2017/06/06/hormones-2/) Voir ma MGC

## Ce que l'équipement d'urgence est recommandé d'avoir sur soi ?

Tout d'abord, vous devez prendre le même équipement d'urgence avec vous, comme tous les autres diabétique de T1 avec une pompe à insuline. En boucle fermée avec AndroidAPS, il est fortement recommandé d'avoir les équipements supplémentaires suivants avec ou près de vous :

* Pack de batterie de recharge pour de votre smartphone, votre montre et (peut-être) votre lecteur Bluetooth
* Sauvegarde dans le cloud (Dropbox, Google Drive ...) des applications que vous utilisez comme : votre dernier apk d'AndroidAPS- et vos clés et mot de passe de vos certificats, fichier de paramètres AndroidAPS, fichier de paramètres xDrip, application Dexcom patchée, ...
* Piles de la Pompe

## Comment attacher en toute sécurité la MGC/MFG ?

You can tape it: There are getting sold pre-perforated 'overpatches' for common CGM systems (ask Google or ebay). Certains Boucleur utilisent également des cassettes Kinesi standard ou des cassettes rock moins chères.

You can fix it: There are getting sold upper arm bracelets that fix the CGM/FGM with a rubber band (ask Google or ebay).

# Paramètres AndroidAPS

La liste suivante a pour but de vous aider à optimiser les paramètres. Il peut être préférable de commencer par le haut et de travailler vers le bas. Essayez de valider un seul paramètre avant d'en changer un autre. Travaillez avec de petites étapes plutôt que de faire de grands changements à la fois. Vous pouvez utiliser [Autotune](https://autotuneweb.azurewebsites.net/) pour guider votre réflexion, même si elle ne doit pas être suivie aveuglément : elle peut ne pas fonctionner correctement pour vous ou en toutes circonstances. Notez que les paramètres interagissent les uns avec les autres - vous pouvez avoir des paramètres "erronés" qui fonctionnent bien ensemble dans certaines circonstances (par exemple si une basal trop élevé se produit en même temps qu'une Gly trop élevée) mais pas dans d'autres. Cela signifie que vous devez tenir compte de tous les paramètres et vérifier qu'ils fonctionnent ensemble dans une variété de circonstances.

## Durée d'Action de l'Insuline (DAI)

### Description & test

La durée que met l'insuline pour descendre à zéro.

C'est très souvent paramétré trop court. La plupart des gens voudront au moins 5 heures, voire 6 ou 7 heures.

### Impact

Une DAI trop courte peut conduire à des hypoglycémies. Et vice-versa.

Si la DAI est trop courte, AAPS pensera que votre bolus précédent est entièrement consommé trop tôt, et si la glycémie est encore élevée, il vous injectera plus d'insuline. (En pratique, il n’attend pas aussi longtemps, mais il prédit ce qui va se passer et continue d’ajouter de l’insuline). Cela crée essentiellement un «empilement d'insuline» dont AAPS n'est pas au courant.

L'exemple d'une DAI trop courte est une hyperglycéùoe suivie d'une correction excessive de AAPS et d'une hypoglycémie derrière.

## Débits de basal (U/h)

### Description & test

La quantité d'insuline nécessaire, dans un bloc de temps donné, pour maintenir glycémie à un niveau stable.

Testez vos débits de basal en suspendant la boucle, en jeûnant, en attendant 5 heures après la nourriture, et en voyant comment la glycémie change. Répétez quelques fois.

Si la glycémie baisse, le débit de basal est trop élevé. Et vice-versa.

### Impact

Un débit de basal trop élevé peut conduire à des hypoglycémies. Et vice-versa.

'Principes de base' AAPS par rapport au débit de basal par défaut. Si le débit de basal est trop élevé, un « zéro-temp » comptabilisera une IA négative plus importante qu’il ne le devrait. Cela conduira AAPS à faire des corrections plus importante qu'il ne le devrait pour amener l'IA à zéro.

Ainsi, un débit de base trop élevé créera des hypoglycémies, à la fois avec le débit par défaut, mais également pendant quelques heures, lorsque AAPS fera les corrections pour atteindre la cible.

Inversement, un débit de basal trop faible peut conduire à des hyperglycémie, et une impossibilité à ramener les niveaux vers la cible.

## Sensibilité à l'Insuline (SI) (mmol/l/U ou mg/dl/U)

### Description & test

La diminution de glycémie prévue suite à l'administration d'1U d'insuline (en anglais ISF).

En supposant que le débit de base est correct, vous pouvez la tester en suspendant la boucle, en vérifiant que l'IA est nulle, et en prenant quelques carrés de sucre pour atteindre un niveau de glycémie "élevé" et stable.

Ensuite, prenez la quantité estimée d'insuline pour atteindre votre glycémie cible : (Gly élevée - Gly Cible) / SI

Soyez prudent, car elle est bien souvent trop faible. Trop basse signifie qu'1 U va faire baisser la glycémie plus vite que prévu.

### Impact

**Diminution de la SI** (par ex. 40 au lieu de 50) = plus agressif et plus forte, conduisant à une plus grande baisse des glycémies pour chaque unité d'insuline. Si elle est trop basse, cela peut conduire à des hypoglycémies.

**Augmentation de la SI** (par ex. 45 au lieu de 35) = moins agressif et plus faible, conduisant à une plus petite baisse des glycmémies pour chaque unité d'insuline. Si elle est trop élevée, cela peut conduire à des hyperglycémies.

**Example:**

* Glycémie est à 190 mg/dl (10,5 mmol) et la cible est à 100 mg/dl (5,6 mmol). 
* Donc, vous voulez une correction de 90 mg/dl (= 190-100).
* SI = 30 -> 90 / 30 = 3 unités d'insuline
* SI = 45 -> 90 / 45 = 2 unités d'insuline

Une SI trop faible (pas rare) peut entraîner des "sur-corrections", car AAPS pense qu'il a besoin de plus d'insuline qu'il ne faudrait pour corriger une glycémie élevée. Cela peut conduire à des glycémies "montagnes russes" (surtout lors du jeûne). Dans ce cas, vous devez augmenter votre SI. Cela conduira AAPS à donner de plus petites doses de correction, et évitera une sur-correction d'une hyperglycémie suivie d'une hypoglycémie.

Inversement, une SI trop élevée peut entraîner une sous-correction, ce qui signifie que votre glycémie reste au-dessus de la cible – c'est particulièrement perceptible après une nuit.

## Rapport Glucides/Insuline (G/I) (g/U)

### Description & test

La quantité de glucides en grammes pour chaque unité d'insuline.

En anglais les acronymes utilisés sont I:C, IC ou également Ratio Carbone (CR).

En supposant que le débit de basal est correct, vous pouvez tester en vérifiant que l'IA est nulle et que vous êtes à l'objectif glycémique, en mangeant une quantité exacte de glucides connue, et en prenant la valeur estimée d'insuline basée sur le rapport actuel de G/I. Le mieux est de manger de la nourriture de votre mangez habituellement à ce moment de la journée et de compter ses glucides précisément.

### Impact

**Diminution du G/I ** = moins de glucides par unité, c'est à dire que vous avez besoin de plus d'insuline pour une quantité fixe de glucides. Peut aussi être appelé "plus agressif".

**Augmentation du G/I ** = plus de glucides par unité, c'est à dire que vous avez besoin de moins d'insuline pour une quantité fixe de glucides. Peut aussi être appelé "moins agressif".

Si, après que le repas ait été digéré et que l'IA est revenu à zéro, votre glycémie reste plus élevée qu'avant avoir mangé, il y a de fortes chances que le ratio G/I soit trop important. Inversement, si votre glycémie est inférieure à celle d'avant la nourriture, le ratio G/I est trop faible.

Si vous avez utilisé jusqu'à présent des facteurs "unité de pain" (combien d'insuline est nécessaire pour couvrir une unité de pain ?) vous pouvez trouver des tables de conversion en ligne, par exemple[ici](https://www.mylife-diabetescare.com/files/media/03_Documents/11_Software/FAS/SOF_FAS_App_KI-Verha%CC%88ltnis_MSTR-DE-AT-CH.pdf).

# Algorithme APS

## Pourquoi est-ce que cela montre "dia: 3" dans l'onglet "OPENAPS AMA" même si j'ai une DAI différente dans mon profil ?

![AAR 3h](../images/Screenshot_AMA3h.png)

Dans l'AMA, dia ne signifie pas "Durée d'Action de l'Insuline". C'est un paramètre qui était connecté au DAI. Maintenant, cela signifie "à quel moment la correction devrait être terminée". Cela n'a rien à voir avec le calcul de l'IA. Dans OpenAPS SMB, ce paramètre n'est plus nécessaire.

## Profil

### Pourquoi utiliser une DAI min. de 5h (heure de fin de l'insuline) au lieu de 2-3h ?

Bien expliqué dans [cet article](http://www.diabettech.com/insulin/why-we-are-regularly-wrong-in-the-duration-of-insulin-action-dia-times-we-use-and-why-it-matters/). N'oubliez pas d'`ACTIVER LE PROFIL` après avoir changé votre DAI.

### Pourquoi la boucle réduit-elle fréquemment ma glycémie à des valeurs hypoglycémiques sans GA ?

Tout d'abord, vérifiez votre débit de basal et faites un test de débits de basal sans glucides. S'il est correct, c'est généralement provoqué par une SI trop faible. Une SI trop basse ressemble généralement à ceci :

![SI trop faible](../images/isf.jpg)

### Quelles sont les causes des pics post-prandiaux en boucle fermée ?

Tout d'abord, vérifiez votre débit de basal et faites un test de débits de basal sans glucides. S'il est correct et que votre glycémie est en train d'atteindre votre cible une fois que les glucides sont complètement absorbés, essayez de définir une cible temporaire pour "Début Repas imminent" dans AndroidAPS un peu avant le repas ou réfléchissez à faire un prébolus avec un décalage horaire adapté vu avec votre diabétologue. Si votre glycémie est trop élevée après le repas et encore trop élevée une fois les glucides absorbés, pensez à diminuer votre G/I avec votre diabétologue. Si votre glycémie est trop élevée en GA et trop faible après l'absorption complète des glucides, pensez à augmenter votre ratio G/I et faite un prébolus avec un décalage horaire vu avec votre diabétologue.

# Autres paramètres

## Paramètres Nightscout

### AndroidAPS NSClient indique 'non autorisé' et ne télécharge pas les données. Que puis-je faire ?

Dans NSClient, vérifiez les 'Paramètres de connexion'. Peut-être n'êtes-vous pas dans un Wi-Fi autorisé ou vous avez activé "Uniquement pendant la charge" et votre câble de charge n'est pas branché.

## Paramètres MGC

### Pourquoi ne AndroidAPS indique 'la source de glycémie actuelle ne supporte pas de filtrage avancé' ?

Si vous utilisez un autre MGC/MGF que le Dexcom G5 ou G6 en mode natif xDrip, vous obtiendrez cette alerte dans l'onglet AndroidAPS OpenAPS SMB. Voir [Lissage des données de glycémie](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md) pour plus de détails.

## Pompe

### Où placer la pompe ?

Il y a de nombreuses possibilités de placer la pompe. Peu importe si vous êtes en boucle fermée ou pas. Si vous avez plutôt une pompe à insuline tubeless et avez une Dana pour le looping, vérifiez le cathéter de 30cm avec la ceinture de ventre d'origine.

### Piles

La boucle peut réduire la durée de vie de la pile de la pompe plus rapidement que la normale car le système interagit bien plus qu'un utilisateur manuel. Il est préférable de changer la pile à 25% car la communication devient alors difficile. Vous pouvez définir des alarmes d'avertissement pour la pile de la pompe à l'aide de la variable PUMP_WARN_BATT_P de votre site Nightscout. Les astuces pour augmenter la durée de vie de la pile sont les suivantes :

* réduire la durée d'affichage de l'écran LCD (dans le menu des paramètres de la pompe)
* réduire la durée du rétro-éclairage (dans le menu des paramètres de la pompe)
* sélectionnez les paramètres de notification à un bip plutôt que de vibrer (dans le menu des paramètres de la pompe)
* appuyez uniquement sur les boutons de la pompe pour recharger, utilisez AndroidAPS pour afficher tout l'historique, le niveau de la pile et le volume du réservoir.
* l'application AndroidAPS peut souvent être fermée pour économiser de l'énergie ou de la RAM libre sur certains téléphones. Lorsque AndroidAPS est réinitialisé à chaque démarrage, il établit une connexion Bluetooth avec la pompe et relit l'historique des débits de basal et des bolus. Cela consomme de la batterie. Pour voir si c'est le cas, allez dans Préférences > NSClient et activer l'option 'Démarrage AAPS entré dans NS'. Nightscout recevra un événement à chaque redémarrage d'AndroidAPS, ce qui facilite le suivi du problème. Pour que cette situation arrive moins souvent, inscrivez AndroidAPS sur la la liste blanche des paramètres de la batterie du téléphone, afin que le moniteur d'alimentation arrête de la fermer.
    
    Par exemple, pour l'inscire sur la liste blanche avec un téléphone Samsung fonctionnant sous Android Pie :
    
    * Accédez à Paramètres -> Maintenance de l'appareil -> Batterie 
    * Faites défiler jusqu'à ce que vous trouviez AndroidAPS et sélectionnez la 
    * Désélectionnez "Mettre l'application en veille"
    * AUSSI allez dans Paramètres -> Applications -> (Trois points en haut à droite de l'écran), sélectionnez "accès spécial" -> Optimiser util. de la batterie
    * Faites défiler jusqu'à AndroidAPS et assurez-vous qu'elle est désélectionnée.

* clean battery terminals with alcohol wipe to ensure no manufacturing wax/grease remains.

* pour les [pompes Dana R/RS](../Configuration/DanaRS-Insulin-Pump.md) la procédure de démarrage établit un courant élevé à travers la batterie pour briser de manière ciblée le film passif (cela empêche la perte d'énergie pendant le stockage) mais cela ne suffit pas toujours à la casser à 100%. Supprimez et réinsérez la batterie 2 à 3 fois jusqu'à ce qu'elle affiche 100 % à l'écran, ou utilisez la clé de batterie pour faire un court circuit bref de la batterie avant de l'insérer en appliquant aux deux bornes une fraction de seconde.
* voir également plus de conseils pour les [types particuliers de piles](../Usage/Accu-Chek-Combo-Tips-for-Basic-usage#battery-type-and-causes-of-short-battery-life)

### Changement des réservoirs et des canules

The change of cartridge cannot be done via AndroidAPS but must be carried out as before directly via the pump.

* Faites un appui long sur "Boucle Ouverte" / "Boucle Fermée" de l'onglet Accueil de AndroidAPS et sélectionnez 'Suspendre la Boucle pour 1h'
* Now disconnect the pump and change the reservoir as per pump instructions.
* Une fois reconnecté à la pompe, continuez la boucle en appuyant sur "Suspendu (X m)".

Le changement d'une canule n'utilise cependant pas la fonction "Remplir tubulure" / "Remplir canule" de la pompe, mais remplit l'ensemble de perfusion et / ou la canule à l'aide d'un bolus qui n'apparaît pas dans l'historique des bolus. Cela signifie qu'il n'interrompt pas un débit de basal temporaire en cours d'exécution. Dans l'onglet Actions (ACT), utilisez le bouton AMORCER/REMPLIR pour définir la quantité d'insuline nécessaire pour remplir la tubulure et la canule et commencer la mise en place. Si la quantité n'est pas suffisante, répétez le remplissage. Vous pouvez définir les quantités par défaut dans les Préférences > Autres > Valeurs prédéfinies pour remplir&amorcer. Consultez les notices de vos canules et tubulures pour savoir combien d'unités doivent être injectées en fonction de la longueur de l'aiguille et de la longueur de la tubulure.

## Fonds d'écran

Vous pouvez trouver le fond d'écran AndroidAPS pour votre téléphone sur la [page téléphones](../Getting-Started/Phones#phone-background).

## Utilisation quotidienne

### Hygiène

#### Que faire pour prendre une douche ou un bain?

Vous pouvez retirer la pompe pour prendre une douche ou un bain. Pour cette courte période de temps, vous n'en aurez généralement pas besoin. Mais vous devez le dire à AAPS, pour que le calcul de l'IA soit juste.

Voir [description ci-dessus](../Getting-Started/FAQ#disconnect-pump).

### Travail

Selon votre type de travail, vous pouvez peut-être utiliser différents paramètres de traitement pendant les jours travaillés. En tant que boucleur, vous devez penser à un [changement de profil](../Usage/Profiles.md) pour votre journée de travail (par exemple, plus de 100% pendant 8h lorsque vous êtes assis ou moins de 100% lorsque vous êtes actif), une cible temporaire élevée ou basse ou un [décalage horaire de votre profil](../Usage/Profiles#time-shift) lorsque vous êtes debout plus tôt ou plus tard que d'habitude. Si vous utilisez des [profils Nightscout](../Configuration/Config-Builder#ns-profile), vous pouvez également créer un second profil (par exemple "Maison" et "Travail") et faire un changement de profil quotidien vers le profil dont vous avez besoin.

## Activités de loisirs

### Sports

You have to rework your old sports habits from pre-loop times. If you simply consume one or more sports carbs as before, the closed loop system will recognize them and correct them accordingly.

So, you would have more carbohydrates on board, but at the same time the loop would counteract and release insulin.

When looping you should try these steps:

* Make a [profile switch](../Usage/Profiles.md) < 100%.
* Set an [activity temp target](../Usage/temptarget#activity-temp-target) above your standard target.
* If you are using SMB make sure ["Enable SMB with high temp targets"](../Usage/Open-APS-features#enable-smb-with-high-temp-targets) and ["Enable SMB always"](../Usage/Open-APS-features#enable-smb-always) are disabled.

Pre- and postprocessing of these settings is important. Make the changes in time before sport and consider the effect of muscle filling.

If you do sports regularly at the same time (i.e. sports class in your gym) you can consider using [automation](../Usage/Automation.rst) for profile switch and TT. Location based automation might also be an idea but makes preprocessing more difficult.

The percentage of the profile switch, the value for your activity temp target and best time for the changes are individual. Start on the safe side if you are looking for the right value for you (start with lower percentage and higher TT).

### Sexe

You can remove the pump to be 'free', but you should tell it to AAPS so that the IOB calculations are right.

Voir [description ci-dessus](../Getting-Started/FAQ#disconnect-pump).

### Boire de l'alcool

Drinking alcohol is risky in closed loop mode as the algorithm cannot predict the alcohol influenced BG correctly. You have to check out your own method for treating this using the following functions in AndroidAPS:

* Deactivating closed loop mode and treating the diabetes manually or
* setting high temp targets and deactivating UAM to avoid the loop increasing IOB due to an unattended meal or
* do a profile switch to noticeably less than 100% 

When drinking alcohol, you always have to have an eye on your CGM to manually avoid a hypoglycemia by eating carbs.

### En veille

#### Comment puis-je boucler pendant la nuit sans rayonnement smartphone et WIFI ?

Many users turn the phone into airplane mode at night. If you want the loop to support you when you are sleeping, proceed as follows (this will only work with a local BG-source such as xDrip+ or patched Dexcom app, it will NOT work if you get the BG-readings via Nightscout):

1. Activez le mode avion de votre mobile.
2. Attendez que le mode avion soit actif.
3. Activez le Bluetooth.

You are not receiving calls now, nor are you connected to the internet. But the loop is still running.

Certaines personnes ont découvert des problèmes de diffusion locale (AAPS ne recevant pas les valeurs Gly de xDrip+) lorsque le téléphone est en mode avion. Dans xDrip+ accédez à Paramètres > Paramètres Inter-app > Identifiez le récepteur, et entrez `info.nightscout.androidaps`.

![xDrip+ Paramètres interapp basiques Identifier le récepteur](../images/xDrip_InterApp_NS.png)

### Voyager

#### Comment traiter les changements de fuseau horaire ?

With Dana R and Dana R Korean you don't have to do anything. For other pumps see [time zone travelling](../Usage/Timezone-traveling.md) page for more details.

## Rubriques médicales

### Hospitalisation

If you want to share some information about AndroidAPS and DIY looping with your clinicians, you can print out the [guide to AndroidAPS for clinicians](../Resources/clinician-guide-to-AndroidAPS.md).

### Rendez-vous médical avec votre diabétologue

#### Rapports

You can either show your Nightscout reports (https://YOUR-NS-SITE.com/report) or check [Nightscout Reporter](https://nightscout-reporter.zreptil.de/).