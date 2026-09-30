Para empezar a utilizar QNX 8.0 en QEMU, la forma más rápida y oficial es mediante el paquete QSTI (Quick Start Target Image) proporcionado por BlackBerry a través de la iniciativa QNX Everywhere. Este paquete incluye un entorno de escritorio completo (XFCE) preconfigurado para que puedas compilar tus aplicaciones directamente dentro de la máquina virtual sin lidiar con configuraciones complejas de compilación cruzada.
Sigue estos pasos prácticos desde tu terminal de Linux (preferiblemente Ubuntu):
1. Preparar las dependencias del Host
Asegúrate de tener instalado QEMU y sus herramientas asociadas en tu sistema operativo principal:
bash
# Para Ubuntu 22.04 / 24.04 LTS
sudo apt install qemu-system qemu-utils qemu-kvm libvirt-daemon-system bridge-utils
Usa el código con precaución.
2. Descargar la imagen desde QNX Software Center (QSC)
1. Abre el QNX Software Center en tu computadora.
2. Ve a la pestaña Available y busca quick start.
3. Instala el paquete llamado "QNX SDP 8.0 Quick Start Target Image for QEMU".
Los archivos se descargarán por defecto en la ruta de instalación de tu SDK, usualmente dentro de ~/qnx800/images/qemu/.
3. Desempaquetar la imagen
QNX distribuye la imagen segmentada en varias partes. Ejecuta el script automatizado para unificarlas:
bash
cd ~/qnx800/images/qemu
./unpack_qemu_image.sh
Usa el código con precaución.
Esto creará una nueva carpeta interna (por ejemplo, ~/qnx800/images/qemu/qemu) con los archivos listos para arrancar.
4. Inicializar el entorno y arrancar QEMU
Antes de lanzar el comando de ejecución, debes cargar las variables de entorno de QNX en tu terminal actual:
bash
# 1. Cargar las variables de entorno de QNX SDP
cd ~/qnx800
source qnxsdp-env.sh

# 2. Ir al directorio de la imagen desempaquetada
cd ~/qnx800/images/qemu/qemu

# 3. Lanzar la máquina virtual con la herramienta oficial
mkqnximage --run
Usa el código con precaución.
Qué verás al iniciar
El comando mkqnximage --run levantará una máquina virtual con 8 CPUs y 4 GB de RAM asignados por defecto. En la pantalla gráfica de QEMU aparecerá el asistente de bienvenida (demolauncher) donde podrás interactuar directamente con:
• Una terminal nativa de QNX.
• El entorno QNX Developer Desktop.
• Aplicaciones de prueba y demos gráficas en OpenGL/GTK.
Tips útiles para la consola
• Consola Serie: La ventana de la terminal de Linux desde donde ejecutaste el comando se transformará automáticamente en una consola serie interactiva ligada al sistema invitado.
• Obtener la IP de la VM: Si necesitas conectarte mediante SSH o herramientas de depuración externas, ejecuta mkqnximage --getip desde otra terminal dentro de la misma carpeta.
• Salir de QEMU: Para apagar la máquina virtual de golpe, presiona las teclas Ctrl + A y luego X dentro de la terminal serie, o cierra directamente la ventana gráfica de QEMU.
¿Pudiste completar la instalación del QNX Software Center, o necesitas ayuda para configurar tu primer hola mundo en C desde el compilador interno qcc de la máquina virtual?
