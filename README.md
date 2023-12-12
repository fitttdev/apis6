# API Gateway with APISIX

1. APISIX Dashboard
  http://localhost:9000/
  username = admin
  password = admin

2. Will need to add route and upsteam
  route = /api/nest-be

3. /api needs to proxy to api-gateway running on 9080 and the accordingly pass it to nest-be

Problem: curl localhost/api/nest-be gives 404.
