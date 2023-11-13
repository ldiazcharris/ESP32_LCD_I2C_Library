# LCD_I2C_Grove_Library
This library contains the basic functions for controlling the Grove Backlight V4.0 LCD, using the ESP-IDF framework for the ESP-WROOM-32. This library is based on the Arduino reference library available at https://www.arduino.cc/reference/en/libraries/grove-lcd-rgb-backlight/ and another references.

This library was adapted from diferent source codes:
- https://github.com/Seeed-Studio/Grove_LCD_RGB_Backlight
- https://controllerstech.com/i2c-in-esp32-esp-idf-lcd-1602/ 
- https://controllerstech.com/i2c-lcd-in-stm32/

This software is licensed under The MIT License. Check License.txt for more information.

# Installation
This library implements the pins `GPIO_NUM_21` and `GPIO_NUM_22` as SDA and SCL I2C pins respectively. Be careful not to use these pins for other purposes when using this library.
Download the files `lcd_i2c_grove.h` and `lcd_i2c_grove.c`, and put them in the library directory of your project. 

# Example
~~~
#include <stdio.h>
#include <string.h>
#include "driver/gpio.h"
#include "driver/i2c.h"
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "esp_log.h"
#include "lcd_i2c_grove.h"  

void app_main()
{
    // Inicialización de la pantalla LCD
    // LCD screen initialization
    lcd_init(); 
    
    // Se pone la pantalla LCD en blanco
    // The LCD screen goes blank
    lcd_clear(); 
   
    while(1){

        // Se pone la pantalla LCD en blanco cada nuevo ciclo
        // The LCD screen goes blank every new cycle
        lcd_clear(); 
        
        // Se coloca el cursor en la posición (0, 0) de la pantalla (fila, columna)
        // The cursor is placed at position (0, 0) on the screen (row, column)
        lcd_cursor(0, 0); 

        // Se escribe el texto en pantalla
        // Text is written on the screen
        lcd_write_string("Hola Mundo..."); 
        
        vTaskDelay(3000/portTICK_PERIOD_MS); 
        
        // Se pone la pantalla LCD en blanco
        // The LCD screen goes blank
        lcd_clear(); 
        
        // Se coloca el cursor en la posición (1, 0) de la pantalla
        // The cursor is placed at position (1, 0) on the screen
        lcd_cursor(1, 0); 
        
        // Se escribe el texto en pantalla
        // Text is written on the screen
        lcd_write_string("...Chao Mundo");  
        
        vTaskDelay(3000/portTICK_PERIOD_MS);
    }
}
~~~

