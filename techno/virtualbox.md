# Augmenter la taille d'un disque de taille fixe

Pour augmenter la taille d'un disque de taille fixe il faut faire les étapes suivantes:
- cloner un disque en creant une copie avec taille dynamique
`.\VBoxManage.exe  clonemedium disk "C:\Users\dias\VirtualBox VMs\agri-factory\agri-factory.vdi" "C:\Users\dias\VirtualBox VMs\agri-factory\b-up\agri-factory-dyn.vdi" -variant Standard`

- augmenter la taille du disque à 60 000Mo (dans la commande ci dessous)
`.\VBoxManage.exe  modifyhd "C:\Users\dias\VirtualBox VMs\agri-factory\b-up\agri-factory-dyn.vdi" --resize 60000`

- cloner le disque en créant un disque de taille fixe
`.\VBoxManage.exe  clonemedium disk "C:\Users\dias\VirtualBox VMs\agri-factory\b-up\agri-factory-dyn.vdi" "C:\Users\dias\VirtualBox VMs\agri-factory\agri-factory.vdi" -variant Fixed`

- lancer gparted depuis la vm pour augmenter la taille de la partition
