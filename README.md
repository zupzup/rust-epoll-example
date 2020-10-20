# rust-epoll-example

Start with `cargo run`. Then, you can send HTTP requests to the server at http://127.0.0.1:8000.

Try to send many requests and look at the log of the server, to see how requests are handled concurrently, although we're only running one thread.

For example, you can send a file:

```bash
while true; do curl --location --request POST 'http://localhost:8000/upload' \--form 'file=@/home/somewhere/some_image.png' -w ' Total: %{time_total}' && echo '\n'; done;
```

If you run this script multiple times at once, you'll see logs of the sort:

```bash
...
requests in flight: 6
...
```

and you'll also see, that the response times stay constant, which means we're handling multple requests concurrently.
