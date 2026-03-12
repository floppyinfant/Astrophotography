![App](orion_m42.jpg)


# Astrophotography

Ausrüstung
- DSLR (Canon EOS 60D)
- Tele-Objektiv 300mm
- Stativ
- Zeitauslöser (Intervalometer)
- Rotlicht Taschenlampe, weißes T-Shirt und Smartphone für Calibration Frames

Stellarium (App) für Orientierung am Nachthimmel
- https://stellarium.org/
- https://stellarium-web.org/

---

# Kamera Einstellungen

- RAW → Post-Processing
- Ordner anlegen für: lights, darks, flats, biases
- Noise Reduction (NR) off
- [Daylight Whitebalance → unwichtig in RAW]


Manual Mode

AF Off (Manual Focus)

Aperture / Blende offen: f/5.6 (besser kleiner)

ISO: 1600 - 6400

Shutter Speed → ca. 1s Sub-Exposure ohne Tracking mit 300mm Brennweite und APS-C Sensor (Rule of 500 oder NPF-Formula, siehe unten)

---

# Durchführung

Fokussierung auf Riegel (benutze digital zoom zur Kontrolle; der weiße Teil des Sterns muss möglichst klein sein); dann zoome heraus, suche den Orion Nebel und zoome wieder heran (ohne den Fokus zu verstellen)

Bulb Mode für Belichtungszeit = es wird so lange belichtet, so lange man den Auslöser gedrückt hält (dies wird jetzt vom Intervalometer vorgegeben)

Intervalometer: https://youtu.be/HerGWr3k06U

Light-Frames: >300 Fotos für Stacking

Calibration Frames: https://youtu.be/uIZtNCd5Ehs
- 50 Dark-Frames: same camera settings, same temperature, lens cap on; capture thermal noise from the sensor
- 30 Flat-Frames: set to A/V, same settings, T-Shirt, Phone (White Light); capture vignetting or dust present
- 50 Bias-Frames: shortest exposure (1/4000), lens cap on; capture the sensor readout noise

---

## Rule of 500

500 / (Crop Factor 1,6 x 300mm Brennweite Teleobjektiv) = 500 / 480 = 1,04

## NPF-Formula

https://web.archive.org/web/20200121080401/http://www.sahavre.fr/tutoriels/astrophoto/34-regle-npf-temps-de-pose-pour-eviter-le-file-d-etoiles (benutze Übersetzer in Browser)

Tracking → longer exposure possible
- Star-Tracker, Star Watcher
- Autoguider
- Parallaktische Montierung

---

# Stacking and Post-Processing

Siril: https://siril.org/

Stacking erhöht das “Increase Signal to Noise Ratio (SNR)”. Die Belichtungen der Fotos (Sub-Exposures) werden addiert (Total Exposure)


Workflow

Homeverzeichnis auswählen

Ordner richtig benennen: lights, darks, flats, biases

Einmalig:
- Skripte > Skripte laden (auswählen für GUI)
- Skripte > Siril Catalog Installer (Astrometrie, SPCC = Spectro Photometric Color Calibration)

Skripte > OSC Preprocessing (One Shot Color = Farbsensor)

Preprocessing (durch Skript, benötigt etwa 200GB freien Speicherplatz)
- Konvertierung: CR2 (RAW) → Fits, export als TIFF
- Kalibrierung
    - darks: Sensor Ausleserauschen, Hotpixel
    - flats: Vignettierung, Staub
    - biases: Grundrauschen
- Registrierung
- Global Star Alignment
- Stacking
- Winsorized Sigma Clipping


Bildbearbeitung (manuell)
- Crop / Freistellen
- Background Extraction = Gradient entfernen (Skripte > Python > Processing > AutoBGE)
- Astrometrie = plate solving (Werkzeuge > Astronomie): M42 für Orion Neben; Pixelgröße = 4.29mm bei Canon EOS 60D: APS-C, 18MP
- Farbkalibrierung: Spectrophotometric Color Calibration (SPCC) (Bildbearbeitung > Farbkalibrierung)
- Histogram Stretching: VeraLux Hypermetric Stretch (Skripte > Python)
- Farbsättigung
- Kurventransformation (Bildbearbeitung > Streckung)
- [Debayering, RGGB Bayer Muster]

---

References

https://www.youtube.com/playlist?list=PLssH_Otzm89CpFYOq4RV7sKtZKzHKKYJw

