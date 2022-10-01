int pino_D0 = 2;
int rpm;
volatile byte pulsos;
unsigned long timeold;

unsigned int pulsos_por_volta = 20;

void contador()
{
  pulsos++;
}

void setup()
{
  Serial.begin(74880);
  pinMode(pino_D0, INPUT);

  attachInterrupt(0, contador, FALLING);
  pulsos = 0;
  rpm = 0;
  timeold = 0;
}

void loop()
{

  if (micros() - timeold >= 1000000)
  {
    
    detachInterrupt(0);
    rpm = (60 * 1000000 / pulsos_por_volta ) / (micros() - timeold) * pulsos;
    timeold = micros();
    pulsos = 0;

    Serial.println("RPM = ");
    Serial.println(pulsos);
    Serial.println(rpm, DEC);

    attachInterrupt(0, contador, FALLING);
  }
}
