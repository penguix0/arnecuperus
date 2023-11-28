---
title: "Playing seperate sounds on the Ring Chime for two doorbells"
date: 2023-11-28
author: Arne Cuperus
cover:
    image: "cover.png"
    alt: "Cover picture"
    # caption: ""
    relative: false # To use relative path for cover image, used in hugo Page-bundles
---

In this post I'll explain how I configured Home Assistant to play two distinct sounds on the Ring Chime for each of my two doorbells.

# Requirements
- A Home Assistant server
- The official Ring Home Assistant [integration](https://www.home-assistant.io/integrations/ring/)
- [Ring Chime](https://ring.com/products/smart-security-chime)
- This won´t work if you use motion alerts on your chime.

# Setup
This project works in the following way: one doorbell is used as usual with the Ring app and linked to the chime, while the other doorbell is imported in Home Assistant along with the chime. If the first doorbell is pressed, the chime plays a sound as usual. However, if the second doorbell is rung, Home Assistant triggers the chime to play the 'motion' sound. This allows us to play two different sounds on the same chime.

## Automation
Firstly, ensure that your chime and doorbell are integrated into Home Assistant. 
> If the chime doesn't appear, ensure that you're logged in with your primary Ring account. Logging in with an account where the doorbell is shared does not work.

Then add the blueprint:


Alternatively, you can create the following automation:
```yaml
automation:
  alias: Second Doorbell Chime
  description: "An automation that triggers a distinct sound on the second doorbell, making the chime ring twice."
  trigger:
    - platform: state
      entity_id:
        - binary_sensor.<your_doorbell_ding>
      from: "off"
      to: "on"
  condition: []
  action:
    - service: siren.turn_on
      data:
        tone: motion
      target:
        entity_id: siren.<your_sirene>
    - delay:
        hours: 0
        minutes: 0
        seconds: 5
        milliseconds: 0
    - service: siren.turn_on
      data:
        tone: motion
      target:
        entity_id: siren.<your_sirene>
  mode: single
```
Adjust the placeholders (<your_doorbell_ding> and <your_siren>) with the appropriate entities for your specific setup.

And that's it, thank you for reading!