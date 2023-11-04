---
title: "ContainerControl"
date: 2023-01-28
author: Arne Cuperus

cover:
    image: "banner.JPG"
    alt: "Logo van de app"
    caption: "Logo van de app"
    relative: false # To use relative path for cover image, used in hugo Page-bundles
---

Op veel containerschepen wordt dagelijks lading af- en opgeladen. Dit verloopt echter niet altijd goed. Vaak worden containers verkeerd geplaatst of staan er containers op het schip die er niet thuishoren. Dit kan desastreuze gevolgen hebben, zoals het instorten van containers of het afvallen van containers in zee.

Om meer inzicht te krijgen in hoe containers een schip belasten, heeft onze opdrachtgever Michiel Gunsing een programma ontwikkeld dat met behulp van een gyroscoop bepaalt hoe containers kracht uitoefenen op het schip en waar mogelijk gevaar kan ontstaan als er te zware containers op de verkeerde plaats worden geplaatst.

In het kader van dit project hebben wij de opdracht gekregen om een systeem te ontwerpen dat containers met behulp van beeldherkenning kan herkennen en registreren. Dit hebben wij opgelost met twee zelfgebouwde programma's: ContainerControl Mobile en ContainerControl Server.

De mobiele versie van de app is geschreven in Flutter en Dart. Wij hebben ons strikt gehouden aan de Material 3-designrichtlijnen, zodat de app een consistente en gebruiksvriendelijke uitstraling heeft.

De serverapplicatie is geschreven in Python en Flask. We hebben een API gebouwd waarmee de app verzoeken kan doen naar de server en containers kan laten herkennen en registreren.

Het herkennen van containers gebeurt met YoloV7, een kunstmatige intelligentie die in Python is geschreven en die wij zelf hebben getraind op foto's van zeecontainers. Deze zeecontainers hebben we deels van internet gehaald en deels zelf gerenderd met Blender, een 3D-ontwerpprogramma.

# Screenshots

![Screenshot 1](Dia7.png#center)

![Screenshot 2](Dia8.png#center)

![Screenshot 3](Dia9.png#center)