# Bot
Code for Arduino Controlled Bot with gun

char data;

const int R1_Pin = 3;
const int R2_Pin = 4;
const int L1_Pin = 5;
const int L2_Pin = 6;

const int C1_Pin = 7;
const int C2_Pin = 8;

const int GUN_Pin = 13;

void setup() {
  Serial.begin(9600); // begin serial communitication 
  Serial.println("Motor test!");
pinMode(R1_Pin, OUTPUT);
pinMode(R2_Pin, OUTPUT);
pinMode(L1_Pin, OUTPUT);
pinMode(L2_Pin, OUTPUT);

pinMode(C1_Pin, OUTPUT);
pinMode(C2_Pin, OUTPUT);
pinMode(GUN_Pin, OUTPUT);
digitalWrite(R1_Pin, LOW);
digitalWrite(R2_Pin, LOW);
digitalWrite(L1_Pin, LOW);
digitalWrite(L2_Pin, LOW);
digitalWrite(C1_Pin, LOW);
digitalWrite(C2_Pin, LOW);
digitalWrite(GUN_Pin, LOW);

}

void loop() {

  if(Serial.available()>0)
  {
    data=Serial.read();
    if(data=='2') 
    {
   Serial.println ("I AM MOVING IN FORWARD DIRECTION !" );

   digitalWrite(R1_Pin, LOW);
digitalWrite(R2_Pin, HIGH);
digitalWrite(L1_Pin, LOW);
digitalWrite(L2_Pin, HIGH);
   
}
  else if (data=='6') {
   Serial.println ("I JUST TURNED RIGHT !");
   delay (15);
 
 digitalWrite(R1_Pin, LOW);
digitalWrite(R2_Pin, LOW);
digitalWrite(L1_Pin, LOW);
digitalWrite(L2_Pin, HIGH);
  } 
  else if (data=='4') {
   Serial.println ("I JUST TURNED LEFT !");
   delay (15);
 
digitalWrite(R1_Pin, LOW);
digitalWrite(R2_Pin, HIGH);
digitalWrite(L1_Pin, LOW);
digitalWrite(L2_Pin, LOW);
  } 
  else if (data=='8') {
   Serial.println ("I AM MOVING IN BACKWARD DIRECTION !");
   delay (15);
 digitalWrite(R1_Pin, HIGH);
digitalWrite(R2_Pin, LOW);
digitalWrite(L1_Pin, HIGH);
digitalWrite(L2_Pin, LOW); 
  } 
 
else if (data=='5') {
   Serial.println ("STOPPED");
   delay (15);
digitalWrite(R1_Pin, LOW);
digitalWrite(R2_Pin, LOW);
digitalWrite(L1_Pin, LOW);
digitalWrite(L2_Pin, LOW);
  }  //RELEASE IS COMMAND TO STOP MOTOR
  else if (data=='3') {
   delay (15);
digitalWrite(C1_Pin, LOW);
digitalWrite(C2_Pin, HIGH);

  }  //RELEASE IS COMMAND TO STOP MOTOR

  else if (data=='9') {
   delay (15);
digitalWrite(C1_Pin, HIGH);
digitalWrite(C2_Pin, LOW);

  }  //RELEASE IS COMMAND TO STOP MOTOR

  else if (data=='1') {
   delay (15);
digitalWrite(C1_Pin, LOW);
digitalWrite(C2_Pin, LOW);

  }  //RELEASE IS COMMAND TO STOP MOTOR

   else if (data=='A') {
   delay (15);
digitalWrite(GUN_Pin, LOW);


  }  //RELEASE IS COMMAND TO STOP MOTOR

   else if (data=='B') {
   delay (15);
digitalWrite(GUN_Pin, HIGH);


  }  //RELEASE IS COMMAND TO STOP MOTOR
}
}


