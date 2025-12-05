# IKEA Bilresa Scroll Wheel Remote Blueprint

Control multiple lights with different modes using the IKEA Bilresa (Fjärr med skroll) remote.

## Troubleshooting / Felsökning

**Remote not working?** First, debug what events it's sending:

1. Copy the content of `bilresa-debug-automation.yaml`
2. In Home Assistant: Settings > Automations > Create Automation
3. Click ⋮ (three dots) > "Edit in YAML"
4. Paste the content
5. Find your device ID:
   - Settings > Devices & Services > Devices
   - Click your Bilresa remote
   - Look at the URL: `.../device/XXXXX` ← that's your device_id
6. Replace `YOUR_DEVICE_ID` in the automation
7. Save and press buttons on your remote
8. Check notifications to see what events are sent

**Fjärrkontrollen fungerar inte?** Debugga först vilka events den skickar (se ovan på engelska).

## Features

- **3 Groups**: Control up to 3 different lights
- **2 Modes per Group**: Switch between brightness and color temperature control
- **Smart Controls**:
  - **Single Press**: Toggle current light on/off
  - **Double Press**: Switch between brightness and temperature modes
  - **Long Press**: Switch to next group (cycles through 1 → 2 → 3 → 1)
  - **Scroll Wheel**: Adjust brightness or temperature based on current mode

## Setup Instructions

### Step 1: Create Helper Entities

Go to **Settings > Devices & Services > Helpers** and create:

1. **Input Select** for Active Group:
   - Name: "Bilresa Active Group" (or your choice)
   - Options: `1`, `2`, `3`
   - Icon: 🎯

2. **Input Boolean** for each group's mode (create 3):
   - Name: "Bilresa Group 1 Mode" (and Group 2, Group 3)
   - Icon: 🔄
   - When OFF = Brightness mode
   - When ON = Temperature mode

### Step 2: Import Blueprint

[![Import Blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/davvarn/ikeamatterdevices/blob/main/bilresa-scrollwheel-blueprint.yaml)

Or manually import: `https://github.com/davvarn/ikeamatterdevices/blob/main/bilresa-scrollwheel-blueprint.yaml`

### Step 3: Configure Automation

1. Select your Bilresa remote device
2. Choose your 3 lights (Group 1, 2, 3)
3. Select the helper entities you created
4. Adjust brightness and temperature step sizes if needed

## Usage

1. **Long press** to switch between groups (lights)
2. **Single press** to turn the current light on/off
3. **Double press** to switch between:
   - Brightness mode (scroll adjusts brightness)
   - Temperature mode (scroll adjusts color temperature)
4. **Scroll** the wheel to adjust current setting

## Example Setup

- **Group 1**: Living room light
- **Group 2**: Kitchen light  
- **Group 3**: Bedroom light

Each group remembers its own mode setting independently!

## Requirements

- IKEA Bilresa (Fjärr med skroll) remote connected via Matter, ZHA, or Zigbee2MQTT
- Home Assistant 2024.1 or newer
- Helper entities as described above