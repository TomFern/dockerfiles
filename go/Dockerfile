FROM golang:1.14

# Install beego bee tool
RUN go get -u github.com/beego/bee

# Enable vendor module management
ENV GO111MODULE=on
ENV GOFLAGS=-mod=vendor

ENV APP_USER app
ENV APP_HOME /go/src/mathapp

# IDs should match the user's
ARG GROUP_ID
ARG USER_ID

# Create matching user in container
RUN groupadd --gid $GROUP_ID app && useradd -m -l --uid $USER_ID --gid $GROUP_ID $APP_USER
RUN mkdir -p $APP_HOME && chown -R $APP_USER:$APP_USER $APP_HOME

USER $APP_USER
WORKDIR $APP_HOME
EXPOSE 8010
CMD ["bee", "run"]
