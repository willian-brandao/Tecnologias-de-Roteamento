# Configurações Básica de Roteadores

## Roteadores

Um roteador é um computador que tem funções específicas composto por CPU, memória, barramento do sistema e interfaces de entrada e saída. Roteadores são projetados para permitir comunicação entre duas ou mais redes diferentes e determinam o melhor caminho para que os dados possam viajarr meio de cáculos.

Os roteadores também possuem sistemas operacionais de rede para executarem os softwares de aplicativos e outros recursos de controle de máquina. Os roteadores Cisco utilizam o sistema operacional IOS que é proprietário da empresa Cisco. Os arquivos de configuração contém as instruções para controlar o tráfego de dados que passa pelos roteadores, usando protocolos de roteamento. Os roteadores tomam decisão de encaminhamento baseando-se cálculos para entregar os pacotes de forma segura aos seus destinatários. 

Um dos principais componentes do roteador são a memória RAM, a NVRAM, a memória flash e a memória de leitura (ROM), e as interfaces de rede que permitem que os roteadores se conectem com outros elementos. 

## Memória RAM

Chamada de DRAM ou RAM dinâmica ou memória de trabalho, tem as seguintes caracterísiticas:

* armazena tabelas de roteamento, que são calculadas pelos protocolos de roteamento e mantém-se registrados as melhores rotas para seus destinos;
* fornece memória ativa e temporária para o arquivo de configuração do roteador enquanto ele estiver ligado;
*  mantém a cache do ARP, a fim de identificar endereços de enlace e outras informações importantes para comnunicação interna;
*  mantém a cache do fast-switching ou comutação rápida, que é uma das técnicas usadas para comutação/chaveamento de pacotes;
*  armazena pacotes em buffers para uma execução seguinte;
*  mantém filas para armazenamento temporário de pacotes, que podem ser utilizadas em priorização de tráfego;
*  memória RAM é um tipo volátil, ou seja, perde todo o seu conteúdo quando o roteador é desligado ou reiniciado.

## Memória NVRAM

Chamada de memória de acesso aleatório não volátil

* armazena o arquivo de configuraçã que será utilizadoo somente no processo de inicialização (startup config), também pode-se chamar de arquivo de backup;
* pode armazenar várias versões de software do IOS. Nesse caso o administrador da rede pode escolher qual das versões do IOS o equipamento venha a utilizar;
* Permite que o software seja atualizado sem remover nem substituir chips do processador;
* Retém seu conteúdo quando roteador é desligado ou reiniciado, pois também é uma memória não volátil;
* É um tipo de ROM programável, apagável eletronicamente (EEPROM).

## Memória ROM

Conhecida como  memória de leitura apenas

* mantém instruções que definem o auteste realizado na inicialização do roteador, como conhecemos pelo nome POST ( Power-on self test);
* Armazena o programa de bootstrap e softwares básicos do sistema operacional de rede, responsáveis pelo boot e pela manutenção do dispositivo;
* Requer substituição de chips plugáveis na placa-mãe para as atualizações de software, pois estes geralmente são gravados em memória de acesso não tão fácil.

## Interfaces Físicas

* conectam o roteador à rede local ou remota para as funções de entrada e saída de pacotes de dados. Ex: seriais, ethernet;
* podem ficar fixadas na placa-mãe ou em um módulo separado e conectado ao barramento (off-board).

Os roteadores possuem as interfaces de rede local (LAN) e de redes remotas (WAN), emnbora sejam usados também para segmentação de redes locais, o objetivo principal do dispositivo é acessar redes WAN. As tecnologias de redes WAN para que os roteadores se conectem entre si por meio de conexõe seriais, ISDN e outras. 

*ISDN: Sigla para Integrated Services Digital Network  ou Rede Digital de Serviços Integrados. A tecnologia é voltada para telecomunicações, permitindo transmissão de voz, dados e vídeo por meio de rede telefônica tradicional.*
