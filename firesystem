#include <LiquidCrystal.h>
LiquidCrystal lcd(12,11,5,4,3,2);
int const gas_sensor = A1;
float vout;
float vout1;
int const buz	= 13;
int LEDGREEN 	= 10;
int LEDYELLOW	= 9;
int LEDRED	= 8;
int ledred2=7;
float temp; 
int pinTemp = A4;


void setup(){
  lcd.begin(16,2);
  pinMode(A4,INPUT);
  lcd.print("hello world");
  pinMode(LEDGREEN, OUTPUT);
  pinMode(LEDYELLOW, OUTPUT);
  pinMode(LEDRED, OUTPUT);
  pinMode(ledred2, OUTPUT);
  pinMode(buz, OUTPUT);
  Serial.begin(9600);
}

void loop(){
  vout=analogRead(A4);
  vout1=(vout/1023)*5000;
  temp=(vout1-500)/10;
  lcd.clear();
  lcd.print(temp);
  
  
 
  
  
  
  
  int value = analogRead(gas_sensor);
  
  if (temp>=40){
  	digitalWrite(ledred2, HIGH);
  }
  else{
    digitalWrite(ledred2, LOW);
  }
  if(value <=24){
  	digitalWrite(LEDGREEN, HIGH);
  	Serial.println ("Gas leak low");
	digitalWrite(buz, LOW);
    lcd.setCursor(0,1);
    lcd.print("No Fire ");
  }else{
  	digitalWrite(LEDGREEN, LOW);
  }
  if(value >= 25 and value<=74){
    digitalWrite(buz, HIGH);
  	digitalWrite(LEDYELLOW, HIGH);
    Serial.println ("Gas leak medium");
    lcd.setCursor(0,1);
    lcd.print("Danger of fire ");
    //digitalWrite(buz, LOW);
  }else{
	digitalWrite(buz, LOW);
  	digitalWrite(LEDYELLOW, LOW);
    
  }
  if(value >= 75){
    lcd.setCursor(0,1);
    lcd.print("FIRE EVACUATE ");
	tone(buz,500);
  	digitalWrite(LEDRED, HIGH);
    Serial.println ("Gas leak high");
    
  }else{
  	digitalWrite(LEDRED, LOW);
	noTone(buz);
  }
  Serial.println(temp);
  delay(250);
}
