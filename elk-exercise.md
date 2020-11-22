# CISC 525 Module 10 Output of Exercise #5.

You must provide this output as a part of your homework assignment.
You must share this repository with me
For each command you run on Kibana's web console, make sure to provide the input and output of the
command as follows:

## Kibana Console

- Commend input: Checking the cluster's health
```http
  GET /_cluster/health
```

- Commend output:
```json
{
  "cluster_name" : "elasticsearch",
  "status" : "yellow",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  "active_primary_shards" : 5,
  "active_shards" : 5,
  "relocating_shards" : 0,
  "initializing_shards" : 0,
  "unassigned_shards" : 4,
  "delayed_unassigned_shards" : 0,
  "number_of_pending_tasks" : 0,
  "number_of_in_flight_fetch" : 0,
  "task_max_waiting_in_queue_millis" : 0,
  "active_shards_percent_as_number" : 55.55555555555556
}
```

- alternative curl:
```bash

curl -XGET "http://localhost:9200/_cluster/health"
```

- Commend input: Listing the cluster's nodes
```http
GET /_cat/nodes?v
```
- Commend output
```json

ip        heap.percent ram.percent cpu load_1m load_5m load_15m node.role master name
127.0.0.1           22          93   2    0.14    0.21     0.24 dilm      *      student-VirtualBox

```
- curl command:
```bash
curl -XGET "http://localhost:9200/_cat/nodes?v"
```

- Commend input: Listing the cluster's indices
```http
GET /_cat/indices?v
```

- Commend output
```json

health status index                    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   .kibana_task_manager_1   9D3oQE8zQ2-q0qM4XCMITg   1   0          2            1     26.9kb         26.9kb
green  open   .apm-agent-configuration DvPDzd-uRPWLOWR-FlVKbQ   1   0          0            0       283b           283b
green  open   .kibana_1                Tye9xrNRSNufstAaXD6HeA   1   0         22           12     70.2kb         70.2kb
yellow open   products                 dBzkx6rsQJyNPs6ohFURgg   2   2          3            8     15.6kb         15.6kb
```
- curl command:
```bash
curl -XGET "http://localhost:9200/_cat/indices?v"
```

- Commend input: Test search query
```http

GET /.kibana/_search
{
  "query": {
    "match_all": {}
  }
}
```

- Commend output
```json
{
  "took" : 1,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 22,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "space:default",
        "_score" : 1.0,
        "_source" : {
          "space" : {
            "name" : "Default",
            "description" : "This is your default space!",
            "color" : "#00bfb3",
            "disabledFeatures" : [ ],
            "_reserved" : true
          },
          "type" : "space",
          "references" : [ ],
          "migrationVersion" : {
            "space" : "6.6.0"
          },
          "updated_at" : "2020-03-21T11:56:30.286Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "config:7.6.1",
        "_score" : 1.0,
        "_source" : {
          "config" : {
            "buildNum" : 29118
          },
          "type" : "config",
          "references" : [ ],
          "updated_at" : "2020-03-21T11:56:40.954Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "telemetry:telemetry",
        "_score" : 1.0,
        "_source" : {
          "telemetry" : {
            "userHasSeenNotice" : true
          },
          "type" : "telemetry",
          "references" : [ ],
          "updated_at" : "2020-03-21T11:56:59.847Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:sampleDataConfirm",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-21T12:31:48.378Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:PUT_index",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-22T13:24:40.385Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "maps-telemetry:maps-telemetry",
        "_score" : 1.0,
        "_source" : {
          "maps-telemetry" : {
            "settings" : {
              "showMapVisualizationTypes" : false
            },
            "indexPatternsWithGeoFieldCount" : 0,
            "mapsTotalCount" : 0,
            "timeCaptured" : "2020-11-22T03:52:35.308Z",
            "attributesPerMap" : {
              "dataSourcesCount" : {
                "min" : 0,
                "max" : 0,
                "avg" : 0
              },
              "layersCount" : {
                "min" : 0,
                "max" : 0,
                "avg" : 0
              },
              "layerTypesCount" : { },
              "emsVectorLayersCount" : { }
            }
          },
          "type" : "maps-telemetry",
          "references" : [ ],
          "updated_at" : "2020-11-22T03:52:35.309Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:kibana-user_agent:Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:82.0) Gecko/20100101 Firefox/82.0",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "references" : [ ],
          "updated_at" : "2020-11-22T03:53:02.984Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:welcomeScreenMount",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 3
          },
          "type" : "ui-metric",
          "updated_at" : "2020-11-22T03:53:02.985Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:sampleDataDecline",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 2
          },
          "type" : "ui-metric",
          "updated_at" : "2020-11-22T03:53:02.985Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:DELETE_delete",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 3
          },
          "type" : "ui-metric",
          "updated_at" : "2020-11-22T04:00:34.047Z"
        }
      }
    ]
  }
}
```

- curl command:
```bash

curl -XGET "http://localhost:9200/.kibana/_search" -H 'Content-Type: application/json' -d'{  "query": {    "match_all": {}  }}'
```

- Commend input: Creating a new index
```http

PUT /pages
```

- Commend output:
``` json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "pages"
}

```
- curl command:
```bash

curl -XPUT "http://localhost:9200/pages"
```

- Commend input: Checking the cluster's health
```http

GET /_cluster/health
```

- Commend output:
```json

{
  "cluster_name" : "elasticsearch",
  "status" : "yellow",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  "active_primary_shards" : 6,
  "active_shards" : 6,
  "relocating_shards" : 0,
  "initializing_shards" : 0,
  "unassigned_shards" : 5,
  "delayed_unassigned_shards" : 0,
  "number_of_pending_tasks" : 0,
  "number_of_in_flight_fetch" : 0,
  "task_max_waiting_in_queue_millis" : 0,
  "active_shards_percent_as_number" : 54.54545454545454
}
```

- curl command:
```bash

curl -XGET "http://localhost:9200/_cluster/health"
```

- Commend input : Listing the cluster's indices
```http

GET /_cat/indices?v
```

- Commend output:
```json
health status index                    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
yellow open   pages                    vlzzdPUPShaHNwZg2lEtQw   1   1          0            0       283b           283b
green  open   .kibana_task_manager_1   9D3oQE8zQ2-q0qM4XCMITg   1   0          2            1     26.9kb         26.9kb
green  open   .apm-agent-configuration DvPDzd-uRPWLOWR-FlVKbQ   1   0          0            0       283b           283b
green  open   .kibana_1                Tye9xrNRSNufstAaXD6HeA   1   0         22           17     88.3kb         88.3kb
yellow open   products                 dBzkx6rsQJyNPs6ohFURgg   2   2          3            8     15.6kb         15.6kb
```

- curl command:
```bash

curl -XGET "http://localhost:9200/_cat/indices?v"
```

- Commend input: Listing the cluster's shards
```http
GET /_cat/shards?v
```

- Commend output:
```json

index                    shard prirep state      docs  store ip        node
products                 1     p      STARTED       1    4kb 127.0.0.1 student-VirtualBox
products                 1     r      UNASSIGNED                       
products                 1     r      UNASSIGNED                       
products                 0     p      STARTED       2 11.5kb 127.0.0.1 student-VirtualBox
products                 0     r      UNASSIGNED                       
products                 0     r      UNASSIGNED                       
pages                    0     p      STARTED       0   283b 127.0.0.1 student-VirtualBox
pages                    0     r      UNASSIGNED                       
.kibana_task_manager_1   0     p      STARTED       2 26.9kb 127.0.0.1 student-VirtualBox
.apm-agent-configuration 0     p      STARTED       0   283b 127.0.0.1 student-VirtualBox
.kibana_1                0     p      STARTED      22 92.8kb 127.0.0.1 student-VirtualBox
```

- curl command:
```bash

curl -XGET "http://localhost:9200/_cat/shards?v"
```

- Commend input: Deleting an index
```http

DELETE /pages
```

- commend output:
```json
{
  "acknowledged" : true
}
```

- curl command:
```bash

curl -XDELETE "http://localhost:9200/pages"
```


- Commend input: Creating an index (with settings)
```http
PUT /products
{
  "settings": {
    "number_of_shards": 2,
    "number_of_replicas": 2
  }
}
```

- Commend output:
```json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "products"
}

```

- curl command:
```bash

curl -XDELETE "http://localhost:9200/products"
```


- Commend input: Indexing document with auto generated ID:
```http

POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}
```

- Commend output:
```json

{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "XHs77nUBhvYc4_8IUMFE",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}
```
- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_doc" -H 'Content-Type: application/json' -d'{  "name": "Coffee Maker",  "price": 64,  "in_stock": 10}'
```

- Commend input: Indexing document with custom ID:
```http

POST /products/_doc/100
{
  "name": "Toaster",
  "price": 49,
  "in_stock": 4
}
```

- Commend Output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_doc/100" -H 'Content-Type: application/json' -d'{  "name": "toster",  "price": 49,  "in_stock": 4}'
```

- Commend input: Check update
```http

GET /products/_doc/100
```

- Commend output: 
```json

{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 1,
  "_seq_no" : 0,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "toster",
    "price" : 49,
    "in_stock" : 4
  }
}
```

- curl command:
```bash

curl -XGET "http://localhost:9200/products/_doc/100"
```

- Commend input: Updating an existing field
```http

POST /products/_update/100
{
  "doc": {
    "in_stock": 3
  }
}
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 2,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 1,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "doc": {    "in_stock": 3  }}'
```

- Commend input: Adding a new field
```http

POST /products/_update/100
{
  "doc": {
    "tags": ["electronics"]
  }
}
```

- Commend output:
```json

{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 3,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 2,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "doc": {    "tags": ["electronics"]  }}'
```

- Commend input: Reducing the current value of in_stockby one
```http

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock--"
  }
}
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 4,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 3,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source": "ctx._source.in_stock--"  }}'
```


- Commend input: Assigning an arbitrary value to in_stock
```http
POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock = 10"
  }
}
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 5,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 4,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source": "ctx._source.in_stock = 10"  }}'
```


- Commend input: Checking the doc 10
```http

GET /products/_doc/100
```

- Commend output:
```json

{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 8,
  "_seq_no" : 7,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "toster",
    "price" : 49,
    "in_stock" : 10,
    "tags" : [
      "electronics"
    ]
  }
}
```

- curl command:
```bash

curl -XGET "http://localhost:9200/products/_doc/100"
```


- Commend input: Using parameters within scripts
```http

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock-= params.quantity", 
    "params": {
      "quantity": 4
    }
  }
}
```http

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 6,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 5,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source": "ctx._source.in_stock-= params.quantity",     "params": {      "quantity": 4    }  }}'
```

- Commend input: Check Update
```http

GET /products/_doc/100
```

- Commend output:
```json

{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 9,
  "_seq_no" : 8,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "toster",
    "price" : 49,
    "in_stock" : 6,
    "tags" : [
      "electronics"
    ]
  }
}
```

- curl command:
```bash

curl -XGET "http://localhost:9200/products/_doc/100"
```


- Commend input:Conditionally setting the operation to noop
```http

POST /products/_update/100
{
  "script": {
    "source": """if (ctx._source.in_stock== 0) {
      ctx.op= 'noop';
    }ctx._source.in_stock--;"""
  }
}
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 7,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 6,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source": "if (ctx._source.in_stock== 0) {\n      ctx.op= \"noop\";\n    }ctx._source.in_stock--;"  }}'
```

- Commend input: Check the update
```http

GET /products/_doc/100 
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 10,
  "_seq_no" : 9,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "toster",
    "price" : 49,
    "in_stock" : 5,
    "tags" : [
      "electronics"
    ]
  }
}
```

- curl command:
```bash

curl -XGET "http://localhost:9200/products/_doc/100"
```

- Commend input:Conditionally update a field value
```http
POST /products/_update/100
{"script": {
  "source": """if (ctx._source.in_stock> 0) {
    ctx._source.in_stock--;
    
  }"""
 }
}
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 11,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 10,
  "_primary_term" : 1
}
```
- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{"script": {  "source": "if (ctx._source.in_stock> 0) {\n    ctx._source.in_stock--;\n    \n  }" }}'
```

- Commend input: Check the update
```http

GET /products/_doc/100 
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 11,
  "_seq_no" : 10,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "toster",
    "price" : 49,
    "in_stock" : 4,
    "tags" : [
      "electronics"
    ]
  }
}
```

- curl command:
```bash

curl -XGET "http://localhost:9200/products/_doc/100"
```


- Commend input:Conditionally delete a document
```http

POST /products/_update/100
{"script": {
  "source": """if (ctx._source.in_stock< 0) {
    ctx.op= 'delete';
  }
    ctx._source.in_stock--;"""
  }
}
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 12,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 11,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{"script": {  "source": "if (ctx._source.in_stock< 0) {\n    ctx.op= \"delete\";\n  }\n    ctx._source.in_stock--;"  }}'
```

- Commend input: Delet the recorde
```http

DELETE /products/_doc/101
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "101",
  "_version" : 1,
  "result" : "not_found",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 12,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XDELETE "http://localhost:9200/products/_doc/101"
```

- Commend input:Upsters
```http

POST /products/_update/101
{"script": {
  "source": "ctx._source.in_stock++"},"upsert": {
    "name": "Blender","price": 399,"in_stock": 5
  }
}
```

- Commend output
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "101",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 13,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPOST "http://localhost:9200/products/_update/101" -H 'Content-Type: application/json' -d'{"script": {  "source": "ctx._source.in_stock++"},"upsert": {    "name": "Blender","price": 399,"in_stock": 5  }}'
```


- Commend input:Check update
```http

GET /products/_doc/101
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "101",
  "_version" : 1,
  "_seq_no" : 13,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "Blender",
    "price" : 399,
    "in_stock" : 5
  }
}
```

- curl command:
```bash

curl -XGET "http://localhost:9200/products/_doc/101"
```


- Commend input:Replacing documents
```http

PUT /products/_doc/100
{
  "name": "Toaster",
  "price": 79,
  "in_stock": 4
}
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 13,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 14,
  "_primary_term" : 1
}
```

- curl command:
```bash

curl -XPUT "http://localhost:9200/products/_doc/100" -H 'Content-Type: application/json' -d'{  "name": "Toaster",  "price": 79,  "in_stock": 4}'
```

- Commend input:Check update
```http
GET /products/_doc/100
```

- Commend output:
```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 13,
  "_seq_no" : 14,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "Toaster",
    "price" : 79,
    "in_stock" : 4
  }
}
```'

- curl command:
```bash

curl -XGET "http://localhost:9200/products/_doc/100"
```

