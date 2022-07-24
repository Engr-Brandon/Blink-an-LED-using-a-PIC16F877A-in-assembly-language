           ;Code written by Engr Brandon NM
;
           list p=p16f84A       ;type of microcontroller
           #include "p16f84A.inc"    
           __CONFIG _CP_OFF & _WDT_OFF & _XT_OSC & _PWRTE_OFF
         org   0x00
         goto  start         ;goto beginning of program

start    bsf    STATUS,RP0      ;bank1 selected
         bsf    TRISA,0         ;RA0 as input
         bcf    TRISB,0         ;RB0 as output
         bcf    STATUS,RP0      ;bank0 slected// move out of status
MAIN
         bcf    PORTB,0         ;off the LED
         btfsc  PORTA,0         ;check if RA0 is at logic 0
         bsf    PORTB,0         ;if RA0 is clear, skip this instruction
                                ;if RA0 is set, execute it
         goto    MAIN
         END
