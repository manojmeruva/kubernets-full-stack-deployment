FROM ruby:3.0.3

# Install system dependencies
RUN apt-get update && apt-get install -y \
  curl vim wget \
  build-essential \
  libpq-dev \
  ca-certificates

# Install Node.js 24 properly
RUN curl -fsSL https://nodejs.org/dist/v24.0.0/node-v24.0.0-linux-x64.tar.xz -o node.tar.xz && \
  tar -xJf node.tar.xz && \
  mv node-v24.0.0-linux-x64 /usr/local/node && \
  ln -s /usr/local/node/bin/node /usr/local/bin/node && \
  ln -s /usr/local/node/bin/npm /usr/local/bin/npm && \
  ln -s /usr/local/node/bin/npx /usr/local/bin/npx && \
  rm node.tar.xz

# Install Yarn
RUN npm install -g yarn

# Copy project files
COPY . .

# Install Ruby dependencies
RUN bundle install && gem install rails

# Start app
ENTRYPOINT ["bash", "commands.sh"]