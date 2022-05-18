import board
import digitalio
import busio
uart = busio.UART(board.TX, board.RX, baudrate=19200)
import adafruit_thermal_printer
ThermalPrinter = adafruit_thermal_printer.get_printer_class(2.69)
printer = ThermalPrinter(uart)

#initializing LCD
lcd_rs = digitalio.DigitalInOut(board.D5)
lcd_en = digitalio.DigitalInOut(board.D6)
lcd_d7 = digitalio.DigitalInOut(board.D12)
lcd_d6 = digitalio.DigitalInOut(board.D11)
lcd_d5 = digitalio.DigitalInOut(board.D10)
lcd_d4 = digitalio.DigitalInOut(board.D9)



lcd_columns = 16
lcd_rows = 2

import adafruit_character_lcd.character_lcd as characterlcd
lcd = characterlcd.Character_LCD_Mono(lcd_rs, lcd_en, lcd_d4, lcd_d5, lcd_d6, lcd_d7, lcd_columns, lcd_rows)

#Displaying message on LCD
lcd.message = "Agree to our\nPrivacy Policy?"


button1 = digitalio.DigitalInOut(board.D13)
button1.switch_to_input(pull=digitalio.Pull.DOWN)

button2 = digitalio.DigitalInOut(board.D2)
button2.switch_to_input(pull=digitalio.Pull.DOWN)

printingVAR = False
printingVAR2 = False
#print out page on button press
while True:
    if button1.value and printingVAR == False:  # button is pushed
        printingVAR = True

    if printingVAR:
        printer.underline = adafruit_thermal_printer.UNDERLINE_THICK
        printer.size = adafruit_thermal_printer.SIZE_MEDIUM
        printer.justify = adafruit_thermal_printer.JUSTIFY_CENTER
        printer.print('Fill this form')
        printer.feed(2)

        printer.size = adafruit_thermal_printer.SIZE_SMALL
        printer.justify = adafruit_thermal_printer.JUSTIFY_LEFT
        printer.underline = None
        printer.print('Name:')
        printer.feed(2)
        printer.print('Email:')
        printer.feed(2)
        printer.print('Age:')
        printer.feed(2)
        printer.print('Occupation/School:')
        printer.feed(2)
        printer.print('Interests:')
        printer.feed(2)
        printer.justify = adafruit_thermal_printer.JUSTIFY_CENTER
        printer.print('Insert into slot after filling.')
        printer.feed(2)
        printingVAR = False
        printer.feed(2)
    
		if button2.value and printingVAR2 == False:
        printingVAR2 = True

    if printingVAR2:
        printer.size = adafruit_thermal_printer.SIZE_MEDIUM
        printer.justify = adafruit_thermal_printer.JUSTIFY_CENTER
        printer.print('Your Reciept!')
        printer.print('--------------------------------')
        printer.feed(2)
        

        printer.size = adafruit_thermal_printer.SIZE_SMALL
        printer.underline = None
        printer.justify = adafruit_thermal_printer.JUSTIFY_LEFT
        printer.print('Name:                     $20.0')
        printer.feed(1)
        printer.print('Email:                   $100.0')
        printer.feed(1)
        printer.print('Age:                      $50.0')
        printer.feed(1)
        printer.print('Occupation/School:       $50.0')
        printer.feed(1)
        printer.print('Interests:               $200.0')
        printer.justify = adafruit_thermal_printer.JUSTIFY_CENTER
        printer.print('--------------------------------')
        printer.size = adafruit_thermal_printer.SIZE_MEDIUM
        printer.justify = adafruit_thermal_printer.JUSTIFY_LEFT
        printer.print('TOTAL AMOUNT:            $420.0')
        printer.justify = adafruit_thermal_printer.JUSTIFY_CENTER
        printer.print_barcode('424242424242', printer.UPC_A)
        printer.feed(1)
        printingVAR2 = False
        printer.feed(2)
    else:
        False
