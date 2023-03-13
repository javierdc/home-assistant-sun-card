# Home assistant Sun card

Home assistant Sun card based on Google weather design

## Preview

![Light mode preview](https://user-images.githubusercontent.com/6829526/118412152-54d93900-b690-11eb-8b2b-e87b4cbcca7f.png)
![Dark mode preview](https://user-images.githubusercontent.com/6829526/118412162-64f11880-b690-11eb-9bd7-b8c6c7d8efd8.png)

## Requirements

- The configured sun integration ([default](https://www.home-assistant.io/integrations/sun/)) needs to be enabled

## Install

### HACS

Home assistant Sun card is available by default on HACS directory.
More info [here](https://hacs.xyz/).

### Manually

1. If necessary, create a `www` folder in your configuration folder (where `configuration.yaml` is found).
1. Download the `home-assistant-sun-card.js` file from the [latest release available](https://github.com/AitorDB/home-assistant-sun-card/releases) and save it in your `<configuration>/www` folder.
1. Go to `Configuration > Lovelace dashboard > Resources` in Home Assistant and click on `Add resource`.
   1. Add `/local/home-assistant-sun-card.js` to the URL.
   1. Choose `Javascript Module` as Resource type.

## Set up

### Using UI

1. Go to your dashboard, enter in edit mode and click on `Add card`, you should be able to find `Custom: Sun card` in the list.
1. Once in the UI editor you can modify the card behavior by adding some of the config that you will find below

Note: If `Custom: Sun card` doesn't appear you will have to reload cleaning the cache.

### Using YAML

1. You just need to add a new card with `type: 'custom:sun-card'` to your cards list and any of the config that you will find below if you want to customize more your card.

Note: If you get an error similar to this `Custom element doesn't exist` you will have to reload cleaning the cache.

## Config


### Basic
| Name           | Accepted values      | Description                          | Default                                             |
| -------------- | -------------------- | ------------------------------------ | --------------------------------------------------- |
| title          | `string`             | Card title                           | Doesn't display a title by default                  |
| darkMode       | `boolean`            | Changes card colors to dark or light | Home Assistant dark mode state                      |
| component      | `string`             | Changes which sun component to use   | Home Assistant `sun.sun`                            |
| language       | `string`<sup>1</sup> | Changes card language                | Home Assistant language or english if not supported |
| fields         | FieldConfiguration   | Fintuned control over visible fields |                                                     |
| use12hourClock | `boolean`            | Use 12/24 hour clock                 | Uses locale of configured language to decide        |

### FieldConfiguration
| Name           | Accepted values | Description    | Default |
|----------------|-----------------|----------------|---------|
| sunrise        | `boolean`       | Show sunrise   | `true`  |
| sunset         | `boolean`       | Show sunset    | `true`  |
| dawn           | `boolean`       | Show dawn      | `true`  |
| noon           | `boolean`       | Show noon      | `true`  |
| dusk           | `boolean`       | Show dusk      | `true`  |
| azimuth        | `boolean`       | Show azimuth   | `false` |
| elevation      | `boolean`       | Show elevation | `false` |


<details>
<summary><sup>1</sup> Supported languages</summary>

- `cs` Czech
- `da` Danish
- `de` German
- `en` English
- `es` Spanish
- `et` Estonian
- `fi` Finnish
- `fr` French
- `he` Hebrew
- `hu` Hungarian
- `it` Italian
- `lt` Lithuanian
- `nb` Norwegian (Bokmål)
- `nl` Dutch
- `nn` Norwegian (Nynorsk)
- `pl` Polish
- `pt-BR` Portuguese (Brazil)
- `ru` Russian
- `sk` Slovak
- `sl` Slovenian
- `sv` Swedish

</details>

## Known issues

- Home assistant seems to provide next events instead today's one

## Developers

1. Fork and clone the repository.
2. Open the [devcontainer][devcontainer] and run `npm start` when it's ready.
3. The compiled `.js` file will be accessible on
   `http://127.0.0.1:5000/roku-card.js`.
4. On a running Home Assistant installation add this to your Lovelace
   `resources:`

```yaml
- url: 'http://127.0.0.1:5000/roku-card.js'
  type: module
```

_Change "127.0.0.1" to the IP of your development machine._

### Bonus

If you need a fresh test instance you can install a fresh Home Assistant instance inside the devcontainer as well.

1. Run the command `dc start`.
2. Home Assistant will install and will eventually be running on port `9123`