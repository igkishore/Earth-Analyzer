#include <SPI.h>
#include <nRF24L01.h>
#include <printf.h>
#include <RF24.h>
#include <RF24_config.h>

RF24 radio(7, 8); // CSN, CE
const byte address[6] = "00001";

int x_key = A1;                                              
int y_key = A0;                                              
int p_key = A3;                                              
int q_key = A2;                                              
int x_pos;
int y_pos;
int p_pos;
int q_pos;

void setup() {
  radio.begin();
  radio.openWritingPipe(address);
  radio.setPALevel(RF24_PA_MIN);
  radio.setChannel(87);
  radio.setDataRate(RF24_250KBPS);
  radio.stopListening();
 
  Serial.begin(9600);
  pinMode (x_key, INPUT) ;                    
  pinMode (y_key, INPUT) ;
  pinMode (p_key, INPUT) ;                    
  pinMode (q_key, INPUT) ;        
}
int pos;
void loop() {
  x_pos = analogRead (x_key) ;  
  y_pos = analogRead (y_key) ;  
  p_pos = analogRead (p_key) ;  
  q_pos = analogRead (q_key) ;  
  Serial.println(x_pos);
  Serial.println(y_pos);
  Serial.println(p_pos);
  Serial.println(q_pos);
  if (p_pos>400 && p_pos<600 && q_pos>400 && q_pos<600)
  {
  if(x_pos>400 && x_pos<600 && y_pos>400 && y_pos<600)
  {
    pos=100;
    radio.write(&pos, sizeof(pos));
  }
  if(x_pos>400 && x_pos<600 && y_pos<400)
  {
    pos=200;
    radio.write(&pos, sizeof(pos));
  }
  if(x_pos>400 && x_pos<600 && y_pos>600)
  {
    pos=300;
    radio.write(&pos, sizeof(pos));
  }
  if(y_pos>400 && y_pos<600 && x_pos<400)
  {
    pos=400;
    radio.write(&pos, sizeof(pos));
  }
  if(y_pos>400 && y_pos<600 && x_pos>600)
  {
    pos=500;
    radio.write(&pos, sizeof(pos));
  }
  Serial.println(pos);
  delay(100);
}
else if(p_pos<400 || p_pos>600)
{
  if(p_pos<400)
  {
    pos=600;
    radio.write(&pos, sizeof(pos));
  }
  if(p_pos>600)
  {
    pos=700;
    radio.write(&pos, sizeof(pos));
  }
  delay(100);
}
}
