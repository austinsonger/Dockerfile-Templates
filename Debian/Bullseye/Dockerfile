#=========================================================
FROM debian:bullseye-slim
ARG user_name
ARG work_dir
#=========================================================
# Update package repositories and install new packages
RUN apt-get update \
      && DEBIAN_FRONTEND=noninteractive \
      apt-get install \
      --assume-yes \
      --no-install-recommends \
      --quiet \
      bash \
      && rm -rf /var/lib/apt/lists/*
#=========================================================
# Set up a non-root user
RUN useradd \
      --create-home \
      --shell '/bin/bash' \
      --user-group \
      $user_name
#=========================================================
# Set user environment variables
ENV HOME "/home/${user_name}"
ENV USER $user_name
#=========================================================
# Set the non-root user
USER $USER
#=========================================================
# Create a working directory
RUN mkdir "${HOME}/${work_dir}"
#=========================================================
# Change to the working directory
WORKDIR "${HOME}/${work_dir}"
#=========================================================
# Runtime entrypoint
ENTRYPOINT ["/bin/bash", "--login"]
