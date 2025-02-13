El orden de Despliegue es el siguiente:

1 - security-group.yaml 
- Una vez se hayan creado los grupos de seguridad, asegurarnos de que tenemos disponible una Subred en la VPC que vayamos a usar en las instancias, que asigne de forma automática una IP Pública IPV4

2 - backend.yaml 
- Puede da error en la version de Tomcat pero simplemente es ir a la web de apache y agarrar la url de tar.gz del Tomcat actual
- Se puede testear la api con curl a localhost/api/health

3 - frontend1.yaml & frontend2.yaml
- El orden da igual simplemente son 2 pilas separadas.
- Lo mismo que el back desde ssh testear que sigue llegando a la api

4 - load-balancer.yaml
- Una vez desplegado vamos al navegador con la IP Pública del output poniendo http:// y debería servir el contenido que esta alojado en cualquiera de los 2 front.


Pruebas y consideraciones:
- En mi caso le cuesta mucho cambiar de frontend por algún motivo que desconozco pero si insistes con el F5 en algún momento pasará.
- En los grupos de seguridad por el enlace que mandaste sale referenciado lo del SourceSecurityGroupId siguiendo eso podemos hacer !Ref a cualquiera de nuestros grupos de seguridad existentes.