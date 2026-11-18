# Zeitshop Converter

Zeitshop Converter is a small Python application that turns DIAMOND CSV exports into Wix product import CSVs.

The converter is simple: it reads DIAMOND-style `.csv` files, maps product rows into Wix's CSV structure, and validates the generated product rows. It can also be used to update inventory in an existing Wix export from a newer DIAMOND inventory CSV.

Currently i have it fixed for a set of brands from the jewelery store that this application is for, if you want to use it for yourself, contact me and i'll tell you how to customize it for any store. 

## Requirements

- Python 3.10 or newer
- Tkinter available in the Python installation if you want to use the GUI
- Windows if you want the packaged desktop build

## Installation

Install the application from source:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -e .[gui]
```


### Windows Installation

For a Windows computer with Python 3.10 or newer installed, run the script:

```bat
scripts\install_windows.cmd
```

## Quick Start

### GUI

Launch the desktop app:

```bash
python -m zeitshop_converter.main gui
```

The GUI lets you:

- choose a DIAMOND CSV export
- run the conversion immediately
- review counts, warnings, and errors
- edit selected product fields before export
- download the Wix CSV
- download a (German) issue report
- switch to update mode, choose a Wix product export plus a newer DIAMOND inventory CSV, review changes, and save the updated Wix CSV
- edit the fixed brand list used by update-mode safety checks in the settings window

### CLI

Convert a DIAMOND CSV export into a Wix CSV:

```bash
python -m zeitshop_converter.main convert \
  --diamond input.csv \
  --output out/wix_import.csv \
  --issues-output out/issues.csv
```

Update a Wix product export with a newer DIAMOND inventory CSV:

```bash
python -m zeitshop_converter.main update \
  --wix-export catalog_products.csv \
  --diamond lager.csv \
  --output out/catalog_products_inventory_update.csv
```
