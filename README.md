Display with a Photon
=======================

## How it looks

![Photon with Display](https://cloud.githubusercontent.com/assets/167882/15657290/d17df282-26af-11e6-9e97-6b22945a60fa.jpg)

## Schematics

It's based on the Arduino schematics: ![Schema](https://cloud.githubusercontent.com/assets/167882/15657264/97fee5c0-26af-11e6-97fb-3ac9449110f6.png)

I use this display: https://www.floris.cc/shop/en/display/667-lcd-display-16x2-white-on-blue.html

This is the datasheet of the screen: https://cdn-shop.adafruit.com/datasheets/TC1602A-01T.pdf

## How to send data from a Cronjob

```
DATA=`bundle exec rails runner 'puts "USERS: #{User.where("created_at >= ?", Time.zone.now.beginning_of_day).count},DESIGNS: #{Design.where("created_at >= ?", Time.zone.now.beginning_of_day).count}"'`
curl -X POST -F "parmams=$DATA" "https://api.particle.io/v1/devices/123xyz/lines?access_token=abcdefghijklmnopqrstuvwxyz"
