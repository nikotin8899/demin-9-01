### Задание 1

Разверните топологию из лекции и выполните установку и настройку сервиса Keepalived. 

```
vrrp_instance test {

state "name_mode"

interface "name_interface"

virtual_router_id "number id"

priority "number priority"

advert_int "number advert"

authentication {

auth_type "auth type"

auth_pass "password"

}

unicast_peer {

"ip address host"

}

virtual_ipaddress {

"ip address host" dev "interface" label "interface":vip

}

}

```

*В качестве решения предоставьте:*   
*- рабочую конфигурацию обеих нод, оформленную как блок кода в вашем md-файле;*   

vrrp_instance failover_test {


state MASTER


interface enp0s8


virtual_router_id 10


priority 110


advert_int 4


authentication {


auth_type AH


auth_pass 1111


}


unicast_peer {


192.168.0.1


}


	virtual_ipaddress {

 
	192.168.0.50 dev enp0s8 label enp0s8:vip

 
}


}




vrrp_instance failover_test {


state BACKUP


interface enp0s8


virtual_router_id 10


priority 110


advert_int 4


authentication {


auth_type AH


auth_pass 1111


}


unicast_peer {


192.168.0.2


}



	virtual_ipaddress {

 
	192.168.0.50 dev enp0s8 label enp0s8:vip

 
}


}




*- скриншоты статуса сервисов, на которых видно, что одна нода перешла в MASTER, а вторая в BACKUP state.*
![image](https://github.com/nikotin8899/home-lab/assets/56605975/ddfe6882-4bf2-4b09-8ed8-1edc7cef1502)

![image](https://github.com/nikotin8899/home-lab/assets/56605975/1cac57fe-575f-456b-8a03-1a86a1f6b63f)


