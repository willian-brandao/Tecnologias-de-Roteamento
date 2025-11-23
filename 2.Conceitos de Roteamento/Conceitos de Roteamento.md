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







