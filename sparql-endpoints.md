# Idea

We want to find URI's of Organizations (e.g. of Gouda) in SPARQL endpoint containing cultural heritage. So lets go and SPARQL endpoints. We want to put them in our interface and have a volunteer decide whether these things are the same.

Purpose of our plan: finally start doing things on real LOD federatively.

## Gouda Time Machine
https://www.goudatijdmachine.nl/sparql/repositories/gtm

## Bob's hobby endpoint
``` bash
curl https://fuseki.coret.org/#/dataset/samh-ric/query --data query=SELECT%20%3Ftype%20%28count%28%3Ftype%29%20as%20%3FtypeCnt%29%20WHERE%20%7B%0A%20%20%3Fsub%20a%20%3Ftype%20.%0A%7D%20 -X POST
```

## IISG
``` bash
curl -I 'https://api.druid.datalegend.net/datasets/IISG/iisg-kg/services/iisg-kg/sparql'

curl https://druid.datalegend.net/_api/datasets/IISG/iisg-kg/services/iisg-kg/sparql --data query=SELECT%20%3Ftype%20%28count%28%3Ftype%29%20as%20%3FtypeCnt%29%20WHERE%20%7B%0A%20%20%3Fsub%20a%20%3Ftype%20.%0A%7D%20 -X POST
```

## KB
Richard gedaan.


## NIBG
``` bash
$ curl -I 'https://cat.apis.beeldengeluid.nl/sparql'

HTTP/1.1 400 Bad Request
Date: Fri, 03 Nov 2023 19:47:42 GMT
Server: Apache/2.4.37 (Red Hat Enterprise Linux) OpenSSL/1.1.1k
Content-Length: 60
Content-Type: application/json; charset=UTF-8
Connection: close

$ curl https://cat.apis.beeldengeluid.nl/sparql --data query=SELECT%20%3Ftype%20%28count%28%3Ftype%29%20as%20%3FtypeCnt%29%20WHERE%20%7B%0A%20%20%3Fsub%20a%20%3Ftype%20.%0A%7D%20 -X POST

{
  "code":503,
  "message":"Service unavailable: error(resource_error(stack),stack_overflow{choicepoints:12,depth:31,environments:17,globalused:16,localused:3,stack:[frame(31,system:'$add_findall_bag'(a/1),[]),frame(30,'$bags':findall_loop(a/1,(:)/2,_4690,[]),[]),frame(29,system:setup_call_catcher_cleanup((:)/2,(:)/2,_4732,(:)/2),[]),frame(25,rdfql_util:select_results(all,[],(:)/2,[1],0,inf,unsorted,row/2,(:)/2),[]),frame(21,'$bags':findall_loop(row/2,(:)/2,_4844,[]),[])],stack_limit:1048576,trailused:1})"
}

```

Werkt niet. Waarom niet?

## HNI
``` bash
$ curl -I 'https://api.collectiedata.hetnieuweinstituut.nl/datasets/the-other-interface/knowledge-graph/services/knowledge-graph/sparql'

$ curl https://api.collectiedata.hetnieuweinstituut.nl/datasets/the-other-interface/knowledge-graph/services/knowledge-graph/sparql --data query=SELECT%20%3Ftype%20%28count%28%3Ftype%29%20as%20%3FtypeCnt%29%20WHERE%20%7B%0A%20%20%3Fsub%20a%20%3Ftype%20.%0A%7D%20 -X POST
```

Wrong url registered as SPARQL endpoint, but it works in the end!!

## RKD
``` bash
$ curl https://api.rkd.triply.cc/datasets/rkd/RKD-Knowledge-Graph/sparql --data query=SELECT%20%3Ftype%20%28count%28%3Ftype%29%20as%20%3FtypeCnt%29%20WHERE%20%7B%0A%20%20%3Fsub%20a%20%3Ftype%20.%0A%7D%20 -X POST
```

Could be improved (for our purpose) if the location of an agent was added.

## Literuurmuseum
``` bash
curl https://LIT.hosting.deventit.net/AtlantisSparql --data query=SELECT%20%3Ftype%20%28count%28%3Ftype%29%20as%20%3FtypeCnt%29%20WHERE%20%7B%0A%20%20%3Fsub%20a%20%3Ftype%20.%0A%7D%20 -X POST
```
Times out.

## Nationaal Archief
``` bash
$ curl https://service.archief.nl/sparql --data query=SELECT%20%3Ftype%20%28count%28%3Ftype%29%20as%20%3FtypeCnt%29%20WHERE%20%7B%0A%20%20%3Fsub%20a%20%3Ftype%20.%0A%7D%20 -X POST
```

Caps the result to a maximum of 25 results. Times out at 10 sec.

## Muziekweb
https://api.data.muziekweb.nl/datasets/MuziekwebOrganization/Muziekweb/services/Muziekweb/sparql

Works, but has no way of finding Gouda's schema:MusicGroup's.