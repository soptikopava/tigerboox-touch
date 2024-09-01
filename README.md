# Tigerboox-Touch
Story box as Android tablet - reverzní inženýrství

Nedávno jsem na outletovém eshopu zakoupil dětskou hudební krabičku Tigerbox Touch. Ovládání, manuál a software byly v němčině. Náš rodný jazyk je čeština a nikdo v naší rodině se německy neučí. Cílem projektu je tedy přizpůsobit hardware a software tak, aby mohl sloužit všem a bez potřeby oficiálního rozhraní v němčině.
![tigerbox touch](https://github.com/soptikopava/tigerboox-touch/blob/main/pics/1725210316353.jpg)
## Hardware
- Android verze 5.1
- Dotykový displej
- Hudební zesilovač
- NFC čtecí zařízení
- USB-C konektor pro nabíjení (ADB přátelský)

Zařízení neobsahuje možnost vložit SD kartu.

## Postup
Pomocí ADB jsem stáhl celou 8 GB paměť, upravil a nahrál zpět do Tigerboxu. Výsledkem je, že Tigerbox má nyní obyčejný Android launcher, všechny funkce povolené a má práva Root. Pokud si chceš upravenou paměť flashnout do svého Tigerboxu, postupuj takto:

1. Vypni Tigerbox.
2. Stiskni a drž špendlíkem tlačítko RESET vedle USB-C konektoru.
3. Stiskni tlačítko HOME pro zapnutí Tigerboxu.
4. Po 10 sekundách pusť RESET.
![reset](https://github.com/soptikopava/tigerboox-touch/blob/main/pics/1725210316306.jpg)
5. Čekej, až naběhne recovery mod.
![recovery](https://github.com/soptikopava/tigerboox-touch/blob/main/pics/1725210496431.jpg)
6. připoj tigerbox pomocí  USB-C k PC
7. Zadej příkaz 
```
adb root
adb push mmcblk0.img /dev/block/mmcblk0
```

7. Nyní budeš dlouho čekat, než se přenos dokončí. Může to trvat i hodinu.
8. Zadej příkaz 
```
adb reboot
```
9. Hotovo. Nyní má tvůj Tigerbox obyčejný launcher a práva root včetně funkčního adb přístupu pro ladění pomocí USB-C konektoru.
![reset](https://github.com/soptikopava/tigerboox-touch/blob/main/pics/1725210316320.jpg)

## Co dál? Jaká je další výzva? Na čem pracuju?
Tigerbox má procesorový čip RK3218 a 8 GB MMC. Prvním úkolem je sestavit vlastní firmware jako soubor IMG nebo BIN, kterým lze flashnout čistý Android. K tomu potřebujeme vytvořit bootovací soubor. Pro RK3128 je jasná sekvence:
1. Miniloader
2. U-boot
3. Android boot, atd.

---
Sure, here's the translation:

# Tigerboox-Touch
Story box as Android tablet - Reverse Engineering

Recently, I purchased a children's music box, the Tigerbox Touch, from an outlet e-shop. The controls, manual, and software were in German. Our native language is Czech, and no one in our family speaks German. The goal of this project is to adapt the hardware and software so that it can serve everyone without the need for the official German interface.
![tigerbox touch](https://github.com/soptikopava/tigerboox-touch/blob/main/pics/1725210316353.jpg)
## Hardware
- Android version 5.1
- Touchscreen
- Music amplifier
- NFC reader
- USB-C connector for charging (ADB friendly)

The device does not have an option to insert an SD card.

## Procedure
Using ADB, I downloaded the entire 8 GB memory, modified it, and uploaded it back to the Tigerbox. As a result, the Tigerbox now has a standard Android launcher, all functions enabled, and root rights. If you want to flash the modified memory to your Tigerbox, follow these steps:

1. Turn off the Tigerbox.
2. Press and hold the RESET button next to the USB-C connector with a pin.
3. Press the HOME button to turn on the Tigerbox.
4. After 10 seconds, release the RESET button.
![reset](https://github.com/soptikopava/tigerboox-touch/blob/main/pics/1725210316306.jpg)
5. Wait for the recovery mode to start.
![recovery](https://github.com/soptikopava/tigerboox-touch/blob/main/pics/1725210496431.jpg)
6. Connect the Tigerbox to the PC using USB-C.
7. Enter the command:
```
adb root
adb push mmcblk0.img /dev/block/mmcblk0
```

8. Now, wait a long time for the transfer to complete. It can take up to an hour.
9. Enter the command:
```
adb reboot
```
10. Done. Now your Tigerbox has a standard launcher and root rights, including functional ADB access for debugging via the USB-C connector.
![reset](https://github.com/soptikopava/tigerboox-touch/blob/main/pics/1725210316320.jpg)

## What's next? What is the next challenge? What am I working on?
The Tigerbox has an RK3218 processor chip and 8 GB MMC. The first task is to build our own firmware as an IMG or BIN file, which can be used to flash a clean Android. For this, we need to create a boot file. For RK3128, the sequence is clear:
1. Miniloader
2. U-boot
3. Android boot, etc.
