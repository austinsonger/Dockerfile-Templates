FROM alpine:3.14
#===============================================================================
# Build arguments
ARG user_name
ARG work_dir
ARG group_name=$user_name
ARG group_id='1000'
ARG user_id='1000'
#===============================================================================
# Update package repositories and install new packages
RUN apk add \
      --no-cache \
      --update \
      bash
#===============================================================================
# Set up a non-root user
RUN addgroup \
      --gid $group_id \
      $group_name \
      && adduser \
      --uid $user_id \
      --disabled-password \
      --ingroup $group_name \
      $user_name
#===============================================================================
# Set user environment variables
ENV HOME "/home/${user_name}"
ENV USER $user_name
#===============================================================================
# Set the non-root user
USER $USER
#===============================================================================
# Create a working directory
RUN mkdir "${HOME}/${work_dir}"
#===============================================================================
# Change to the working directory
WORKDIR "${HOME}/${work_dir}"
#===============================================================================
# Runtime entrypoint
ENTRYPOINT ["/bin/bash", "--login"]
