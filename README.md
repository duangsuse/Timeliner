# Timeliner

Simple Timeline

## Dependencies

tokio-minihttp, lazy_static, serde_json, tokio_signal, websocket

## Models

Post: String author, Date time, String text

Comment: String author, Date time, String text

## APIs

```http
GET /version -> version

GET / -> num_posts
GET /<nth>/ -> Post
GET /<nth>/views -> num_views
GET /<nth>/comments/ -> [Comment
POST /<nth>/comment/<author> body=<text> -> new_len
GET /<nth>/comments/len -> num_comments


GET /pop/ (auth) -> new_len
POST /<author>/ body=<text> (auth) -> new_len
```

## Extra

数据库不使用，采用每次启动读取数据每次退出序列化数据的方式 🌚

WebSocket 在文章被回复的时候发送文章索引。

Using: `timelinerd <password>`

SIGQUIT: output data and exit

SIGUSR1: output data

SIGUSR2: clear anti-spamming log

编译前下载好 tokio-minihttp 放在 `../tokio-minihttp/` 里