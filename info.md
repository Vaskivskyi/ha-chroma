[![GitHub Release](https://img.shields.io/github/release/Vaskivskyi/ha-chroma.svg?style=for-the-badge&color=blue)](https://github.com/Vaskivskyi/ha-chroma/releases) [![License](https://img.shields.io/github/license/Vaskivskyi/ha-chroma.svg?style=for-the-badge&color=yellow)](https://github.com/Vaskivskyi/ha-chroma/blob/main/LICENSE)

## Control your Chroma-enabled devices from Home Assistant

`Chroma` is a custom integration for Home Assistant to control your Razer Chroma-enabled devices using the [AIOChroma](https://github.com/Vaskivskyi/aiochroma) python library.

Please, refer to the GitHub [Readme](https://github.com/Vaskivskyi/ha-chroma/) for detailed information on the available sensors and controls.

## Installation

1. Click Install
2. Restart Home Assistant
3. In the Home Assistant UI:
   `Configuration -> Devices & Services -> Integrations -> Add integration -> Chroma`

## Usage

To connect you need to provide the following data:
- IP address or hostname
- Which devices do you want to control (e.g. `chromalink`, `headset`, `keyboard`, `keypad`, `mouse`, `mousepad`)
- Layout of your keyboard (if the `keyboard` option is selected)

#### Lights

The integration provides a light entity per each device selected during the configuration process. Every entity supports `rgb_color` and `brightness` attributes.

#### Services

The `chroma.service_send_message` service allows sending any string message to your per-key RGB keyboard. The message will be displayed symbol by symbol. Please, refer to the [how-to documentation](https://github.com/Vaskivskyi/ha-chroma/blob/main/docs/how-to.md) for more details.

Currently, the following keyboard layouts are supported: `EN_US`.

You can still use the service if your keyboard layout is not yet supported. E.g. you can change your string from `Lazy fox was here` to `Layz fox was here` to properly be displayed with the German layout.

---

<a href="https://www.buymeacoffee.com/vaskivskyi" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;"></a>
