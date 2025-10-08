
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
venkat.A51

ORG 00H 
MOV TMOD, #20H 
MOV TH1, #0FDH 
MOV SCON, #50H 
SETB TR1 
MAIN_LOOP:
MOV SBUF, #'B' 
WAIT_TI:
JNB TI, WAIT_TI 
CLR TI 
END

venkat.c

#include<reg51.h>
void main(void)
{
unsigned char msg[]="VENKAT";
unsigned char i;
TMOD=0X20; 
TH1=0XFA;
SCON=0X50;
TR1=1;
for(i-0;i<=12;i++)
{
SBUF=msg[i];
while(TI==0);
TI=0;
}
while(1);
}


```
### (ii) Serial Port to Transfer a Message

```
venkat.A51

ORG 00H 
START:
 MOV TMOD, #20H 
 MOV TH1, #0FAH 
 MOV SCON, #50H 
 SETB TR1 
 MOV DPTR, #4500H 
 SEND_MESSAGE: MOVX A, @DPTR 
  MOV SBUF, A 
 WAIT_TI:
 JNB TI, WAIT_TI 
 CLR TI 
 INC DPTR 
 SJMP SEND_MESSAGE 
 L1:SJMP L1


Venkat.c

#include<reg51.h>
void main(void)
{
unsigned char msg[]="VENKAT";
unsigned char i;
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
for(i-0;i<=12;i++)
{
SBUF=msg[i];
while(TI==0);
TI=0;
}
while(1);
}



```

### OUTPUT:
![WhatsApp Image 2025-10-08 at 09 11 53_412535a1](https://github.com/user-attachments/assets/4f881cff-08d5-4c9c-ae2d-bb0ae3b7941e)
![WhatsApp Image 2025-10-08 at 09 17 58_c48165ba](https://github.com/user-attachments/assets/8afe8ad7-ae17-4484-b903-7d8127b8d352)



### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
