docker compose up --scale novel-worker=12

for i in {1..20}; do curl --location --request POST 'http://localhost:8080/novel/trigger' --header 'Content-Type: application/json' --data-raw '{"url": "https://insidethemirror1.wordpress.com/2021/05/16/chapter-18-reason/","tableOfContents": "false"}'; done