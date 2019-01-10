# Current Page template layouting

## HAPROXY is to Create Proxy Server
``` 
cd haproxy/
ls
docker-stack.yml
```
### Create the Stack:
- Deploy the Stack by specifying the stack file and name of our stack

```
docker swarm init --advertise-addr <IP-Address>
docker stack deploy -c docker-stack.yml node

#### OutPut
Creating network node_nodenet
Creating service node_proxy
Creating service node_app
```
`docker stack ps node`

#### OutPut
```
ID            NAME          IMAGE                       NODE                   DESIRED STATE  CURRENT STATE           ERROR  PORTS
lyxcfgstvtd1  node_app.1    shariftest/testswarm:04     localhost.localdomain  Running        Running 40 seconds ago
ywxbm3m1o1dk  node_proxy.1  dockercloud/haproxy:latest  localhost.localdomain  Running        Running 42 seconds ago
o89n77szaehv  node_app.2    shariftest/testswarm:04     localhost.localdomain  Running        Running 40 seconds ago
utpw6giks83n  node_app.3    shariftest/testswarm:04     localhost.localdomain  Running        Running 40 seconds ago
```


Create the web app

Technologies and tools:

- Dockerfile 
  - Install the npm 
- docker-compose
  - Container creation 
- main.sh
  - runs the docker-compose
  - checks the docker registery login
  - It creates the Tag
  - It pusshed the new images to registery.
  
# RUN the shell script

./main.sh
