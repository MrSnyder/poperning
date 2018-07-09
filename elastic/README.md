# elastic search & co.

## tutorials

- https://www.elastic.co/blog/a-practical-introduction-to-elasticsearch
- https://www.udemy.com/elasticsearch-complete-guide/
- https://github.com/codingexplained/complete-guide-to-elasticsearch

## ELK stack / Elastic stack

- Elasticsearch: Analytics and full-text search engine
- Logstash: Get data into the ES cluster (not only for log messages)
- Kibana: Analytics and visualisation platform. Answer business intelligence questions.
- Beats: Platform of data shippers
- X-Pack: Security, monitoring, alerting, reporting

## api endpoints

    ${base_url}
    ${base_url}/${index}
    ${base_url}/${index}/_analyze
    ${base_url}/${index}/${type}
    ${base_url}/${index}/${type}/_search
    ${base_url}/${index}/${type}/_mapping
    ${base_url}/${index}/${type}/_bulk

## query parameters

    pretty
    format=yaml
    size
    from

## data types

- object
- nested
- join: be careful (query performance!)

## query types

### term
- Not analyzed, use for keywords, dates, number, etc. 

### bool
- Filter context: ignored for relevance score
- Query context: included in relevance score

### match
- Analyzed, use for fulltext
- Can be expressed as an equivalent bool query with (manually analyzed) terms

### match_phrase
- slop parameter

### parent_id

### has_parent

### has_child

### nested
- Used for filtering on properties that are part of a nested datatype
- Nested datatype vs array of objects: Nested respects the associations of object properties

### fuzzy

## stuff to remember
- type nested vs array of objects
- multi-typed index are going away. use "_doc" as type name for future compatibility
- For join queries, parent/child documents must be on the same index and shard.

## example requests

    curl -H "Content-Type: application/json" -XPOST "https://user:pw@host:port/index/default/_bulk?pretty" --data-binary @test-data.json
