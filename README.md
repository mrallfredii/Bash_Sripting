Pràctica 1: FSO Curs:2022-23 DEIM-ETSE-URV


Objectiu.
L’objectiu d’aquesta pràctica és familiaritzar-se amb els shell-scripts,
programació de l’intèrpret de comandes UNIX, el llenguatge de programació
Python.

Entorn de treball.
Les implementacions s’han de poder executar sobre la distribució Linux dels
laboratoris de l'assignatura. De fet, la correcció de la pràctica es farà amb un
ordinador equivalent, o en el propi laboratori.
Lliuraments.

El lliurament de la pràctica 1 de FSO cal fer-lo a través del Moodle, seguint
estrictament totes les instruccions donades. La data límit de lliurament en
primera convocatòria és la mateixa per a tots els grups de laboratori (veure
l’entrada Distribució de classes dins l’espai Moodle de l’assignatura).

Documentació a lliurar:
Lliureu un document 'tar' comprimit amb 'gzip' (extensió .tgz) amb els
següents fitxers:
• Informe amb format PDF.
• fitxers .py i fitxers shell-script.
Aquests fitxers han d'estar comentats. Cada secció i funció ha de tenir
comentaris de la mena: descripció de què fan, paràmetres d’entrada,
resultats obtinguts i feina que realitza, també quins casos d'excepció
contempla (fitxers no oberts, llistes buides, etc....)
• fitxers .tgz amb els jocs de proves realitzats.

En l’informe PDF s’ha de fer constar les següents parts:
• Índex
• Decisions de disseny
• Codi, en format text (copiar i enganxar), no en una imatge.
• Joc de proves. Descripció de les proves fetes, quins fitxers s’han obtingut
i explicació de la seva casuística.


- 1 -


Script que es vol implementar:
Volem crear un script que rebi per paràmetre tres rutes relatives o absolutes
(font1, font2 i un directori destí) i compara el contingut de font1 i de font2 a
nivell de línies si són fitxers o a nivell de fitxers/directoris recursivament si són
directoris. Volem que es mostrin:
– les diferències pel canal d'error
– un percentatge de similitud per la sortida estàndard
– la ruta absoluta dels fitxers amb data de modificació més nova per un
fitxer de log.

També voldrem crear el directori destí amb la fusió dels fitxers iguals i dels
fitxers modificats més actuals.
Per tal de fer aquest script, ho farem, a poc a poc. Tots els errors els treurem
per la sortida d’errors. (redireccionarem echo amb >&2)

1.- Crearem una funció bash tipus.sh que donat un arxiu que li passem per
paràmetre ens retorna 1 si és de tipus fitxer, 2 si és de tipus directori i 3 si és
de qualsevol altre tipus. (retorn de l’script, no per la sortida estàndard)

2.- Crearem una funció de la bash compfitxer.sh que donats dos arxius de
text els compari i tregui per la sortida d'error les línies diferents i per la sortida
estàndard un percentatge de similitud ((la suma de totes les línies iguals / la
suma de totes les línies comparades) * 100). Per a fer la comparació de fitxers
usarem la comanda diff. Considerarem que les línies en blanc, els caràcters en
blanc duplicats, i la diferència entre majúscules i minúscules no comptin a
nivell de diferència.

3.- Crearem una funció en bash mesactual.sh i en python mesactual.py que
compari la data de modificació de dos arxius i ens escrigui per la sortida
estàndard la ruta absoluta de l'arxiu modificat més actual.

4.- Crearem una funció de la bash que compari dos directoris compdir.sh a
nivell de fitxers. Els directoris els rebrà per paràmetre. Per a fer-ho usarem la
funció compfitxer.sh. Aquesta funció crearà un arxiu recents.log amb la ruta
absoluta dels fitxers modificats més recentment, i traurà per la sortida
estàndard el percentatge de similitud dels dos directoris.

5.- Crearem un script bash comptot.sh i un script python comptot.py que
usant la funció compdir.sh compari les dues rutes que rebrà per paràmetre de
manera recursiva. També volem que indiqui per la sortida estàndard el
percentatge total de similitud de les dues rutes rebudes per paràmetre. I que
en l'arxiu recents.log i hi hagi la informació de totes les rutes absolutes més
noves.

6.- Crearem un script bash creanou.sh que usant el fitxer recents.log, crearà
dins d'un directori rebut per paràmetre, els fitxers i directoris necessaris,
mantenint les dates de creació i modificació dels diferents fitxers.

7.- Crear els scripts p1.sh i p1.py que usant totes les funcions anteriors faci el
que s'ha descrit inicialment.

- 2 -
