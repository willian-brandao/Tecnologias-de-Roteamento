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

## Memória Flash

* mantém a imagem do sistema operacional (IOS) que será usado no processo de boot do equipamento;
* pode armazenar várias versões do software do IOS. Nesse caso o administrador da rede pode escolher qual das versões do IOS o equipamento venha a utilizar;
* permite que o software seja atualizado sem remover nem substituir chips do processador;
* retém seu conteúdo quando o roteador é desligado ou reiniciado, pois também é uma memória não volátil;
* é um tipo de ROM programável, apagável eletronicamente (EEPROM).
## Interfaces Físicas

* conectam o roteador à rede local ou remota para as funções de entrada e saída de pacotes de dados. Ex: seriais, ethernet;
* podem ficar fixadas na placa-mãe ou em um módulo separado e conectado ao barramento (off-board).

![[Pasted image 20251117215154.png]]
Os roteadores possuem as interfaces de rede local (LAN) e de redes remotas (WAN), embora sejam usados também para segmentação de redes locais, o objetivo principal do dispositivo é acessar redes WAN. As tecnologias de redes WAN para que os roteadores se conectem entre si por meio de conexõe seriais, ISDN[^1] e outras. 

[^1]: *ISDN: Sigla para Integrated Services Digital Network  ou Rede Digital de Serviços Integrados. A tecnologia é voltada para telecomunicações, permitindo transmissão de voz, dados e vídeo por meio de rede telefônica tradicional.*

O roteadores são os equipamentos de rede que compõem o backbone das grandes redes, como intranets e até mesmo da internet. São equipamentos da camada de rede, operando na camada 3 do modelo ISO/OSI, tomando decisões de encaminhamento com base nos endereços de rede destino, que foi previamente calculada por um algoritmo de roteamento ou até mesmo por uma rota estaticamente configurada. As duas principais funções de um roteador são a seleção do melhor caminho para a entrega de dados a um destino e a comutação de pacotes para a interfaces apropriadas. Os roteadores realizam essas funções criando tabelas de roteamento e trocando informações de rede com outros roteadores em uma topologia.

Um administrador de redes pode manter tabelas de roteamento através da configuração de rotas estáticas, mas geralmente as tabelas de roteamento são mantidas dinamicamente por meio da utilização de um protocolo de roteamento dinâmico, que trocam informações sobre toda a topologia. 

![[Pasted image 20251117220331.png]]

## Determinação de Caminho

Uma interconexão de redes corretamente configurada oferece as seguinte funcionalidade:

* Endereçamento fim a fim consistente;
* Endereços que representam topologias de rede;
* Seleção do melhor caminho;
* Roteamento dinâmico ou estático;
* Comutação.

Considera-se que uma rede WAN opera na camada física e na camada de enlace do modelo OSI, não significa que as outras cinco camadas desse modelo de referência não sejam encontradas em uma WAN. Significa apenas que as características que diferenciam uma WAN de uma LAN normalmente são encontradas na camada física e na camada de enlace. Sendo que os padrões e os protocolos utilizados nas camadas 1 e 2 das WANs são diferentes dos utilizados nas mesmas camadas das LANs.

A camada física WAN descreve a interface entre o equipamento terminal de dados (DTE) e o equipamento de terminação do circuito de dados (DCE). Tradicionalmente, o DCE é o provedor do serviço e o DTE é o dispositivo conectado à rede de um determinado cliente. Neste modelo, os serviços oferecidos para o DTE são disponibilizados através de um modem ou CSU/DSU, que é uma espécie de modem digital usado em grandes instalações.

Como já foi percebido e como o nome indica, a principal função de um roteador é o roteamento, que ocorre na camada de rede do modelo OSI, que ocorre na camada de rede do modelo OSI, mas se uma WAN opera nas camadas 1 e 2, logo, ele opera em redes locais e redes WAN. Como geralmente ocorre na área de redes, pois ele possui interfaces tanto para conexão local como conexão remota. Um roteador pode ser exclusivamente um dispositivo de rede local, pode ser exclusivamente um dispositivo WAN, ou seja, pode ser um dispositivo de rede local e de WAN ao mesmo tempo. 

Tanto em LAN como em WAN a função do roteador é rotear pacotes pacotes , quando um roteador usa os padrões e os protocolos das camadas físicas e de enlace que estão associados às WANs, ele opera como um dispositivo WAN. As principais funções na WAN de um roteador, portanto, não são de roteamento, mas de oferecer conexões entre vários padrões físicos e de enlace de dados de uma WAN. Ex:  um roteador pode ter uma interface ISDN, que utiliza encapsulamento PPP, e uma interface serial na terminação de uma linha T1, que usa encapsulamento Frame Relay. O roteador deve ser capaz de mover um fluxo  de bits de um tipo de serviço, como ISDN, para outro, como T1, e mudar o encapsulamento do enlace de dados de PPP para Frame Relay.  É por esse motivo que o roteador faz o papel de gateway da rede, que é possibilitar a interconexão de redes diferentes, encapsulando e desencapsulando seus protocolos.

![[Pasted image 20251117224623.png]]

## Protocolos da Camada Física WAN

Alguns protocolos da camada física WAN que os roteadores suportam:

* EIA/TIA-232 (RS 232);
* EIA/TIA-449 (RS 449);
* V.24; V.34; X.21; G.703 e EIA-530;
* ISDN;
* T1, T3, E1 e E3;
* xDSL (ADSL, SDSL, HDSL, etc.);
* SONET (OC-3, OC-2, OC-48, OC-192).

Exemplos de protocolos e padrões da camada de enlace da WAN

