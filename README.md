# P7
cpp 
CopyEdit 
const int sensorPin = A0;      
float temperatureC = 0;        
void setup() { 
Serial.begin(9600);          
// LM35 connected to analog pin A0 
// Variable to store temperature in Celsius 
// Start serial communication at 9600 baud 
Serial.println("CLEARDATA");  // Clear previous data in PLX-DAQ 
Serial.println("LABEL,Time,Temperature (C)"); // Labels for columns 
} 
void loop() { 
int sensorValue = analogRead(sensorPin);  // Read analog value (0–1023) 
// Convert to voltage 
float voltage = sensorValue * (5.0 / 1023.0);   
// Convert voltage to temperature 
temperatureC = voltage / 0.01;  // LM35 gives 10mV per °C 
// Send data to PLX-DAQ or serial monitor
Serial.print("DATA,TIME,");   
// Required format for PLX-DAQ 
Serial.println(temperatureC); // Send temperature data 
delay(1000);  // Delay 1 second between readings 
} 
