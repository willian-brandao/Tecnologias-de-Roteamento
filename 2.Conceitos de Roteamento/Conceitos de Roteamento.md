# Conceitos de Roteamento

O processo do roteamento é realizado por roteador com o intuito de encaminhar pacotes para uma rede de destino, tomando decisões de encaminhamento baseando-se nos endereços IPs de destino de um determinado pacote.
Todos os dispositivos e rede ao longo de um caminho utilizam o endereço IP de destino para orientar o pacote na direção correta e sem erros até o seu destino. 
Para que os entendedores possam tomar as decisões corretas, eles precisam aprender através de um algoritmo de roteamento e/ou através da configuração de um administrador de rede, como podem alcançar essas redes remotamente. 
Caso estiverem utilizando um processo de roteamento dinâmico, essa informação é obtida de outros roteadores da topologia. No entanto, se estiverem utilizando o roteamento estático, essas informações sobre as redes remotas configuradas manualmente por um administrador de rede.

No roteamento estático, as rotas precisam ser configuradas manualmente por um administrador da rede, nesse caso qualquer alteração na toplogia da rede requer que este operador adicione e exclua rotas estáticas manualmente a fim de refletir essass alterações, ou seja, uma eventual mudança na rede, também pode acarretar um retrabalho e um processo de configuração cansativo e demorado. Em uma rede grande, essa manutenção das tabelas na administração da rede. Já em redes pequenas e com poucas alterações, as rotas estáticas acabam exigindo muito pouca manutenção e por esse motivo é uma técnica mais utilizada, pois não utiliza tantos recursos de máquina como CPU, consumo de banda dos roteadores. 

## Roteamento de Pacotes IP

O roteamento na internet funciona com um GPS: ele cria mapas e escolhe os melhores caminhos para que pacotes IP cheguem ao destino. A internet é formada por várias redes chamadas Sistemas Autonômos (AS), interligadas de diversas maneiras, o que garante resiliência, mas exige decisões constantes sobre por onde encaminhar dados. 

Os roteadores fazem esse trabalho aprendendo caminhos de três formas: rotas estáticas configuradas manualmente, redes diretamente conectadas e protocolos de roteamento dinâmico trocados entre roteadores vizinhos. Todas as informações ficam na tabela de rotas (RIB), que armazena todos os caminhos conhecidos.

Para agilizar o processo, os roteadores usam também a tabela de encaminhamento (FIB), onde fica registrado apenas a melhor rota para cada destino, incluindo a interface usada para enviar pacote. A escolha das melhores rotas depende de fatores como topologia da rede, políticas de roteamento e métricas como distância, atraso e banda. 

Os roteadores sempre escolhem a rota mais específica (maior prefixo) quando um destino se encaixa em mais de uma rede. Como o GPS recalcula caminhos, os roteadores também adaptam suas escolhas conforme mudanças na rede, garantindo eficiência no tráfego dos pacotes IP.

### Tabelas Importantes

* RIB - Routing Information Base
   * Todas as rotas conhecidas.
   * Armazena prefixos e próximos saltos.
* FIB - Forwarding prefixos e próximo salto
  * Apenas a melhor rota para cada destino.
  * Inclui interface de saída.
  * Usada no encaminhamento real.

### Critérios de Melhor Escolha
* Topologia.
* Políticas de roteamento.
* Métricas: distância, atraso, banda, custo, filtros.

## Protocolos de Roteamento

### Interno

#### IGP 
Utilizado dentro de um único Sistema Autônomo (AS). Eles cuidam do roteamento interno, garantindo que as redes internas troquem rotas de forma rápida e eficiente. 

* ISIS (intermediate system to intermediate system)
  * Usa o algoritmo Dijkstra (SPF).
  * Boa Escalagem.
  * Muito comum em redes de operadoras e ISPs de grande porte.
  * Menos dependente de IP para funcionar, pois atua diretamente na camada de enlace. 

* OSPF (Open Shortest Path First)
  * Usa o algoritmo Dijkstra (SPF).
  * Convergência Rápida.
  * Suporta áreas, facilitando redes grandes.
  * Muito usado em ambientes corporativos e provedores.

*Obs: Esses protocolos usam métricas internas para decidir o melhor caminho, como custo, banda, atraso e distância.*

### Externo
#### EGP 
Usados entre Sistemas Autônomos diferentes, ou seja, fazem o roteamento entre organizações e provedores. 

* BGP (Border Gateway Protocol)
  * Considerado o coração da internet.
  * Define por onde os AS vão trocar rotas entre si.
  * Não usa métricas como banda ou atraso; sua decisão envolve políticas, preferências administrativas e atributos como AS-PATH, MED, LOCAL PREF, etc.
  * Altamente escalável e robusto.
  * Indispensável para trânsito, peering, e roteamento global.

O BGP não escolhe rotas baseado em métricas tradicionais como custo ou velocidade, como fazem OSPF e IS-IS. Em vez disso, ele segue uma sequência de regras de decisão baseada em políticas de roteamento e atributos de rotas.

Esses atributos dizem ao roteador qual rota é mais desejável, seguindo critérios definifos pelo administrador da rede. 

Os atributos são:

* LOCAL PREF (Local Preference)
  * Diz ao roteador qual rota deve ser preferida dentro do seu próprio AS.
  * Quanto maior o valor, maior preferência.
  * É o critério mais importante após as rotas originadas localmente.

* AS-PATH
  * Lista de quais Sistemas Autônomos a rota atravessou.
  * Quanto mais longo o caminho (mais AS na lista), menos desejável é a rota.
  * Ajuda a evitar loops e escolher rotas mais curtas.

* MED ( Multi-Exit Discriminator)
  * Usado para indicar a rotas externas qual caminho deve ser preferido para entrar no seu AS.
  * Quanto menor o valor, mais preferível.

* ORIGIN, NEXT-HOP, WEIGHT, entre outros
  * São atribuitos que ajudam a refinar, ajustar e personalizar decisões específicas.

O BGP foi projetado para escalar ao tamanho da internet, literalmente. Hoje existem centernas de milhares de rotas na tabela global, e o BGP consegue manter e distribuir essas informações entre milhares de operadoras, provedores e grandes organizações ao redor do mundo. 

É escalável porque:

* trabalha de forma incremental ( não recalcula tudo como OSPF/IS-IS).
* matém conexões estáveis usando TCP.
* permite políticas complexas sem sobrecarregar o roteamento.
* suporta agrupamento por route reflectors e confederations, reduzindo carga de redes gigantes.

É robusto porque:

* mantém rotas alternativas se houver falha.
* evita loops de roteamento de forma eficiente.
* se recupera bem de quedas sem precisar refazer toda a topologia.
* é resistente a mudanças rápidas ou instabilidades internas. 

O BGP é o único protocolo capaz de controlar como os Sistemas Autônomos do mundo inteiro trocam informações de roteamento, por isso ele é essencial em três operações-chave:

* Trânsito (Transit) - Quando uma operadora leva tráfego seu e de outros AS para a internet. Ex: pequenos ISPs usam operadoras maiores para alcançar a Internet global.

**Sem BGP -> impossível anunciar suas redes e receber rotas globais.**

* Peering - Conexão direta entre dois AS para trocar tráfego sem intermediários. Ex: Netflix faz peering com operadoras para entregar vídeos mais rápido.

**Sem BGP -> não há controle de qual tráfego passa por esse acordo.**
* Roteamento global
O mapa da internet é construído pelo BGP.
Cada anúncio representa um pedaço da rede mundial, sem ele não existiram:
 * tabelas globais de rotas
 * CDNs
 * trânsito internacional
 * operadoras interconectadas
 * a própria Internet como conhecemos

## Termos comuns ao BGP

AS (Autonomous System) - Conjunto de redes sob uma mesma administração. Cada AS possui um número (ASN).

* ASN (Autonomous System Number) - Identificador numérico do AS. Pode ser público ou privado.

* BGP Peers / Vizinhos - Roteadores que estabelecem uma sessão BGP entre si para trocar rotas.

* EBGP - Sessão BGP entre AS diferentes.

* IBGP - Sessão BGP dentro do mesmo AS.

* NEXT-HOP - Endereço IP que indica o próximo roteador no caminho para o destino.

* AS-PATH - Lista de AS pelos quais a rota passou. Ajuda a evitar loops e escolher rotas mais curtas.

* LOCAL PREF (Local Preference) - Atributo interno que define preferência de rota dentro do AS. Valor maior = rota preferida.

* MED (Multi-Exit Discriminator) - Indica para AS vizinhos qual entrada preferir. Valor menor = mais preferível.

* WEIGHT - Atributo usado apenas localmente no roteador. Valor maior = rota preferida.

* ORIGIN - Indica como a rota foi originada: IGP, EGP ou INCOMPLETE.

* Route Reflector (RR) - Recurso para evitar que todos os roteadores IBGP tenham sessões entre si.

* Communities- Tags usadas para aplicar políticas de roteamento (ex.: bloquear, preferir, anunciar, não anunciar).

* Full Routing Table - Tabela contendo todas as rotas públicas da Internet (mais de 900 mil prefixos).

* Peering - Troca direta de rotas entre dois AS sem intermediários.

* Transit - Quando um AS paga outro para alcançar a Internet.

*Obs: O termo EGP também se refere a um protocolo antigo, chamado Exterior Gateway Protocol, que antecedeu o BGP, mas hoje EGP é usado quase sempre como categoria e não como o protocolo histórico.*




