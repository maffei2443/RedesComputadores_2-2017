+ 1. Diferenca entre router and switch?!
+ 2. O que sao link-layer switches?
NEXT HOP :: ficaa em ooooutro sistema autonomo!!


1. Duas funcoes principais :
    + Roteamento     : consiste em DETERMINAR a interface de saida adequada a cada pacote recebido nas interfaces de entrada do roteador.
    + Encaminhamento : processo de MOVER um pacote da interface de saida para
                        interface de saida adequada [despachar entra aqui??].

2. A camada de transporte oferece comunicacao entre *processos*, ao
passo que a de redes oferece transpore entre *dispositivosss finais*.
Além disso, aquela é distribuída ao longo dos diversos roteadores/switches
enquanto que essa roda "cada uma em um dispositivo".
A camada de redes oferece, na Internet, o __serviço de melhor esforço__.
### Serviços que ela pode prover
    + Garantia de entrega
    + Garantia de entrega com limite de tempo
    + Para fluxos de pacotes, pode também prover:
        + Entrega em ordem
        + *Jitter* maximo
        + Segurança 
        + Largura de banda mínima
3. 
4. Um circuito virtual é composto por:
    + Um caminho (origem - ... - destino)
    + Enlaces com VC numbers
    + Tabelas de encaminhamento (uma por roteador)
Sua configuracao se dah pela troca de __mensagens sinalizadoras__ entre
os roteadores da VCN.
5. Funcionam com cada roteador possuindo sua própria tabela de encaminhamento
, a qual é usada segundo a lógica do *longest prefix matching* e pode ser
alterada a qualquer instante. Também, sempre que um pacote de dados vai
ser enviado, é necessário que nele haja um campo com o enderço destino.
6.  + Vantagens Redes de Circuitos Virtuais
        + Garantia de uma *rota fixa*, impedindo assim a chegada fora de ordem.
        + Garantia da largura de banda informada pela rede após o estabelecimen
        to da conexao.
    + Desvantagens
        + Rede se torna muito complexa.
        + Permite um número de usuarios simultâneos muito inferior se
        comparada com uma rede de comutação pordatagramas "de mesmas 
        especificações". 
    + Vantagens Redes de Comutação por Datagrama
        + Flexibilidade de rotas; caso um nó da rede caia, ela pode
        prontamente enviar pacotes que passavam por esse ó por outra
        rota.
        + Melhor aproveitamento da largura de banda, pois não corre o ris-
        co de a rede possuir recursos não utilizados quando há quem precise deles
    + Desvantagens
        + Como permite muito mais usuarios simultâneos, pode ocorrer de
        o fluxo efetivo de dados na rede caia tanto a ponto de a mesma
        ficar inutilizável.
        + Não garante largura de banda, entrega em ordem ou tempo máximo
        até que se entregue um pacote.
7.
    1. Portas de entrada
    2. Fábrica de switches(conectam as interfaced ed entrada às de saída).
        Obs: é totalmente interna ao roteador.
    3. Portas de saída
    4. Processador de roteamento (respondavel por eecutar os algoritmos
    de roteamento e portanto preencher a tabela de encaminhamento)

8. Sua função é de servir como uma *terminação* para os enlces que chegam
ao roteador, ..?

9. É uma *tabela* que consiste ma qual cada entrada possui uma saída associada.
Além disso, têm ainda uma tabela em cada porta de entrada. [???]
+ Implementações:
    1. Comutação em *memória*
        + Implementação **muito usada**.
        + Controlada *diretamente* pela CPU, que trata as portas de E/S como fossem dispositivos tradicionais em SOs tradicionais.
        + Devido a existir apenas um processador, não é possível efetuar vários encaminnhamentos em simultâneo. (PROBLEMA!!!)
        + **ROTEADORES MODERNOS** o fazem, porém com umm processador em cada
        *line card* [??? O que é isso?]

    2. Comutação via *barramento*
        + Velocidade de transmissao do barramento é o limitante.
        + CPU de roteamento *não interfere*.
        + Transferência *direta* de uma porta de entrada para uma porta de saída.
        + *TODAS* as portas recebem o pacote; apenas mantem-o as portas cujo rótulo[qual rótulo?] emparelha.
        + **PROBLEMA**: por serem compartilhados os barramentos, é possível que um pacote tenha de esperar a porção do barramento que ele vai utilizar ser liberada.

    3. [???] Nao entendi :/
[DUVIDA: pgn 323, em AMARELO]

10. Enviar os pacotes recebidos nas portas de entrada ao destino seu destino   (informado pela tabela de encaminhamento). Cada saída leva a um único lugar.
[???]

11. Podem ocorrer dois tipos de enfileiramento : 
    1. Fila na Entrada : quando a velocidade com que a comutação é feita é inferior à soma da taxa de recepção das portas de entrada.
    2. Fila na Saída : quando a velocidade com que a comutação é feita é superior à soma da taxa de envio das portas de saída.

+ **Head of The Line (HOL)** blocking : ocorre quando o próximo pacote da fila não pode ser mandado para sua respectiva porta de saída e, por conta disso,
------------------------------------------------------
+ Principais Componentes da __CAMADA DE REDES__: 
    + Protocolos de roteamento
    + protocolo IP
    + protocolo ICMP
------------------------------------------------------

12. A fragmentação de datagramas ocorre nos *roteadores*. Seu objetivo é permitir que datagramas cujos tamanhos sejam maiores do que a **MTU** do enlace ao qual um datagrama será enviado sejam enviados de alguma forma.
ESSA FORMA é a chamada *fragmentação de datagramas*, a qual consistem em 'quebrar' o pacote recebido pelo roteador em artefatos chamados *fragmentos*, de sorte que esses fragmentos são finalmente encapsulados e enviados pelo enlace adequado. OBVIAMENTE, esse ovo datagrama deve poder sre enviado pelo enlace (ou seja, posuir um tamanho inferior ou igual à MTU).
Os fragmentos são remontados no datagrama IP apenas nos *sistemas finais*.

13. O endereço IP é formado por 32bits, porém é geralmennte representado como três números, *na base decimal*, separados por pontos.

14. É uma rede que interconecta um roteador e sistemas finais.
Cada sub-rede é endereçada por um número *variável* de bytes, sendo que esses bytes são representados na base 10, bem como o endereço IP, e esses números da base 10 são separados por pontos.
Para especificar *quantos são os bytes* que identificam uma subrede (a chamada **Máscara de Sub-rede**) da forma [Mascara].x, onde 'x' significa o tamanho, em bits, da máscara da subrede (o seu identificador).
[DÚVIDA !!! Pgn 341. Nao entendi a definicao. :/]

15. Sua função é permitir que dispositivos finais obtenham endereços IP de forma *automática*.
Obs : **DHCP** é arquitetura Cliente-Servidor e usa TCP.
Ele é utilizado de duas maneiras em geral:
    + Provendo sempre o mesmo endereço IP para um dado dispositivo sempre que este conecta-se à rede; ou
    + Provendo endereços *temporários* para os disositivos que entram na rede, e redistribuindo-os conforme eles vão dela saindo.
    + É um protocolo **Plug-and-Play**

16. [???]

17. Eh uma estrategia para aumentar a quantidade de dispositivos que um endereço IP eh capaz 
de endereçar. Usado para endereçar dispositivos em sub-redes.

18. Principal problema é o estabelecimento de conexões de um dispositivo EXTERNO à rede com um dispositivo INTERNO a ela E que não se conenctou ainda a esse dispositivo externo.

19. 

20. Ele 

22. 
+ Traducao entre IPv4 E ipV6
+ Pilha dupla (dispositivos vem configurados com ambos os IPs)
+ Tunelamento 

24)  Sao algoritmos que  buscam pela rota menos cutosa possivel.
Sao dinamicos so que usam metricas(unidade de medida)/medidas que mudam com o 
tmepo dinamicas, e estaticos os que usam metricas 
estaticas.

25)

26) Possiveis oscilacoes nas metricas dinamicas de custo.

27) Cada noh possui a informacao de distancias para seus vizinhos em um vetor;
entao, ele passa esse vetor de distancias para seus vizinhos (de tempos em tem-
pos e/ou on-demand).

28) Sao limitados a redes de ateh 16 nos (poucos nohs).

+ Mudancas de custo para pior DEMORAM a serem propagadas
+ Covergencia pode ser demorada.
+ 

29)

30)

34) É quando uma fonte lança mensagens para *todos* os des-
tinos possíveis de uma sub-rede.
Técnicas para melhorá-lo : 
    + inundação (não usada)
    + inundação controlada (pacote é encaminhado por um roteador
    ss ele _ainda nao encaminhou_ esse pacote).
        + **R**everse **P**ath **F**orwarding::
        encaminhar o pacote sse ele chegou *pelo caminho mais curto* da origem e o roteador em questão.
    + Spanning tree: não ocorre duplicação de pacotes; o rotea-
    dor encaminha apenas para as arestas que pertencem à MST
    a menos da aresta pelaqual chegou o pacote.

35) É quando uma fonte lança mensagens para *os roteadores da rede*
**interessados** no conteúdo da fonte. Muito usado para transmissões
ao vivo.
Objetivo : encontrar a árvore que conecta os roteadores que possuem
*multicast local*.
Solução : árvore geradora.. compartilhadas ou não :p.

Técnicas para melhorá-lo :
    + Árvores baseadas em origem : uma por origem.
    Como?!?!
        + Shortest Path Tree
        + **RPF**
    + Árvore compartilhada pelo grupo:
        + MST (Steiner)
        + Árvore CENTRALIZADA

36) O **DVMRP**  multicast com vetor de distâncias,
árvore baseada na fonte (NÃO É COMPARTILHADA)
    + (inundamento **+** poda) : **RPF**. Depois de mon-
    tada a árvore, os que não querem participar da árvore
    informam isso à fonte, e poda a aresta da árvore.
    Além disso, periodicamente checa se os componentes
    da árvore ainda está vivos, e corta-os em caso de
    mortos.
    + **tunelamento** : solução para fazer multicast
    entre roteadores que tem, entre eles,, roteadores que
    *não rodam protocolos multicast*. Para estes roteado-
    res, é simplesmente mais um pacote encaminhado.

37) PIM :: possui **dois** modos:
    1. Recursos sobrando (**esparso**):
        + Participantes que solicitam a entrada na rede 
            multicast.
        + gasto banda *conservador*

    2. Recursos faltando (**denso**):
        + Inundação controlada *+* poda
        + Confia nos procolos *unicast* 

