# NATS Streaming

The NATS Streaming connector provides a source and a sink to receive and publish messages from/to NATS subjects.


Please visit the [official documentation](https://docs.nats.io/) for details.

@@project-info{ projectId="nats" }

## Artifacts

@@dependency [sbt,Maven,Gradle] {
  group=com.lightbend.akka
  artifact=akka-stream-alpakka-nats_$scala.binary.version$
  version=$project.version$
  symbol2=AkkaVersion
  value2=$akka.version$
  group2=com.typesafe.akka
  artifact2=akka-stream_$scala.binary.version$
  version2=AkkaVersion
}

The table below shows direct dependencies of this module and the second tab shows all libraries it depends on transitively.

@@dependencies { projectId="nats" }

## NATS Connection

Create a connection with `NatsStreamingConnectionBuilder`.
Either a configuration object `NatsStreamingConnectionSettings` or a `com.typesafe.config` object can be used for that purpose. 

Once created a connection can be shared for multiple sources and sinks. It has to be closed manually.

## NATS Source

The connector contains two types of NATS sources a `NatsStreamingSimpleSource` and a `NatsStreamingSourceWithAck`
The simple source will acknowledge incoming messages right away and will send a type of message downstream, which will
not provide a method to acknowledge the messages in a manual way. Both incoming messages contain a payload of type
`Array[Byte]` the payload can be deserialized via the `.map()` method.

Both factories require a NATS Connection to be present.

### NatsStreamingSourceWithAck

Create a `Source[IncomingMessage[Array[Byte]]]` with the two factory methods provided in @scaladoc[NatsStreamingSourceWithAck](akka.stream.alpakka.nats.scaladsl.NatsStreamingSourceWithAck$)
and @javadoc[NatsStreamingSourceWithAck](akka.stream.alpakka.nats.scaladoc.NatsStreamingSourceWithAck).

Both provided factories contain two methods to create a simple source with a configuration object or a `com.typesafe.config`

### Configuration


### NatsStreamingSimpleSource



