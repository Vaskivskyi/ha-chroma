[![GitHub Release](https://img.shields.io/github/release/Vaskivskyi/ha-chroma.svg?style=for-the-badge&color=blue)](https://github.com/Vaskivskyi/ha-chroma/releases) [![License](https://img.shields.io/github/license/Vaskivskyi/ha-chroma.svg?style=for-the-badge&color=yellow)](LICENSE)<a href="https://github.com/Vaskivskyi/ha-chroma/actions/workflows/build.yaml"><img src="https://img.shields.io/github/workflow/status/Vaskivskyi/ha-chroma/Build?style=for-the-badge" alt="Build Status" align="right" /></a><br/>
[![HACS Default](https://img.shields.io/badge/HACS-default-blue.svg?style=for-the-badge)](https://hacs.xyz) [![Community forum discussion](https://img.shields.io/badge/COMMUNITY-FORUM-success?style=for-the-badge&color=yellow)](https://community.home-assistant.io/t/custom-component-chroma-integration-control-your-rgb/464511)<a href="https://www.buymeacoffee.com/vaskivskyi" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 28px !important;" align="right" /></a><br/>
[![Installations](https://img.shields.io/endpoint?url=https://vaskivskyi.github.io/ha-custom-analytics/badges/chroma/total.json&style=for-the-badge&color=blue)](https://github.com/Vaskivskyi/ha-custom-analytics)

## Control your Chroma-enabled devices from Home Assistant

`Chroma` is a custom integration for Home Assistant to control your Razer Chroma-enabled devices using the [AIOChroma](https://github.com/Vaskivskyi/aiochroma) python library.

A short presentation of the features can be found in this [YouTube video](https://www.youtube.com/watch?v=ytdS9JUWSb4).

## Installation

#### HACS

You can add this repository to your HACS:
`HACS -> Integrations -> Explore & Download Repositories -> Chroma`

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

To use the integration, you might need to adjust your firewall settings on the device with Chroma devices. Please, allow the incoming `TCP` connection on port `54236` from your HA instance. In case, this connection is not allowed, the integration will not be able to connect and might be stuck in the `configuring` state for an extended period.

#### Lights

The integration provides a light entity per each device selected during the configuration process. Every entity supports `rgb_color` and `brightness` attributes.

#### Services

The `chroma.service_send_message` service allows sending any string message to your per-key RGB keyboard. The message will be displayed symbol by symbol. Please, refer to the [how-to documentation](https://github.com/Vaskivskyi/ha-chroma/blob/main/docs/how-to.md) for more details.

Currently, the following keyboard layouts are supported: `EN_US`.

You can still use the service if your keyboard layout is not yet supported. E.g. you can change your string from `Lazy fox was here` to `Layz fox was here` to properly be displayed with the German layout.

## Supported SDK versions

Some older versions of the Chroma SDK might be not compatible with the integration. Unfortunately, I cannot test all the versions, so the following table contains only those I know about.

<table>
<tr><th>Supported</th><th>Possible issues</th><th>Not supported</th></tr>
<tr><td>
3.28.01 - 3.28.03
</td><td>
3.27.04 (issue <a href="https://github.com/Vaskivskyi/ha-chroma/issues/22">#22</a>)
</td><td>

</td></tr>
</table>

### SDK troubleshooting

#### `[SSL: BAD_SIGNATURE] bad signature`
This issue might appear when updating Synapse software between versions and can be observed on different versions. In this case, your HA instance won't be able to connect to Chroma SDK. At the same time, you won't be able to connect to SDK even locally using the local [https://chromasdk.io:54236/razer/chromasdk](https://chromasdk.io:54236/razer/chromasdk) alias (different browsers are showing a variety of SSL errors).

 This issue can be fixed in the following way:
- Open your Synapse software;
- On the main `Synapse` tab switch from the `Dashboard` view to the `Modules` view (page with installed and available for installation modules);
- Uninstall `Chroma Connect` (no need to close Synapse afterwords, just proceed to the next step);
- Install `Chroma Connect`.

Check the SDK again. It should work now.

## Supported devices

This list provides only the models tested by me or other users. If your device is not listed yet but works well, please open a [Device Support](https://github.com/Vaskivskyi/ha-chroma/issues/new/choose) ticket with the device model and it will be added to the list.

Some of the devices might be in the group which you would not expect. This is not related to the integration but the Chroma SDK.

<table>

<tr><th>Group</th><th>Devices</th></tr>

<tr><td>Chromalink</td><td>

`Chroma Addressable RGB Controller` ([link*](https://amzn.to/3T0E4UG))<br />
Mousepads: `Goliathus Extended Chroma` ([link](https://amzn.to/3VsDsZU))<br/>
Services: `AuraConnect`

</td></tr>

<tr><td>Headset</td><td>

`Kraken 7.1 V2` ([link](https://amzn.to/3VsN1rt)), `Kraken X USB` ([link](https://amzn.to/3rWZshC))

</td></tr>

<tr><td>Keyboard</td><td>

`BlackWidow Chroma`, `BlackWidow V3 Pro` ([link](https://amzn.to/3CUAy8X))<br/>
`Huntsman Elite` ([link](https://amzn.to/3rQ36tJ))

</td></tr>

<tr><td>Keypad</td><td>


</td></tr>

<tr><td>Mouse</td><td>

`DeathAdder V2 Pro` ([link](https://amzn.to/3VrDAsg))<br/>
`Mamba Tournament Edition` ([link](https://amzn.to/3RZBqgP))<br/>
`Naga Left-Handed Edition`<br/>
`Viper Ultimate` (+ `Mouse Dock`) ([link](https://amzn.to/3RXXt7w))

</td></tr>

<tr><td>Mousepad</td><td>

`Firefly V2` ([link](https://amzn.to/3S01V5w))<br />
`Mouse Bungee V3 Chroma` ([link](https://amzn.to/3MAproL))

</td></tr>

</table>
* As an Amazon Associate I earn from qualifying purchases. Not like I ever got anything yet (:

## Support the integration

This integration is a free-time project. If you like it, you can support me by buying a coffee.

<a href="https://www.buymeacoffee.com/vaskivskyi" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;"></a>
