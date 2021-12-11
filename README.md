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
      - uses: jdowning/p2g-action
        with:
          peloton_email: ${{ secrets.PELOTON_EMAIL }}
          peloton_password: ${{ secrets.PELOTON_PASSWORD }}
          garmin_email: ${{ secrets.GARMIN_EMAIL }}
          garmin_password: ${{ secrets.GARMIN_PASSWORD }}
```
