FROM ruby

# Install apt based dependencies required to run Rails as 
# well as RubyGems. As the Ruby image itself is based on a 
# Debian image, we use apt-get to install those.
RUN apt-get update && apt-get install -y build-essential nodejs

# copy directory with ruby app
ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

# install all the gems specified in the Gemfile to your application.
ONBUILD RUN bundle install

# migrations setup the tables in the database.
ONBUILD RUN bundle exec rake db:migrate

# populate db with default values
ONBUILD RUN bundle exec rake db:seed

# ONBUILD - adds to the image a trigger instruction to be executed at a later time, 
# when the image is used as the base for another build


# TEST
# build image: docker build -t ft-rails:on-build .

# ADD SAMPLE APP
# mkdir test && cd test
# git clone https://bitbucket.org/railstutorial/sample_app_4th_ed.git app

# copy Dockefile FROM SUBJECT
# FROM ft-rails:on-build
# EXPOSE 3000
# CMD ["rails", "server", "--binding", "0.0.0.0", "--port", "3000"]

# BUILD IMAGE && RUN CONTAINER
# build image: docker build -t ex02 .
# run container: docker run --name app -d -p 3000:3000 ex02

# test the app
# via curl: curl $(docker-machine ip <machine>):3000
# web browser: http://$(docker-machine ip <machine>):3000
