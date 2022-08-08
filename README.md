# Flower Card

# BREAKING CHANGES

>**Warning**
>
> **This card is about to be completely rewritten.  Versions >= 2.0.0 will *not* be compatible with the original plant integration in HA or with earlier releases of this integration.**


This fork of the flower-card depends on this Plant component:
https://github.com/Olen/homeassistant-plant

Instead of reading the max/min-values from the huge data-file, it gets the values from the plant entity, using a websocket connection.

## Version 1 

Version 1 of this card has been deprecated and requires Version 1 of https://github.com/Olen/homeassistant-plant

The rest of this readme describes Version 2 of this card.

## Version 2

Several new sensors from the new version of the plant integration has been added to the card. 

The card also now use websockets to retrieve extended information about the plants from the backend.

![image](https://user-images.githubusercontent.com/203184/183286657-824a0e7f-a140-4d8e-8d6a-387070419dfd.png)


* The flower card also handles both °C and °F

![image](https://user-images.githubusercontent.com/203184/181259071-58622446-3e24-4f93-8334-293748958bd2.png)

You can also select what bars you want to show for each card

![image](https://user-images.githubusercontent.com/203184/183286691-02294d6b-84cf-46e6-9070-845d00f24a14.png)


## Dependencies
1. lovelace-card-tools (https://github.com/thomasloven/lovelace-card-tools)
2. Custom Plant integration (https://github.com/Olen/homeassistant-plant)

## Installation
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg?style=for-the-badge)](https://github.com/hacs/integration)

This can be installed manually or through HACS
### Via HACS
* Add this repo as a "Custom repository" with type "Lovelace"
  * Click HACS in your Home Assistnat
  * Click Frontend
  * Click the 3 dots in the top right corner and select "Custom Repositories"
  * Add the URL to this github repository and category "Lovelace"
* Click "Install" in the new "Flower Card" card in HACS.
* Select "Show beta versions" and select the latest beta
* Wait for install to complete
* You should not need to restart Home Assistant, but will probably need to refresh the frontend and/or "shift-reload" to refresh the browser cache.

### Manual Installation
1: Download the file flower-card.js and add it to somewhere in your `<config>/www/` folder in HA 
 
2: Click your profile picture in the bottom left corner -> Turn on Advanced Mode.
 
3: Go to Configuration -> Lovelace Dashboards -> Resources -> press the + (lower right corner of screen) and add the following information:

```yaml
  Url: /local/<path to>/flower-card.js
  Resource type: JavaScript Module
```
![image](https://user-images.githubusercontent.com/45675902/80322223-ebd41880-8823-11ea-992d-7070d4197f8b.png)

4: Press *Create* afterwards to add the new resource.

5: You should not need to restart Home Assistant, but will probably need to refresh the frontend and/or "shift-reload" to refresh the browser cache.

### Setup card

Add it as a custom card and select which bars you want to show on the card

```yaml
type: custom:flower-card
entity: plant.my_plant
show_bars:
- brigthness
- humidity
- moisture
- conductivity
- temperature
- dli
```


### Disclaimer
I looked into several forks of the original card https://github.com/thomasloven/lovelace-flower-card. Some forks were very interesting and I edited several of those source codes changes into my own new fork. Credits to those original authors.

