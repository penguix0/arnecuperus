---
title: "Algenreactor"
date: 2022-02-19
author: Arne Cuperus

cover:
    image: "P1010114.JPG"
    alt: "Een foto van de algenreactor"
    caption: "De algenreactor"
    relative: false # To use relative path for cover image, used in hugo Page-bundles
---

Samen met Hylke Ietswaart en Thor Koning heb ik dit project in VWO 4 op Het Streek Lyceum uitgevoerd.

# Het probleem
De wereldbevolking groeit, waardoor er meer voedsel en energie nodig is. Dit is een probleem,
omdat er steeds meer afvalstoffen en fossiele brandstoffen worden gebruikt. Een oplossing is de
biobased economy, waarin duurzame producten worden gemaakt van biologische grondstoffen.
Algen kunnen een belangrijke rol spelen in de biobased economy. 

# De opdracht
Onze opdrachtgever: het Wageningse AlgaePARC, gaf ons de opdracht om een duurzaam kweeksysteem voor algen te ontwerpen, bouwen en testen. Hierbij moesten we zelf een doel stellen zoals:
- Een zo hoog mogelijke concentratie algen kweken
- Zo goedkoop mogelijk algen kweken (euro’s per kg algen)
- Een zo hoog mogelijke concentratie van een algenproduct maken (zoals het pigment
fycocyanine).

Wij kozen ervoor om zo veel mogelijk concentratie algen te kweken binnen twee weken. Dit doel verwerkte we in ons plan van aanpak.

# Planning
Vrijwel gelijk toen we de opdracht ontvingen van de opdrachtgever zijn we gaan plannen en kwam Hylke Ietswaart met het idee om een sponsor te zoeken, dit was gedurende eerste week dan ook onze topprioriteit.

Na een week hadden we een sponsor gevonden en zijn we gaan plannen wat er komende periode gedaan moest worden. 

# Sponsor
De heer Eijkman, directeur bij Carbogen AMCIS, heeft ons project gesponsord. Hylke bracht ons in contact met hem, omdat hij contacten heeft bij het bedrijf. Carbogen AMCIS is zelf ook actief in de algensector, dus was het voor hen een mooie kans om ons te steunen.

# Uitvoering
Nadat we een overzicht hadden van de taken, zijn we aan de slag gegaan. We begonnen met een vooronderzoek naar microalgen, hierin stelden we onszelf de volgende vragen:
- Wat zijn microalgen?
- Wat zijn essentiële groeifactoren voor algen?
- Wat is het verschil tussen microalgen en planten?
- Waar zijn toepassingen met microalgen tot nu toe al gebruikt?

Op basis van ons vooronderzoek hebben we een schematische weergave van de reactor gemaakt. Deze weergave gaf ons een goed overzicht van de benodigde componenten. We hebben de componenten uitgezocht en een begroting gemaakt.
![Schematische weergave van de algenreactor](schents.jpg#center)

Met de componenten in huis zijn we begonnen met de bouw van de reactor. We hebben dit gedaan in een werkplaats op het terrein van Carbogen AMCIS. Thor en Hylke waren verantwoordelijk voor de hardware, ik voor de software en bijbehorende elektronica



## Software
De reactor was volledig autonoom. Hij regelde zelf de verlichting en temperatuur. De besturing werd verzorgd door een ESP8266-chip, die we op school vonden. Ik heb een besturingssysteem geschreven in Arduino (AlgaeOS) om de temperatuur via relais te regelen. Het verwarmingselement was op deze relais aangesloten. We gebruikten twee temperatuursensoren, een boven in het vat en een onder in het vat. De temperatuurdelta tussen deze twee sensoren werd gebruikt om het verwarmingselement aan of uit te zetten. We stelden de temperatuur in op 34 graden Celsius, wat de ideale temperatuur is voor algengroei.

De ESP8266 zette een eigen wifi-hotspot op, zodat de slimme verlichting erop kon verbinden. De ESP8266 verbond zich ook met het wifi-netwerk van school om de temperatuurgegevens te loggen in een Google Spreadsheet. Zo konden we de reactor op afstand monitoren vanaf onze telefoon of tablet. De reactor gaf ook informatie over de status op de reactor zelf, via status-leds die informatie gaven over de internetverbinding, de temperatuur en het schrijven van gegevens naar de cloud.
![Foto van elektronica](P1010122.JPG#center)

## Medium
Algen hebben voeding nodig om te groeien. In samenwerking met een hoogleraar van de HAN universiteit hebben we een recept ontwikkeld voor een bufferoplossing en voeding. Deze voeding zorgt voor een stabiel pH-niveau en bevordert de groei van de algen. We hebben de benodigde stoffen bij het scheikundekabinet van school gehaald.


# Eindproduct
Dit is de uiteindelijke algenreactor, we hebben hiermee de competitie gewonnen en de mensen van het Wageningse AlgaePARC waren zeer enthousiast.

![Foto van de afgwerkte reactor](P1010110.JPG#center)
