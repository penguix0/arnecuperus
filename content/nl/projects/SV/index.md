---
title: "Stochastic Volatility and Parallelization"
date: 2023-04-05
author: Arne Cuperus

cover:
    image: "banner.png"
    alt: "Een foto van een NVIDIA A10"
    caption: "De videokaart waarop we testte"
    relative: false # To use relative path for cover image, used in hugo Page-bundles
---

Het laatste project van mijn O&O carrière heette: "Stochastic Volatility Models and Paralellization". Dit project was onze opdrachtgever Prof. Czellar ons gaf ging om het accelereren van een economisch model met de videokaart. 

# Zoeken naar een opdrachtgever
We begonnen het project met het zoeken naar een opdrachtgever, uit ons eigen onderzoek bleek dat we allemaal interesse hadden in de informatica. Ook bleek dat we allemaal een project wouden doen, dat uit een combinatie van hard- en software. Ook deden we onderzoek naar bedrijven die bij deze interesses zouden passen, we contacteerde deze bedrijven met de vraag of ze opdrachtgever woudne worden:
- Supermicro  
- ARM  
- Nvidia  
- AWI  
- Blender  
- KPN IoT  
- BIT  
- Lambda  
- Cloudflare  
- AMS-IX  
- CTS  
- NXP-semiconductors  
- Scope4mation  
- Tuxis  
- Wentzo  
- Defensie  
- Baulds  
- SKEMA

Na contact te leggen met deze bedrijven was SKEMA het enige bedrijf met een positief antwoord. Onze opdrachtgever, Veronika Czellar, gaf ons de opdracht om haar economische model te versnellen met behulp van de videokaart.

# Profielwerkstuk

Om meer te weten te komen over het model wat de opdrachtgever hebben ik en mijn groepsgenoot onderzoek gedaan naar het model. In dit onderzoek keken we naar de functies in de C-code en wat deze functies deden. We kwamen meer te weten over hoe het model werkte en waarom sommige dingen raar waren geïmplementeerd.

We stelden onszelf de volgende onderzoeksvragen:

Main research question 

- How does the code work? 

Sub-questions 

- How does the algorithm which the code uses work? 
- What functions are there? 
- How do these functions work? 
- How is the I/O of the program structured? 
- How is the program compiled? 

# Programmeren
Na de onderzoeksfase begonnen we met het identificeren van parallellizeerbare onderdelen van de code. We kwamen er achter dat de nlminLvectSimplex functie de meest belangrijke functie was om te parallelliseren. We besloten ook welk *library* we wouden gebruiken. We kozen het CUDA-library omdat het een bekend library is en uitstekend werkt met NVIDIA videokaarten.

Het converteren van de applicatie van CPU- naar GPU-code bestond uit het verplaatsen van stukken code naar de device. Ook hebben we het programma gebruik laten maken van half's inplaats van 64-bit floats. We deden dit, omdat het rekenen met half's veel sneller is op de videokaart. De videokaart heeft namelijk meer rekenkernen voor 16-bit half's, dan 64-bit floats, omdat deze 16-bit half's meer gebruikt worden. 

Ook hebben we de prestaties van het model geoptimaliseerd met behulp van NVIDIA NSIGHT COMPUTE, deze tool gemaakt door NVIDIA stelde ons in staat om meer inzicht te krijgen in hoe de applicatie gebruik maakte van de videokaart en waar we nog verbeteringen konden doorvoeren. Ook moesten we functies veranderen, sommige rekenfuncties waren namelijk niet beschikbaar op de videokaart. We moesten alternatieven vinden voor deze functies en dat was lastig. NVIDIA's documentatie is namelijk slecht en veel is verborgen voor *niet*-developers.

De laatste paar weken hebben we de code gedebugd. De conversie naar GPU-code zorgde voor probelemen. We kwamen tijdens deze periode er ook achter dat debuggen op de videokaart lastiger is dan op de processor. *printf* statements bijvoorbeeld kwamen niet altijd optijd aan en dat maakte het lastig om inzicht te krijgen in wat er precies gebeurde op de videokaart.

Een ander probleem wat we tijdens het probleem vaak tegenkwamen was dat CUDA op Windows slecht werkte. Bij het gebruik van CUDA op Windows, wordt je bijna verplicht om Visual Studio te gebruiken. Visual Studio is een soort Word om code te schrijven en verbergt vele knopjes in submenu's inplaats van dat gewoon de CLI van CUDA gebruikt kan worden. Onze oplossing hiervoor was om een Arch Linux machine op te zetten, waar we gezamenlijk op konden werken. Hier konden we onze eigen tools kiezen en beter doorwerken dan op Windows.

# Eindproduct
In Prof. Czellar's initiële testen kwam naar voren dat één trial of run 23.45 minuten duurde. Op basis van onze testen met de omgeschreven code, duurde één trial 300.65 minuten. Echter, doordat de code geparallelliseerd is, duren twee trials ook 300.65 minuten, maar 3, 4, 5, 7, 200, 1000 trials ook. Ons programma is met een klein aantal trials of runs dus niet sneller dan het oude programma, maar zodra er meerdere trials worden uitgevoerd wel. Aan de ene kant is dit gunstig, maar aan de andere kant ook niet. Je wil namelijk zo veel mogelijk trials uitvoeren om een zo nauwkeurig mogelijk resultaat te krijgen, maar dit duurt alsnog te lang voor nuttig gebruik in de aandeelmarkt.
  