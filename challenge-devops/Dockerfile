FROM ruby:2.6.3-slim
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs postgresql postgresql-contrib libpq-dev \
    && apt-get clean autoclean \
    && apt-get autoremove -y
RUN mkdir /app
RUN gem install pg
WORKDIR /app
COPY Gemfile /app/
RUN bundle install 
RUN rails db:create
RUN rails db:migrate
COPY . /app
CMD bundle exec rails s -p 3000 -b '0.0.0.0'
