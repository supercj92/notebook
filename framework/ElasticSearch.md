
第一个业务需求就是存储雇员数据。 这将会以 雇员文档 的形式存储：一个文档代表一个雇员。存储数据到 Elasticsearch 的行为叫做 索引 ，但在索引一个文档之前，需要确定将文档存储在哪里。

列出所有索引：
curl -XGET 'localhost:9200/_cat/indices?v&pretty'