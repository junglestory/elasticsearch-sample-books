# 엘라스틱서치 설치와 실행
	<https://www.elastic.co/downloads/elasticsearch>
	

# 인덱스 매핑 설정
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

# 데이터 bulk 인덱스
<pre><code> 
curl -XPOST localhost:9200/_bulk --data-binary @books.json
</code></pre>

# 검색
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
