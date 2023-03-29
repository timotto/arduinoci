# Concourse Arduino CLI Resource

Supports checking Arduino Board Manager Packages.

## Source Configuration

* `board_manager_url`: *Optional* The URL for use in the Arduino Board Manager, e.g. `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`.
    The stock Arduino boards will be used, when omitted.

* `package`: *Required* The package, e.g. `esp32` or `esp8266`.

* `platform`: *Required* The platform, e.g. `esp32` or `esp8266`.

## Behavior

### `check`: discover new versions

Reports the current version of the `package` / `platform` combination available at `board_manager_url`.

### `in`: get a version

Saves the version, Board Manager URL, package, and platform into files with the names `version`, `board_manager_url`, `package`, and `platform`.
