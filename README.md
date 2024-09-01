# Tigerboox-Touch
Story box as Android tablet - reverzní inženýrství

Nedávno jsem na outletovém eshopu zakoupil dětskou hudební krabičku Tigerbox Touch. Ovládání, manuál a software byly v němčině. Náš rodný jazyk je čeština a nikdo v naší rodině se německy neučí. Cílem projektu je tedy přizpůsobit hardware a software tak, aby mohl sloužit všem a bez potřeby oficiálního rozhraní v němčině.

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
5. Čekej, až naběhne recovery mod.
6. Zadej příkaz 
```
adb push mmcblk0.img /dev/block/mmcblk0
```

7. Nyní budeš dlouho čekat, než se přenos dokončí. Může to trvat i hodinu.
8. Zadej příkaz 
```
adb reboot
```
9. Hotovo. Nyní má tvůj Tigerbox obyčejný launcher a práva root včetně funkčního adb přístupu pro ladění pomocí USB-C konektoru.

## Co dál? Jaká je další výzva? Na čem pracuju?
Tigerbox má procesorový čip RK3218 a 8 GB MMC. Prvním úkolem je sestavit vlastní firmware jako soubor IMG nebo BIN, kterým lze flashnout čistý Android. K tomu potřebujeme vytvořit bootovací soubor. Pro RK3128 je jasná sekvence:
1. Miniloader
2. U-boot
3. Android boot, atd.

---

# Tigerboox-Touch
Story box as Android tablet - Reverse Engineering

Recently, I purchased a children's music box, Tigerbox Touch, from an outlet store. The controls, manual, and software were in German. Our native language is Czech, and no one in our family speaks German. The goal of this project is to adapt the hardware and software so that it can serve everyone without the need for the official German interface.

## Hardware
- Android version 5.1
- Touchscreen display
- Music amplifier
- NFC reader
- USB-C connector for charging (ADB friendly)

The device does not have an SD card slot.

## Procedure
Using ADB, I downloaded the entire 8 GB memory, modified it, and uploaded it back to the Tigerbox. As a result, the Tigerbox now has a standard Android launcher, all functions enabled, and root access. If you want to flash the modified memory to your Tigerbox, follow these steps:

1. Turn off the Tigerbox.
2. Press and hold the RESET button next to the USB-C connector with a pin.
3. Press the HOME button to turn on the Tigerbox.
4. After 10 seconds, release the RESET button.
5. Wait for the recovery mode to start.
6. Enter the command 
```
adb push mmcblk0.img /dev/block/mmcblk0
```
7. Now, wait a long time for the transfer to complete. It can take up to an hour.
8. Enter the command 
```
adb reboot
```
9. Done. Your Tigerbox now has a standard launcher and root access, including functional ADB access for debugging via the USB-C connector.

## What's next? What is the next challenge? What am I working on?
The Tigerbox has an RK3218 processor chip and 8 GB MMC. The first task is to create custom firmware as an IMG or BIN file that can flash a clean Android. For this, we need to create a boot file. For the RK3128, the sequence is clear:
1. Miniloader
2. U-boot
3. Android boot, etc.
