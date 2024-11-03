# RabbitMQ
- Modelo de Mensagem: Utiliza um modelo baseado em push, onde as mensagens são "empurradas" para os consumidores. O RabbitMQ tenta entregar as mensagens assim que elas são produzidas, assumindo que os consumidores estão prontos para recebê-las.
- Prioridade de Mensagem: RabbitMQ permite a definição de prioridade nas filas. Isso significa que mensagens com maior prioridade podem ser consumidas antes das outras, independentemente da ordem em que foram enviadas.
- Entrega e Confirmação: Suporta várias garantias de entrega (como at-least-once e exactly-once) e os consumidores podem enviar acknowledgments (confirmações) de que receberam as mensagens corretamente.
- Casos de Uso: Ótimo para comunicação de curta duração e sistemas que requerem alta confiabilidade, como processamento de transações bancárias ou sistemas de e-commerce.
- Suporte para Protocolos: Utiliza o protocolo AMQP (Advanced Message Queuing Protocol), o que permite grande interoperabilidade com diferentes plataformas.
- Persistência: Suporta filas persistentes, o que garante que as mensagens não sejam perdidas em caso de falha.
# Kafka
- Modelo de Mensagem: Baseado em pull, onde os consumidores escolhem quando recuperar as mensagens. Isso permite que os consumidores façam o processamento em seu próprio ritmo, ao contrário do modelo push.
- Tolerância a Falhas e Escalabilidade: Kafka é altamente escalável e distribuído, com foco em particionamento de dados e replicação, garantindo alta disponibilidade e resiliência.
- Modelo de Retenção: As mensagens são armazenadas no log, o que permite que os consumidores possam reprocessar as mensagens antigas (o Kafka não apaga automaticamente as mensagens após o consumo). A retenção pode ser configurada para tempo, espaço ou outras políticas.
- Caso de Uso: Kafka é ideal para o processamento de fluxos de eventos (event streams) em tempo real, e grandes volumes de dados. Ele é amplamente usado em sistemas de análise de dados, pipelines de ETL (Extract, Transform, Load) e microserviços que precisam compartilhar estados de forma assíncrona.
- Performance: Kafka oferece alta taxa de transferência, conseguindo lidar com milhões de mensagens por segundo em ambientes distribuídos.
- Persistência: As mensagens são mantidas de forma durável no log, sendo persistidas no disco com retenção configurável.
# BullMQ
- Baseado em Node.js: Diferente de RabbitMQ e Kafka, BullMQ é uma solução de fila de mensagens específica para o Node.js, escrita em JavaScript/TypeScript e funcionando sobre o Redis.
- Modelo de Mensagem: Suporta tanto FIFO (First In, First Out) quanto LIFO (Last In, First Out), o que permite flexibilidade no processamento de mensagens em cenários onde a ordem de consumo das mensagens pode variar.
- Execução de Jobs e Retries: BullMQ é projetado principalmente para fila de jobs, com suporte embutido para processamento de falhas, retries automáticos, atrasos de mensagens e programação de tarefas.
- Casos de Uso: Usado em aplicações que rodam no ecossistema Node.js, onde é necessário orquestrar tarefas pesadas (jobs) ou que precisam ser realizadas de forma assíncrona, como envio de e-mails, processamento de imagens, ou outras tarefas demoradas.
- Persistência e Storage: BullMQ utiliza o Redis como mecanismo de armazenamento, o que traz alta performance, mas também uma limitação em termos de volume de dados comparado com Kafka e RabbitMQ. - Redis, sendo um banco de dados em memória, é ótimo para mensagens de curta vida ou de alta frequência.
- Prioridades e Retries: BullMQ permite definir prioridades para as mensagens e gerenciar o número de tentativas de reprocessamento em caso de falha.
- Suporte a Concurrency: Permite processamento concorrente de jobs, o que aumenta o throughput das aplicações.
