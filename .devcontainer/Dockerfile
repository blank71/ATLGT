# https://hub.docker.com/r/ocaml/opam
FROM docker.io/ocaml/opam:fedora-41-ocaml-5.2@sha256:cf783a5bb72326cec8dcf17a3a3c32d4f23a339e09e947edca245daa86f80deb

RUN sudo dnf update -y \
  && sudo dnf group install -y "development-tools"

# Install dependencies
RUN opam install dune xml-light 

# For development environment
RUN opam install core ocaml-lsp-server ocamlformat

RUN echo "eval \$(opam env)" >> /home/opam/.bashrc 

# Install Graphviz, dot
RUN sudo dnf install -y graphviz

# Install mona
RUN sudo dnf install -y rpmbuild
RUN git clone https://github.com/cs-au-dk/MONA.git \
  && cd MONA \
  && sudo ./configure \
  && sudo make install-strip

