FROM node:10.16.0-alpine
RUN mkdir -p /opt/app
WORKDIR /opt/app
RUN adduser --disabled-password app
RUN npm install pm2 -g
COPY addressbook/ .
RUN chown -R app:app /opt/app
USER app
RUN npm install
EXPOSE 3000
# CMD [ "npm", "run", "pm2" ]
CMD ["pm2-runtime", "processes.json"]
