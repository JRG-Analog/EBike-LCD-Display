# EBike-LCD-Display
A display to read VESC over UART using Teensy 4.1

SW must not hinder VESC operation, merely supplement it

Default operation is pass through of handlebar signals (Brakes and Throttle) to the VESC by hard wires
Thus a SW bug does not brick the bike.

Read VESC over UART (like RS-232) to display speed, odometer, other vital data on primary display screen

Control Lights

  Headlight (High Priority)
    main beam and angel eye
    both have separate PWM intensity
  Will have a button on Secondary Screen to turn off, on , high, low
  Will have adjustment of levels off Tertiary Setup Screen
  
  Tail Light (High Priority)
    Has brake and Tail light signal
      both have separate PWM intensity
    Will have a button on Secondary Screen to turn off, on
    Will have adjustment of levels off Tertiary Setup Screen
    Brake light functional regardless of tail light setting
    
LED String Lights (Medium Priority)
  Based on WS2811 controller
  RGB 16 million colors, in groups of 3 LEDs
  Use library at this link (or other links)
  Initial setting is static, amber, 10% intensity
  Future Development is animations (Christmas colors scrolling, etc. )
  Will have a button on Secondary Screen to turn off, on
  Will have adjustment of levels and color options off Tertiary Setup Screen

Audio (Low Priority)
  Teensy 4.1 will have mono wave file on SD card
  On depression of horn button will play default file
  Will have adjustment of sound and volume off Tertiary Setup Screen

External Power Control and Monitoring (Highest Priority, but LOL, easiest and nothing else works until this is done)
  After boot set P34 “EN_PWR” bit high
  Monitor 12V and 5V inputs with ADC reading

Cruise Control (Low Priority)
  Button on Primary Display
  Throttle setting is read via ADC
  PWM output is set to match ADC
Cruise is enabled by asserting “CRUISE_ON” P17
Cruise is indicated on display
If BRAKE is enabled, Cruise is turned off on display
There is HW control that automatically cuts off the Cruise throttle and reconnects the actual throttle
Don’t want runaway bike due to SW bug!
