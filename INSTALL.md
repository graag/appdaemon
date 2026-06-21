Przed budowanie obrazu trzeba wygenerować wheel dla appdaemon.

```
curl -LsSf https://astral.sh/uv/install.sh | sh
bash -l
uv build --wheel --refresh -q
sudo docker compose build
````

W nowszych wersjach będzie niezbędne aby po dodaniu do pyproject.toml simple-pid trzeba ponownie wygenerować uv.lock.
```
curl -LsSf https://astral.sh/uv/install.sh | sh
bash -l
uv build --wheel --refresh -q
sudo docker compose build
# Edit pyproject.toml
sudo docker run --rm -it --entrypoint /bin/sh -v $PWD:/code appdaemon-appdaemon
cd /code
uv lock -p /usr/local/bin/python3
exit
sudo docker compose build
```
