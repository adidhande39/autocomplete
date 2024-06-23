https://chatgpt.com/share/7cca50ff-8722-4daf-88fc-5875eaeee213

Step 1: Create an Index
Create an index named qa_index (you can name it anything you like).

curl -X PUT "localhost:9200/qa_index"

Step 2: Index Documents
Add your question-answer documents to the index. Here's an example with two documents:


curl -X POST "localhost:9200/qa_index/_doc/1" -H 'Content-Type: application/json' -d'
{
  "question": "What is Elasticsearch?",
  "answer": "Elasticsearch is a distributed, RESTful search and analytics engine."
}'

curl -X POST "localhost:9200/qa_index/_doc/2" -H 'Content-Type: application/json' -d'
{
  "question": "How to use Elasticsearch?",
  "answer": "You can interact with Elasticsearch using RESTful APIs, clients, or Kibana."
}'


Step 3: Query the Index
Search for documents that contain the string in the question field. Here's an example of querying for the string "Elasticsearch":


curl -X GET "localhost:9200/qa_index/_search" -H 'Content-Type: application/json' -d'
{
  "query": {
    "match": {
      "question": "Elasticsearch"
    }
  }
}'



Step 3: Elasticsearch Configuration
Ensure that Elasticsearch is configured to accept requests from your web browser. If there are any CORS issues, you might need to adjust the Elasticsearch configuration:

Open your elasticsearch.yml file (usually found in the config directory of your Elasticsearch installation).
Add or update the following lines to allow CORS:

http.cors.enabled: true
http.cors.allow-origin: "*"
Restart Elasticsearch after making these changes.
