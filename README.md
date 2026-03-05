
# 🎬 Demonstração em Vídeo


<div align="center">
  
https://github.com/user-attachments/assets/7b63a89a-39f8-44c1-93f7-9112d35a294b

</div>


### Explicação 

Código em C++ para ESP32 (Arduino) que utiliza um sensor de umidade do solo inserido em uma planta para monitorar o nível de umidade.
O sistema lê os dados do sensor e acende um LED automaticamente quando detecta pouca umidade
indicando que a planta precisa ser regada. O projeto demonstra uma solução simples de monitoramento de plantas com microcontrolador, resistor, jumpers e sensor de umidade.

## Código

```
// Configuração dos Pinos
const int PINO_SENSOR_UMIDADE = 33;
const int PINO_LED_SECO = 32;

// Calibração
// No ESP32, 12 bits variam de 0 (muito umido) a 4095 (muito seco)
const int LIMIAR_SECO = 2000;

void setup()
{
  // Inicia a comunicação serial a 115200
  Serial.begin(115200);

  // Configura o pino do LED como saída
  pinMode(PINO_LED_SECO, OUTPUT);

  // Nota: O ESP32 já configura o ADC34 como entrada padrão
  }

void loop()
{
  // Ação: ler o valor do sensor de umidade
  int valor_umidade = analogRead(PINO_SENSOR_UMIDADE);

  // Exibe a leitura do Monitor Serial
  Serial.print("Valor do sensor:");
  Serial.print(valor_umidade);

  if(valor_umidade > LIMIAR_SECO){
    Serial.print("ALERTA: Solo seco! Hora de Regar.");
    digitalWrite(PINO_LED_SECO, HIGH);

  }
  else{
    Serial.print("Solo Umido. Tudo Certo!");
    digitalWrite(PINO_LED_SECO, LOW);
  }
delay(5000);

}
```
