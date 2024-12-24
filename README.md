# Kubernetes RBAC Tutorial

This repository contains the starter projects for the Kubernetes RBAC Tutorial on YouTube.

## API Calls

Here are commands that you can use to add grades to the Grade Submission API. **Windows Users should use Git Bash**.

```bash
curl -X POST http://localhost:3000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Harry", "subject": "Defense Against Dark Arts", "score": 95}'

curl -X POST http://localhost:3000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Ron", "subject": "Charms", "score": 82}'

curl -X POST http://localhost:3000/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Hermione", "subject": "Potions", "score": 98}'
```

To verify, you can get all grades with:
```bash
curl http://localhost:3000/grades
```