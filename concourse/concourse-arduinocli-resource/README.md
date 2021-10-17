# Concourse Arduino CLI Resource

Supports checking Arduino Board Manager Packages.

## Source Configuration

* `board_manager_url`: *Required* The URL for use in the Arduino Board Manager, e.g. `https://dl.espressif.com/dl/package_esp32_index.json`.

* `package`: *Required* The package, e.g. `esp32` or `esp8266`.

* `platform`: *Required* The platform, e.g. `esp32` or `esp8266`.

## Behavior

### `check`: discover new versions

Reports the current version of the `package` / `platform` combination available at `board_manager_url`.

### `in`: get a version

Saves the version, Board Manager URL, package, and platform into files with the names `version`, `board_manager_url`, `package`, and `platform`.
