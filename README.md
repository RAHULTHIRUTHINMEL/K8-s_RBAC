# Kubernetes RBAC 

the yaml file rade-submission-api-deployment contains two containers. kube-rbac-proxy is the side car container which controls the access to the grade-api container. 

we get an authorization error after inpleteing this setup

create a service account in rbac.yaml

to make it connectd to the service account we need token, and is created by usins secret 
   "annotations:   kubernetes.io/service-account.name: grade-sa   # This annotation links the secret to theservice account
type: kubernetes.io/service-account-token "


we get the encoded secret in .data.token like "kl get secrets grade-sa-token -n grade-demo -o jsonpath="{.data.token}" | base64 -d   "

still ater trying to curl -k https://localhost:31000/grades -H "Authorization: Bearer $TOKEN" tis wont succed it(kube-prox) says the failed to create token review with kubernetes api. we need then to create another service account for this container(kube-rbac-proxy) that is the file 05-rbac...yaml.and add this into the deployment file spec.template.spec.serviceaacount. this way we will succed. 

--now how to permit this service account with the roles agievn to it, cause we have for the ease of working given admin rights to this service account. 


---continued.


in the second part we have modified the 05-rbac.....yaml to create our custom cluster role and cluster role binding. 


that might be deprecated in the newly committed file. 

for insights watch this video https://www.youtube.com/watch?v=hWj4y3Ok9Tg&t=321s

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

