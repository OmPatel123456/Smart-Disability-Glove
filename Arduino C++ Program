#include <Adafruit_LiquidCrystal.h>

Adafruit_LiquidCrystal lcd_1(0);

#define alarm 4
#define RED 13
#define BLUE 12 
//int minBend = 767; //0 degrees
//int maxBend = 964; //180 degrees
int PIN_three = 3;
int buffer = 50;

void setup()
{
  pinMode(A0, INPUT);
  pinMode(A1, INPUT);
  pinMode(A2, INPUT);
  pinMode(A3, INPUT);
  pinMode(A4, INPUT);
  pinMode(alarm, OUTPUT);
  pinMode(RED, OUTPUT);
  pinMode(BLUE, OUTPUT);
  Serial.begin(9600);
  
  lcd_1.begin(16, 2);
}

void loop()
{
  
  int flex1 = analogRead(A0); //reads in volage-based value 
  int flex2 = analogRead(A1);
  int flex3 = analogRead(A2);
  int flex4 = analogRead(A3);
  int flex5 = analogRead(A4);
  
  int minbend[5] = {767, 767, 767, 767, 930}; //temporary(will change when we have actual sensors)
  int maxbend[5] = {964, 964, 964, 964, 1040};
  
  if (minbend[0] < flex1 - buffer && flex1 <= maxbend[0] && flex2 - buffer < minbend[1] && flex3 - buffer < minbend[2] && flex4 - buffer < minbend[3] && flex5 - buffer < minbend[4]){
    
    lcd_1.setCursor(0, 0);
    lcd_1.print("I'm Hungry/");
    lcd_1.setCursor(0, 1);
    lcd_1.print("Thirsty");
    digitalWrite(alarm, HIGH);
  }
  
   if (minbend[1] < flex2 - buffer && flex2 <= maxbend[1] && flex1 - buffer < minbend[0] && flex3 - buffer < minbend[2] && flex4 - buffer < minbend[3] && flex5 - buffer < minbend[4]){
     
    lcd_1.setCursor(0, 0);
    lcd_1.print("I Need the");
    lcd_1.setCursor(0, 1);
    lcd_1.print("Bathroom");
    digitalWrite(alarm, HIGH);
    
  }
  
  if (minbend[2] < flex3 - buffer && flex3 <= maxbend[2] && flex1 - buffer < minbend[0] && flex2 - buffer < minbend[1] && flex4 - buffer < minbend[3] && flex5 - buffer < minbend[4]){
    
    lcd_1.setCursor(0, 0);
    lcd_1.print("I'm in Pain");
    lcd_1.setCursor(0, 1); 
    digitalWrite(alarm, HIGH);
  }
  
  if (minbend[3] < flex4 - buffer && flex4 <= maxbend[3] && flex1 - buffer < minbend[0] && flex2 - buffer < minbend[1] && flex3 - buffer < minbend[2] && flex5 - buffer < minbend[4]){
    
    lcd_1.setCursor(0, 0);
    lcd_1.print("EMERGENCY");
    lcd_1.setCursor(0, 1);
    lcd_1.print("SITUATION");
    digitalWrite(alarm, HIGH);
    
    digitalWrite(BLUE, LOW);
    digitalWrite(RED, HIGH);
    delay(200);
    digitalWrite(RED, LOW);
    digitalWrite(BLUE, HIGH);
    delay(100);
  }
  
  if (minbend[4] < flex5 - buffer && flex5 <= maxbend[4] && flex4 - buffer < minbend[3] && flex3 - buffer < minbend[2] && flex2 - buffer < minbend[1] && flex1 - buffer < minbend[0]){
    
    lcd_1.setCursor(0, 0);
    lcd_1.print("I Want to go");
    lcd_1.setCursor(0, 1);
    lcd_1.print("Outside");
    digitalWrite(alarm, HIGH);
  }
  
  //monitoring test values for first flex sensor
  Serial.println(flex1); 
  

  
}
