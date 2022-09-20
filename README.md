[![GitHub Release](https://img.shields.io/github/release/Vaskivskyi/ha-chroma.svg?style=for-the-badge&color=blue)](https://github.com/Vaskivskyi/ha-chroma/releases) [![License](https://img.shields.io/github/license/Vaskivskyi/ha-chroma.svg?style=for-the-badge&color=yellow)](LICENSE)<a href="https://github.com/Vaskivskyi/ha-chroma/actions/workflows/build.yaml"><img src="https://img.shields.io/github/workflow/status/Vaskivskyi/ha-chroma/Build?style=for-the-badge" alt="Build Status" align="right" /></a><br/>
<!--[![HACS Default](https://img.shields.io/badge/HACS-default-blue.svg?style=for-the-badge)](https://hacs.xyz) [![Community forum discussion](https://img.shields.io/badge/COMMUNITY-FORUM-success?style=for-the-badge&color=yellow)](https://community.home-assistant.io/t/custom-component-asusrouter-integration/416111)--><a href="https://www.buymeacoffee.com/vaskivskyi" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 28px !important;" align="right" /></a>

## Control your Chroma-enabled devices from Home Assistant

`Chroma` is a custom integration for Home Assistant to control your Razer Chroma-enabled devices using the [AIOChroma](https://github.com/Vaskivskyi/aiochroma) python library.

## Installation

#### HACS

Chroma will be added to the default of HACS as soon as [this PR](https://github.com/hacs/default/pull/1500) is merged.

Meanwhile, you can add this repository (https://github.com/Vaskivskyi/ha-chroma) to your HACS as a custom repository.

#### Manual

Copy content of the [stable branch](https://github.com/Vaskivskyi/ha-chroma/tree/stable) `custom_components/chroma/` to `custom_components/chroma/` in your Home Assistant folder.

## Usage

After Chroma is installed, you can add your device from Home Assistant UI.

[![Open your Home Assistant instance and start setting up a new integration.](https://my.home-assistant.io/badges/config_flow_start.svg)](https://my.home-assistant.io/redirect/config_flow_start/?domain=chroma)

To connect you need to provide the following data:
- IP address or hostname
- Which devices do you want to control (e.g. `chromalink`, `headset`, `keyboard`, `keypad`, `mouse`, `mousepad`)
- Layout of your keyboard (if the `keyboard` option is selected)

[![Open your Home Assistant instance and show your integrations.](https://my.home-assistant.io/badges/integrations.svg)](https://my.home-assistant.io/redirect/integrations/)

#### Allow the connection (adjust your firewall settings)

In order to use the integration, you might need to adjust your firewall settings on the device with Chroma devices. Please, allow the incoming `TCP` connection on port `54236` from your HA instance. In case, this connection is not allowed, the integration will not be able to connect and might be stuck in the `configuring` state for an extended period.

#### Lights

The integration provides a light entity per each device selected during the configuration process. Every entity supports `rgb_color` and `brightness` attributes.

#### Services

The `chroma.service_send_message` service allows sending any string message to your per-key RGB keyboard. The message will be displayed symbol by symbol. Please, refer to the [how-to documentation](https://github.com/Vaskivskyi/ha-chroma/blob/main/docs/how-to.md) for more details.

Currently, the following keyboard layouts are supported: `EN_US`.

You can still use the service if your keyboard layout is not yet supported. E.g. you can change your string from `Lazy fox was here` to `Layz fox was here` to properly be displayed with the German layout.

## Support the integration

This integration is a free-time project. If you like it, you can support me by buying a coffee.

<a href="https://www.buymeacoffee.com/vaskivskyi" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;"></a>
