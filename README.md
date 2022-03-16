# dockercoins
```
git clone https://github.com/academiaonline-org/dockercoins
cd dockercoins
docker network create dockercoins
docker login
docker build -t ggacer/ruby:sinatra-thin hasher/
docker push ggacer /ruby:sinatra-thin
docker run -d --entrypoint ruby --name hasher --read-only --restart always -u nobody -v $PWD/hasher/hasher.rb:/data/hasher.rb -w /data/ --network dockercoins ggacer/ruby:sinatra-thin hasher.rb
docker pull redis:alpine
docker inspect redis:alpine
docker build -t ggacer/redis:alpine redis/ 
docker push ggacer/redis:alpine
docker run -d --entrypoint docker-entrypoint.sh --name redis --read-only --restart always -u redis -v redis:/data/ -w /data/ --network dockercoins ggacer/redis:alpine redis-server
docker build -t ggacer/python:flask rng/
docker push ggacer/python:flask
docker run -d --entrypoint python --name rng --read-only --restart always -u nobody -v $PWD/rng/rng.py:/data/rng.py -w /data/ --network dockercoins ggacer/python:flask rng.py
docker build -t ggacer/python:redis-requests worker/
docker push ggacer/python:redis-requests
docker run -d --entrypoint python --name worker --read-only --restart always -u nobody -v $PWD/worker/worker.py:/data/worker.py -w /data/ --network dockercoins ggacer/python:redis-requests worker.py 
```
