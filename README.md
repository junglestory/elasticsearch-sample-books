# Downloading and running ElasticSearch
	* [다운로드](https://www.elastic.co/downloads/elasticsearch)


# Index Mapping
<pre><code> 
curl -XPUT http://localhost:9200/books/ -d '
{
	"mappings" : {
   		"book" : {
   			"properties" : {
       			"title" : { "type" : "string" },
       			"author" : { "type" : "string" },
       			"publisher" : { "type" : "string"},
       			"publish_date": { "type" : "date" , "format" : "yyyy-MM-dd"},
       			"price" : { "type" : "long" },
       			"summary" : { "type" : "string"}
 		     }
   		}
  }
}'
</code></pre>

# Bulk Indexing
<pre><code> 
curl -XPOST localhost:9200/_bulk --data-binary @books.json
</code></pre>

# Searching
<pre><code> 
curl -XGET 'localhost:9200/books/book/_search?pretty' -H 'Content-Type: application/json' -d'
{
    "query": {
        "match" : {
            "summary" : "사회"
        }
    }
}
'
</code></pre>
