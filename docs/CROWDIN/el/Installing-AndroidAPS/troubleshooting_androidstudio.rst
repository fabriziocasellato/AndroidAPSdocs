Troubleshooting Android Studio
*****
Lost keystore
=====
If you use the same keystore when updating AndroidAPS you do not have to uninstall the previous version on your smartphone. That's why it is recommended to store the keystore in a save place.

In case you cannot find your old keystore anymore, proceed as follows:

1. `Export settings <../Usage/ExportImportSettings.html#how-to-export-settings>`_ on your phone.
2. Copy settings from your phone to an external location (i.e. your computer, cloud storage service...).
3. Make sure settings file "AndroidAPS Preferences" is stored safely.
4. Generate signed apk of new version as described on the `update page <../Installing-AndroidAPS/Update-to-new-version.html>`_.
5. Uninstall previous AAPS version on your phone.
6. Install new AAPS version on your phone.
7. `Import settings <../Usage/ExportImportSettings.html#how-to-export-settings>`_ - if you can't find them on your phone copy them from the external storage.
8. Keep on looping.

Προειδοποίηση μεταγλωττιστή Kotlin
=====
Αν η κατασκευή ολοκληρώθηκε με επιτυχία, αλλά έχετε προειδοποιήσεις μεταγλωττιστή Kotlin τότε απλώς αγνοήστε αυτές τις προειδοποιήσεις. 

Η εφαρμογή κατασκευάστηκε με επιτυχία και μπορεί να μεταφερθεί στο τηλέφωνο.

.. image:: ../images/GIT_WarningIgnore.PNG
  :alt: ignore Kotline compiler warning

Key was created with errors
=====
When creating a new keystore for building the signed APK, on Windows the following error message might appear

.. image:: ../images/AndroidStudio35SigningKeys.png
  :alt: Key was created with errors

This seems to be a bug with Android Studio 3.5.1 and its shipped Java environment in Windows. The key is created correctly but a recommendation is falsely displayed as an error. This can currently be ignored.

Δεν ήταν δυνατή η λήψη... / εργασία εκτός σύνδεσης
=====
Εάν λάβετε ένα μήνυμα αποτυχίας όπως αυτό

.. image:: ../images/GIT_Offline1.jpg
  :alt: Warning could not download

βεβαιωθείτε ότι η εργασία "εκτός σύνδεσης" είναι απενεργοποιημένη.

Αρχείο -> Ρυθμίσεις

.. image:: ../images/GIT_Offline2.jpg
  :alt: Settings offline work

Error: buildOutput.apkData must not be null
=====
Sometimes you might get an error message when building the apk saying

  `Errors while building APK.`
   
  `Cause: buildOutput.apkData must not be null`

This is a known bug in Android Studio 3.5 and will probably not be fixed before Android Studio 3.6. Three options:

1. Manually delete the three build folders (normal "build", build folder in "app" and build folder in "wear") and generate signed apk again.
2. Set destination folder to project folder instead of app folder as described in `this video <https://www.youtube.com/watch?v=BWUFWzG-kag>`_.
3. Change apk destination folder (different location).

No CGM data
=====
* In case you are using xDrip+: Identify receiver as described on `xDrip+ settings page <../Configuration/xdrip.html#identify-receiver>`_.
* In case you are using `patched Dexcom G6 app <../Hardware/DexcomG6.html#if-using-g6-with-patched-dexcom-app>`_: Make sure you are using the correct version from the `2.4 folder <https://github.com/dexcomapp/dexcomapp/tree/master/2.4>`_.

Μη δεσμευμένες αλλαγές
=====
Εάν λάβετε μήνυμα αποτυχίας όπως

.. image:: ../images/GIT_TerminalCheckOut0.PNG
  :alt: Failure uncommitted changes

Option 1 - Check git installation
-----
* git might be not installed correctly (must be globally available)
* when on Windows and git was just installed, you should restart your computer or at least log out and re-login once, to make git globally available after the installation
* `Check git installation <../Installing-AndroidAPS/git-install.html#check-git-settings-in-android-studio>`_
* If no git version is shown in check but git is installed on your computer, make sure Android Studio knows where `git is located <../Installing-AndroidAPS/git-install.html#set-git-path-in-android-studio>`_ on your computer.

Option 2 - Reload source code
-----
* In Android Studio select VCS -> GIT -> Reset HEAD

.. image:: ../images/GIT_TerminalCheckOut3.PNG
  :alt: Reset HEAD
   
Option 3 - Check for updates
-----
* Copy ‘git checkout --’ to clipboard (without quote signs)
* Switch to Terminal in Android Studio (lower left side of Android Studio window)

  .. image:: ../images/GIT_TerminalCheckOut1.PNG
  :alt: Android Studio Terminal
   
* Paste copied text and press return

  .. image:: ../images/GIT_TerminalCheckOut2.jpg
    :alt: GIT checkout success

Η εφαρμογή δεν έχει εγκατασταθεί
=====
.. image:: ../images/Update_AppNotInstalled.png
  :alt: phone app note installed

* Make sure you have transferred the “app-full-release.apk” file to your phone.
* If "App not installed" is displayed on your phone follow these steps:
  
1. `Export settings <../Usage/ExportImportSettings.html>`_ (in AAPS version already installed on your phone)
2. Καταργήστε την εγκατάσταση του AAPS στο τηλέφωνό σας.
3. Enable airplane mode & turn off bluetooth.
4. Εγκατάσταση νέας έκδοσης ("app-full-release.apk")
5. `Import settings <../Usage/ExportImportSettings.html>`_
6. Ενεργοποιήστε ξανά το bluetooth και απενεργοποιήστε τη λειτουργία του αεροπλάνου

Η εφαρμογή έχει εγκατασταθεί αλλά είναι παλαιά έκδοση
=====
If you build the app successfully, transferred it to your phone and installed it successfully but the version number stays the same then you might have missed to `update your local copy <../Update-to-new-version.html#update-your-local-copy>`.

Κανένα από τα παραπάνω δεν δούλεψε
=====
Εάν δεν βοηθηθήκατε από τις παραπάνω συμβουλές, μπορείτε να εξετάσετε το ενδεχόμενο να δημιουργήσετε την εφαρμογή από την αρχή:

1. `Export settings <../Usage/ExportImportSettings.html>`_ (in AAPS version already installed on your phone)
2. Have your key password and key store password ready
    In case you have forgotten passwords you can try to find them in project files as described `here <https://youtu.be/nS3wxnLgZOo>`_. Or you just use a new keystore. 
3. Build app from scratch as described `here <../Installing-AndroidAPS/Building-APK.html#download-code-and-additional-components>`_.
4.	Όταν έχετε δημιουργήσει το APK, διαγράψτε με επιτυχία την εξερχόμενη εφαρμογή στο τηλέφωνό σας, μεταφέρετε το νέο APK στο τηλέφωνό σας και εγκαταστήστε το.
5. `Import settings <../Usage/ExportImportSettings.html>`_

Στη χειρότερη περίπτωση
=====
Σε περίπτωση που ακόμη και η οικοδόμηση της εφαρμογής από το μηδέν δεν λύσει το πρόβλημά σας ίσως να θέλετε να προσπαθήσετε να απεγκαταστήσετε πλήρως το Android Studio. Μερικοί χρήστες ανέφεραν ότι αυτό λύνει το πρόβλημά τους.

Βεβαιωθείτε ότι έχετε καταργήσει την εγκατάσταση όλων των αρχείων που σχετίζονται με το Android Studio. Manuals can be found online i.e. `https://stackoverflow.com/questions/39953495/how-to-completely-uninstall-android-studio-from-windowsv10 <https://stackoverflow.com/questions/39953495/how-to-completely-uninstall-android-studio-from-windowsv10>`_.

Install Android Studio from scratch as described `here <../Installing-AndroidAPS/Building-APK.html#install-android-studio>`_ and **do not update gradle**.
