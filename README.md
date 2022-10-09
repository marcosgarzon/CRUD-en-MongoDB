DESAFIO CLASE 18. "CRUD en MongoDB"

*Alumno: Marcos Garzon*

-----------------------------------------------

1- Crear una base de datos llamada ecommerce 

use ecommerce 

-----------------------------------------------

2- Que contenga dos colecciones:

db.createCollection("mensajes")

db.createCollection("productos")

-----------------------------------------------

3- Agregar 10 documentos con valores distintos a las colecciones mensajes y productos.

----------10 documentos mensajes:

db.mensajes.insertMany([{email: "email_1@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_1"}, {email: "email_2@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_2"}, {email: "email_3@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_3"}, {email: "email_4@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_4"}, {email: "email_5@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_5"}, {email: "email_6@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_6"}, {email: "email7@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_7"}, {email: "email_8@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_8"}, {email: "email_9@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_9"}, {email: "email_10@gmail.com", timestamp: new Date().toLocaleString(), message: "mensaje_10"}])


----------10 documentos productos:

db.productos.insertMany([{title:"producto_1", price:110, thumbnail: "url_1"}, {title:"producto_2", price:240, thumbnail: "url_2"}, {title:"producto_3", price:320, thumbnail: "url_3"}, {title:"producto_4", price:837, thumbnail: "url_4"}, {title:"producto_5", price:1100, thumbnail: "url_5"}, {title:"producto_6", price:2400, thumbnail: "url_6"}, {title:"producto_7", price:2660, thumbnail: "url_7"}, {title:"producto_8", price:4111, thumbnail: "url_8"}, {title:"producto_9", price:4740, thumbnail: "url_9"}, {title:"producto_10", price:4990, thumbnail: "url_10"}])

-----------------------------------------------

4- Listar todos los documentos en cada colección.

db.mensajes.find()

db.productos.find() 

-----------------------------------------------

5- Mostrar la cantidad de documentos almacenados en cada una de ellas.

db.mensajes.estimatedDocumentCount()

db.productos.estimatedDocumentCount()

-----------------------------------------------

6- Agregar un producto más en la colección de productos 

db.productos.insertOne({title:"producto_11", price:2988, thumbnail: "url_11"})

-----------------------------------------------

7- Realizar una consulta por nombre de producto específico

db.productos.findOne({title:"producto_5"})

-----------------------------------------------

8- Listar los productos con precio menor a 1000 pesos.

db.productos.find({price:{$lt:1000}})

-----------------------------------------------

9- Listar los productos con precio entre los 1000 a 3000 pesos.

db.productos.find({$and:[{price:{$gt:1000}},{price:{$lt: 3000}}]})

-----------------------------------------------

10- Listar los productos con precio mayor a 3000 pesos.

db.productos.find({price:{$gt:3000}})

-----------------------------------------------

11- Realizar una consulta que traiga sólo el nombre del tercer producto más barato.

db.productos.find({},{"title":1, "_id":0}).sort({"price":1}).limit(1).skip(2)

-----------------------------------------------

12- Hacer una actualización sobre todos los productos, agregando el campo stock a todos ellos con un valor de 100.

db.productos.updateMany({},{$set: {"stock": 100}})

-----------------------------------------------

13- Cambiar el stock a cero de los productos con precios mayores a 4000 pesos. 


db.productos.updateMany({"price":{$gt: 4000}}, {$set:{"stock": 0}})

-----------------------------------------------

14- Borrar los productos con precio menor a 1000 pesos 

db.productos.deleteMany({"price":{$lt:1000}})

-----------------------------------------------

15- Crear un usuario 'pepe' clave: 'asd456' que sólo pueda leer la base de datos ecommerce. Verificar que pepe no pueda cambiar la información.

Comando 1) use admin

Comando 2) db.createUser({user:"pepe", pwd:"asd456", roles:[{role:"read", db:"ecommerce"}]})

Comando 3) Cerrar y abrir con usuario: mongosh -u pepe -p asd456


