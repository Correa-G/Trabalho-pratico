# Trabalho-pratico

Trabalho prático do Grau B de Roteamento em Redes de Computadores

## Topologia
![alt text](https://raw.githubusercontent.com/Correa-G/Trabalho-pratico/master/topologia.png)

## Configuração da topologia

Definidos 3 protocolos para a topologia: EIGRP, OSFP e RIP.

### EIGRP
4 Routers com portas Gigabit Ethernet

#### Routers A1, A2, A3:
```
Router>Enable
Router#configure terminal
Router(config)#router eigrp 100
Router(config-router)#network IP-REDE MASCARA-DE-REDE (repetir de acordo com a quantidade de interfaces de rede)
Router(config-router)#exit
Router(config)#exit
```

#### Router A0:

Interface interna:
```
Router>Enable
Router#configure terminal
Router(config)#router eigrp 100
Router(config-router)#network IP-REDE MASCARA-DE-REDE
Router(config-router)#redistribute bgp 100
Router(config-router)#exit
Router(config)#
```
Interface Externa:
```
Router(config)#router bgp 100
Router(config-router)#neighbor IP ROUTER C0 remote-as 200
Router(config-router)#neighbor IP ROUTER B0 remote-as 300
Router(config-router)#redistribute eigrp 100
Router(config-router)#exit
Router(config)#exit
```

### OSPF
5 Routers com portas Gigabit Ethernet

#### Routers C1, C2, C3, C4:
```
Router>Enable
Router#configure terminal
Router(config)#router ospf 1
Router(config-router)#network IP-REDE MASCARA-DE-REDE area 0 (repetir de acordo com a quantidade de interfaces de rede)
Router(config-router)#exit
Router(config)#exit
```

#### Router C0:

Interface interna:
```
Router>Enable
Router#configure terminal
Router(config)#router ospf 1
Router(config-router)#network IP-REDE MASCARA-DE-REDE area 0 (repetir de acordo com a quantidade de interfaces de rede)
Router(config-router)#redistribute bgp 200
Router(config-router)#exit
Router(config)#
```
Interface Externa:
```
Router(config)#router bgp 200
Router(config-router)#neighbor IP ROUTER A0 remote-as 100
Router(config-router)#redistribute ospf 1
Router(config-router)#exit
Router(config)#exit
```


### RIP
3 Routers com portas Gigabit Ethernet

#### Routers B1, B2:
```
Router>Enable
Router#configure terminal
Router(config)#router rip
Router(config-router)#network IP-REDE (repetir de acordo com a quantidade de interfaces de rede)
Router(config-router)#exit
Router(config)#
```

#### Router C0:

Interface interna:
```
Router>Enable
Router#configure terminal
Router(config)#router rip
Router(config-router)#network IP-REDE (repetir de acordo com a quantidade de interfaces de rede)
Router(config-router)#exit
Router(config)#
```
Interface Externa:
```
Router(config)#router bgp 300
Router(config-router)#neighbor IP ROUTER A0 remote-as 100
Router(config-router)#exit
Router(config)#exit
```
