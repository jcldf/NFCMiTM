# NFCMiTM - Manual de Configuração e Solução de Problemas

Este manual fornece instruções detalhadas para a configuração, uso e solução de problemas do software NFCMiTM, especificamente adaptado para ambientes que utilizam Python 2.7, dois leitores PN532, e um Raspberry Pi.

## Preparação e Configuração Inicial

### Instalação do Python 2.7

Python 2.7 geralmente vem pré-instalado em muitas distribuições Linux, incluindo Raspberry Pi OS. Para verificar a versão do Python instalada, execute:

    python --version

### Instalação e Configuração da LibNFC

#### Atualização do Sistema

    sudo apt-get update
    sudo apt-get upgrade

#### Instalação de Dependências

    sudo apt-get install autoconf libtool libpcsclite-dev libusb-dev

#### Baixe e Compile a LibNFC

    git clone https://github.com/nfc-tools/libnfc.git
    cd libnfc
    autoreconf -vis
    ./configure --prefix=/usr --sysconfdir=/etc
    make
    sudo make install

#### Verificação

    nfc-list

### Configuração dos Dispositivos PN532

Conecte um dispositivo PN532 via SPI e outro via UART ao Raspberry Pi. Verifique se as conexões estão corretas.

## Solução de Problemas de Execução

### Problemas de Importação

#### Importação de `pyHex.hexfind`

Se `pyHex.hexfind` não estiver disponível diretamente via pip, integre manualmente o módulo `hexfind.py` ao seu projeto, ajustando as importações conforme necessário.

### Configuração e Diagnóstico do libnfc

Ajuste `/etc/nfc/libnfc.conf` com as informações corretas para seus dispositivos PN532, especificando as strings de conexão para os dispositivos SPI e UART.

### Testes e Diagnósticos de Comunicação

Utilize a biblioteca `pySerial` para testar a comunicação UART:

    pip2 install pyserial

## Execução do `main.py`

Execute o script principal com Python 2.7:

    sudo python main.py

## Diagnóstico de Problemas de Detecção de Tags NFC

Assegure-se de que as tags NFC estejam corretamente posicionadas próximas ao leitor configurado como iniciador.

## Considerações Finais

Este manual aborda a instalação de dependências, execução e solução de problemas com o NFCMiTM, focado em ambientes Python 2.7. Para suporte adicional, consulte a documentação do libnfc ou entre em contato com os desenvolvedores do software.

> **Nota**: Python 2.7 alcançou o fim da vida útil. Considere migrar para Python 3 para projetos futuros para melhor segurança e suporte.




# NFCMiTM
NFC MiTM made with two PN532 readers and a Raspberry PI. Created by Aleksei Stennikov.

build:
TODO

You can also download a raspberry image file with all installed modules

PN532 Connection scheme: https://github.com/a66at/NFCMiTM/blob/main/raspberry.jpg
