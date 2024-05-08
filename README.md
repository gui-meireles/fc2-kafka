# Funcionamento do Kafka

## Primeiros passos

- Subir o docker no terminal: ```docker-compose up -d```
- Após baixar as imagens do kafka, acesse o bash do kafka: ```docker exec -it fc2-kafka-kafka-1 bash```

### Tópicos (dentro do bash):
**Obs:** Para limpar a tela do bash: `CTRL + L`

- **Criar tópico:** ```kafka-topics --create --topic=teste --bootstrap-server=localhost:9092 --partitions=3```
> `--create` = Criar o tópico
> 
> `--topic` = Nome do tópico
> 
> `--bootstrap-server` = Lugar que será criado o tópico (**Obrigatório**)
> 
> `--partitions` = Quantidade de partições do tópico

<br>

- **Listar todos os tópicos:** ```kafka-topics --list --bootstrap-server=localhost:9092```
> `--list` = Listar os tópicos
> 
> `--bootstrap-server` = Lugar onde foi instanciado o tópico (**Obrigatório**)

<br>

- **Ver a descrição do nosso tópico específico:** `kafka-topics --describe --bootstrap-server=localhost:9092 --topic=teste`
> `--describe` = Ler o tópico
>
> `--bootstrap-server` = Lugar onde foi instanciado o tópico (**Obrigatório**)
>
> `--topic` = Nome do tópico

---

### Consumer e Producer (dentro do bash):

- **Acessa o consumer:** `kafka-console-consumer --bootstrap-server=localhost:9092 --topic=teste --from-beginning --group=x`
> `--bootstrap-server` = Lugar onde foi instanciado o tópico (**Obrigatório**)
>
> `--topic` = Nome do tópico
> 
> `--from-beginning` = Lê as mensagens desde o início (**Não obrigatório**)
>
> `--group` = Adiciona o consumer em um grupo (**Não obrigatório**)

<br>

- **Por dentro de um consumer group:** `kafka-consumer-groups --bootstrap-server=localhost:9092 --group=x --describe`
> `--bootstrap-server` = Lugar onde foi instanciado o tópico (**Obrigatório**)
>
> `--group` = Adiciona o consumer em um grupo (**Obrigatório**)
> 
> `--describe` = Descreve o grupo/tópicos/partições

<br>

- **Acessa o producer:** `kafka-console-producer --bootstrap-server=localhost:9092 --topic=teste`
> `--bootstrap-server` = Lugar onde foi instanciado o tópico (**Obrigatório**)
>
> `--topic` = Nome do tópico

---

### Utilizando o Confluent control center (Interface do kafka)

- Clique [aqui](http://localhost:9021/), para abrir o link em seu navegador.

![confluent_part1](https://github.com/gui-meireles/fc2-kafka/assets/88151632/2481ff12-8e4b-483c-9bdf-af36afeae330)

<br>

![confluent_part2](https://github.com/gui-meireles/fc2-kafka/assets/88151632/996cbfdc-bd07-496b-95ac-c2ee2ac43a68)

<br>

- Abaixo você terá todos os registros da partição 0, com os headers, timestamp, key, value

![confluent_part3](https://github.com/gui-meireles/fc2-kafka/assets/88151632/1b0560e2-dbde-4aa2-814a-a8a6137ae264)
