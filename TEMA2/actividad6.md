# Master DNS

Para hacer esta práctica necesitaremos un servidor que actuará como master, donde haremos la malloria de la confiuración. Primero vamos a named.conf.options y modificamos la recursión:

<img width="243" height="127" alt="image" src="https://github.com/user-attachments/assets/392f019c-eb63-4a65-8d31-caf2290c2486" />

Después vamos a editar el named.conf.local para indicarle que es el máster de la zona marisma.intranet y de la inversa. Lo dejaremos así:

<img width="688" height="231" alt="image" src="https://github.com/user-attachments/assets/6162fb27-1ad0-4acf-bae2-2535c2871aa9" />

El siguiente paso es crear el archivo de zona directa. Aquí definiremos los nombres que pide el ejercicio (ns1, ftp1, mail1, www, etc.). Vamos a hacer una copia de la plantilla vacía y la modificaremos:

<img width="699" height="355" alt="image" src="https://github.com/user-attachments/assets/e055a7fb-67a8-4a9b-80c8-df5de9cf749f" />

Ahora creremos el archivo de la zona inversa. Lo mismo, copiamos uno vacío y lo editamos:

<img width="685" height="290" alt="image" src="https://github.com/user-attachments/assets/aa2d72ea-5ab5-40d8-baef-e617becdabd8" />

Vamos a comprobar que la sintaxis de todos nuestros archivos están bien. Usaremos named-checkconf y named-checkzone pasandole el nombre de los archivos recién creados:

<img width="851" height="87" alt="image" src="https://github.com/user-attachments/assets/739ebcce-4806-4001-b403-6fef0c046275" />

Una vez comprobado que todo está OK, reiniciamos:

<img width="1064" height="407" alt="image" src="https://github.com/user-attachments/assets/372d40bd-bc8e-4900-86de-61063dfdd97f" />

Ahora nos iremos al segundo servidor. Vamos a configurarlo simplemente editando el resolve.conf, añadiendo el nameserver con la IP del servidor máster y diciendole que busque la zona marisma.intranet:

<img width="248" height="84" alt="image" src="https://github.com/user-attachments/assets/bb21cff4-3f27-46c7-adcf-03d1d5678c60" />

Y ahora hacemos las comprobaciones:

<img width="584" height="183" alt="image" src="https://github.com/user-attachments/assets/3f3c0658-6214-467f-8f01-e3457055cb00" />

<img width="535" height="426" alt="image" src="https://github.com/user-attachments/assets/63860d96-ee53-4b7d-a04a-1a0e70c07e39" />

<img width="557" height="449" alt="image" src="https://github.com/user-attachments/assets/b54e597d-7f20-472e-a94a-2d2e047dc6b2" />

<img width="919" height="368" alt="image" src="https://github.com/user-attachments/assets/f31c7809-61ff-43be-9216-b908a3ef5b95" />

<img width="535" height="414" alt="image" src="https://github.com/user-attachments/assets/a514ebc0-5b1c-4f92-be3b-28b8f486d7ab" />
