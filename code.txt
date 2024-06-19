int switch1 = 3;
int switch2 = 4; 
int pin1 = 10;
int pin2 = 11;
//int pin3 = 9;
int pmeter = A0;
//int motor;
 void setup() {
  // put your setup code here, to run once:
  pinMode(switch1, INPUT);
  pinMode(switch2, INPUT);
  pinMode(pmeter, INPUT);
  //pinMode(motor, OUTPUT);
  pinMode(pin1, OUTPUT);
  pinMode(pin2, OUTPUT);
  Serial.begin(9600);

}

void loop() {
  // put your main code here, to run repeatedly:
  int switch_signal = digitalRead(switch1);
  int switch_signal2 = digitalRead(switch2);
  int pmeter_signal = analogRead(pmeter);
  Serial.print("Pmeter : ");
  
  int pmeter_angle = map(pmeter_signal, 0, 1023, 0, 255);
  Serial.println(pmeter_angle);
  
  //Serial.print("Switch one : ");
  //Serial.print("Switch two : ");
  Serial.println(switch_signal);
  Serial.println(switch_signal2);
  //delay(1000);

  if(switch_signal  > 0){
    analogWrite(pin1, pmeter_angle);
  }
  else{
    analogWrite(pin1, 0);
  }

   if(switch_signal2 > 0){
    analogWrite(pin2, pmeter_angle);
  }
  else{
    analogWrite(pin2, 0);
  }
  delay(500);


}
