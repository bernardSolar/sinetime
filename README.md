# Sinusoidal Time Clock - Installation Guide

This guide will help you install and run the Sinusoidal Time Clock on your Mac.

## Prerequisites

The program requires Python and a few dependencies. Here's how to set everything up:

1. Make sure you have Python 3 installed on your Mac. Most Macs come with Python pre-installed, but you can verify by opening Terminal and typing:
   ```
   python3 --version
   ```

2. Install the required packages using pip:
   ```
   pip3 install pillow pytz
   ```

## Running the Program

1. Save the Python code to a file named `sinusoidal_clock.py`

2. Open Terminal and navigate to the directory where you saved the file:
   ```
   cd path/to/directory
   ```

3. Run the program with your latitude as a command line argument:
   ```
   python3 sinusoidal_clock.py --latitude 51.5
   ```
   
   Replace `51.5` with your actual latitude:
   - Positive values for locations in the Northern Hemisphere
   - Negative values for locations in the Southern Hemisphere
   
   For example:
   - London: `--latitude 51.5`
   - New York: `--latitude 40.7`
   - Sydney: `--latitude -33.9`
   - Quito (near equator): `--latitude 0.18`
   
   If you don't specify a latitude, the program will default to 51.5° (London).

## How It Works

The Sinusoidal Time Clock shows both standard time and a gradually adjusting "sinusoidal time" that smoothly transitions between standard time and Daylight Saving Time throughout the year, eliminating the abrupt one-hour shifts.

- **Standard Time**: Shows the current time according to your system clock
- **Sinusoidal Time**: Shows the gradually adjusted time
- **Adjustment Info**: Displays how many minutes the sinusoidal time differs from standard time

The program calculates the adjustment using a sinusoidal function that gradually shifts between standard time and DST, with the maximum difference of one hour occurring midway between the spring forward and fall back dates.

## Latitude Effects

The program now adjusts the sinusoidal time pattern based on latitude:

- **Equatorial Regions** (near 0°): Minimal adjustment since daylight hours remain fairly constant throughout the year
- **Mid-Latitudes** (23.5° to 66.5°): Standard adjustment based on seasonal variations
- **Polar Regions** (above 66.5°): More pronounced adjustment to account for extreme daylight variations

The program automatically scales the adjustment based on your latitude, with more extreme latitudes resulting in more pronounced time shifts to match the natural daylight patterns in those regions.

In the Southern Hemisphere, the seasonal pattern is inverted to match the opposite seasons.

## Additional Customization

You can modify these parameters in the code if needed:
- `max_adjustment`: Currently set to 3600 seconds (1 hour)
- `spring_forward_day`: Currently set to March 31st
- `fall_back_day`: Currently set to October 31st

The actual DST transition dates vary by year, so you might want to adjust these to match the specific dates for any given year.
