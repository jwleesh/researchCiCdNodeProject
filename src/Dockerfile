FROM node:10

COPY /root/package.json ./
RUN npm install

# pm2 설치
RUN npm install -g pm2 

# dockerfile을 실행하는 경로에서 소스 복사
COPY /root/app.js .
COPY /root/ecosystem.config.js .
COPY /root/babel.config.json .

# 아래 포트로 매핑
EXPOSE 8000

RUN npm run build

# pm2-runtime으로 실행 
CMD ["pm2-runtime", "start", "ecosystem.config.js", "--env", "production"]