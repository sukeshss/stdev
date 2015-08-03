FROM ubuntu:14.04

RUN apt-get update
RUN apt-get install wget vim git --assume-yes

# install RVM
RUN apt-get install build-essential curl --assume-yes
RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys D39DC0E3
RUN curl -L https://get.rvm.io | bash -s stable
RUN echo 'source /etc/profile.d/rvm.sh' >> ~/.bashrc
RUN /usr/local/rvm/bin/rvm-shell -c "rvm requirements"

# install Ruby
RUN /bin/bash -l -c "rvm autolibs enable"
RUN /bin/bash -l -c "rvm install 2.1.2"

# install Rails
RUN echo "gem: --no-rdoc --no-ri" >> ~/.gemrc
RUN /bin/bash -l -c "gem install rails -v 4.1.5"

# Install Nginx.
RUN \
  apt-get install -y nginx && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx

# Define mountable directories.
VOLUME ["/usr/share/nginx/html"]

# Define working directory.
WORKDIR /etc/nginx

# Define default command.
CMD ["nginx"]

# Expose ports.
EXPOSE 80
EXPOSE 443
