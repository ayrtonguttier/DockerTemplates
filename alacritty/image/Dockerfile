FROM rust AS build
RUN rustup override set stable && rustup update stable

RUN git clone https://github.com/alacritty/alacritty.git /alacritty

WORKDIR /alacritty

RUN cargo build --release

FROM scratch 
COPY --from=build /alacritty/ /
