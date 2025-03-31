# Ejercicio de Tuneles Proxy

En este ejercicio veremos proteger nuestra identidad cuando navegamos

Necesitaremos al menos: 2 VPS

## Instalamosy configuramos Proxychains en nuestor hosts

1. Instalamos proxychains

```bash
sudo apt install proxychains
```
2. Configuramos el archivo /etc/proxychains.conf y añadimmos

```plaintext
dynamic_chain
proxy_dns
socks5  127.0.0.1 7777
socks5  127.0.0.1 7778
socks5  127.0.0.1 7779
```
3. En esta configuración vemos 

## Configurar los VPS

1. Creamos los tuneles dinamicos 

```bash
ssh -D 7777 root@172.233.116.217
```

Dentro del VPS

2. Añadimos otro tunel dinamico

```bash
ssh -D 7778 root@172.233.116.44
```

Dentro VPS

3. Añadimos otro tunel dinamico

```bash
ssh -D 7779 root@172.233.116.45
```

## Comprobar que este funcionado correctamente

1. Podemos comprobar que funciona ejecutando este comando en el hosts

```bash
proxychains curl ifconfig.me
```
