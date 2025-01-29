## Casos Practicos.

**a)** Versión de Nginx instalado.

  La versión que e intalado de Nginx es la **1.26.2** ya que es la mas estable que me aparecía en la página.


**b)** Servicio asociado.

  En mi caso **no** es un servicio ya que lo inicio manuálmente. 
  ¿Cómo lo se? 
  Para saber esto precionamos la tecla wondows + R > ponemos services.msc > y buscamos un servicio llamado nginx o nginx service, si no lo encointramos como en mi caso nos damos cuenta de que no lo tines como un servicio.


**c)** Ficheros de configuración.

  Estos ficheros los encontramos en la **misma** carpeta que descomprimimos antes con el nombre de 'conf', solo hay que tener ubicado donde lo descomprimimos.


**d)** Página web por defecto: Modifica la página web que lanza por defecto y personalízala.

  Para realizar esto tenemos que entrar en los fichero de nginx que es donde descomprimimos anteriormente, buscmaos la carpeta llamada *html* y entramos en ella > abrimos el archo **index** con visual studio por ejemplo y lo modificamso a nuestro justo > guardamos >  reiniciamos el nginx > y lo volmemos a buscar en el buscador y ya estaría todo listo.
![image](https://github.com/user-attachments/assets/91ca19a2-d30e-4504-b61d-4b2d0ca9bf98)


**e)** Virtual Hosting: Queremos que nuestro servidor web ofrezca dos sitios web
