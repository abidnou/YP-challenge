# YP-challenge IEEE ENSTAB SB
# 1 The moon's resources:
Scientists and space planners have long acknowledged that extended human residence on the Moon would be greatly aided by the use of local resources. Most lunar rocks are about 40 percent oxygen, so extracting oxygen would not be impossible there are several methods for this project extraction from lunar ilmenite (FeTiO3) with either hydrogen or carbon monoxide, carbothermal reduction of iron oxides and silicates with methane, and  molten regolith electrolysis (MRE) of silicates.Possibly on some moons and asteroids, water is present in the form of mineral hydrates, hydroxyl (-OH) groups on minerals, andor water adsorbed on mineral surfaces. Heating of the minerals can liberate the water which can be electrolyzed to provide a source of oxygen as well.The idea of extracting oxygen from rockets is to provide a clean water so that the astronauts used it during their missions. We can combinate the oxygen with hydrogen to provide water in some certain condition. Adding to that,one promising technology takes advantage of the chemistry of the moon dirt - or regolith - by adding hydrogen, which then reacts with iron oxide in the moon dirt to produce water. Such hydrogen reduction reactors heat the regolith to about 1,832 degrees Fahrenheit (1,000 degrees Celsius) so that the proper chemical reactions can occur.A process known as electrolysis can then split the extracted water into pure hydrogen and oxygen, either for rocket fuel or astronaut air supplies.NASA has already tested a hydrogen reduction reactor on Hawaii's MaunaKea Volcano. During a year-long operation, it produced 1,455 pounds (660 kg) of oxygen from a rocky soil containing 5 percent iron oxide. Now engineers have a second-generation system in the works that can produce 2,205 pounds (1,000 kg). https://www.space.com/7350-nasa-hopes-water-moon.html.
https://www.space.com/7350-nasa-hopes-water-moon.html.
# 2 Resource management:
The NASA provide a special food for the astronaut but is that food enough for them during their journey. The solution for managing resources is to make one meal pill or powders that can replacing food. For example, Rob Rhinehart thought to economize through chemistry. He found out what the body needed to survive, ordered the raw ingredients mostly in powder form, tossed them in a blender, added water, and mixed up a healthy, hearty cocktail[https://insh.world/science/what-if-there-was-a-meal-replacement-pill/] . Adding to that, NASA found that there is possibility to grow plants under certain condition, so to provide food for the astronauts the first step is to install a special environment for plants with the water extracting from rocks, hydrogen in the atmosphere, UV protection, atmosphere, and nutrients, The main challenge for astronauts is to maintain all this conditions. Many research proves that there are many veggie can be successfully grow on the moon.
# 3 Testing robotics:
Nowadays, Robots are the main important technologies in our life, the ARTEMIS mission will need an intelligent robot to help astronauts with their research for example the water research.  There is a wisdom says that more automation is always better. After all, with automation, the job usually gets done faster, and the more tasks (or sub-tasks) robots can do on their own, the less the workload on the operator for example water research, supervising, prevent dangers and many other tasks. 
# 4 Assuring data transmission and communication
#### Lora communication protocol:
The term LoRa stands for Long Range. It is a long-range, low power wireless platform that has become the de-facto technology for Internet of Things (IoT) networks worldwide. LoRa is a spread spectrum modulation technique derived from chirp spread spectrum (CSS) technology. LoRa was introduced by a company called Semtech.The basic principle is that information is encoded using chirp (a gradual increase or decrease in the frequency of the carrier wave over time). Before sending a message, the LoRa transmitter will send out a chirp signal to check that the band is free to send the message. Once the LoRa receiver has picked up the preamble chirp from the transmitter, the end of the preamble is signalled by the reverse chirp, which tells the LoRa transmitter that is it clear to begin transmission.
#### Arduino Lora transmitter with DHT11 sensor:
The DHT11 is a basic, ultra low-cost digital temperature and humidity sensor. It uses a capacitive humidity sensor and a thermistor to measure the surrounding air, and spits out a digital signal on the data pin (no analog input pins needed).
The transmitter part contains Arduino UNO Board, DHT11 Humidity & Temperature Sensor and LoRa SX1278 Module (images).
>#include <SPI.h>
>#include <LoRa.h>
>#include "DHT.h"
>#define DHTPIN A0     
 > #define DHTTYPE DHT11   
 
> DHT dht(DHTPIN, DHTTYPE);
> int hum;
> float temp; //Stores temperature value
 
>void setup() {    
  >Serial.begin(9600);
  >dht.begin();
  >while (!Serial);
  >Serial.println("LoRa Sender");
 
  >if (!LoRa.begin(433E6)) {
    >Serial.println("Starting LoRa failed!");
    >while (1);
  >}
>}
 
>void loop() 
>{
 > temp = dht.readTemperature();
 > hum = dht.readHumidity();
 
 > Serial.println("Sending packet: ");
 
  // send packet
  >LoRa.beginPacket();
  >LoRa.print("Humidity: ");
 > LoRa.print(hum);
 > LoRa.print("%");
 > LoRa.print(" Temperature:");
 > LoRa.print(temp);
 > LoRa.print("C");
  
  >Serial.print("Humidity: ");
  >Serial.print(hum);
  >Serial.print("%");
  >Serial.print(" Temperature:");
  >Serial.print(temp);
  >Serial.println("C");
  >Serial.println(""); 
 
  >LoRa.endPacket();
  >delay(1000);
>}
