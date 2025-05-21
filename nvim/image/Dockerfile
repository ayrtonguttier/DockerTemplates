FROM debian AS build
RUN apt-get update && apt-get upgrade
RUN apt-get install git ninja-build gettext cmake unzip curl build-essential -y
RUN git clone https://github.com/neovim/neovim /neovim
WORKDIR /neovim
RUN git checkout stable
RUN make CMAKE_BUILD_TYPE=Release

FROM scratch
COPY --from=build /neovim /
#COPY --from=build /neovim/build/lib /lib
#COPY --from=build /neovim/build/share /share
