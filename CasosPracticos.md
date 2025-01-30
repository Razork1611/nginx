## Casos Practicos.

**a)** Versión de Nginx instalado.

Para ver la versión de Nginx ponemos el siguiente comando 'dpkg -l | grep nginx'

![image](https://github.com/user-attachments/assets/4e202298-b13d-41b7-94df-a0c15c50bd88)


**b)** Servicio asociado.

Para comprobar el servicio ponemos el comando 'systemctl status nginx'

![image](https://github.com/user-attachments/assets/42b08333-c9fb-4846-ba50-063ea02ffd32)



**c)** Ficheros de configuración.

Los ficheros de configuración principales se encuentran en el archivo: /etc/nginx/nginx.conf

Los ficheros de configuración de sitios habilitados se encuentran en el archivo: /etc/nginx/sites-enabled/default


**d)** Página web por defecto: Modifica la página web que lanza por defecto y personalízala.

Para cambiar esto tenemos que entrar en el fichero de la imagen y lo personalizamos a nuestro gusto.

![image](https://github.com/user-attachments/assets/a891b5d3-00f5-477b-9637-d53ad0699fc1)

Luego de eso, reiniciamos el nginx con el comando 'sudo systemctl restart nginx' y volvemos a buscarlo en el buscador.

![image](https://github.com/user-attachments/assets/526a4c9a-8457-4807-b068-e37a4f546e4a)


**e)** Virtual Hosting: Queremos que nuestro servidor web ofrezca dos sitios web.

Primero, creamos los directorios para cada sitio web. 'sudo mkdir -p /var/www/web1' / 'sudo mkdir -p /var/www/web2'

![image](https://github.com/user-attachments/assets/67079ec4-063a-4024-acde-b02d79ad4f36)

Segundo, creamos una página de inicio para cada uno, usando los siguientes comandos: echo '<h1>Bienvenidos a la página web1</h1>' | sudo tee /var/www/web1/index.html             echo '<h1>Bienvenidos a la página web2</h1>' | sudo tee /var/www/web2/index.html

![image](https://github.com/user-attachments/assets/55cae44f-3fb2-4409-be5c-e6b6a02adaf1)

Tercero, creamos los archivos de configuración para cada sitio web usamos los siguientes comandos para empezar a crear el archivo y ponemos en cada uno de ellos lo mismo idénticamente que en las imágenes. sudo nano /etc/nginx/sites-available/web1            sudo nano /etc/nginx/sites-available/web2


![image](https://github.com/user-attachments/assets/35628d14-f629-4dc3-b07c-6c965d2336be)

![image](https://github.com/user-attachments/assets/195e7984-5e36-492b-9b8a-f2ceaf1b7616)

Cuarto, habilitamos los sitios y reiniciamos Nginx.

Usamos los comandos de abajo para habilitarlos

sudo ln -s /etc/nginx/sites-available/web1 /etc/nginx/sites-enabled/
sudo ln -s /etc/nginx/sites-available/web2 /etc/nginx/sites-enabled/

Usamos el siguiente comando para reiniciar el servicio 'sudo systemctl restart nginx'

Quinto, simular los dominios en el archivo /etc/hosts

Entramos al archivo con un nano y ponemos las 2 líneas en las que salen web1 y web2 al igual que en la imagen.

![image](https://github.com/user-attachments/assets/98ac897d-81fd-4de1-9dfa-816ac131e1c3)

Sexto, probar a entrar a los sitios web, para ello entramos al buscador y ponemos www.web1.org y despues www.web2.org

![image](https://github.com/user-attachments/assets/c4f97c39-4ac4-4053-ab31-90f4aeb04777)

![image](https://github.com/user-attachments/assets/e59b0feb-6a52-4ed8-be94-c0d80af341b2)


**f)** Autentificación, Autorización y Control de acceso: queremos acceder a la web 1 desde una red interna y externa, y a la web2 solo desde una red interna.

Para este ejercicio en el fichero  > nano /etc/nginx/sites-available/web1 <  no habría que cambiar nada, en cambio en el > nano /etc/nginx/sites-available/web2 < si habría que cambiar para que no se pueda acceder desde una red externa, para ello entramos en él y aplicamos lo mismo que en la foto a continuación.

![image](https://github.com/user-attachments/assets/ee86e487-2f18-410d-83f6-4698090fc80a)


Aplicamos lo cambios y reiniciamos el nginx

aplicar los cambios: sudo nginx -t
Reiniciar: sudo systemctl restart nginx

Desde la red interna.

![image](https://github.com/user-attachments/assets/efe0fd93-6adc-439e-9ec5-5254a6c8cac5)

Desde la red externa.

Me da error.


**g)** Autentificación, Autorización y Control de acceso: Configura una autenticación básica. Sólo pueden acceder usuarios válidos.

Entramos en el archivo de web1 > nano /etc/nginx/sites-available/web1 < y lo modificamos al igual que en la foto a continuación

![image](https://github.com/user-attachments/assets/5297f6ec-e0d7-4c50-8569-27b3e2d81e0d)

aplicar los cambios: sudo nginx -t
Reiniciar: sudo systemctl restart nginx

Intentamos buscarla poniendo: http://www.web1.org/privado

![image](https://github.com/user-attachments/assets/f610a988-d3b6-49e0-b02d-4576ddb5a4fd)

si fallamos nos sale esto.

![image](https://github.com/user-attachments/assets/eaab8dc1-8061-48a7-b009-3e81b3033cfd)


**h)** Autentificación, Autorización y Control de acceso: Desde la red externa pide autorización y desde la red interna NO.

Entramos en el archivo de web1 > nano /etc/nginx/sites-available/web1 < y lo modificamos al igual que en la foto a continuación.


![image](https://github.com/user-attachments/assets/a5b38755-6649-4102-a4b1-8e12e556c742)

aplicar los cambios: sudo nginx -t
Reiniciar: sudo systemctl restart nginx


**i)** Seguridad: Configura el sitio virtual www.web1.org para que el acceso sea seguro, emplear el HTTPS.

Entramos en el archivo de web1 > nano /etc/nginx/sites-available/web1 < y lo modificamos al igual que en la foto a continuación.

![image](https://github.com/user-attachments/assets/1f3fa3ef-409e-410d-91ad-c75a0185d282)



