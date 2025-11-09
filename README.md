
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
ORG 00H
MOV TMOD, #20H
MOV TH1, #0FCH
MOV SCON, #40H
SETB TR1
AG: MOV SBUF, #'B'
WAIT:JNB TI, WAIT
CLR TI
END
#include<reg51.h>
void main(void)
{
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFC;
SCON=0X40;
TR1=1;
while(1)
{
SBUF='B';
while(TI==0);
T1=0;
}
}


```
### (ii) Serial Port to Transfer a Message

```
ORG 00H
MOV TMOD,#20H
MOV TH1,#0FCH
MOV SCON,#40H
SETB TR1
MOV B,30H
MOV DPTR,#4500H
AGAIN:MOVX A,@DPTR
MOV SBUF,A
WAIT:JNB TI,WAIT
CLR TI
INC DPTR
DJNZ B,AGAIN
END
#include<reg51.h>
#include<string.h>
void main(void)
{
unsigned char msg[]="Tamilselvan R";
unsigned char i;
int l = strlen(msg);
TMOD=0X20;//TIMER 1,MODE 2
TH1=0XFC;
SCON=0X40;
TR1=1;
for (i=0; i<l;i++)
{
SBUF= msg[i];
while(TI==0);
TI=0;
}
while(1);
}







```

### OUTPUT:
...

<img width="890" height="807" alt="Screenshot (89)" src="https://github.com/user-attachments/assets/0e81d743-42a1-4c6b-992c-2a02380860f6" />


### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
