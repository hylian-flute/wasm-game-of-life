FROM rust
ENV USER charines
COPY ./script /home/script/
RUN cargo install wasm-pack && \
  cargo install cargo-generate && \
  apt update && apt install -y npm && \
  npm install -gy create-wasm-app && \
  cd /home && \
  cargo generate --name wasm-app --git https://github.com/rustwasm/wasm-pack-template && \
  cd /home/wasm-app && \
  mv /home/script /home/wasm-app && \
  alias wasm-app-init=/home/wasm-app/script/init.sh && \
  wasm-pack build && \
  create-wasm-app www && \
  mkdir /home/module && \
  ln -s /home/module/node_modules /home/wasm-app/www/node_modules
WORKDIR /home/wasm-app
