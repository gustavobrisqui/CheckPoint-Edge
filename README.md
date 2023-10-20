# CheckPoint-Edge
Gustavo Brisqui Martinez || RM: 97969
Guilherme Matheus Dal Posolo || RM: 98694
Ryan Perez Pacheco || RM: 98782
Guilherme Rezende Bezerra || RM: 98508
Matheus Brisqui Martinez || RM: 97892




Readme código C++:
Pré-requisitos
Para fazer este código funcionar, você precisará de:

Um ESP32 (dispositivo de hardware).
Acesso a uma rede Wi-Fi com um nome (SSID) e senha (PASSWORD) configurados.
Um servidor MQTT (broker) com um endereço (BROKER_MQTT) e porta (BROKER_PORT) definidos.
Inicialização e Configuração
Antes de começar, você precisará fazer algumas configurações iniciais no código:

Defines: No início do código, você encontrará algumas definições (defines) importantes, como IDs MQTT, tópicos MQTT para publicação e subscrição, tipo de sensor DHT e pinos de hardware. Certifique-se de ajustar essas definições conforme necessário, especialmente se estiver usando vários dispositivos ESP32 em sua rede MQTT.

Conexão Wi-Fi: Configure o nome da rede Wi-Fi (SSID) e a senha (PASSWORD) da sua rede Wi-Fi, para que o ESP32 possa se conectar à rede.

Broker MQTT: Configure o endereço do servidor MQTT (BROKER_MQTT) e a porta (BROKER_PORT) para que o ESP32 possa se conectar ao servidor MQTT.

Funções no Código
O código é dividido em várias funções para facilitar a leitura e a manutenção. Vamos explicar o que cada função faz:

setup()
Inicializa o LED onboard.
Inicializa a comunicação serial para fins de depuração.
Configura a conexão Wi-Fi.
Inicializa a conexão com o servidor MQTT.
Publica uma mensagem no tópico MQTT para indicar que o LED está desligado.
initSerial()
Inicializa a comunicação serial com uma taxa de baud de 115200, permitindo a exibição de mensagens de depuração no terminal serial.
initWiFi()
Inicializa e conecta-se à rede Wi-Fi especificada (SSID e PASSWORD).
initMQTT()
Inicializa a configuração MQTT, definindo o servidor MQTT (BROKER_MQTT) e a porta (BROKER_PORT) a serem usados.
Atribui a função mqtt_callback como função de callback para lidar com mensagens MQTT recebidas.
mqtt_callback()
Esta função é chamada sempre que uma mensagem é recebida em um dos tópicos MQTT assinados.
Analisa a mensagem recebida e controla o LED onboard do ESP32 com base na mensagem ("lamp104@on|" liga o LED, "lamp104@off|" desliga o LED).
reconnectMQTT()
Reconecta-se ao servidor MQTT, caso a conexão não esteja ativa ou tenha sido perdida.
Subscreve novamente aos tópicos MQTT após a reconexão bem-sucedida.
reconectWiFi()
Garante que o ESP32 esteja conectado à rede Wi-Fi, reconectando-se se necessário.
VerificaConexoesWiFIEMQTT()
Verifica o status das conexões Wi-Fi e MQTT.
Reestabelece as conexões se estiverem desconectadas.
EnviaEstadoOutputMQTT()
Publica o estado atual do LED onboard no tópico MQTT definido.
Isso permite monitorar remotamente se o LED está ligado ou desligado.
InitOutput()
Inicializa o pino do LED onboard como saída e configura-o para o estado lógico alto, que, neste caso, significa que o LED está desligado.
O código também pisca o LED algumas vezes durante a inicialização.
loop()
Garante o funcionamento das conexões Wi-Fi e MQTT.
Envia o estado do LED onboard e informações de telemetria (luminosidade, temperatura e umidade) para o servidor MQTT em intervalos regulares.
Continua a receber mensagens do servidor MQTT e chama a função mqtt_callback quando novas mensagens são recebidas.
Execução do Código
Após configurar o código e as conexões de acordo com suas necessidades, faça o upload do código para o ESP32. O ESP32 se conectará à sua rede Wi-Fi e ao servidor MQTT. Agora, você pode controlar o LED onboard e receber informações de telemetria do ESP32 usando mensagens MQTT. Certifique-se de configurar os tópicos MQTT correspondentes no servidor MQTT para receber e enviar informações.

Esse código é útil para projetos de IoT, onde você deseja controlar dispositivos remotamente e coletar dados de sensores em tempo real. Certifique-se de que as bibliotecas necessárias estejam instaladas em seu ambiente de desenvolvimento para evitar erros de compilação.

Lembre-se de que este README é um guia simplificado e pode ser necessário mais conhecimento em eletrônica e IoT para adaptar o código a suas necessidades específicas.

Readme Código Python:
O código demonstra como criar um cliente MQTT que se inscreve em tópicos específicos e imprime as mensagens recebidas. O código não se conecta a um servidor MQTT específico, portanto, você deve substituir o endereço do servidor e as informações do tópico pelos valores apropriados para seu caso de uso.

Pré-requisitos
Para fazer este código funcionar, você precisará:

Instalar a biblioteca paho-mqtt.

Funções no Código
O código Python é relativamente simples e consiste em definir funções de callback para lidar com eventos de conexão e mensagens MQTT. Aqui estão as principais partes do código:

Instalação da Biblioteca
O código começa com a instalação da biblioteca paho-mqtt usando o comando pip install.

Execução do Código
Depois de instalar a biblioteca paho-mqtt e configurar o código com os detalhes do seu servidor MQTT, você pode executá-lo. O cliente MQTT se conectará ao servidor MQTT e começará a receber mensagens dos tópicos especificados.

Certifique-se de que o servidor MQTT esteja publicando mensagens nos tópicos /TEF/lamp104/attrs/l, /TEF/lamp104/attrs/u e /TEF/lamp104/attrs/t ou substitua os tópicos pelos apropriados para o seu caso de uso.

Este código é útil quando você deseja criar um cliente MQTT para receber dados publicados em tópicos específicos, o que é comum em projetos de IoT e comunicações MQTT em tempo real. Certifique-se de ajustar as configurações do cliente MQTT de acordo com suas necessidades específicas.
