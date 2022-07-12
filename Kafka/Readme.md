# Comandos con Kafka

Primero es necesario desplegar la imagen

```
docker exec -it kafka /bin/sh
```

Para acceder al Kafka Shell se emplea el siguiente comando:

```
docker exec -it kafka /bin/sh
```

## Comandos para gestión de tópicos

Primero se debe montar la siguiente ruta:

```
cd /opt/kafka/bin
```

### Crear un tópico
```
kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 3 --topic first_kafka_topic
```

### Listar tópicos creados
```
kafka-topics.sh --zookeeper zookeeper:2181 --list
```

### Obtener descripción de un tópico
```
kafka-topics.sh --zookeeper zookeeper:2181 --topic first_kafka_topic --describe
```

### Eliminar un tópico
```
kafka-topics.sh --zookeeper zookeeper:2181 --topic first_kafka_topic --delete
```

## Comandos para enviar mensajes (Producer) 

Nota: Si el tópico no existe, el primer mensaje tendrá error, y luego el tópico será creado automáticamente

```
kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic first_kafka_topic --producer-property acks=all
```

La consola abre una sesión en el terminal para recibir los mensajes, para terminar cancele la sesión con Ctrl+C

## Comandos para leer mensajes (Consumer)

```
kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic first_kafka_topic 
```




