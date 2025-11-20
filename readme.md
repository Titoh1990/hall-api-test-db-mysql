##SciKey 
SciKey is a system that extracts scientific publications from HAL, enriches them through Wikidata, stores relationships inside a Neo4j graph database, and exposes data through a Django-based frontend.
SciKey automates
-Extracting publications (HAL API)
-Mapping keywords to Wikidata entities (QIDs)
-Checking hierarchical relationships (P279 / P31 paths)
-Validating classification using Rameau
-Storing relationships in Neo4j
-Rendering an interactive UI for exploring research knowledge

## What’s inside
api/ – Python service that pulls records from HAL and exposes a small REST  API (JSON).

wikidata/ – ETL worker that reads JSON from the API, looks up entities in Wikidata, and builds mappings.

graph/ – Neo4j graph database storing authors, papers, organizations, topics, and relationships.

web/backend/ – Django frontend/backend (neo4j-keywords) that queries Neo4j and renders the interactive graph UI and filters

## how to run the system
Make sure Docker and Docker Compose are installed

#Navigate to the folder containing docker-compose.yml
```
cd path/to/project
```
#Start all services
Runs HAL API, Neo4j, Django, and all pipelines
```
docker-compose up -d
```
#Stop and clean everything (optional)
```
docker compose down --rmi all --volumes
```

Remove leftover container/image
```
docker rm -f mysql-container-scikey && docker rmi scikey-mysql-db
```
#Verify Neo4j is running
```
docker ps --filter name=neo4j
```

##  project structure
#api 
fech information from HAL
creates a json

#wikidata 
wikidate loads json then we generate a mapping 
insert information into neo4j graph database

#neo4j 
database that stores information in graph to be showed and filter in fronen

#web/backend
django front and backconnect with  n4j databases allows queri an interac with generated data 


## database(Neo4j)
Neo4j stores all graph data.
To explore it, connect with DBeaver Versión24.3.1.202412221611 - free for neo4j
Host: localhost, Port: 7687
User: neo4j, Password: (from docker-compose)
