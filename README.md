# tempandhumiditysensor_iotbased
#include "thingProperties.h"
#include "DHT.h"

#define DHTpin D4 // D4 on the nodemcu ESP8266

#define DHTTYPE DHT11

DHT dht(DHTpin,DHTTYPE);

void setup() {
  // Initialize serial and wait for port to open:
  Serial.begin(1152600);
  // This delay gives the chance to wait for a Serial Monitor without blocking if none is found
  delay(1500); 

  // Defined in thingProperties.h
  initProperties();

  // Connect to Arduino IoT Cloud
  ArduinoCloud.begin(ArduinoIoTPreferredConnection);
 setDebugMessageLevel(2);
  ArduinoCloud.printDebugInfo();
}

void loop() {
  ArduinoCloud.update();
  // Your code here 
   float hm= dht.readHumidity();

    Serial.print("Humidity ");

    Serial.println(hm);

    float temp=dht.readTemperature();

      Serial.print("Temperature ");

    Serial.println(temp);

    humidity=hm;

    temperature=temp;

    message="Temperature = " + String (temperature)+"  Humidity = " + String(humidity);

}
void onHumidityChange()  {
  // Add your code here to act upon Humidity change
}

/*
  Since Msg is READ_WRITE variable, onMsgChange() is
  executed every time a new value is received from IoT Cloud.
*/
void onMsgChange()  {
  // Add your code here to act upon Msg change
}



/*
  Since Message is READ_WRITE variable, onMessageChange() is
  executed every time a new value is received from IoT Cloud.
*/
void onMessageChange()  {
  // Add your code here to act upon Message change
}
void dht_sensor_getdata()

  {

    float hm= dht.readHumidity();

    Serial.print("Humidity ");

    Serial.println(hm);

    float temp=dht.readTemperature();

      Serial.print("Temperature ");

    Serial.println(temp);

    humidity=hm;

    temperature=temp;

    message="Temperature = " + String (temperature)+"  Humidity = " + String(humidity);

  }
