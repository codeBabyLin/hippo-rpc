# hippo-rpc

Hippo Transport Library enhances spark-commons with easy stream management & handling


                    ,.I ....
                  ... ZO.. .. M  .
                  ...=.       .,,.
                 .,D           ..?...O.
        ..=MD~,.. .,           .O  . O
     ..,            +I.        . .,N,  ,$N,,...
     O.                   ..    .~.+.      . N, .
    7.,, .                8. ..   ...         ,O.
    I.DMM,.                .M     .O           ,D
    ...MZ .                 ~.   ....          ..N..    :
    ?                     .I.    ,..             ..     ,
    +.       ,MM=       ..Z.   .,.               .MDMN~$
    .I.      .MMD     ..M . .. =..                :. . ..
    .,M      ....   .Z. .   +=. .                 ..
       ~M~  ... 7D...   .=~.      . .              .
        ..$Z... ...+MO..          .M               .
                     .M. ,.       .I   .?.        ..
                     .~ .. Z=I7.. .7.  .ZM~+N..   ..
                     .O   D   . , .M ...M   . .  .: .
                     . NNN.I....O.... .. M:. .M,=8..
                      ....,...,.  ..   ...   ..

## build & install

```
mvn clean compile install
```

## using hippo-rpc

 `HippoServer` enhances TransportServer with stream manager(open, streaming fetch, close)
 ```
   val server = HippoServer.create("test", new HippoRpcHandler() {
   ...
   }, 1224)

 ```
 `HippoClient` enhances TransportClient with stream request and result boxing (as Stream[T])
 ```
   val client = HippoClient.create("test", "localhost", 1224)
 ```

more examples, see <https://github.com/bluejoe2008/hippo-rpc/blob/master/src/test/scala/hippo/HippoRpcTest.scala>

## using hippo-rpc with spark-rpc

`spark-rpc`, or `kraps-rpc` uses a messaging mechanism to improve the performance of RPC calling.

`HippoRpcEnvFactory` is provided to enable RPC calls on `kraps-rpc`, and stream handling on `hippo-rpc`.

`HippoRpcEnv` enhances `NettyRpcEnv` with stream handling functions, besides RPC messaging
 usage of `HippoRpcEnv` is like that of `NettyRpcEnv`:

```
   rpcEnv = HippoRpcEnvFactory.create(config)
   val endpoint: RpcEndpoint = new FileRpcEndpoint(rpcEnv)
   rpcEnv.setupEndpoint("endpoint-name", endpoint)
   rpcEnv.setStreamManger(new FileStreamManager())
   ...
   ...
   val endPointRef = rpcEnv.setupEndpointRef(RpcAddress(...), "...");
```

## dependencies

`spark-commons`: spark common library, https://github.com/apache/spark
`kraps-rpc`: A RPC framework leveraging Spark RPC module, https://github.com/neoremind/kraps-rpc

## licensing

`hippo-rpc` is licensed under the BSD 2-Clause "Simplified" License.
