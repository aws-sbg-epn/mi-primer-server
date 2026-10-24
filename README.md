# Mi primer servidor en la nube

Página del taller **"Tu primer servidor en la nube"** del AWS Student Builder Group EPN.

La idea es lanzar una instancia EC2, instalar un servidor web y publicar esta página para verla desde cualquier navegador con la IP pública.

## Requisitos

- Una cuenta de AWS
- Una instancia EC2 con Ubuntu Server 24.04 LTS (t3.micro)
- Un security group con el puerto 80 (HTTP) abierto

## Pasos

Conéctate a la instancia con EC2 Instance Connect y ejecuta:

```bash
sudo apt update
sudo apt install -y nginx git
git clone https://github.com/aws-sbg-epn/mi-primer-server.git
sudo cp mi-primer-server/index.html /var/www/html/
```

Personaliza la página con tus datos:

```bash
sudo sed -i 's/Tu Nombre/Tu nombre real/; s/Tu Carrera/Tu carrera/; s/Tu Semestre/Tu semestre/' /var/www/html/index.html
```

Abre `http://TU_IP_PUBLICA` en el navegador. Para saber tu IP:

```bash
curl -s checkip.amazonaws.com
```

## Si no carga

- Usa `http://`, no `https://`
- Revisa que el security group tenga la regla HTTP en el puerto 80
- Reinicia nginx: `sudo systemctl restart nginx`

## Al terminar

Termina la instancia para no consumir créditos. Si creaste una Elastic IP, libérala.
