# Home-Assistant-MicrosoftVision
This custom integration calls the Microsoft Azure Cognitive services Vision API https://azure.microsoft.com/en-us/services/cognitive-services/#api

## Setup
Get the service endpoint and key, follow these instructions https://docs.microsoft.com/en-us/azure/search/search-get-started-postman

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
<b>
{{ states.sensor.bible_word.attributes.words[0].word.spanish }}</b></br>
{{ states.sensor.bible_word.attributes.words[0].language }}
<i>{{ states.sensor.bible_word.attributes.words[0].transliteration }}</i>,
{{ states.sensor.bible_word.attributes.words[0].definition.spanish }}
</br>
Aparece {{ states.sensor.bible_word.attributes.words[0].occurrences }}
veces</br>
{{ states.sensor.bible_word.attributes.words[0].key_verse }}
</br>
{{ states.sensor.bible_word.attributes.words[0].verses }}
```
