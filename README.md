# QuicTor

## Instructions for Running Shadow:
- Follow the normal process to build `libquicsock`.
- `cp libquicsock.so ~/.shadow/lib`
- `cd ~/shadow-plugin-tor`
- `./build_cmd.sh`
- `./setup install`
- `cd ~/shadow-plugin-tor/resource/quic`
- `shadow-tor -i shadow.config.xml`

### Instructions to build QuicTor: 
- autogen
- configure --disable-asciidocs
- Patch the Makefile by running `patch Makefile < libquicsock_makefile.patch`
- Build libquicsock (see below)
- Se up certificates for QUIC (see below)
- make 

### Instructions to build libquicsock:
- in `quictor/`, run `git submodule init && git submodule update`
- go into `src/simple-quic`, run `./init_repo.sh`
- make (or 'make debug' for logging and assertions) inside src/simple-quic
- fix all dependency problems by downloading needed packages (see below) 
- wait ~5 mins for building
- change `LD_LIBRARY_PATH` to include the path to src/simple-quic

### Instructions on generate certificates for QUIC:
- use the scrips under `src/simple-quic/certs/` to generate cerificates
- set environment variables for `QUICTOR_CERT_PATH` and `QUICTOR_KEY_PATH`
  Set `QUICTOR_CERT_PATH` to point to `lead_cert.pem`
  and `QUICTOR_KEY_PATH` to point to `lead_cert.key`.

### External dependencies:
- for libquic: `go` (`gccgo-go` on Ubuntu)
- for libquicsock: `libevent` (`libevent-dev` on Ubuntu)
