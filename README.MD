# chatgpt-web
### 使用GPT-3.5中的text-davinci-003模型，利用OpenAI API实现简单HTML网页版在线聊天（基于[此项目](https://github.com/AlliotTech/chatgpt-web)调整而来）
#### ![G L%7VF I~{@83}SVRI_WPN](https://user-images.githubusercontent.com/58287293/207792987-a0a781df-8273-4148-a369-aa4a2379686a.png)（重要）ChatGPT与GPT-
## 部署
### 获取OpenAI API KEY
- 建议参考[此教程](https://blog.csdn.net/hekaiyou/article/details/128303729)获取
### 配置
#### 从源码配置
- 请参考原作者[github](https://github.com/AlliotTech/chatgpt-web)
#### 使用Docker Compose
- 下

- 新建`docker-compose.yml`配置文件，粘贴以下内容并保存，放在与`chat.html`文件相同的目录下
```bash
version: '3'
services:
  chatgpt:
    image: sheepgreen/chatgpt-web #如果是arm架构，需要改成chatgpt-web:arm
    container_name: webchat
    environment:
      - OPENAI_API_KEY=前面你获取到的OpenAI API KEY
    volumes:
      - ./chat.html:/chatgpt-web/templates/chat.html
    ports:
      - "8888:80" #80为容器内部端口，不可更改；8888为外部映射端口，可自行更改
    restart: always
```
- 输入`docker-compose up -d`即启动成功
## 注意事项
- 访问地址为http://ip:port/chat
- 修改`chat.html`文件后，需要docker restart webchat才能生效
