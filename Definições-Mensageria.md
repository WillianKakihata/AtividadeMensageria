# Definição
Mensageria é o conceito que possibilita a comunicação entre sistemas distribuídos por meio da troca de mensagens (ou eventos), com essas mensagens sendo intermediadas por um Message Broker (servidor ou módulo de mensageria). Esse mecanismo permite que os sistemas interajam de forma assíncrona, ou seja, sem a necessidade de aguardarem uma resposta imediata.

# Definição simplificada:
Diferente do modelo síncrono usado em requisições HTTP, onde a resposta é aguardada para continuar o processamento, a mensageria permite que a comunicação entre sistemas ocorra de maneira assíncrona. Isso significa que o sistema emissor envia uma mensagem e pode continuar suas operações sem precisar esperar pela resposta do receptor.

# Exemplo:
Considere dois sistemas, o Sistema A e o Sistema B. O Sistema A deseja enviar um e-mail. Em vez de realizar o envio diretamente e esperar que o Sistema B complete a tarefa, o Sistema A cria uma mensagem com a solicitação ("enviar e-mail com o conteúdo X") e a entrega para o Message Broker.

O Message Broker se encarrega de passar essa mensagem para o Sistema B, que, por sua vez, processará o envio do e-mail no momento adequado. Caso ocorra um problema no envio, a mensagem pode ser reenviada ou tratada posteriormente, sem impactar o funcionamento do Sistema A, que já seguiu seu fluxo de trabalho normalmente após entregar a mensagem.

# Vantagens:
- Assincronia: O sistema que envia a mensagem não precisa parar para aguardar o processamento da tarefa.
- Desacoplamento: Sistemas emissores e receptores podem funcionar independentemente, sem precisar de conexão direta ou sincronização.
- Escalabilidade: O uso de mensageria facilita a distribuição de tarefas entre diferentes sistemas, permitindo que elas sejam executadas em paralelo ou em momentos distintos, conforme a disponibilidade do sistema receptor.

# Caracteristicas:
1. Filas
- O que são: Filas são estruturas de dados que armazenam mensagens de forma ordenada, geralmente no modelo FIFO (First In, First Out), ou seja, a primeira mensagem a entrar é a primeira a ser processada.
- Função: Elas permitem que os produtores enviem mensagens sem a necessidade de os consumidores estarem prontos imediatamente para processá-las. Isso ajuda a garantir a continuidade do sistema mesmo quando há picos de carga ou problemas temporários com os consumidores.

2. Produtores
- O que são: São os componentes ou serviços que criam mensagens e as enviam para a fila.
- Função: Eles são responsáveis por gerar dados ou eventos, encapsulando-os em mensagens que posteriormente serão consumidas por outros serviços (consumidores).
Detalhe Importante: Os produtores não têm controle sobre quando suas mensagens serão processadas. Eles apenas "empurram" as mensagens para a fila e seguem seu trabalho.

3. Consumidores
- O que são: São os componentes ou serviços que recuperam as mensagens da fila e as processam.
- Função: Eles são responsáveis por realizar a lógica de negócio ou o processamento das mensagens. Um consumidor pode ser um serviço que, por exemplo, envia e-mails, processa dados, ou atualiza um banco de dados, com base nas informações contidas na mensagem.


4. Tópicos
- O que são: Tópicos são categorias ou canais dentro de uma fila que permitem a classificação e o roteamento das mensagens. Eles são usados para definir o "assunto" ou o tipo da mensagem, facilitando o direcionamento para os consumidores certos.
- Diferença para Filas: Ao contrário das filas, onde cada mensagem é processada por um consumidor, em sistemas baseados em tópicos (como o Kafka ou o Pub/Sub), várias aplicações podem "assinar" o mesmo tópico e processar a mesma mensagem simultaneamente.

5. Partições
- O que são: Em sistemas distribuídos, como o Kafka, os tópicos são subdivididos em partições. Cada partição é uma coleção de mensagens de um mesmo tópico.
- Função: As partições permitem escalabilidade horizontal, dividindo o trabalho entre diferentes servidores (ou brokers). Cada partição pode ser armazenada e processada de forma independente.
- Vantagem: Isso aumenta a capacidade de paralelismo no consumo e armazenamento de mensagens, garantindo alta disponibilidade e redundância. Quando uma partição falha, outra pode assumir seu lugar, ou suas mensagens podem ser reprocessadas a partir do log da partição.

6. Brokers
- O que são: Atuam como intermediário, entre produtores e consumidores, ele basicamente gerencia a fila se o consumidor recebeu a mensagem do produtor.
