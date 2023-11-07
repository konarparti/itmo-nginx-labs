### Вход в консоль docker контейнера с nginx
```powershell
docker exec -it itmo_nginx bin/bash/
```

### Конфиг nginx
```bash
cd etc/nginx/
cat nginx.conf
```
Изменять nginx.conf не стоит, лучше менять conf.d

### Переменная в пути конфига nginx
```nginx
location '/?<destination>' {
        return http://localhost:9000/$1
    }
```

### NGINX для раздачи статики
Надо указать в конфиге путь к статике
```nginx
root /www/server1/
```

### Балансировка по ip адресам серверов через upstream
```nginx
upstream app1{
    10.10.10.10:8080
    10.10.10.11:8080;
}
```

### Директива для проксирования
```nginx
proxy_pass http://app1:9000/$1
```