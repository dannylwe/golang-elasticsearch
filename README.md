## Pull images
docker pull docker.elastic.co/elasticsearch/elasticsearch:7.4.2

## Start a Single Node Cluster
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.4.2

## To run elasticsearch cluster
`RUN` docker-compose up

## Verify if elasticsearch is running
use browser and go to localhost:9200

'''
{
  "name" : "d73a5341942e",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "OUDtOJ_oRwqL674hMdBhRA",
  "version" : {
    "number" : "7.4.2",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "2f90bbf7b93631e52bafb59b3b049cb44ec25e96",
    "build_date" : "2019-10-28T20:40:44.881551Z",
    "build_snapshot" : false,
    "lucene_version" : "8.2.0",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
'''

## Create an Index Called 'students'
`PUT localhost/9200/students`
{
	"settings": {
    	"number_of_shards": 1,
    	"number_of_replicas": 1
	},
   "mappings": {
       "properties": {
         "name": {
               "type": "text"
         },
         "age": {
               "type": "integer"      
         },
         "average_score": {
               "type": "float"
         }
     }
   }
}

## Add data to 'students' index
`POST localhost:9200/students/_doc`
{
	"name":"Alice",
	"age":17,
	"average_score":81.1
}

## Buk Insert to index
`POST localhost:9200/students/_bulk`
{ "index":{"_index": "students" } }
{ "name":"john doe","age":18, "average_score":77.7 }
{ "index":{"_index": "students" } }
{ "name":"bob","age":16, "average_score":65.5 }
{ "index":{"_index": "students" } }
{ "name":"mary doe","age":18, "average_score":97.7 }
{ "index":{"_index": "students" } }
{ "name":"eve","age":15, "average_score":98.9 }


### Helpful Links
- https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#docker-cli-run-dev-mode  
- https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-docker.html  
- https://github.com/olivere/elastic  
- https://www.freecodecamp.org/news/go-elasticsearch/  
