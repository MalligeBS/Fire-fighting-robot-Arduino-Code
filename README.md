# Fire-fighting-robot-Arduino-Code
const int M1 = 7;
const int M2 = 6;
const int M3 = 5;
const int M4 = 4;
const int M5 = 3;
const int M6 = 2;
const int M7 = 10;
const int M8 = 9;
const int M9 = 11;
int ok = 0;

void setup() {
  // put your setup code here, to run once:
pinMode(M1, OUTPUT);
pinMode(M2, OUTPUT);
pinMode(M3, OUTPUT);
pinMode(M4, OUTPUT);
pinMode(M5, OUTPUT);
pinMode(M6, OUTPUT);
pinMode(M7, OUTPUT);
pinMode(M8, INPUT);
pinMode(M9, OUTPUT);
Serial.begin(9600);
digitalWrite(M1,LOW);
digitalWrite(M2,LOW);
digitalWrite(M3,LOW);
digitalWrite(M4,LOW);
digitalWrite(M5,LOW);
digitalWrite(M6,LOW);
digitalWrite(M7,LOW);
digitalWrite(M9,LOW);
}

void loop() {
  // put your main code here, to run repeatedly:
  if(ok == 1)
  {
    if((digitalRead(M8) == HIGH))
  {
    digitalWrite(M7,HIGH);
    digitalWrite(M9,HIGH);
    Serial.println("FIRE PUMP AUTO ON");
  }
  else
  {
    digitalWrite(M7,LOW);
    digitalWrite(M9,LOW);
  }
  }
if(Serial.available()>0)
{
  char t = Serial.read();

  if(t == '1')
  {
    digitalWrite(M1,LOW);
    digitalWrite(M2,HIGH);
    digitalWrite(M3,LOW);
    digitalWrite(M4,HIGH);
    Serial.println("FORWARD");
  }
  else if(t == '2')
  {
    digitalWrite(M1,HIGH);
    digitalWrite(M2,LOW);
    digitalWrite(M3,HIGH);
    digitalWrite(M4,LOW);
    Serial.println("BACKWARD");
  }
  else if(t == '3')
  {
    digitalWrite(M1,HIGH);
    digitalWrite(M2,LOW);
    digitalWrite(M3,LOW);
    digitalWrite(M4,HIGH);
    Serial.println("RIGHT");
  }
  else if(t == '4')
  {
    digitalWrite(M1,LOW);
    digitalWrite(M2,HIGH);
    digitalWrite(M3,HIGH);
    digitalWrite(M4,LOW);
    Serial.println("LEFT");
  }
    else if(t == '5')
  {
    digitalWrite(M1,LOW);
    digitalWrite(M2,LOW);
    digitalWrite(M3,LOW);
    digitalWrite(M4,LOW);
    Serial.println("STOP");
  }
    else if(t == '6')
  {
    digitalWrite(M5,HIGH);
    digitalWrite(M6,LOW);
    Serial.println("FIRE ARM UP");
    delay(20);
    digitalWrite(M5,LOW);
    digitalWrite(M6,LOW);
  }
    else if(t == '7')
  {
    digitalWrite(M6,HIGH);
    digitalWrite(M5,LOW);
    Serial.println("FIRE ARM DOWN");
    delay(20);
    digitalWrite(M5,LOW);
    digitalWrite(M6,LOW);
  } 
      else if(t == '8')
  {
    digitalWrite(M7,HIGH);
    Serial.println("FIRE PUMP ON");
  }
    else if(t == '9')
  {
    digitalWrite(M7,LOW);
    Serial.println("FIRE PUMP OFF");
    ok = 0;
  }
      else if(t == '0')
  {
    Serial.println("FIRE controlle auto mode");
    ok = 1;
  }     
  }
}
