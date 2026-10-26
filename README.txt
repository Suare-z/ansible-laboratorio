=====================================================
LABORATORIO ASO: DESPLIEGUE DE SERVICIOS CON ANSIBLE
=====================================================

a) Link del repositorio de GitHub:
https://github.com/Mariel-MF/ansible-laboratorio.git

b) Pasos para ejecutar el proyecto Ansible:

Como deployar y descargar el archivo zip 

//Ejecuta para descomprimir 
unzip ansible-laboratorio.zip
* PARA INICIAR EL DEPLOY * 
cd ansible-laboratorio
nano inventory.ini   # Aquí cambian la IP, usuario y clave de su máquina destino
deployar
ansible-playbook -i inventory.ini playbook.yml

En la maquina destino debes ejecutar
1. Encender SSH y abrirlo en su firewall
sudo systemctl enable --now sshd
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload

 2. Asegurar que su usuario pueda usar sudo sin quedarse colgado pidiendo password
echo "USERALL=(ALL)NOPASSWD:ALL"|sudotee/etc/sudoers.d/USER

3. Apagar PackageKit para que no bloquee la descarga de paquetes con zypper
sudo systemctl stop packagekit
sudo systemctl mask packagekit

Si tienes varias máquinas en inventory.ini pero solo quieres desplegar a una en específico (ej. solo a clonMariel):

ansible-playbook -i inventory.ini playbook.yml -l clonRamber

Se aumenta en inventory.ini   la cantidad de usuarios 
