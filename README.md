# Terraform 

```
https://www.terraform.io/downloads.html
```
```
terraform.zip 
```
unzip 
```
sudo mv /usr/local/bin
```

```
terraform -v 
```

```
mkdir terraform1
```

```
vi main.tf
```


Proveedor y aprovicionador 

### Inicializar 
```
terraform init
```
### Planificar
```
terraform plan
```
### Aplicar 
```
terraform apply
```
### Destruir 
```
terraform destroy
```

```
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "2.13.0"
    }
  }
}

provider "docker" {
  host = "unix:///var/run/docker.sock"
}

# Pulls the image
resource "docker_image" "ubuntu" {
  name = "ubuntu:latest"
}

# Create a container
resource "docker_container" "ubuntu" {
  image = "ubuntu:18.04"
  name = "ubuntu1"
  command = ["/bin/bash","-c","while true; do sleepp 60000; done"]
  provisioner "local-exec"{
    command = "echo ${docker_container.ubuntu.network_data[0].ip_address} >> inventario.txt"
    }
    
}
```
