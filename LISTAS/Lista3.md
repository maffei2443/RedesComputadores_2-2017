+ 1. Diferenca entre router and switch?!
+ 2. O que sao link-layer switches?
NEXT HOP :: ficaa em ooooutro sistema autonomo!!


1. Duas funcoes principais :
    + Roteamento     : consiste em DETERMINAR a interface de saida adequada a cada pacote recebido nas interfaces de entrada do roteador.

    + Encaminhamento : processo de MOVER um pacote da interface de saida para
    interface de saida adequada [despachar entra aqui??].
    Como?? Olhar o cabeçalho do datagrama. Decidir via **longest prefix matching** com as entradas da tabela de encaminhamento.

2. A camada de transporte oferece comunicacao entre *processos*, ao
passo que a de redes oferece comunicacao entre *dispositivos finais*.
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
    + Não orientadoa a conexão : camada de redes recebe o *segmento*, encapsula-o e MANDA para o próximo roteador de acordo com a tabela de encaminhamento.

    + Orientada a conexão : implementada por meio de circuitos virtuais.
    Antes de que comece a trafegar dados por um circuito

4. Um circuito virtual é composto por:
    + Um caminho (origem - ... - destino)
    + Enlaces com VC numbers
    + Tabelas de encaminhamento (uma por roteador)
Sua configuracao se dah pela troca de __mensagens sinalizadoras__ entre
os roteadores da VCN.

5. Funcionam com cada roteador possuindo sua própria tabela de encaminhamento
, a qual é usada segundo a lógica do *longest prefix matching* e pode ser
alterada a qualquer instante. Também, sempre que um pacote de dados vai
ser enviado, é necessário que nele haja um campo com o endereço destino.

6.  + Vantagens Redes de **Circuitos Virtuais**
        + Garantia de uma *rota fixa*, impedindo assim a chegada fora de ordem.
        + Garantia da largura de banda informada pela rede após o estabelecimen
        to da conexao.
    + Desvantagens
        + Rede se torna muito complexa.
        + Permite um número de usuarios simultâneos muito inferior se
        comparada com uma rede de comutação pordatagramas "de mesmas 
        especificações". 
    + Vantagens Redes de **Comutação por Datagrama**
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
    2. Fábrica de switches/ Matriz de comutação
        (conectam as interfaces de entrada às de saída).
        Obs: é totalmente interna ao roteador.
    3. Portas de saída
    4. Processador de roteamento (respondavel por eecutar os algoritmos
    de roteamento e portanto preencher a tabela de encaminhamento)

8. É composta por uma interface com a camada física, o *terminador*. Ao final do módulo, existem BITS. Eses bits vao para a camada de enlace, e dps para a camada de redes. Cai enntão no *buffer de entrada*.

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

    3.  Ouvir áudio novamente.
[DUVIDA: pgn 323, em AMARELO]

10. Enviar os pacotes recebidos nas portas de entrada ao destino seu destino   (informado pela tabela de encaminhamento). Cada saída leva a um único lugar.


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

16. [REVER NO LIVRO]
    1. As informacoes de alcançabilidade sao **ENDEREÇOS DE SUBREDES**.
    2. Pode endereçar varios endereços de rede

17. Eh uma estrategia para aumentar a quantidade de dispositivos que um endereço IP eh capaz de endereçar. Usado para endereçar dispositivos em sub-redes.

18. Principal problema é o estabelecimento de conexões de um dispositivo EXTERNO à rede com um dispositivo INTERNO a ela E que não se conenctou ainda a esse dispositivo externo.
Soluções: 
    1. Transversal NAT
        + Basicamente, dado um host A *não atrás de um NAT*, o mesmo conecta-se a um servidor *que mantém uma conexão* com um outro host B, o qual está atrás de um NAT, Então, por intermédio desse servidor, A solicita a B que etabeleça umm conexão TCP com ele. Caso B aceite, então o servidor solicita a conexão com A e o servidor não é mais necessário para essa conexão.
    2. UPnP (**Universal Plug and Play**)
        + É um protocolo cuja função é permitir o NAT tranversal.
        + Interface : permite que um host *atrás de um NAT* solicite um mapping de seu par (IP privado, porta) para um (IP publico, porta), provido pelo roteador com NAT.
        + Funcionamento : 

19. Atraves da estrategia de *agregação* de endereços. Em geral, s tabbelas de roteamento, por conta disso, são compostas praticamente de apenas subredes.

20. - Reportar erros
    - Transmitir informação sobre rotas/alcançabilidade e etc. 
21. Obj : aumentar o espaço de endereçamento.
    + Cabeçalho FIXO de 40 bytes.( ver no livro )
    + NO MORE CHECKSUM
    + Sem fragmentação (correção na ORIGEM)
    + Versão

22. 
    + Traducao entre IPv4 E IPv6

    + Pilha dupla (dispositivos vem configurados com ambos os IPs). O endereço de um host para o qual se quer mandar é consultado via __DNS__, o qual responde com todos os IPs que a máquina em questão possui.

    + Tunelamento : o roteador fonte , quando vai mandar o datagrama IP para um roteador que não suporta IPv6, antes de mandar encapsula-o num datagraa IPv4. Daí, o roteador que recebe o datagrama encapsulado age como se esse datagrama fosse um IPv4 e o passa adiante. Chegando no destino, o qual roda IPv6, o mesmo detecta que recebeu um datagrama IPv4, e desencapsula para ver o que está dentro dele.

23. Obviedade pura.

24.  Sao algoritmos que  buscam pela rota menos cutos possivel.
Sao dinamicos so que usam metricas(unidade de medida)/medidas que mudam com o 
tmepo dinamicas, e estaticos os que usam metricas estaticas.

25. 
    + Algoritmo com visão GLOBAL
    + 

26. Possiveis oscilacoes nas metricas de custo.(Overhead de controle para atualizar os menores caminhos; famooosa *inundação*).

27. Cada noh possui a informacao de distancias para seus vizinhos em um vetor;
entao, ele passa esse vetor de distancias para seus vizinhos (de tempos em tem-
pos e/ou on-demand).

28. Sao limitados a redes de ateh 15 nos (poucos nohs).
VER NO LIVRO.

+ Mudancas de custo para pior DEMORAM a serem propagadas
+ Covergencia pode ser demorada.
+ 

29.

30. É o rotaeamento *entre sistemas autônomos*.

31. OSPF : ver no livro.

32. BGP : 

33. 
    + eBGP : 
    
    + iBGP : 

34. É quando uma fonte lança mensagens para *todos* os des-
tinos possíveis de uma sub-rede.
Técnicas para melhorá-lo : 
    + inundação (não usada)
    + inundação controlada (pacote é encaminhado por um roteador
    ss ele _ainda nao encaminhou_ esse pacote).
        + **R**everse **P**ath **F**orwarding::
        encaminhar o pacote sse ele chegou *pelo caminho mais curto* da origem e o roteador em questão.
    + Spanning tree: não ocorre duplicação de pacotes; o rotea-
    dor encaminha apenas para as arestas que pertencem à MST
    a menos da aresta pela qual chegou o pacote..

35. É quando uma fonte lança mensagens para *os roteadores da rede*
**interessados** no conteúdo da fonte. Muito usado para transmissões
ao vivo.
Objetivo : encontrar a árvore que conecta os roteadores que possuem
*multicast local*.
Solução : árvores geradoras compartilhadas ou não :p.

Técnicas para melhorá-lo :
    + Árvores baseadas em origem : uma por origem.
    Como?!?!
        + Shortest Path Tree
        + **RPF**
    + Árvore compartilhada pelo grupo:
        + MST (Steiner)
        + Árvore CENTRALIZADA

36. O **DVMRP** (*Distanc Vector Multicasting Routing Protocol*) é um algoritmo de roteamento  multicast com vetor de distâncias e árvore baseada na fonte (NÃO É COMPARTILHADA)
    + (inundamento **+** poda) : **RPF**. Depois de mon-
    tada a árvore, os que não querem participar da árvore
    informam isso à fonte, e poda a aresta da árvore.
    Além disso, periodicamente checa se os componentes
    da árvore ainda está vivos, e corta-os em caso de
    mortos.
    + >>> ÁRVORE BASEADA NA FONTE <<<


    + **tunelamento** : solução para fazer multicast
    entre roteadores que tem, entre eles,, roteadores que
    *não rodam protocolos multicast*. Para estes roteado-
    res, é simplesmente mais um pacote encaminhado.

37) PIM (Protocol Independent Multicast routing protocol) :: possui **dois** modos:
    1. Recursos sobrando (**esparso**):
        + Participantes que solicitam a entrada na rede 
            multicast.
        + gasto banda *conservador*

    2. Recursos faltando (**denso**):
        + Inundação controlada *+* poda
        + Confia nos procolos *unicast* 

