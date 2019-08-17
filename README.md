# cratedb adapter for prometheus 

> with cratedb cluster && grafana && grok exporter demo

## Create cratedb table

```code
CREATE TABLE "metrics" (
    "timestamp" TIMESTAMP,
    "labels_hash" STRING,
    "labels" OBJECT(DYNAMIC),
    "value" DOUBLE,
    "valueRaw" LONG,
    "day__generated" TIMESTAMP GENERATED ALWAYS AS date_trunc('day', "timestamp"),
    PRIMARY KEY ("timestamp", "labels_hash", "day__generated")
  ) PARTITIONED BY ("day__generated");
```

## Running

```code
docker-compose up -d
```

## View UI && info

* cratedb ui

```code
open http://localhost:4200
```

* prometheuss

```code
open http://localhost:9090
```

* grafana

```code
open http://localhost:3000
```