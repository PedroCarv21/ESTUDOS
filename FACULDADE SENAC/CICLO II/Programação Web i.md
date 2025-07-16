
# RabbitMQ

É um intermediador de mensagem que permite que diferentes aplicações e serviços se comuniquem entre si de forma assíncrona.

**OBS.: Comunicação assíncrona é um método de troca de informações onde os participantes não precisam estar conectados ao mesmo tempo. Ou seja, o emissor envia a mensagem e o receptor pode acessá-la e respondê-la quando for mais conveniente para si, sem a necessidade de interação imediata. **

O RabbitMQ trabalha com dois tipos de sistema: 
- Publicador (publish): envia a mensagem.
- Consumidor (subscribe): recebe a mensagem.

## Alguns conceitos

- **Fila (queue)**: local onde as mensagens são armazenadas. É possível definir se as mensagens serão armazenadas em disco ou em memória.
- **Mensagem (playload)**: ela pode aparecer em vários formatos (PDF ou texto) e são transmitidas em bytes.
- **Troca (exchange)**: é responsável por definir em qual fila a mensagem será armazenada.
