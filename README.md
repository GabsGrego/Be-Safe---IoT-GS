# 🌧️ Be Safe - Sistema de Monitoramento Climático com ESP32 + Node-RED

Este projeto foi desenvolvido como parte do Global Solution 2025 da FIAP, com o objetivo de propor uma solução tecnológica para um dos desafios da atualidade: desastres naturais causados pelas mudanças climáticas.

Diante do aumento da frequência e intensidade de eventos como enchentes, tempestades e alagamentos, sentimos a necessidade de criar como solução um monitoramento climático em tempo real, que possa ajudar comunidades a se prepararem melhor e a agirem com rapidez diante desses riscos.

Nosso projeto integra um **ESP32** com sensores e atuadores para monitorar **temperatura**, **umidade** e **nível de precipitação**, enviando os dados em tempo real via **MQTT** para um painel visual em **Node-RED**. 
O sistema também emite **alertas visuais e sonoros** caso detecte a possibilidade de chuvas fortes e enchentes.

---

## 📦 Componentes Utilizados

### 🧠 Microcontrolador
- ESP32 DOIT DEVKIT V1

### 🌡️ Sensores
- DHT22 (Temperatura e Umidade)
- Sensor de Precipitação

### 🔊 Atuadores
- LED (indicação visual)
- Buzzer (alerta de chuva forte e enchente)

---

## 📡 Funcionalidade

O projeto implementa um sistema IoT completo onde:
- Conecta um ESP32 a uma rede Wi-Fi e estabelece comunicação com broker MQTT.
- O ESP32 lê os sensores e envia um **JSON via MQTT** com os dados para o Node-RED.
- O Node-RED recebe, armazena, exibe em **dashboards** e **aciona alertas visuais e sonoro** se necessário.
- Os dados armazenados fornecem um histórico e a visualização de tendências.

---

## 💡 Por que essa solução?
Em cenários de risco climático, cada minuto conta. Monitoramentos centralizados nem sempre conseguem atender áreas afastadas ou com infraestrutura limitada. 
Por isso, propusemos um sistema que pode ser:

- Instaurado em comunidades locais;
- Integrado a planos de defesa civil;
- Usado por moradores, ONGs ou prefeituras para criar alertas preventivos e acompanhar a evolução do clima com base em dados reais, coletados diretamente no local.

---

### 🎥 Link do video de demonstração do app no Youtube

      https://youtu.be/CXInRf-vhz0

## ⚙️ Pré-requisitos para uso

1. **Software**
   - Visual Studio Code
   - Extensão PlatformIO IDE
   - Git (para clonar o repositório)

2. **Simulação**
   - Conta Wokwi
   - Licença Wokwi Simulator
   - Extensão Wokwi no VS Code


## 🛠️ Como Usar

### Instalação e Configuração

### 1. Clone o Repositório

```bash
git clone https://github.com/GabsGrego/Be-Safe---IoT-GS.git
cd BE SAFE - IOT GS
```

### 2. Configuração do VS Code

1. Abra o VS Code
2. File > Open Folder
3. Selecione a pasta `BE SAFE - IOT GS`
4. Aguarde o PlatformIO inicializar

### 3. Configuração do Wokwi

1. Instale a extensão Wokwi
2. Faça login na sua conta
3. Verifique a licença ativa

### 4. Dependências

O projeto utiliza as seguintes bibliotecas:
- ArduinoJson (JSON)
- DHT sensor library (Sensor)
- Adafruit Unified Sensor (Base)
- PubSubClient (MQTT)

> ⚠️ **Importante**: Aguarde a instalação completa das dependências antes de compilar!

## Estrutura do Projeto

```
2TDS-GS2025/
├── q1/
│   ├── src/
│   |    └── main.cpp         # Código principal
|   └── diagram.json          # Diagrama do sistema IoT
├── platformio.ini            # Configuração
└── README.md                 # Documentação
```

## Formato dos Dados

O JSON enviado segue este formato:
```json
{
    "ID": "ID_do_Grupo",          // Identificador do grupo
    "Sensor": "Meu_ESP32",        // Nome do dispositivo
    "IP": "xxx.xxx.xxx.xxx",      // IP local
    "MAC": "XX:XX:XX:XX:XX:XX",   // Endereço MAC
    "Temperatura": xx.xx,         // Em graus Celsius
    "Umidade": xx.xx,             // Em porcentagem
    "Precipitação": xxxx          // Em milimetros
}
```

### Monitor Serial

O monitor serial (115200 baud rate) exibe informações detalhadas:

### Inicialização
```
Conectando ao Wi-Fi.....
Wi-Fi conectado!
IP: 192.168.1.100
MAC Address: A4:CF:12:BF:7A:E5
Conectando ao Broker MQTT...
Conectado ao Broker!
```

### Envio de Dados
```
{
  "ID": "BeSafe_553766",
  "Sensor": "Modulo_de_Monitoramento_ESP32",
  "IP": "10.13.37.2",
  "MAC": "24:0A:C4:00:01:10",
  "Temperatura": 24,
  "Umidade": 40,
  "Precipitacao": 87.45
}
Mensagem publicada com sucesso!
```

### Possíveis Erros
```
Reconectando Wi-Fi...     // Perda de conexão
Erro na leitura do DHT    // Falha no sensor
Falha na conexão. Estado: -2   // Problema MQTT
```

O LED onboard (GPIO2) pisca após cada envio bem-sucedido!

O LED conectado a placa acende em caso de chuva forte!

O Buzzer irá tocar em caso de possibilidade de enchente!

## Visualização dos Dados

1. **Node-RED**
   - Inicialize no cmd para rodar localmente: cmd > `node-red`
   - Acesse: `htt´://localhost:1880`

2. Importar o Fluxo no Node-RED
   - Vá até a pasta node-red/
   - Copie o conteúdo de flow.json
   - No Node-RED clique no menu > Import > Cole o conteúdo

3. Clique em Implementar

![image](https://github.com/user-attachments/assets/67187248-af19-489c-a0c5-fbd7fe249d3e)

4. Visualização dos dados chegando

![image](https://github.com/user-attachments/assets/3dfc8ffe-9a46-4f81-81a9-4edfede0c954)

5. Visualização em tempo real dos gráficos

![image](https://github.com/user-attachments/assets/b841b3f1-8293-4d05-a488-e436ed80cbf6)

---

## Expansão Futura

- **Integração com o aplicativo Be Safe**


##💡 Créditos

Desenvolvedores do Projeto:
- Gabriel Grego
- Kayque Ferreira
- André Alves

Professor Orientador: André Tritiack

FIAP - Global Solutions 2025

