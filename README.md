# IOT_CODE
IOT Practical 5 to 13

Assignment No: 5
Code:
// C++ code
//
void setup()
{
 pinMode(LED_BUILTIN, OUTPUT);
}
void loop()
{
 digitalWrite(LED_BUILTIN, HIGH);
 delay(100); // Wait for 1000 millisecond(s)
 digitalWrite(LED_BUILTIN, LOW);
 delay(100); // Wait for 1000 millisecond(s)
}
Output:
Assignment No: 6
Code:
// C++ code
//
int counter = 0;
void setup()
{
Serial.begin(9600);
pinMode(7,OUTPUT);
pinMode(8,OUTPUT);
pinMode(9,OUTPUT);
}
void loop() {
if(counter == 31)
{
counter=0;
}
if(counter < 31)
{
Serial.println(counter);
}
counter = counter + 1;
delay(100);
if(counter > 0 && counter < 11 )
{
digitalWrite(7,HIGH);
digitalWrite(8,LOW);
digitalWrite(9,LOW);
}
if(counter > 10 && counter < 21 )
{
digitalWrite(7,LOW);
digitalWrite(8,HIGH);
digitalWrite(9,LOW);
}
if(counter > 20 && counter < 31 )
{
digitalWrite(7,LOW);
digitalWrite(8,LOW);
digitalWrite(9,HIGH);
}
}
Output:
Assignment No: 7
Code:
int redPin = 11;
int greenPin = 10;
int bluePin = 9;
//uncomment this line if using a Common Anode LED
//#define COMMON_ANODE
void setup()
{
 pinMode(redPin, OUTPUT);
 pinMode(greenPin, OUTPUT);
 pinMode(bluePin, OUTPUT);
}
void loop()
{
 setColor(255, 0, 0); // red
 delay(1000);
 setColor(0, 255, 0); // green
 delay(1000);
 setColor(0, 0, 255); // blue
 delay(1000);
 setColor(255, 255, 0); // yellow
 delay(1000);
 setColor(80, 0, 80); // purple
 delay(1000);
 setColor(0, 255, 255); // aqua
 delay(1000);
}
void setColor(int red, int green, int blue)
{
 #ifdef COMMON_ANODE
 red = 255 - red;
 green = 255 - green;
 blue = 255 - blue;
 #endif
 analogWrite(redPin, red);
 analogWrite(greenPin, green);
 analogWrite(bluePin, blue);
}
Output:
Assignment No: 8
Code:
// C++ code
void setup()
{
 Serial.begin(9600);
}
void loop()
{
 int sqrt;
 if(Serial.available()>0)
 {
 int read=Serial.readString().toInt();
 Serial.print("You Entered:");
 Serial.println(read);
 int out=read*read;
 Serial.print("Square is:");
 Serial.println(out);
 }
}
Output:
You Entered:2
Square is:4
You Entered:2
Square is:4
You Entered:6
Square is:36
Assignment No: 9
Code:
// Define the pins for the RGB LED
const int redPin = 7;
const int greenPin = 6;
const int bluePin = 5;
// Define the pin for the potentiometer
const int potPin = A0;
void setup() {
 // Set the RGB LED pins as outputs
 pinMode(redPin, OUTPUT);
 pinMode(greenPin, OUTPUT);
 pinMode(bluePin, OUTPUT);
}
void loop() {
 // Read the value from the potentiometer
 int potValue = analogRead(potPin);
 // Map the potentiometer value to a range of 0-255
 int colorValue = map(potValue, 0, 1023, 0, 255);
 // Set the color of the RGB LED based on the potentiometer value
 analogWrite(redPin, colorValue);
 analogWrite(greenPin, colorValue/2);
 analogWrite(bluePin, colorValue/4);

 // Add a small delay to reduce flickering
 delay(10);
}
Output:
Assignment No: 10
Code:
float temp;
int tempPin = 0;
void setup()
{
Serial.begin(9600);
}
void loop()
{
temp = analogRead(tempPin);
temp = temp * 0.48828125;
 Serial.print("TEMPERATURE =");
 Serial.print(temp);
 Serial.print("*C");
 Serial.println();
 delay(1000);
}
Output:
TEMPERATURE =347.66*C
TEMPERATURE =4.88*C
TEMPERATURE =417.48*C
TEMPERATURE =278.32*C
TEMPERATURE =460.45*C
TEMPERATURE =449.71*C
TEMPERATURE =263.18*C
TEMPERATURE =309.57*C
TEMPERATURE =244.14*C
TEMPERATURE =146.48*C
TEMPERATURE =331.05*C
TEMPERATURE =252.44*C
TEMPERATURE =63.96*C
TEMPERATURE =42.48*C
TEMPERATURE =81.05*C
TEMPERATURE =193.36*C
TEMPERATURE =106.93*C
TEMPERATURE =235.84*C
TEMPERATURE =396.48*C
TEMPERATURE =33.69*C
TEMPERATURE =41.02*C
TEMPERATURE =39.06*C
TEMPERATURE =183.59*C
Assignment NO: 11
Code:
int baselineTemp = 0;
int celsius = 0;
int fahrenheit = 0;
int hfahrenheit = 0;
int lfahrenheit = 0;
void setup()
{
 pinMode(A0, INPUT);
 Serial.begin(9600);
}
void loop()
{
 baselineTemp = 40;

 celsius = map(((analogRead(A1) - 20) * 3.04), 0, 1023, -40, 125);

 fahrenheit = ((celsius * 9) / 5 + 32);
 if(fahrenheit>hfahrenheit)
 {
 hfahrenheit=fahrenheit;
 }
 if(fahrenheit<lfahrenheit)
 {
 lfahrenheit=fahrenheit;
 }
 Serial.print(fahrenheit);
 Serial.println(" F : Current Temperature");
 Serial.println("");
 Serial.print(hfahrenheit);
 Serial.println(" F :The Heighest temprature");
 Serial.print(lfahrenheit);
 Serial.println(" F : The lowest temprature");
 Serial.println("");
 delay(2000);
 }
Output:
77 F : Current Temperature
77 F :The Heighest temprature
0 F : The lowest temprature
77 F : Current Temperature
77 F :The Heighest temprature
0 F : The lowest temprature
77 F : Current Temperature
77 F :The Heighest temprature
0 F : The lowest temprature
77 F : Current Temperature
77 F :The Heighest temprature
0 F : The lowest temprature
Assignment No: 12
Code:
#define fsrpin A0
#define buzzer 9
int fsrreading;
void setup() {
 Serial.begin(9600);
}
void loop() {
 fsrreading = analogRead(fsrpin);
 Serial.println(fsrreading);
 if(fsrreading>200){
 buzzerAlert();
 }
}
void buzzerAlert() {
 // Activate the buzzer for a specific duration
 tone(9, 220, 100);
 delay(200);
}
Output:
0
0
0
0
0
0
0
0
0
385
385
385
385
385
385
385
385
401
401
401
401
401
401
401
401
401
401
401
381
381
381
346
295
280
280
280
280
255
255
323
323
385
385
417
417
417
425
425
425
425
425
425
425
425
Assignment No:13
Code:
float cm=0;
float inches=0;
int LEDR=2;
int LEDB=3;
int LEDG=4;
long readultrasonicDistance (int triggerPin, int echoPin)
{
pinMode (triggerPin, OUTPUT); // clear the trigger
digitalWrite (triggerPin, LOW);
delay(5000);
// Sets the trigger pin to HIGH state for 10 microseconds
digitalWrite(triggerPin, HIGH);
delay(5000);
digitalWrite(triggerPin, LOW);
pinMode (echoPin, INPUT);
// Reads the echo pin, and returns the sound wave travel time
return pulseIn(echoPin,HIGH);
}
void setup()
{
pinMode(LEDR,OUTPUT);
pinMode(LEDB,OUTPUT);
pinMode(LEDG,OUTPUT);
Serial.begin(9600);
}
void loop()
{
 // measure the ping tine in cm
cm =0.01723 *readultrasonicDistance (6,5);
//convert to inches by dividing by 2.34
if(cm>=0 && cm<50)
{
 digitalWrite(LEDR,HIGH);
 Serial.print("LED= RED, ");
 delay(500);
}
else
{
digitalWrite(LEDR,LOW);
}
if(cm>=50 && cm<100)
{
 digitalWrite(LEDG,HIGH);
 Serial.print("LED= GREEN, ");
 delay(5000);
}
else
{
digitalWrite(LEDG,LOW);
}
if(cm>=100 && cm<150)
{
 digitalWrite(LEDB,HIGH);
 Serial.print("LED= BLUE, ");
 delay(5000);
}
else
{
digitalWrite(LEDB,LOW);
}
if(cm>=150 && cm<200)
{
 digitalWrite(LEDR,HIGH);
 digitalWrite(LEDB,HIGH);
 digitalWrite(LEDG,HIGH);
 Serial.print("LED= WHITE, ");
 delay(5000);
}
else
{
digitalWrite(LEDR,LOW);
digitalWrite(LEDG,LOW);
digitalWrite(LEDB,LOW);
}
if(cm>=200 && cm<250)
{
 digitalWrite(LEDB,HIGH);
 digitalWrite(LEDG,HIGH);
 Serial.print("LED= WHITE, ");
 delay(5000);
}
else
{
digitalWrite(LEDG,LOW);
digitalWrite(LEDB,LOW);
}
if(cm>=250 && cm<300)
{
 digitalWrite(LEDR,HIGH);
 digitalWrite(LEDG,HIGH);
 Serial.print("LED= WHITE, ");
 delay(5000);
}
else
{
digitalWrite(LEDR,LOW);
digitalWrite(LEDG,LOW);
}
if(cm>=300 && cm<325)
{
 digitalWrite(LEDR,HIGH);
 digitalWrite(LEDB,HIGH);
 Serial.print("LED= WHITE, ");
 delay(5000);
}
else
{
digitalWrite(LEDR,LOW);
digitalWrite(LEDG,LOW);
}
inches= (cm/2.54);
Serial.print (cm);
Serial.print(" CM, ");
Serial.print (inches);
Serial.print(" IN ");
Serial.println();
delay(5000); // wait for 100 millisecond(s)
}
Output:
LED= WHITE, 176.35 CM, 69.43 IN
LED= WHITE, 322.06 CM, 126.80 IN
LED= WHITE, 220.32 CM, 86.74 IN
LED= GREEN, 94.54 CM, 37.22 IN
LED= WHITE, 200.59 CM, 78.97 IN

