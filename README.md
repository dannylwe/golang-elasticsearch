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

### Helpful Links
- https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#docker-cli-run-dev-mode  
- https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-docker.html  
- https://github.com/olivere/elastic  
- https://www.freecodecamp.org/news/go-elasticsearch/  
