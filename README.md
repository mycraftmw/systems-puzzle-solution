# Insight DevOps Engineering Systems Puzzle Solution

1. At first, I just tried to start the whole progress, and then unsurprisingly failed.
1. Then I found that I cannot access the `8080` port in my web browser. I realized docker exposed wrong port.
1. Then I checked the `nginx` service part in the `docker-compose.yml` and fixed the ports option.
1. After that, I still cannot access the flask app, then I check the configuration of `nginx`. In the original configuration, the nginx server transfer the package to the port `5001` of flaskapp which actually should be `5000`, since the `app.py` did not specify the port and by default it is `5000`.
1. Besides, since we used the special port `8080`, we have to set `Host` to `$http_host` that keeps the port in the URL.
1. At last, to make it clearer, I changed `EXPOSE 5001` to `EXPOSE 5000`.