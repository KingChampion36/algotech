# Local Setup

## Follow the given steps for setup in your local:

1. Install pip

```shell
sudo apt-get install python3-pip
```

2. Install `mkdocs` using pip

```shell
pip3 install mkdocs
```

3. Install `mkdocs` and material theme

```shell
pip3 install mkdocs-bootswatch
```

```shell
pip3 install mkdocs-material==9.2.0b3
```

4. Install plugins:

```shell
pip3 install mkdocs-glightbox
```

```shell
pip3 install mkdocs-minify-plugin
```

5. Preview the website locally

```shell
python3 -m mkdocs serve
```

Website can be viewed at [localhost:8000](http://localhost:8000) or [127.0.0.1:800](http://127.0.0.1:8000).

## Blog Documentation in mkdocs

https://squidfunk.github.io/mkdocs-material/plugins/blog/#config.post_readtime
