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

 HippoServer enhances TransportServer with stream manager(open, streaming fetch, close)
 HippoClient enhances TransportClient with stream request and result boxing (as Stream[T])

# HippoRpcEnvFactory

HippoRpcEnv enhances NettyRpcEnv with stream handling functions, besides RPC messaging
 usage of HippoRpcEnv is like that of NettyRpcEnv:

```
   rpcEnv = HippoRpcEnvFactory.create(config)
   val endpoint: RpcEndpoint = new FileRpcEndpoint(rpcEnv)
   rpcEnv.setupEndpoint("endpoint-name", endpoint)
   rpcEnv.setStreamManger(new FileStreamManager())
   ...
   ...
   val endPointRef = rpcEnv.setupEndpointRef(RpcAddress(...), "...");
```
