# ESPHome based dashboard using Lilygo T5 4,7" e-ink display + ESP32

![Sample](/sample.png)

This is my hobby project to create an information-dense kitchen countertop dashboard for my Home Assistant based smart home.

My work was inspired by geekuillaume and Plawasan.

Disclaimer: this is really not a cleaned up version yet. 🙂

## Device

I used a Lilygo T5 4,7" e-ink display + ESP32 ordered from Aliexpress, PH 2.0 9102 Chip version. The device came in a nice package with a USB cable included. Once installing the proper driver it was ready to use.

## Getting started

Steps I needed to get this project up and running on Windows:

- install latest python
- install esp-idf from [https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/windows-setup.html]
  - (this was needed for Windows to recognize my Lilygo T5 properly)
- install ESPHome addon and integration to Home Assistant
- follow the [ESPHome CLI guide](https://esphome.io/guides/getting_started_command_line.html)
- add passwords to `secrets.yaml` (not pushed to this repo)

```bash
pip3 install esphome
pip3 install pillow
esphome wizard dashboard.yaml
esphome run dashboard.yaml
```

## Custom solutions behind

My dashboard code may not be reusable directly for anyone else, but it might give some ideas, or perhaps a motivation that it is not that difficult to just create something like this from scratch. The layout is fully custom and tailored for my own needs. I tried to produce just a little bit better code than a 5 year old would do, but I'm not that proud of it. Oh boy, I haven't used C++ in ages... 🙂

Date related things and some other stuff are localized in an ugly/custom way, since strftime doesn't do that.

Data sources used behind:

- HA date and time
- `sun` and `moon` HA sensors
- google calendar to get today's "nameday"
- spotify
- temperature+humidity sensors
- custom weather integration (scraping a local provider in HA, that's why everything seems to be a separate sensor)

## Other resources

- [https://github.com/tiaanv/esphome-components]
- [https://github.com/Xinyuan-LilyGO/LilyGo-EPD47]
- [https://github.com/vroland/epdiy]
- [https://esphome.io/components/display/index.html]
- [https://www.reddit.com/r/homeassistant/comments/rm71z4/lilygo_t5_epaper_display_now_using_esphome/]
- [https://www.reddit.com/r/homeassistant/comments/rwwy6r/i_built_a_personal_dashboard_with_a_47_epaper/]
- [https://pictogrammers.github.io/@mdi/font/5.3.45/]

## License

Feel free to use any code from this repo, in any way you want. (A.k.a: WTFPL)
