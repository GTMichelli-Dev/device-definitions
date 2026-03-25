# Device Definitions

Community-maintained JSON configuration files for common industrial and commercial hardware devices. Used by applications to auto-configure device connections.

## Structure

```
device-definitions/
├── cameras/          IP and USB camera snapshot configurations
├── scales/           Serial and network scale communication profiles
├── printers/         Ticket and label printer configurations
└── scanners/         Barcode and RFID scanner configurations
```

## How It Works

Each JSON file contains an array of device definitions with brand, type, and connection templates. Applications download the latest JSON at startup and use it to build connection strings from user-provided settings (IP, credentials, device name, etc.).

### Template Placeholders

Templates use `{placeholder}` syntax. Common placeholders:

| Placeholder | Description |
|-------------|-------------|
| `{ip}` | Device IP address |
| `{port}` | Device port number |
| `{user}` | Authentication username |
| `{password}` | Authentication password |
| `{deviceName}` | Local device name (USB, serial port) |
| `{baudRate}` | Serial baud rate |

## Usage

Applications fetch the raw JSON from this repo:

```
https://raw.githubusercontent.com/SeanSolleder/device-definitions/main/cameras/camera-brands.json
```

If the remote fetch fails, applications should fall back to a bundled local copy.

## Contributing

To add a new device:

1. Find the appropriate category folder (cameras, scales, printers, scanners)
2. Add your entry to the JSON array with: `brand`, `type`, template fields, and `notes`
3. Test the template with your actual device
4. Submit a pull request

## Categories

### Cameras (`cameras/camera-brands.json`)
IP camera snapshot URLs and USB camera capture commands. Used for ticket photo capture at weigh stations.

### Scales (`scales/scale-models.json`)
Serial and TCP scale communication profiles including data formats, baud rates, and command strings.

### Printers (`printers/printer-models.json`)
Ticket and label printer configurations for direct printing.

### Scanners (`scanners/scanner-models.json`)
Barcode and RFID scanner input configurations.

## License

MIT
