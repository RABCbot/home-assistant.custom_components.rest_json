# Home-Assistant-Json_rest
Custom Restful sensor, return a json attribute
Based on https://github.com/mad-ady/home-assistant-customizations/tree/master/custom_components/sensor

## Installation
Copy all the files from this repo, to your custom_component folder

## Configuration
Add to your configuration yaml:
```yaml
sensor:
- platform: json_rest
  resource: https://rabcbot.github.io/bible/words.json
  name: bible_word
  scan_interval: 21600
  verify_ssl: false
```

## Usage
Add a markdown card to your UI
Set content to
```
<b>{{ states.sensor.bible_word.attributes.words[0].word.english }}</b></br>
{{ states.sensor.bible_word.attributes.words[0].language }}
<i>{{ states.sensor.bible_word.attributes.words[0].transliteration }}</i>,
{{ states.sensor.bible_word.attributes.words[0].definition.english }}
</br>
Appears {{ states.sensor.bible_word.attributes.words[0].occurrences }} times</br>
{{ states.sensor.bible_word.attributes.words[0].key_verse }}</br>
{{ states.sensor.bible_word.attributes.words[0].verses }}
```
