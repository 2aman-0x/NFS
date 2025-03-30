# Network File System

A network protocol for disributed file system. Using this, a user on the client computer can access the files on server side like as they are accessing locally.  

## NFS Configuration setup

Setup process in two parts

- Client side Configuration
- Server side Configuration

## Server side Configuration

- to install NFS packages
```yum install nfs-utils libnfsidmap```

- Enable and start the NFS Services
```systemctl enable rpcbind, nfs-server```  
```systemctl start rpcbind.service nfs-server.service rpc-statd.service nfs-idmapd.service```

- Create a directory for NFS and give all the permissions
```mkdire /server/apps```  
```chmod 777 /server/apps```

- modify the ```/etc/exports``` file and add new shared filesystem
```/apps IP_address(rw,sync,no_root_squash)```

- ```exportfs -rv```

---

## Client side Configuration

- To install NFS packages
```yum install nfs-utils rpcbind```

- Enable and start the rpcbind service
```systemctl enable rpcbind```

- To stop the firewall (both serverside and clientside)
```systemctl stop firewall/iptables```

- Show mount from NSF Server
```showmount -e SERVERside_IP```

- Create a mount point (a directory)
```cd /```  
```mkdir /mnt/apps```

- Mount the NFS file system
```mount SERVER_IP:/server/apps /mnt/apps```

- How to check mounted or not?
```df -h```




