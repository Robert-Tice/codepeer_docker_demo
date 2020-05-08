FROM ubuntu:18.04

# Add codepeer tar to image
ADD codepeer-*-x86_64-linux-bin.tar.gz /
RUN cd /codepeer-*-x86_64-linux-bin \
    && printf '/codepeer\ny\n' | ./doinstall \
    && cd / \
    && rm -rf /cdp_install

ENV PATH="/codepeer/bin:${PATH}"

# Create mount point for src to analyze
VOLUME /my_project
WORKDIR /my_project

# Run codepeer on docker run
# Cannot use ARG in ENTRYPOINT directly. Must use ENV as proxy
ARG project
ENV cdp_proj=$project
ENTRYPOINT codepeer -P $cdp_proj
