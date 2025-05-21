FROM ubuntu
ARG XDG_CONFIG_HOME="/setup/.config"
RUN apt update && apt upgrade -y
RUN apt install git stow curl php -y
RUN apt install ninja-build gettext cmake unzip curl build-essential -y

WORKDIR /setup
RUN git clone https://github.com/neovim/neovim.git
RUN git clone https://github.com/ayrtonguttier/dotfiles.git

WORKDIR /setup/neovim
RUN make install

ENV XDG_CONFIG_HOME=${XDG_CONFIG_HOME}
RUN mkdir ${XDG_CONFIG_HOME}
WORKDIR /setup/dotfiles
RUN stow nvim


ENTRYPOINT [ "nvim" ]
