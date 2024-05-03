#include <ESP8266WiFi.h>
#include <Arduino.h>

extern "C" {
  #include <user_interface.h>
}

static void ICACHE_FLASH_ATTR handlePacket(unsigned char* buf, uint16_t len) {
  for (int c=0; c < len; c++){
    Serial.printf("%d:%d  ", c, (int)buf[c]);
  }
  Serial.println();
}

void setup() {
  Serial.begin(115200);
  Serial.println();
  wifi_set_opmode(STATION_MODE);
  wifi_promiscuous_enable(0);
  WiFi.disconnect();
  wifi_set_promiscuous_rx_cb(handlePacket);
  wifi_set_channel(6);
  wifi_promiscuous_enable(1);
}

void loop(){}
