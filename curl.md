# Send Parameter

```
curl -d "param1=value1&param2=value2" ...
curl -X {POST/GET/...}
```

# Set Content-Type

```
-H "Content-Type:application/json"
```

# Send JSON Body

    curl -X POST -H "Content-Type: application/json" -d '{"username":"xyz","password":"xyz"}' http://localhost:3000/api/login
