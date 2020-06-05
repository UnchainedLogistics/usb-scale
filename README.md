# usb-scale

Reads input from Dymo M25 Digital USB Postal Scale

Raw data format:

    => [0] Unknown 3
    => [1] Stability (2 when at 0, 3 when getting stable, 4 when stable, 5 when negative, 6 when too much weight)
    => [2] Mode (lbs = 12, kg = 3)
    => [3] Scale factor
    => [4-5] 16 bit weight

## Scale

    $ irb -I ./lib -r ./lib/scale.rb
    > scale = Scale.new
    > scale.output_as_json
    
### Notes

- Can use `lsusb` on linux to list connected devices and get vendor id / product id
- On OS X can get this same info from "System Menu > About this Mac > System Report"
- On linux, needed to symlink the HID API library that the gem is looking for:


    sudo ln -s /usr/lib/x86_64-linux-gnu/libhidapi-libusb.so /usr/local/lib/libhidapi.so

