# Usar imagen base JRE 17 Alpine
FROM eclipse-temurin:17-alpine

# Agregar usuario y grupo
RUN addgroup -g 1028 devopsc \
    && adduser -D -G devopsc admin

#Create a new mount point at /tmp on native host because a volume is mor efficient and speed that filesystem
VOLUME /tmp

#Copiamos el jar a la imagen
ARG JAR_FILE
# Variable de entorno para la contraseña de la base de datos
ARG DB_PASSWORD

#Estabece una variable de entorno DE_PASSWORD con el valor del argumento
ENV DB_PASSWORD=$DB_PASSWORD

#Copia el archivo jar
COPY ${JAR_FILE} /tmp/app.jar

#Change ownership pf the /app directory to the "admin" user
RUN chown -R admin:devopsc /tmp

#Cambia el usuario 'admin'\
USER admin

# Comando por defecto al ejecutar el contenedor
ENTRYPOINT ["java", "-jar", "/tmp/app.jar"]