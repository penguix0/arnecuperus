---
title: "MOBA devops dashboard"
date: 2023-10-13
author: Arne Cuperus

cover:
    image: "dashboard.png"
    alt: "Screenshot van het dashboard"
    caption: "Screenshot van het dashboard in werking"
    relative: false # To use relative path for cover image, used in hugo Page-bundles
---

Als laatste projec van VWO 5, hebben we een softwaredashboard gemaakt voor de softwareontwikkelaars bij MOBA. Dit dashboard vervangt het huidige dashboard dat bij MOBA wordt gebruikt. Het oude dashboard toonde informatie zoals het aantal projecten en of een project alle kwaliteitstests had doorstaan. Het nieuwe dashboard biedt deze functies ook, maar met enkele verbeteringen. Zo geeft het een meer gedetailleerde status van de kwaliteit van de projecten en een timer die aangeeft wanneer een nieuwe versie van het programma kan worden gebouwd.

Het dashboard is geschreven in TypeScript en Angular.

# Live demo
Je kan zelf een live demo maken door de repository te clonen:
```bash
git clone https://github.com/FunkyWonder/Mobalisator-5000.git
```

Ga daarna de directory in:
```bash
cd Mobalisator-5000-main
```

Bouw de `Dockerfile`:
```bash
sudo docker build .
```

Vervolgens kan men met het gegeven ID van de container de container starten:
```bash
sudo docker run -dp 3000:80 id
```
Vervang `id` hier voor jouw eigen id, bijvoorbeeld `7dafc99e30c6`.

Daaropvolgend kan de webpagina bezocht worden op `127.0.0.1:3000` en kan er een project aangemaakt worden, gebruik hiervoor een `project ID` van `381`.

De `spatie` toets opent het menu.

# Screenshots
![Screenshot 1](dialog.png#center)

![Screenshot 2](menu.png#center)

![Screenshot 3](dashboard.png#center)
