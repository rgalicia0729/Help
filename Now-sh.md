# Como hacer Deploy con Now.sh

## Componentes de una aplicación

Una aplicación web moderna se divide en varias partes, algunas aplicaciones tienen más que otras, en este curso vamos a ver alguna:

* Archivos estáticos o Frontend. Estos archivos son enviados al usuario a través de un CDN.
* Backend for Frontend. Este es el servidor que pide datos al API y responde HTML al usuario.
* Backend API. Puede estar hecho en cualquier tecnología e incluso puede estar dividido en múltiples aplicaciones pequeñas encargadas de distintas responsabilidades cada una.
* Bases de Datos. Puede estar hecha en lo tecnología de BD que sea y pueden existir diferentes bases de datos creadas en distintas tecnologías.
   
 Definiciones importantes:
 
* CDN = Content Delivering Network. Muchos servidores distribuidos por todo el mundo proveer de estos archivos comunes y que no están generados dinámicamente a nuestros usuarios y que puedan acceder rápidamente a ellos.
    
* API = Aplication Programming Interface. Representa la capacidad de comunicación entre componentes de software.

## Opciones para hacer Deploy

Estas son algunas de las opciones para llevar una aplicación a producción:

* Amazon Web Services **(Control en la infraestructura)
* Microsoft Azure (Control en la infraestructura)
* Google Cloud Platform (Control en la infraestructura)
* Heroku (Sin control en la infraestructura)
* Digital Ocean (Control en la infraestructura)
* GitHub Pages (Para sitios estáticos)
* Surge.sh (Para sitios estáticos)
* Zeit Now (Sin control en la infraestructura)

## ¿Por que Zeit Now?

### Tipos de Deploys

* Aplicación de Node.js
* Sitios estáticos
* Contenedores docker

### Características

* Es fácil (Un comando)
* Escala automáticamente
* Deploy inmutables
* Deploy sin caídas
* Deploys ilimitados
* HTTP2 Automaticamente
* Certificado SSL gratis
* Logs por deploy
* DNS (zeit.world)
* Comprar dominios por CLI
