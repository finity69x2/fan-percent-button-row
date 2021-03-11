Provides a means to program 3 preset speed percentage settings for fans selectable from a Lovelace button row. 

## NOTE: You must be on Home Assistant V2021.3.X or higher to use this plug-in

<b>Configuration Examples:</b>
    
  ```
    cards:
      - type: entities
        title: Hall Fan Presets
        show_header_toggle: false
        entities:
        ## USE THIS CONFIG TO HAVE IT MATCH YOUR THEME ##
          - entity: fan.hall_fan
            type: custom:fan-percent-button-row
            name: Fan Not Custom Theme
            customTheme: false
        ## USE THIS CONFIG TO USE A DEFAULT CUSTOM THEME
          - entity: fan.hall_fan
            type: custom:fan-percent-button-row
            name: Fan Default Custom Theme
            customTheme: true
            customSetpoints: true
            lowPercent: 30
            medPercent: 60
            hiPercent: 90
        ## USE THIS CONFIG TO USE A 'CUSTOMZED' CUSTOM THEME
          - entity: fan.hall_fan
            type: custom:fan-percent-button-row
            name: Fan Custom Custom Theme
            reverseButtons: true
            customTheme: true
            isOnLowColor: 'rgb(255, 0, 0)'
            isOnMedColor: '#888888'
            isOnHiColor: '#222222'
            buttonInactiveColor: '#aaaaaa'
            isOffColor: 'purple'
        ## USE THIS CONFIG TO SET CUSTOM BUTTON TEXT (NOT REQUIRED TO SET "customTheme: true" TO USE THESE )
          - entity: fan.hall_fan
            type: custom:fan-percent-button-row
            name: Fan Custom Button Text
            customHiText: me
            customLowText: do
            customMedText: re
            customOffText: not
            
  ```

This is with the default Lovelace frontend theme set:

![Default](images/fan_percent_default.jpg)

This is with the "Slate" frontend theme set:

![Slate](images/fan_percent_default_2.jpg)

This is how this plugin looks with the plugin fully themed:

![Slate-Themed](images/fan_percent_themed.jpg)

