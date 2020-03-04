# Configuración de Vagrant para máquinas virtuales del curso de Redis

Las configuraciones que utilizaremos durante el curso se han distribuido en tres carpetas:

* `single_node`
* `replication`
* `cluster`

Todas las máquinas virtuales están basada en Alpine Linix 3.11.3. Puedes ver en cada caso
los scripts de aprovisionamiento en el fichero `Vagrantfile` de cada carpeta.

## single_node

Levanta una máquina virtual que no tiene ninguna configuración especial. Contiene una instalación limpia de Redis.

Para levantar la máquina virtual:

```bash
> cd single_node
single_node > vagrant up --provider virtualbox
```

Para acceder a la máquina virtual:

```bash
single_node > vagrant ssh
```

## replication

Levanta dos máquinas virtuales con una instalación limpia de Redis. **La configuración de replicación
no está incluida en el aprovisionamiento**, esto es precisamente lo que hacemos durante el curso: 
configurar la replicación.

Para levantar ambas máquinas virtuales:

```bash
> cd replication
replication > vagrant up --provider virtualbox
```

Para acceder a alguna de las máquinas virtuales:

```bash
single_node > vagrant ssh master | replica
```


## cluster

Levanta tres máquinas virtuales con una instalación limpia de Redis y una parte de la configuración
del cluster. **La configuración completa no está incluida en el aprovisionamiento**, por lo que este
cluster de Redis no está operativo. Durante el curso terminamos de hacer la configuración completa
de manera manual y usando el comando `redis-cli --cluster`.

Para levantar todas las máquinas virtuales:
```bash
> cd replication
replication > vagrant up --provider virtualbox
```

Para acceder a alguna de las máquinas virtuales:

```bash
single_node > vagrant ssh nodea | nodeb | nodec
```

# Providers

El `box` utilizado en todos los casos es 
[`becorecode/alpinelinux-3.11`](https://app.vagrantup.com/becorecode/boxes/alpinelinux-3.11).
Este box se distribuye con dos `providers`: virtualbox y vmware_fusion. Si prefieres ejecutar
las máquinas virtuales en VMWare, sustituye `--provider virtualbox` en los comandos anteriores.

# Sobre Vagrant

Algunos comandos adicionales para gestionar las máquinas virtuales si no has trabajado antes con Vagrant. 
Estos comando debes ejecutarlos desde la misma carpeta en la que se encuentra el fichero `Vagrantfile`. En nuestro
caso utilizaremos la carpeta `cluster` como ejemplo:

```bash
cluster > vagrant halt
```

Detiene todas las máquinas virtuales definidas en el fichero `Vagrantfile` de la carpeta `cluster` (en este caso
serían `nodea`, `nodeb`y `nodec`.

```bash
cluster > vagrant destroy
```

Destruye (borra del disco duro) todas las máquinas virtuales definidas en el fichero `Vagrantfile` 
de la carpeta `cluster` (en este caso serían `nodea`, `nodeb`y `nodec`.



