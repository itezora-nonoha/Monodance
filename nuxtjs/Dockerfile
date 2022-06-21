FROM node:14
USER node
WORKDIR /home/node
RUN npm install create-nuxt-app
RUN npm init nuxt-app src --answers "{ \
  \"name\": \"test-app\", \
  \"language\": \"ts\", \
  \"pm\": \"npm\", \
  \"ui\": \"vuetify\", \
  \"features\": \"axios\", \
  \"linter\": \"eslint\", \
  \"test\"  : \"none\", \
  \"mode\"  : \"universal\", \
  \"target\"  : \"server\", \
  \"devTools\": \"dependabot\", \
  \"ci\": \"github-actions\", \ 
  \"gitUsername\": \"\", \
  \"vcs\": \"git\" }"
