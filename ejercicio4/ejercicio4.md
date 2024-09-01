# EJERCICIOS EVASIÓN DE WINDOWS DEFENDER
## Prerrequisitos
* Kali Linux
* Windows 10 Evasion
## Ejercicio - Metasploit, Windows UAC y Windows Defender
* Entrar en el entorno gráfico de Windows 10 Evasion con el usuario user1, habilitar Windows UAC eligiendo nivel predeterminado y deshabilitar Windows
Defender.

![alt text](image.png)

deshabilitar windows defender https://aboutdevice.com/how-to-enable-or-disable-windows-defender/?authuser=1

![alt text](image-1.png)

* Crear un troyano y transferirlo al escritorio del usuario user1 en el sistema Windows 10 Evasion.

![alt text](image-3.png)

![alt text](image-2.png)
* Utilizar un exploit multi/handler para obtener un meterpreter reverso.

![alt text](image-4.png)
* En la sesión, abrir una shell y comprobar los permisos del usuario user1 y los grupos a los que pertenece para después corroborar si pertenece a algún grupo
con privilegios.
![alt text](image-5.png)
![alt text](image-6.png)
![alt text](image-7.png)
* Intentar elevar privilegios a NT Authority\System con comando de meterpreter. En caso de no funcionar la elevación con meterpreter utiliza algún módulo que
te permita elevar privilegios haciendo un bypass del Windows UAC.

```bash
meterpreter > run post/multi/recon/local_exploit_suggester 
```
![alt text](../Evacion_elinar_log/image-12.png)
* Crear un backdoor persistente y reiniciar el sistema Windows 10 Evasion para obtener una sesión que demuestre que funciona.

![alt text](../ejercicio3/image-9.png)