# syntax=docker/dockerfile:1.3
FROM rust:1.58
RUN  --mount=type=cache,target=/root/.cargo \
    cargo install \
        mdbook \
        mdbook-mermaid
RUN useradd --create-home gcp-student
RUN chsh -s /bin/bash gcp-student
USER gcp-student
ENTRYPOINT [ "/bin/bash", "-c" ]
CMD ["make", "serve"]