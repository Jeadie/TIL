# Warm up KNN opensearch segment for reduced ANN cold starts
The Opensearch KNN plugin stores neighbour information, for regularly indices, on disk as Lucene segments. Initial KNN search operations will incur heavy disk read latency (thereafter, they remain in memory). Instead of performing [deep pings](https://stackoverflow.com/questions/46192797/what-is-the-difference-between-a-shallow-and-deep-ping) on each index, Opensearch comes with a warmup operation out-of-the-box [link](https://opensearch.org/docs/latest/search-plugins/knn/api/#warmup-operation):
```
GET /_plugins/_knn/warmup/index1,index2,...
```
