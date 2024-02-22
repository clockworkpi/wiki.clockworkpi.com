---
layout: simple
title: GPIO
revisions:
- author: Cuu 
  date: 2024-02-22
  comment: First version
---
## GPIO

### GameShell

| Type |  Pin # (ext.) |   Pin # (Package) |   Function 1   | Function 2 | Pin # (sysfs)  |  Color  |
|------|---------------|-------------------|----------------|------------|----------------|---------|
|3V0   | 1             |                   |                |            |                | blue    |
|GPIO  | 2             | PB0               | UART0/2_TX     | PB-EINT0   | 32             | green   |
|GPIO  | 3             | PB1               | UART0/2_RX     | PB-EINT1   | 33             | yellow  |
|GND   | 4             |                   |                |            |                | white   |
|GPIO  | 5             | PH5               | I2C1-SDA       |            | 229            | red     |
|GPIO  | 6             | PH4               | I2C1-SCL       |            | 228            | brown   |
|GND   | 7             |                   |                |            |                | black   |
|GPIO  | 8             | PH6               | UART3-TX       | SPI0-CS    | 230            | blue    |
|GPIO  | 9             | PH7               | UART3-RX       | SPI0-CLK   | 231            | green   |
|GPIO  | 10            | PH9               | UART3-CTS      | SPI0-MISO  | 233            | yellow  |
|GPIO  | 11            | PH8               | UART3-RTS      | SPI0-MOSI  | 232            | white   |
|GND   | 12            |                   |                |            |                | red     |
|5V0   | 13            |                   |                |            |                | brown   |
|5V0   | 14            |                   |                |            |                | black   |



| Type | Pin \# (ext.) | Pin \# (Package) | Function 1 | Function 2 | Pin \# (sysfs) | Color   |
|------|---------------|------------------|------------|------------|----------------|---------|
| 3V0  | 1             |                  |            |            |                | blue    |
| TODO | Example       | Example          | Example    | Example    | Example        | Example |
|      |               |                  |            |            |                |         |

Source: <https://p3dt.net/post/2019/12/26/gameshell-gpios.html>

### A04

Raw output from `gpio readall`:  


```
+-----+------+------+------+---+-----+------+------+------+---+
| BCM | GPIO | Name | Mode | V | BCM | GPIO | Name | Mode | V |
+-----+------+------+------+---+-----+------+------+------+---+
|   0 |   58 | PD26 | ALT2 | 0 |  23 |  129 | PG1  | ALT2 | 0 |
|   1 |   57 | PD25 | ALT2 | 0 |  24 |  130 | PG2  | ALT2 | 0 |
|   2 |  167 | PH7  | ALT6 | 1 |  25 |  131 | PG3  | ALT2 | 0 |
|   3 |    0 | PC0  |  OUT | 1 |  26 |  132 | PG4  | ALT2 | 0 |
|   4 |    1 | PC1  |  OFF | 0 |  27 |  133 | PG5  | ALT2 | 0 |
|   5 |    2 | PC2  |  OUT | 1 |  28 |    9 | PC9  |  OUT | 0 |
|   6 |    3 | PC3  |   IN | 1 |  29 |  201 | PL9  |  OUT | 0 |
|   7 |    4 | PC4  |  OUT | 1 |  30 |  196 | PL4  |  OUT | 0 |
|   8 |    5 | PC5  |  OUT | 0 |  31 |  199 | PL7  |  OUT | 0 |
|   9 |    6 | PC6  |  OUT | 1 |  32 |  161 | PH1  | ALT2 | 0 |
|  10 |    7 | PC7  |   IN | 0 |  33 |  160 | PH0  | ALT2 | 0 |
|  11 |    8 | PC8  |  OUT | 1 |  34 |  227 | PM3  |   IN | 1 |
|  12 |   15 | PC15 |  OFF | 0 |  35 |  198 | PL6  |   IN | 1 |
|  13 |   54 | PD22 |  OFF | 0 |  36 |  163 | PH3  |  OUT | 1 |
|  14 |  134 | PG6  | ALT2 | 0 |  37 |  166 | PH6  |  OUT | 0 |
|  15 |  135 | PG7  | ALT2 | 0 |  38 |  165 | PH5  | ALT2 | 0 |
|  16 |  137 | PG9  | ALT2 | 0 |  39 |  164 | PH4  | ALT2 | 0 |
|  17 |  136 | PG8  | ALT2 | 0 |  40 |  228 | PM4  |  OUT | 0 |
|  18 |  139 | PG11 |  OFF | 0 |  41 |  224 | PM0  |  OUT | 0 |
|  19 |  138 | PG10 |  OFF | 0 |  42 |  225 | PM1  |  OFF | 0 |
|  20 |  141 | PG13 |  OFF | 0 |  43 |  226 | PM2  |  OFF | 0 |
|  21 |  140 | PG12 |  OFF | 0 |  44 |   56 | PD24 | ALT2 | 0 |
|  22 |  128 | PG0  | ALT2 | 0 |  45 |   55 | PD23 | ALT2 | 0 |
+-----+------+------+------+---+-----+------+------+------+---+
| BCM | GPIO | Name | Mode | V | BCM | GPIO | Name | Mode | V |
+-----+------+------+------+---+-----+------+------+------+---+
```
#### Details

    
| wiringpi# | GPIO (?) | Name | Mode | Value | Description                                        |
|-----------|----------|------|------|-------|----------------------------------------------------|
| 0         | 58       | PD26 | ALT2 | 0     | PMU-SDA                                            |
| 1         | 57       | PD25 | ALT2 | 0     | PMU-SCK                                            |
| 2         | 167      | PH7  | ALT6 | 1     | PMU-IRQ                                            |
| 3         | 0        | PC0  | OUT  | 1     | WL_REG_ON                                          |
| 4         | 1        | PC1  | OFF  | 0     | WL_HOST_WAKE                                       |
| 5         | 2        | PC2  | OUT  | 1     | BT_REG_ON                                          |
| 6         | 3        | PC3  | IN   | 1     | BT_HOST_WAKE                                       |
| 7         | 4        | PC4  | OUT  | 1     | BT_WAKE                                            |
| 8         | 5        | PC5  | OUT  | 0     | LCD_RESET                                          |
| 9         | 6        | PC6  | OUT  | 1     | BL_CTRL                                            |
| 10        | 7        | PC7  | IN   | 0     | HP_DET: 1 if headphone is plugged in, 0 if not     |
| 11        | 8        | PC8  | OUT  | 1     | PA_EN: write 1 to enable speaker, 0 to disable     |
| 12        | 15       | PC15 | OFF  | 0     | AUD_PWM0                                           |
| 13        | 54       | PD22 | OFF  | 0     | AUD_PWM1                                           |
| 14        | 134      | PG6  | ALT2 | 0     | UART_RXD                                           |
| 15        | 135      | PG7  | ALT2 | 0     | UART_TXD                                           |
| 16        | 137      | PG9  | ALT2 | 0     | UART_RTS_N                                         |
| 17        | 136      | PG8  | ALT2 | 0     | UART_CTS_N                                         |
| 18        | 139      | PG11 | OFF  | 0     | PCM_CLK                                            |
| 19        | 138      | PG10 | OFF  | 0     | PCM_SYNC                                           |
| 20        | 141      | PG13 | OFF  | 0     | PCM_OUT                                            |
| 21        | 140      | PG12 | OFF  | 0     | PCM_IN                                             |
| 22        | 128      | PG0  | ALT2 | 0     | SDIO_CLK                                           |
| 23        | 129      | PG1  | ALT2 | 0     | SDIO_CMD                                           |
| 24        | 130      | PG2  | ALT2 | 0     | SDIO_D0                                            |
| 25        | 131      | PG3  | ALT2 | 0     | SDIO_D1                                            |
| 26        | 132      | PG4  | ALT2 | 0     | SDIO_D2                                            |
| 27        | 133      | PG5  | ALT2 | 0     | SDIO_D3                                            |
| 28        | 9        | PC9  | OUT  | 0     | (Ext, Printer) AIN1                                |
| 29        | 201      | PL9  | OUT  | 0     | (Ext, Printer) AIN2                                |
| 30        | 196      | PL4  | OUT  | 0     | (Ext, Printer) BIN1                                |
| 31        | 199      | PL7  | OUT  | 0     | (Ext, Printer) BIN2                                |
| 32        | 161      | PH1  | ALT2 | 0     | (Ext) UART_TX                                      |
| 33        | 160      | PH0  | ALT2 | 0     | (Ext) UART_RX                                      |
| 34        | 227      | PM3  | IN   | 1     | (Ext, Printer) PAPER                               |
| 35        | 198      | PL6  | IN   | 1     | (Ext, Printer) ALERT                               |
| 36        | 163      | PH3  | OUT  | 1     | (Ext, Printer) LATCH                               |
| 37        | 166      | PH6  | OUT  | 0     | (Ext, Printer) STROBE                              |
| 38        | 165      | PH5  | ALT2 | 0     | (Ext) MOSI                                         |
| 39        | 164      | PH4  | ALT2 | 0     | (Ext) SCK                                          |
| 40        | 228      | PM4  | OUT  | 0     | (Ext, Printer) PRT_EN                              |
| 41        | 224      | PM0  | OUT  | 0     | (Ext, Fan) FAN_EN: write 1 to start fan, 0 to stop |
| 42        | 225      | PM1  | OFF  | 0     | (Ext, Camera) CAM_EN                               |
| 43        | 226      | PM2  | OFF  | 0     | (Ext, Camera) CAM_LED                              |
| 44        | 56       | PD24 | ALT2 | 0     | (Ext) I2C_SDA                                      |
| 45        | 55       | PD23 | ALT2 | 0     | (Ext) I2C_SCL                                      |


#### Controller 1: From /sys/kernel/debug/pinctrl/300b000.pinctrl/pinmux-pins
   
   
| pin (name)     | mux_owner       | gpio_owner          | hog?                         | Description                                               |
|----------------|-----------------|---------------------|------------------------------|-----------------------------------------------------------|
| pin 0 (PA0)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 1 (PA1)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 2 (PA2)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 3 (PA3)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 4 (PA4)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 5 (PA5)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 6 (PA6)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 7 (PA7)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 8 (PA8)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 9 (PA9)    | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 32 (PB0)   | 2-2010          | (GPIO UNCLAIMED)    | function ccir group PB0      |                                                           |
| pin 33 (PB1)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 34 (PB2)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 35 (PB3)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 36 (PB4)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 37 (PB5)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 38 (PB6)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 39 (PB7)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 40 (PB8)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 41 (PB9)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 42 (PB10)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 43 (PB11)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 44 (PB12)  | 508f000.i2s     | (GPIO UNCLAIMED)    | function i2s3 group PB12     | connects to ac200                                         |
| pin 45 (PB13)  | 508f000.i2s     | (GPIO UNCLAIMED)    | function i2s3 group PB13     |                                                           |
| pin 46 (PB14)  | 508f000.i2s     | (GPIO UNCLAIMED)    | function i2s3 group PB14     |                                                           |
| pin 47 (PB15)  | 508f000.i2s     | (GPIO UNCLAIMED)    | function i2s3 group PB15     |                                                           |
| pin 48 (PB16)  | 508f000.i2s     | (GPIO UNCLAIMED)    | function i2s3 group PB16     |                                                           |
| pin 49 (PB17)  | 5002c00.i2c     | (GPIO UNCLAIMED)    | function i2c3 group PB17     | connects to ac200                                         |
| pin 50 (PB18)  | 5002c00.i2c     | (GPIO UNCLAIMED)    | function i2c3 group PB18     |                                                           |
| pin 51 (PB19)  | ac200_clk       | (GPIO UNCLAIMED)    | function pwm1 group PB19     |                                                           |
| pin 52 (PB20)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 64 (PC0)   | (MUX UNCLIAMED) | 300b000.pinctrl:64  |                              | GPIO3: WL_REG_ON; /wifi-pwrseq/reset-gpios                |
| pin 65 (PC1)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO4: WL_HOST_WAKE                                       |
| pin 66 (PC2)   | (MUX UNCLIAMED) | 300b000.pinctrl:66  |                              | GPIO5: BT_REG_ON; bluetooth/shutdown-gpios                |
| pin 67 (PC3)   | (MUX UNCLIAMED) | 300b000.pinctrl:67  |                              | GPIO6: BT_HOST_WAKE; bluetooth/host-wakeup-gpios          |
| pin 68 (PC4)   | (MUX UNCLIAMED) | 300b000.pinctrl:68  |                              | GPIO7: BT_WAKE; bluetooth/device-wakeup-gpios             |
| pin 69 (PC5)   | 1-000e          | (GPIO UNCLAIMED)    | function gpio_out group PC5  | GPIO8: LCD_RESET                                          |
| pin 70 (PC6)   | backlight@0     | 300b000.pinctrl:70  | function gpio_out group PC6  | GPIO9: BL_CTRL; ocp8178_backlight/backlight-control-gpios |
| pin 71 (PC7)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO10: HP_DET; IN; =1 if 3.5mm is plugged in             |
| pin 72 (PC8)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO11: PA_EN; OUT; write 1 to enable speaker             |
| pin 73 (PC9)   | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO28: Ext. AIN1                                         |
| pin 74 (PC10)  | 1-000e          | 300b000.pinctrl:74  | function gpio_out group PC10 | dsi_bridge/reset-gpios                                    |
| pin 75 (PC11)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 76 (PC12)  | (MUX UNCLIAMED) | 300b000.pinctrl:76  |                              | /ac200_codec_spk/gpio-switch                              |
| pin 77 (PC13)  | 1-000e          | 300b000.pinctrl:77  | function gpio_out group PC13 | dsi_bridge/power-gpios                                    |
| pin 78 (PC14)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 79 (PC15)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO12: AUD_PWM0                                          |
| pin 80 (PC16)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 96 (PD0)   | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD0      |                                                           |
| pin 97 (PD1)   | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD1      |                                                           |
| pin 98 (PD2)   | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD2      |                                                           |
| pin 99 (PD3)   | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD3      |                                                           |
| pin 100 (PD4)  | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD4      |                                                           |
| pin 101 (PD5)  | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD5      |                                                           |
| pin 102 (PD6)  | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD6      |                                                           |
| pin 103 (PD7)  | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD7      |                                                           |
| pin 104 (PD8)  | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD8      |                                                           |
| pin 105 (PD9)  | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD9      |                                                           |
| pin 106 (PD10) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD10     |                                                           |
| pin 107 (PD11) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD11     |                                                           |
| pin 108 (PD12) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD12     |                                                           |
| pin 109 (PD13) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD13     |                                                           |
| pin 110 (PD14) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD14     |                                                           |
| pin 111 (PD15) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD15     |                                                           |
| pin 112 (PD16) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD16     |                                                           |
| pin 113 (PD17) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD17     |                                                           |
| pin 114 (PD18) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD18     |                                                           |
| pin 115 (PD19) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD19     |                                                           |
| pin 116 (PD20) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD20     |                                                           |
| pin 117 (PD21) | panel           | (GPIO UNCLAIMED)    | function lcd0 group PD21     |                                                           |
| pin 118 (PD22) | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO13: AUD_PWM1                                          |
| pin 119 (PD23) | 5002800.i2c     | (GPIO UNCLAIMED)    | function i2c2 group PD23     | GPIO44: Ext. I2C_SCL                                      |
| pin 120 (PD24) | 5002800.i2c     | (GPIO UNCLAIMED)    | function i2c2 group PD24     | GPIO44: Ext. I2C_SDA                                      |
| pin 121 (PD25) | 5002000.i2c     | (GPIO UNCLAIMED)    | function i2c0 group PD25     | GPIO1: PMU-SCK                                            |
| pin 122 (PD26) | 5002000.i2c     | (GPIO UNCLAIMED)    | function i2c0 group PD26     | GPIO0: PMU-SDA                                            |
| pin 160 (PF0)  | 4020000.mmc     | (GPIO UNCLAIMED)    | function mmc0 group PF0      | connects to SD card                                       |
| pin 161 (PF1)  | 4020000.mmc     | (GPIO UNCLAIMED)    | function mmc0 group PF1      |                                                           |
| pin 162 (PF2)  | 4020000.mmc     | (GPIO UNCLAIMED)    | function mmc0 group PF2      |                                                           |
| pin 163 (PF3)  | 4020000.mmc     | (GPIO UNCLAIMED)    | function mmc0 group PF3      |                                                           |
| pin 164 (PF4)  | 4020000.mmc     | (GPIO UNCLAIMED)    | function mmc0 group PF4      |                                                           |
| pin 165 (PF5)  | 4020000.mmc     | (GPIO UNCLAIMED)    | function mmc0 group PF5      |                                                           |
| pin 166 (PF6)  | (MUX UNCLIAMED) | 300b000.pinctrl:166 |                              | mmc0/cd-gpios                                             |
| pin 192 (PG0)  | 4021000.mmc     | (GPIO UNCLAIMED)    | function mmc1 group PG0      | GPIO22: SDIO_CLK; wifi                                    |
| pin 193 (PG1)  | 4021000.mmc     | (GPIO UNCLAIMED)    | function mmc1 group PG1      | GPIO23: SDIO_CMD; wifi                                    |
| pin 194 (PG2)  | 4021000.mmc     | (GPIO UNCLAIMED)    | function mmc1 group PG2      | GPIO24: SDIO_D0; wifi                                     |
| pin 195 (PG3)  | 4021000.mmc     | (GPIO UNCLAIMED)    | function mmc1 group PG3      | GPIO25: SDIO_D1; wifi                                     |
| pin 196 (PG4)  | 4021000.mmc     | (GPIO UNCLAIMED)    | function mmc1 group PG4      | GPIO26: SDIO_D2; wifi                                     |
| pin 197 (PG5)  | 4021000.mmc     | (GPIO UNCLAIMED)    | function mmc1 group PG5      | GPIO27: SDIO_D3; wifi                                     |
| pin 198 (PG6)  | 5000400.serial  | (GPIO UNCLAIMED)    | function uart1 group PG6     | GPIO14: UART_RXD; bluetooth                               |
| pin 199 (PG7)  | 5000400.serial  | (GPIO UNCLAIMED)    | function uart1 group PG7     | GPIO15: UART_TXD; bluetooth                               |
| pin 200 (PG8)  | 5000400.serial  | (GPIO UNCLAIMED)    | function uart1 group PG8     | GPIO17: UART_CTS_N; bluetooth                             |
| pin 201 (PG9)  | 5000400.serial  | (GPIO UNCLAIMED)    | function uart1 group PG9     | GPIO16: UART_RTS_N; bluetooth                             |
| pin 202 (PG10) | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO19: PCM_SYNC                                          |
| pin 203 (PG11) | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO18: PCM_CLK                                           |
| pin 204 (PG12) | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO21: PCM_IN                                            |
| pin 205 (PG13) | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO22: PCM_OUT                                           |
| pin 206 (PG14) | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              |                                                           |
| pin 224 (PH0)  | 5000000.serial  | (GPIO UNCLAIMED)    | function uart0 group PH0     | GPIO33: Ext. UART_RX                                      |
| pin 225 (PH1)  | 5000000.serial  | (GPIO UNCLAIMED)    | function uart0 group PH1     | GPIO32: Ext. UART_TX                                      |
| pin 226 (PH2)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | should be /connector/ddc-en-gpios???                      |
| pin 227 (PH3)  | 5011000.spi     | (GPIO UNCLAIMED)    | function spi1 group PH3      | GPIO36: Ext. LATCH                                        |
| pin 228 (PH4)  | 5011000.spi     | (GPIO UNCLAIMED)    | function spi1 group PH4      | GPIO37: Ext. STROBE                                       |
| pin 229 (PH5)  | 5011000.spi     | (GPIO UNCLAIMED)    | function spi1 group PH5      | GPIO38: Ext. MOSI                                         |
| pin 230 (PH6)  | 5011000.spi     | (GPIO UNCLAIMED)    | function spi1 group PH6      | GPIO39: Ext. SCK                                          |
| pin 231 (PH7)  | (MUX UNCLIAMED) | (GPIO UNCLAIMED)    |                              | GPIO2: PMU-IRQ                                            |
| pin 232 (PH8)  | 6000000.hdmi    | (GPIO UNCLAIMED)    | function hdmi group PH8      |                                                           |
| pin 233 (PH9)  | 6000000.hdmi    | (GPIO UNCLAIMED)    | function hdmi group PH9      |                                                           |
| pin 234 (PH10) | 6000000.hdmi    | (GPIO UNCLAIMED)    | function hdmi group PH10     |                                                           |

