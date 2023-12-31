# RASA
The project was forked from [rasa-bot](https://github.com/Chunshan-Theta/Mentor-MBTI).

This is a mentor bot that can help to introduce the discussion event and teach the user how to discussion, built with the rasa framework and LLM. 
We design ideas from ChatDev and try to build a step-by-step framework. 

# Design

```
actions:
- action_ActionAskGpt
- action_ActionGoNext

intents:
- confirm
- faq

```

### UI Demo

![img](./doc/demo.png)



# Service

### Start Service
1. Update OpenAI API Key in docker-compose.yml
2. Update Domain name in botroom/App.js:23 -> (frontend)
3. up service with docker-compose
```
docker-compose up
```
4. go to weeb
```
http://127.0.0.1
```

### Ask bot by cmd
```
curl -o output.txt -X POST -H "Content-Type: application/json; charset=UTF-8" -d '{"sender": "user-001","message": "早安"}'  http://127.0.0.1:5005/webhooks/rest/webhook && echo -e "$(<output.txt)"
curl -o output.txt -X POST -H "Content-Type: application/json; charset=UTF-8" -d '{"sender": "user-001","message": "昆蟲是甚麼?"}'  http://127.0.0.1:5005/webhooks/rest/webhook && echo -e "$(<output.txt)"
curl -o output.txt -X POST -H "Content-Type: application/json; charset=UTF-8" -d '{"sender": "user-001","message": "是的"}'  http://127.0.0.1:5005/webhooks/rest/webhook && echo -e "$(<output.txt)"
```


# Testing
- with rasa tests
```
docker-compose up test-model
```

- interactive
```

docker-compose up rasa-actionServer

```

- Testing In docker Container
```
docker run -it -v ./actionsServer:/app --entrypoint=/bin/bash rasa/rasa:3.6.6-full
```