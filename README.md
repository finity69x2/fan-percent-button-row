# light-brightness-preset-row
Provides a means to program 3 preset brightness settings for dimmable lights selectable from a Lovelace button row.

This pluig-in was inspired by user @jazzyisj on the Home Assistant forum (community.home-assistant.io) as a thematically complementary plug-in for my fan control row.

Installation:

The easiest way to install this is to use the Home Assistant Community Store (HACS) in Home Assistant.

Follow the instructions there for installation making sure you note the "url:" section for the resources addition.


Conversely, if you don't use HACS you can install it manually by performing the following:

Copy the light-brightness-preset-row.js file to the appropriate folder in your Home Assistant Configuration directory (/config/www/).

Place the following in your "resources" section in your lovelace configuration (updating the localation to where you placed the above file):

  ```
    - url: /local/light-brightness-preset-row.js
      type: module
  ```
    
Then to use this in a card place the following in your entity card:


<b>Options:</b>

| Name | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| entity | String | Yes | none | any dimmable light entity_id (including "light group" entities) |
| type | String | Yes | none | custom:light-brightness-entity-row |
| name | String | No | none | A custom name for the entity in the row |
| customTheme | Boolean | No | false | set to true to use a custom theme |
| customSetpoints | Boolean | No | false | set to true to use custom brightness setpoints |
| reverseButtons | Boolean | No | false | set to true to reverse the button order |
| isOffColor | String | No | '#f44c09' | Sets the color of the 'Off' button if light is off |
| isOnLowColor | String | No | '#43A047' | Sets the color of the 'Low' button if light is on low |
| isOnMedColor | String | No | '#43A047' | Sets the color of the 'Med' button if light is on Medium |
| isOnHiColor | String | No | '#43A047' | Sets the color of the 'Hi' button if light is on high |
| buttonInactiveColor | String | No | '#759aaa' | Sets the color of the the buttons if that selection is not "active" |
| lowBrightness | Integer | No | 43 | Sets the brighness level for the "Low" button |
| medBrightness | Integer | No | 128 | Sets the brighness level for the "Med" button  |
| hiBrightness | Integer | No | 213 | Sets the brighness level for the "High" button (max 254) |
| customOffText | String | No | 'OFF' | Sets the text of the "off" button |
| customLowText | String | No | 'LOW' | Sets the text of the "low" speed button |
| customMedText | String | No | 'MED' | Sets the text of the "medium" speed button |
| customHiText | String | No | 'HIGH' | Sets the text of the "High" speed button |


The values for the colors can be any valid color string in "HEX", "RGB" or by color name.

If the light brightness is changed via any other means (slider, service call, etc) the buttons will indicate which range the light brightness is in based on the setpoint settings in the config.

This plugin can also be used with a group of dimmable lights by creating a "light group". Then each light in the group will be simultaneously controlled by the plugin.

<b>Configuration Examples:</b>
    
  ```
    cards:
      - type: entities
        title: Hall Light Presets
        show_header_toggle: false
        entities:
        ## USE THIS CONFIG TO HAVE IT MATCH YOUR THEME ##
          - entity: light.hall_light
            type: custom:light-brightness-preset-row
            name: Light Not Custom Theme
            customTheme: false
        ## USE THIS CONFIG TO USE A DEFAULT CUSTOM THEME
          - entity: light.hall_light
            type: custom:light-brightness-preset-row
            name: Light Default Custom Theme
            customTheme: true
            customSetpoints: true
            lowBrightness: 30
            medBrightness: 100
            hiBrightness: 225
        ## USE THIS CONFIG TO USE A 'CUSTOMZED' CUSTOM THEME
          - entity: light.hall_light
            type: custom:light-brightness-preset-row
            name: Light Custom Custom Theme
            reverseButtons: true
            customTheme: true
            isOnLowColor: 'rgb(255, 0, 0)'
            isOnMedColor: '#888888'
            isOnHiColor: '#222222'
            buttonInactiveColor: '#aaaaaa'
            isOffColor: 'purple'
        ## USE THIS CONFIG TO SET CUSTOM BUTTON TEXT (NOT REQUIRED TO SET "customTheme: true" TO USE THESE )
          - entity: light.hall_light
            type: custom:light-brightness-preset-row
            name: Light Custom Button Text
            customHiText: me
            customLowText: do
            customMedText: re
            customOffText: not
            
  ```

This is with the default Lovelace frontend theme set:

![Default](ex2.gif)


This is with the "Slate" frontend theme set:

![Slate](ex3.gif)

This is how this plugin looks with the Fan control & Binary Button Rows:

![Slate-Compare](button-row-example-compare.gif)
