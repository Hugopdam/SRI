# Actividad 9

**1. Crea cinco usuarios: usuario1, usuario2, usuario3, usuario4, usuario5.**

<img width="983" height="82" alt="image" src="https://github.com/user-attachments/assets/dfd028d7-b204-41cc-8297-6063db21fe7d" />

Repetimos hasta que tengamos los 5:  
<img width="804" height="114" alt="image" src="https://github.com/user-attachments/assets/2758ea8c-b42b-4e4c-84e5-7cc63d0f86ea" />

**2. Crea dos grupos de usuarios, el primero formado por usuario1 y usuario2; y el segundo por el resto de usuarios.**

<img width="867" height="30" alt="image" src="https://github.com/user-attachments/assets/bd9f5768-ddcb-4521-80d8-a253ec180dbf" />  
<img width="769" height="72" alt="image" src="https://github.com/user-attachments/assets/f2c73070-0747-4239-ab27-7028f72eae16" />  

**3. Crea un directorio llamado privado1 que permita el acceso a todos los usuarios.**

<img width="885" height="38" alt="image" src="https://github.com/user-attachments/assets/fea406c4-1f78-4cbc-98a7-682bbbff4ebe" />

Ahora nos vamos a apache2.conf y ponemos esto:  
<img width="381" height="128" alt="image" src="https://github.com/user-attachments/assets/1c70aa27-eb23-4be8-99bd-0118082d3f0e" />

Y comprobamos:  
<img width="843" height="348" alt="image" src="https://github.com/user-attachments/assets/1208d2fa-7497-4d33-b5c4-881340d8b62f" />


**4. Crea un directorio llamado privado2 que permita el acceso sólo a los usuarios del grupo1.**

Ponemos la siguiente directiva:  
<img width="442" height="140" alt="image" src="https://github.com/user-attachments/assets/7030ee29-6239-45f0-bdf6-437c67d72f0c" />  

Si iniciamos con usuarios del grupo1 veremos que funciona, pero con usuarios del grupo2 nos dira esto:  
<img width="1204" height="216" alt="image" src="https://github.com/user-attachments/assets/4fb3ea48-87b2-4352-85a9-aeee85e4d364" />

**6. En el directorio privado2 haz que sólo sea accesible desde el localhost, y estudia cómo se comporta la autorización si ponemos: satisfy any, satisfy all**

Tenemos que activar este modulo:  
<img width="825" height="86" alt="image" src="https://github.com/user-attachments/assets/6c419da8-618c-42cb-bab7-dde1546ac3c9" />

La primera, con Satisfy All nos dice que debemos cumplir todas las condiciones.  
<img width="392" height="268" alt="image" src="https://github.com/user-attachments/assets/1e38bec5-7372-44a6-b4ef-3ea2cd512e6b" />

Y en el segundo cado con que solo se cumpla uno ya valdría:  
<img width="414" height="268" alt="image" src="https://github.com/user-attachments/assets/7b1c18e9-d5f6-4c8b-92fe-b3c602dafa22" />
