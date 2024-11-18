# bevardis19.github.io

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nusikaltimų pasekmės ir Baudos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            background-color: #000000;
            color: #FFFFFF;
        }

        .section-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 10px;
        }

        .section-title {
            font-size: 20px;
            font-weight: bold;
            margin: 10px 0;
            color: #FFFFFF;
        }

        .button-section {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
        }

        .button, .double-ket-button {
            background-color: #007BFF;
            border: none;
            color: white;
            padding: 10px 15px;
            border-radius: 5px;
            font-size: 14px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .button.selected, .double-ket-button.selected {
            background-color: #28a745;
        }

        .total, .total-second {
            font-size: 24px;
            font-weight: bold;
            margin: 10px 0;
            color: #FFFFFF;
        }
    </style>
</head>
<body>

    <h1>Nusikaltimų pasekmės ir Baudos</h1>

    <!-- Button to double KET fines and jail times -->
    <button class="double-ket-button" onclick="doubleKETPenalties()">Padvigubinti KET pažeidimų baudas</button>

    <!-- Total fines and jail time display -->
    <div class="total" id="totalSum">Baudos: 0</div>
    <div class="total-second" id="totalAdditionalSum">Kalejimo laikas: 0</div>

    <!-- Crime Sections -->
    <div class="section-container">
        <div class="section-title">Nusikalstama veikla</div>
        <div class="button-section">
            <button class="button" onclick="toggleButton(5000, 35, 'Buvimas neleistinoje lokacijoje', 'ket')">Buvimas neleistinoje lokacijoje</button>
            <button class="button" onclick="toggleButton(5000, 35, 'Trp. vagystė', 'ket')">Trp. vagystė</button>
            <button class="button" onclick="toggleButton(3000, 45, 'Ginkluotas pasikėsinimas į gyvybę', 'ket')">Ginkluotas pasikėsinimas į gyvybę</button>
            <button class="button" onclick="toggleButton(5000, 45, 'Daugkartinis namų plėšimas', 'ket')">Daugkartinis namų plėšimas</button>
            <button class="button" onclick="toggleButton(2000, 15, 'Svetimo turto išviliojimas', 'ket')">Svetimo turto išviliojimas</button>
            <button class="button" onclick="toggleButton(5000, 45, 'Pasikesinimas i pareiguno/ų gyvybę/es', 'ket')">Pasikesinimas i pareiguno/ų gyvybę/es</button>
            <button class="button" onclick="toggleButton(2500, 10, 'Neteisėtų pinigų laikymas (nuo 3k iki 20k)', 'ket')">Neteisėtų pinigų laikymas (nuo 3k iki 20k)</button>
            <button class="button" onclick="toggleButton(7500, 20, 'Neteisėtų pinigų laikymas (nuo 20k)', 'ket')">Neteisėtų pinigų laikymas (nuo 20k)</button>
            <button class="button" onclick="toggleButton(5000, 45, 'Neteisėto ginklo laikymas', 'ket')">Neteisėto ginklo laikymas</button>
            <button class="button" onclick="toggleButton(7500, 25, 'Narkotinių medžiagų turėjimas (siekiant parduoti)', 'ket')">Narkotinių medžiagų turėjimas (siekiant parduoti)</button>
            <button class="button" onclick="toggleButton(2500, 45, 'Narkotinių medžiagų turėjimas', 'non-ket')">Narkotinių medžiagų turėjimas</button>
            <button class="button" onclick="toggleButton(2000, 15, 'bendradarbiavimas nusikalstamoje veikloje', 'ket')">bendradarbiavimas nusikalstamoje veikloje</button>
            <button class="button" onclick="toggleButton(4500, 45, 'Banko plėšimas', 'ket')">Banko plėšimas</button>
            <button class="button" onclick="toggleButton(5000, 30, 'Brakonieriavimas', 'ket')">Brakonieriavimas</button>
            <button class="button" onclick="toggleButton(2500, 45, 'Asmens pagrobimas', 'ket')">Asmens pagrobimas</button>
            <button class="button" onclick="toggleButton(4500, 60, 'Pareigūno/Mediko/Mechaniko užpuolimas/pasikesinimas i gyvybę', 'ket')">Pareigūno/Mediko/Mechaniko užpuolimas/pasikesinimas i gyvybę</button>
            <button class="button" onclick="toggleButton(5000, 75, 'Organizuotas nusikalstamumas', 'ket')">Organizuotas nusikalstamumas</button>
            <button class="button" onclick="toggleButton(4500, 55, 'Šarvuočio plėšimas', 'ket')">Šarvuočio plėšimas</button>
            <button class="button" onclick="toggleButton(2500, 30, 'Neteisėtas medžiojimas ar žvejojimas arba kitoks laukinės gyvūnijos išteklių naudojimas', 'non-ket')">Neteisėtas medžiojimas ar žvejojimas arba kitoks laukinės gyvūnijos išteklių naudojimas</button>
            <button class="button" onclick="toggleButton(800, 10, 'Svetimo turto apgadinimas', 'non-ket')">Svetimo turto apgadinimas</button>
            <button class="button" onclick="toggleButton(2000, 10, 'Svetimo turto vagystė', 'non-ket')">Svetimo turto vagystė</button>
            <button class="button" onclick="toggleButton(5000, 40, 'Ginkluotas apiplėšimas (įstaiga)', 'non-ket')">Ginkluotas apiplėšimas (įstaiga)</button>
            <button class="button" onclick="toggleButton(2500, 50, 'Ginkluotas apiplėšimas (asmuo)', 'non-ket')">Ginkluotas apiplėšimas (asmuo)</button>
            <button class="button" onclick="toggleButton(3000, 45, 'Reketas', 'non-ket')">Reketas</button>
            <button class="button" onclick="toggleButton(10000, 70, 'Prekyba ginklais neturint tam leidimo', 'non-ket')">Prekyba ginklais neturint tam leidimo</button>
            <button class="button" onclick="toggleButton(3500, 30, 'Neteisėtų cheminių medžiagų laikymas (didelis kiekis)', 'non-ket')">Neteisėtų cheminių medžiagų laikymas (didelis kiekis)</button>
            
        </div>
    </div>

    <div class="section-container">
        <div class="section-title">Smurtiniai nusikaltimai</div>
        <div class="button-section">
            <button class="button" onclick="toggleButton(800, 5, 'Smulkių sužalojimų sukėlimas', 'non-ket')">Smulkių sužalojimų sukėlimas</button>
            <button class="button" onclick="toggleButton(2000, 10, 'Apiplėšimas', 'non-ket')">Apiplėšimas</button>
            <button class="button" onclick="toggleButton(4000, 30, 'Piktybiniai sužalojimai', 'non-ket')">Piktybiniai sužalojimai</button>
            <button class="button" onclick="toggleButton(6000, 60, 'Žmogžudystė', 'non-ket')">Žmogžudystė</button>
            <button class="button" onclick="toggleButton(2500, 15, 'Kankinimai', 'non-ket')">Kankinimai</button>
            <button class="button" onclick="toggleButton(2500, 30, 'Riaušių kurstymas', 'non-ket')">Riaušių kurstymas</button>
            <button class="button" onclick="toggleButton(21000, 90, 'Daugybinė žmogžudystė', 'non-ket')">Daugybinė žmogžudystė</button>
            <button class="button" onclick="toggleButton(9000, 60, 'Žmogžudystė', 'non-ket')">Žmogžudystė</button>
            <button class="button" onclick="toggleButton(2500, 45, 'Ginkluotas pasikėsinimas į gyvybę', 'non-ket')">Ginkluotas pasikėsinimas į gyvybę</button>
            <button class="button" onclick="toggleButton(1500, 20, 'Daugybinių sužalojimų sukėlimas', 'non-ket')">Daugybinių sužalojimų sukėlimas</button>
            <button class="button" onclick="toggleButton(800, 10, 'Smulkių sužalojimų sukėlimas', 'non-ket')">Smulkių sužalojimų sukėlimas</button>
        </div>
    </div>

    <div class="section-container">
        <div class="section-title">KET pažeidimai</div>
        <div class="button-section">
            <button class="button" onclick="toggleButton(850, 0, 'KET pažeidimas', 'ket')">KET pažeidimas</button>
            <button class="button" onclick="toggleButton(1000, 0, 'KET pažeidimas', 'ket')">KET pažeidimas</button>
            <button class="button" onclick="toggleButton(1250, 0, 'KET pažeidimas', 'ket')">KET pažeidimas</button>
            <button class="button" onclick="toggleButton(3000, 0, 'KET kompleksinis', 'ket')">KET kompleksinis</button>
        </div>
    </div>

    <div class="section-container">
        <div class="section-title">Viešos tvarkos pažeidimai</div>
        <div class="button-section">
            <button class="button" onclick="toggleButton(500, 5, 'Triukšmo kėlimas naktį', 'non-ket')">Triukšmo kėlimas naktį</button>
            <button class="button" onclick="toggleButton(1000, 10, 'Viešas neblaivumas', 'non-ket')">Viešas neblaivumas</button>
            <button class="button" onclick="toggleButton(1500, 15, 'Nevykdomas pareigūnų reikalavimas', 'non-ket')">Nevykdomas pareigūnų reikalavimas</button>
            <button class="button" onclick="toggleButton(2000, 20, 'Nesusiklausymas į viešąją tvarką', 'non-ket')">Nesusiklausymas į viešąją tvarką</button>
            <button class="button" onclick="toggleButton(2500, 25, 'Netinkamas elgesys viešose vietose', 'non-ket')">Netinkamas elgesys viešose vietose</button>
            <button class="button" onclick="toggleButton(800, 0, 'Melagingas iškvietimas', 'non-ket')">Melagingas iškvietimas</button>
            <button class="button" onclick="toggleButton(2000, 10, 'Klaidinamos informacijos pateikimas siekiant pakenkti tyrimo eigai', 'non-ket')">Klaidinamos informacijos pateikimas siekiant pakenkti tyrimo eigai</button>
            <button class="button" onclick="toggleButton(900, 0, 'Trukdymas pareigūnui vykdyti teisingumą', 'non-ket')">Trukdymas pareigūnui vykdyti teisingumą</button>
            <button class="button" onclick="toggleButton(450, 0, 'Nedidelis viešosios tvarkos pažeidimas', 'non-ket')">Nedidelis viešosios tvarkos pažeidimas</button>
            <button class="button" onclick="toggleButton(850, 0, 'Viešosios tvarkos pažeidimas', 'non-ket')">Viešosios tvarkos pažeidimas</button>
            <button class="button" onclick="toggleButton(300, 0, 'Tapatybės slėpimas viešoje vietoje esant su kauke', 'non-ket')">Tapatybės slėpimas viešoje vietoje esant su kauke</button>
            <button class="button" onclick="toggleButton(900, 20, 'Ginklo demonstravimas viešoje vietoje', 'non-ket')">Ginklo demonstravimas viešoje vietoje</button>
            
        </div>
    </div>

    <!-- JavaScript Functionality -->
    <script>
        let totalFine = 0;
        let totalJailTime = 0;
        let selectedButtons = {};

        function updateTotals() {
            totalFine = 0;
            totalJailTime = 0;
            for (const key in selectedButtons) {
                totalFine += selectedButtons[key].fine;
                totalJailTime += selectedButtons[key].jail;
            }
            document.getElementById("totalSum").innerText = `Baudos: ${totalFine}`;
            document.getElementById("totalAdditionalSum").innerText = `Kalejimo laikas: ${totalJailTime}`;
        }

        function toggleButton(fine, jail, description, type) {
            if (selectedButtons[description]) {
                delete selectedButtons[description];
            } else {
                selectedButtons[description] = { fine, jail, type };
            }
            updateTotals();
        }

        function doubleKETPenalties() {
            for (const key in selectedButtons) {
                if (selectedButtons[key].type === 'ket') {
                    selectedButtons[key].fine *= 2;
                    selectedButtons[key].jail *= 2;
                }
            }
            updateTotals();
        }

        // Initial calculation
        updateTotals();
    </script>

</body>
</html>
