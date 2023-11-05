스마트폰의 버튼 2개를 만들고 서버 컴퓨터(PC)의 USB와 연결된 아두이노의 13번 LED를 제어할 수 있도록 코딩하는 방법:
먼저, 아두이노에 스마트폰과 연결할 수 있는 USB 통신을 사용해야 합니다. 스마트폰 앱을 개발하여 이러한 USB 통신을 활용하여 아두이노와 통신할 수 있습니다. 아래는 아두이노와 스마트폰 앱 간의 간단한 예시입니다.

아두이노 코드:
int ledPin = 13;
int button1Pin = 2;
int button2Pin = 3;
bool ledState = LOW;

void setup() {
  pinMode(ledPin, OUTPUT);
  pinMode(button1Pin, INPUT_PULLUP);
  pinMode(button2Pin, INPUT_PULLUP);
  Serial.begin(9600);
}

void loop() {
  if (digitalRead(button1Pin) == LOW) {
    ledState = !ledState;
    digitalWrite(ledPin, ledState);
    Serial.println("Button 1 pressed");
  }

  if (digitalRead(button2Pin) == LOW) {
    ledState = !ledState;
    digitalWrite(ledPin, ledState);
    Serial.println("Button 2 pressed");
  }
}

위의 코드는 13번 핀에 연결된 LED를 두 개의 버튼으로 제어합니다. 버튼1을 누르면 LED의 상태가 변경되고 버튼2를 누르면 다시 변경됩니다. 또한, 버튼 누름 이벤트를 시리얼 포트를 통해 보냅니다.

스마트폰 앱은 USB 통신을 통해 아두이노와 통신하고 버튼 상태를 전송하고 아두이노의 응답을 표시할 수 있어야 합니다. 스마트폰 앱을 개발하기 위해서는 해당 플랫폼(Android 또는 iOS)에 따라 적절한 프로그래밍 언어 및 라이브러리를 사용해야 합니다.

아두이노에서 온도와 조도 회로를 만들고 데이터를 1초에 한 번 스마트폰 화면에 표시하는 방법:
아두이노에서 온도와 조도 센서를 연결하고 데이터를 수집한 다음, 스마트폰 앱을 통해 이 데이터를 화면에 표시할 수 있습니다. 아래는 간단한 예시입니다.

아두이노 코드:
#include <Adafruit_Sensor.h>
#include <DHT.h>

#define DHTPIN A0
#define LIGHTPIN A1

DHT dht(DHTPIN, DHT22);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  delay(1000);
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();
  int lightValue = analogRead(LIGHTPIN);

  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.print(" °C, Humidity: ");
  Serial.print(humidity);
  Serial.print(" %, Light: ");
  Serial.print(lightValue);
  Serial.println(" lux");
}

위의 코드는 DHT22 온도 및 습도 센서와 조도 센서를 사용하여 온도, 습도 및 조도 값을 읽고 시리얼 포트를 통해 출력합니다.

스마트폰 앱은 USB 또는 무선 통신을 통해 아두이노로부터 데이터를 읽고 화면에 표시해야 합니다. 이 부분은 스마트폰 앱 개발 및 데이터 표시를 위한 프레임워크 및 라이브러리에 따라 다를 수 있습니다. 스마트폰 앱을 개발하는 것은 일반적으로 Android Studio (Android) 또는 Xcode (iOS)를 사용하여 수행됩니다.
