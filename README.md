#Clone Repo

$ git clone git@github.com:sukeshss/stdev.git

$ cd stdev

#Change to branch dev

$ git checkout dev

$ cd Docker/ruby-2.2.0

# Build Docker image

$ docker build -t test/ruby .

##Run Docker

##exposing the port 

$ docker run --name ruby-nginx -d -p 8080:80 test/ruby

##Run Docker mount volume

$ docker run --name ruby-nginx -v /usr/share/nginx/html:/usr/share/nginx/html -d -p 8080:80 test/ruby


