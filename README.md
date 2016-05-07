# QuicTor
### Instructions to build QuicTor: 
- autogen
- configure --disable-asciidocs
- patch the Makefile with libquicsock_makefile.patch
- pull and build libquicsock (see below)
- set environment variables for QUICTOR_CERT_PATH and QUICTOR_KEY_PATH
- change LD_LIBRARY_PATH to include the path to src/simple-quic
- make 

### Instructions to build libquicsock
- in quictor/, initialize submodule
- go into src/simple-quic, initialize submodule
- go further into lib/libquic and pull, change branch to kku1993-mod
- make (or 'make debug' for debug logging) inside src/simple-quic
- fix all dependency problems by downloading needed packages (see below) 
- wait ~5 mins for building

### Possible needed dependencies
- for libquic: gccgo-go, ninja-build
- others: libevent-dev
