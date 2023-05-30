FROM fuzzers/cargo-fuzz:0.11.0 as builder

ADD . /fastwebsockets
WORKDIR /fastwebsockets

RUN cd fuzz/ && cargo fuzz build

FROM ubuntu:20.04
COPY --from=builder /fastwebsockets/fuzz/target/x86_64-unknown-linux-gnu/release/parse_frame /
COPY --from=builder /fastwebsockets/fuzz/target/x86_64-unknown-linux-gnu/release/parse_frame_fragment /
COPY --from=builder /fastwebsockets/fuzz/target/x86_64-unknown-linux-gnu/release/unmask /
