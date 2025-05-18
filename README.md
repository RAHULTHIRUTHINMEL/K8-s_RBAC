# Kubernetes RBAC Tutorial

This repo contains all the code needed to follow along with our **[YouTube Tutorial](https://youtu.be/hWj4y3Ok9Tg)**

## API Calls

Here are commands that you can use to add grades to the Grade Submission API. **Windows Users should use Git Bash**.

```bash
curl -X POST http://localhost:31000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Harry", "subject": "Defense Against Dark Arts", "score": 95}'

curl -X POST http://localhost:31000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Ron", "subject": "Charms", "score": 82}'

curl -X POST http://localhost:31000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Hermione", "subject": "Potions", "score": 98}'
```

To verify, you can get all grades with:
```bash
curl http://localhost:31000/grades
```

## API Calls with Authentication

Here are commands that you can use to add grades to the Grade Submission API. **Windows Users should use Git Bash**.

```bash
curl -k -X POST https://localhost:31000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Harry", "subject": "Defense Against Dark Arts", "score": 95}' -H "Authorization: Bearer $TOKEN"

curl -k -X POST https://localhost:31000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Ron", "subject": "Charms", "score": 82}' -H "Authorization: Bearer $TOKEN"

curl -k -X POST https://localhost:31000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Hermione", "subject": "Potions", "score": 98}' -H "Authorization: Bearer $TOKEN"
```

To verify, you can get all grades with:
```bash
curl -k https://localhost:31000/grades -H "Authorization: Bearer $TOKEN"
```
## Become a Cloud and DevOps Engineer

Learn every tool that matters: https://rayanslim.com
