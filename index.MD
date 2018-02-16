---
title: Facundo Montero
published: true
---

# Welcome to my personal site!

This is the place where I'll post some of my most important projects and any other kind of experiments I do.

## TVHeadend FFMPEG conversion script

# EN

Sometimes, TVHeadend might become a true headache when it comes to setting it up for IPTV. For example, one of the most common problems that you might face are general decoding bugs, unstability and huge difficulties while trying to scan a list (mainly m3u lists).

Browsing the internet reading about this issue, took me to a thread of a forum that finally had a solution. Even though this solution could sound too "heavy" for a homemade system, it actually works!

I'm talking about [this](https://tvheadend.org/boards/5/topics/22969?r=22972#message-22972) post.

Well, enough intro, lets do it!

- Copy the URL of your remote IPTV channels list to the clipboard.
- Download the script to your device, fire up a terminal and run the next command.

`wget https://raw.githubusercontent.com/FacuM/shellscripts/master/tvheadend/workarounds/convertoffmpeg.sh -qO ~/convertoffmpeg.sh`

or

`curl -q https://raw.githubusercontent.com/FacuM/shellscripts/master/tvheadend/workarounds/convertoffmpeg.sh > ~/convertoffmpeg.sh`

### Method 1

###### (if you are going to use a remote list)

`bash ~/convertoffmpeg.sh http://example.com/yourlist.m3u`

### Method 2

###### (if you are going to use a local list)

`bash ~/convertoffmpeg.sh -f /path/to/your/list.m3u`

This will leave a list.m3u file in the working dir from where you ran the script.

---

Once the script is done, simply go to your TVHeadend web interface, go to **Configuration**, **DVB Inputs**, **Networks** and, in the toolbar, hit **Add**. In **Type**, choose **IPTV Automatic Network**.

Now, fill as follows:

- **Network name:** anything you want to name it.
- **Maximum # input streams:** set to your device's threads amount. **IMPORTANT!** *If you don't set it, your kernel will likely crash cause of being unable to process such amount of OOM triggering.*
- **URL:** set to *file:///path/to/the/list/processed/by/the/script.m3u*
- **Accept zero value for TSID:** mark it.
- **Maximum timeout (seconds):** increase to 30 seconds, just in case.

Done, hit **Create**. Now...

- Click or tap the network you just created, and hit **Force scan**. 

The column **Scan queue** will show you the remaining scans and auto-update itself as necessary. Once it reaches **0 (zero)**...

- Switch to the tab **Services**.
- Hit **Map services** and choose **Map all services**.
- In the dialog, tick everything excepting from **Merge same name** *(unless you want to)*.
- Click or tap **Map services**.
- When the bar fills, go back to **Configuration**.
- Go to the tab **Channel / EPG**.

**That's all!** You've successfully configured your TVHeadend instance!

### Buffering issues? Enable _Timeshifting_ in _Recording_ settings.

# ES

A veces, TVheadend puede volverse un verdadero dolor de cabeza en lo que a configurarlo para IPTV se refiere. Por ejemplo, uno de los problemas más comunes que puedes experimentar son los errores generales de decodificación, inestabilidad y grandes difcultades al momento de intentar escanear una lista (principalmente las m3u).

Navegando por internet y leyendo sobre esta falla me llevó al hilo de un foro que tenía la solución final. Incluso teniendo en cuenta que esta solucion puede sonar algo "pesada" para un sistema casero, actualmente, ¡funciona!

Estoy hablando de [este](https://tvheadend.org/boards/5/topics/22969?r=22972#message-22972) post.

Bien, suficiente intro, ¡hagámoslo!

- Copia la URL remota de tu lista de canales de IPTV al portapapeles.
- Descarga el script a tu dispositivo, abre una terminal y ejecuta lo siguiente.

`wget https://raw.githubusercontent.com/FacuM/shellscripts/master/tvheadend/workarounds/convertoffmpeg.sh -qO ~/convertoffmpeg.sh`

o

`curl -q https://raw.githubusercontent.com/FacuM/shellscripts/master/tvheadend/workarounds/convertoffmpeg.sh > ~/convertoffmpeg.sh`

### Método 1

###### (si vas a usar una lista remota)

`bash ~/convertoffmpeg.sh http://ejemplo.com/tulista.m3u`

### Método 2

###### (si vas a usar una lista local)

`bash ~/convertoffmpeg.sh -f /ruta/a/tu/lista.m3u`

Esto dejará un archivo (list.m3u) en el directorio de trabajo desde el cual ejecutaste el script.

---

Una vez que el script haya terminado, simplemente ve a tu interfaz web de TVHeadend, ve a **Configuration**, **DVB Inputs**, **Networks** y, en la barra de herramientas, pulsa **Add**. En **Type**, elige **IPTV Automatic Network**.

Ahora, rellena de la siguiente manera:

- **Network name:** como quieras llamarle.
- **Maximum # input streams:** coloca la cantidad de hilos del procesador de tu dispositivo. **¡IMPORTANTE!** *Si no configuras esto, probablemente, tu núcleo fallará ya que no podrá procesar tal cantidad de solicitudes OOM.*
- **URL:** ingresa *file:///ruta/a/la/lista/procesada/por/el/script.m3u*
- **Accept zero value for TSID:** márcalo.
- **Maximum timeout (seconds):** incrementalo a 30 segundos, sólo por si acaso.

Hecho, pulsa **Create**. Ahora...

- Cliquea o toca en la red que acabas de crear, y pulsa **Force scan**. 

La columna **Scan queue** te mostrará la cantidad de escaneos restantes y se actualizará a sí misma cuando sea necesario. Cuando llegue a **0 (cero)**...

- Cambia a la pestaña **Services**.
- Pulsa **Map services** y elige **Map all services**.
- En el diálogo, marca todo excepto **Merge same name** _(a menos que desees **unir los canales con mismo nombre**)_.
- Cliquea o toca **Map services**.
- Cuando la barra se llene, vuelve a **Configuration**.
- Ve a la pestaña **Channel / EPG**.

**¡Eso es todo!** ¡Configuraste tu instancia de TVHeadend correctamente!