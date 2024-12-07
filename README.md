# Peloton to Garmin

Uses
[philosowaffle/peloton-to-garmin](https://github.com/philosowaffle/peloton-to-garmin)
to upload Peloton workouts to Garmin

## Usage

Sync your workouts every day:
```
name: Sync Peloton to Garmin
on:
  schedule:
    - cron: "12 */6 * * *" # Every 6 hours on the 12th minute (4x/day)
  push: 
    branches:
      - main
jobs:
  peloton-to-garmin:
    name: Sync Peloton to Garmin
    runs-on: ubuntu-latest
    steps:
      - uses: jdowning/p2g-action@1.0.0
        with:
          peloton_email: ${{ secrets.PELOTON_EMAIL }}
          peloton_password: ${{ secrets.PELOTON_PASSWORD }}
          garmin_email: ${{ secrets.GARMIN_EMAIL }}
          garmin_password: ${{ secrets.GARMIN_PASSWORD }}
```

## Configuration

This action accepts the following inputs:

```
inputs:
  peloton_email:
    description: Peloton Email
    required: true
  peloton_password:
    description: Peloton Password
    required: true
  garmin_email:
    description: Garmin Email
    required: true
  garmin_password:
    description: Garmin Password
    required: true
  docker_tag:
    description: Docker Hub tag
    default: stable
  device_info_url:
    description: location of custom Garmin device info
    default: https://gist.githubusercontent.com/jdowning/457eee9c797083043358c8e5cb523c02/raw/337f695fb293cb7247fb3f234524117c46dd2e5b/venu.xml
  timezone:
    description: Timezone used
    default: US/Pacific
  workouts_to_download:
    description: How many workouts to download from Peloton
    default: 10
  enable_fit_format:
    description: Enable FIT file format
    default: true
  enable_json_format:
    description: Enable JSON file format
    default: true
  enable_tcx_format:
    description: Enable TCX file format
    default: true
  include_time_in_hr_zones:
    description: Include time in heart rate zones
    default: true
  include_time_in_power_zones:
    description: Include time in power zones
    default: true
  upload_to_garmin:
    description: Upload target file to Garmin
    default: true
  upload_format:
    description: File format to upload to Garmin
    default: fit
```
