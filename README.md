# Current Page template layouting
## Technologies and tools:

- Haproxy
  - Proxy setup
- nginx
  - Proxy setup
- Dockerfile 
  - Install the npm 


## HAPROXY is to Create Proxy Server

### Create the Stack:
- Deploy the Stack by specifying the stack file and name of our stack

```
# docker swarm init --advertise-addr <IP-Address>
# docker stack deploy -c docker-stack.yml node

#### OutPut
Creating network node_nodenet
Creating service node_proxy
Creating service node_app
```

## List the Services in the Stack:

``` # docker stack ps node ```

#### OutPut
```
ID            NAME          IMAGE                       NODE                   DESIRED STATE  CURRENT STATE           ERROR  PORTS
lyxcfgstvtd1  node_app.1    shariftest/testswarm:04     localhost.localdomain  Running        Running 40 seconds ago
ywxbm3m1o1dk  node_proxy.1  dockercloud/haproxy:latest  localhost.localdomain  Running        Running 42 seconds ago
o89n77szaehv  node_app.2    shariftest/testswarm:04     localhost.localdomain  Running        Running 40 seconds ago
utpw6giks83n  node_app.3    shariftest/testswarm:04     localhost.localdomain  Running        Running 40 seconds ago
```
#### Scaling:

Scale our Application down to 5 replica's

``` # docker service scale node-app=5 ```

#### Cleanup:

Remove the Stack:

``` 
#docker stack rm node 

Removing service node_proxy
Removing service node_app
Removing network node_nodenet
```


# nginx is to Create Proxy Server

Create the Stack:
Deploy the Stack by specifying the stack file and name of our stack

```
# docker swarm init --advertise-addr <IP-Address>
# docker stack deploy -c docker-stack.yml node
```

#### OutPut

```
Creating network node_nodenet
Creating service node_proxy
Creating service node_app
```

## List the Services in the Stack:

```
# docker stack ps  node
```

## OutPut:

```
ID            NAME          IMAGE                    NODE                   DESIRED STATE  CURRENT STATE             ERROR  PORTS
1qxrg2hazypi  node_proxy.1  nginx:latest             localhost.localdomain  Running        Preparing 12 seconds ago
wsqwy8ti7ksm  node_app.1    shariftest/testswarm:04  localhost.localdomain  Running        Running 13 seconds ago
```

### Scaling:

- Scale our Application down to 5 replica's

``` # docker service scale node-app=5 ```

### Cleanup: Remove the Stack

``` # docker stack rm node ``` 

## OutPut:

```
Removing service node_proxy
Removing service node_app
Removing network node_nodenet
```


