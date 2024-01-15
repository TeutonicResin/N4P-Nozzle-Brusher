# N4P-Nozzle-Brusher

 N4P Nozzle Cleaning Solution

Beim Elegoo Neptune 4 Pro erfolgt die Messung des Z-Offsets sehr nah an der Druckbettoberfläche. Dies kann dazu führen, dass Verunreinigungen an der Düse schnell zu fehlerhaften systemseitig gemessenen Z-Offsets führen. Eventuell vorhandener Materialrückstand bewirkt, dass das Bett während der Offset-Messung nach unten gedrückt wird, wodurch der gemessene Abstand zu hoch ist. Dies führt dazu, dass die Düse zu nah am Bett liegt. Die Ausprägung dieses Effekts wird durch die Härte und Menge des Rückstands beeinflusst.

Da ich nicht auf automatisiertes Bettleveling (KAMP) vor jedem Druck verzichten möchte, habe ich einen Ansatz für ein automatisiertes Reinigungssystem entworfen.

Du benötigst lediglich eine Bürste, das Makro und eine Anpassung in deinem Start-Print-Makro. Außerdem habe ich eine No-Go-Area (Polygon) für den Orca-Slicer erstellt, damit diese nicht genutzt wird.

Die Bürste habe ich von Amazon (<https://www.amazon.de/dp/B0CHNZ458F>) bezogen und den Bürstenkopf nach 40 mm am Griff abgetrennt. Du kannst auch jede halbwegs passende andere Bürste verwenden. Das parametrisierte Fusion360-Modell, eine Step-Datei sowie die STL-Datei werden bereitgestellt.

#### Installation ####

Drucke die Halterung aus hitzebeständigem Material (ABS, ASA, ...).
Setze die Bürste in die Halterung ein.
Befestige die Halterung an der vorderen linken Ecke des Druckbetts.
Kopiere das Makro (**macro.cfg**) in deine **printer.cfg**.

Füge folgende Zeile in dein Start-Makro nach dem Aufheizen des Bettes und vor dem Bettleveling ein: `CLEAN_NOZZLE EXTRUDER_TEMP={params.EXTRUDER_TEMP|default(200)|float} WIPES={10}`.
(Parameter WIPES: Anzahl der Reinigungsbewegungen (Standardwert = 10).
Reinigungstemperatur = Extrusionstemperatur - 40°C.)

Optional: Füge unter Druckereinstellungen -> ausgenommene Druckbettfläche im Orca-Slicer das folgende Polygon hinzu: `0x0,25x0,25x5,5x5,5x42,0x42`.

Dein N4P sollte nun vor jedem Bettleveling seine Düse reinigen und hoffentlich anschließend einen korrekten Z-Offset liefern.

Viel Spaß!

---

As the Z-offset measurement on the Elegoo Neptune 4 Pro occurs very close to the print bed surface, contaminants on the nozzle can quickly lead to inaccuracies in the system-measured Z-offset. Any existing material residue causes the bed to be pressed down during the offset measurement, resulting in a higher measured distance. This, in turn, positions the nozzle too close to the bed. The severity of this effect is influenced by the hardness and quantity of the residue.

Since I don't want to forgo automated bed leveling (KAMP) before each print, I've devised an approach for an automated cleaning system.

All you need is a brush, the macro, and an adjustment in your Start-Print-Macro. Additionally, I've created a No-Go-Area (Polygon) for the Orca Slicer to avoid its usage.

I sourced the brush from Amazon (https://www.amazon.de/dp/B0CHNZ458F) and cut the brush head after 40mm from the handle. You can also use any reasonably fitting alternative brush. The parameterized Fusion360 model, a Step file, and the STL file are provided.

### Installation ###:

Print the holder in a heat-resistant material (ABS, ASA, ...).
Insert the brush into the holder.
Attach the holder to the front left corner of the print bed.
Copy the macro (**macro.cfg**) into your **printer.cfg**.

Add the following line to your Start-Macro after heating the bed and before bed leveling: `CLEAN_NOZZLE EXTRUDER_TEMP={params.EXTRUDER_TEMP|default(200)|float} WIPES={10}`.
(Parameter WIPES: Number of cleaning movements (default = 10).
Cleaning temperature = Extrusion temperature - 40°C.)


Optional: Add the following polygon under Printer Settings -> Excluded Print Bed Area in the Orca Slicer: `0x0,25x0,25x5,5x5,5x42,0x42`.

Your N4P should now clean its nozzle before each bed leveling and hopefully deliver a correct Z-offset afterward.

Enjoy!
