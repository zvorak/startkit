FROM ruby:2.5.3

ENV DEBCONF_NOWARNINGS yes
ENV DEBIAN_FRONTEND noninteractive

ENV APP_ROOT /app
ENV SRC_DIR ./src

WORKDIR $APP_ROOT

RUN apt-get update -qq && \
    apt-get install -y apt-utils \
                       build-essential \
                       libpq-dev \
                       nodejs \
                       mysql-client
COPY $SRC_DIR/Gemfile $APP_ROOT/Gemfile
COPY $SRC_DIR/Gemfile.lock $APP_ROOT/Gemfile.lock
RUN bundle install

EXPOSE 3000
CMD ["bundle", "exec", "rails", "server", "-b", "0.0.0.0"]
