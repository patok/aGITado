!SLIDE
    Cómo funciona?

!SLIDE
    Estructura del repositorio

!SLIDE transition=fade

## git directory ##

.git (sólo en el root de la carpeta de trabajo)

    $ tree .git
    .git
    |-- config
    |-- description
    |-- HEAD
    |-- hooks
    |   |-- commit-msg.sample
    |-- index
    |-- info
    |   `-- exclude
    |-- objects
    |   |-- info
    |   `-- pack
    `-- refs
        |-- heads
        `-- tags

!SLIDE bullets incremental transition=fade
## Git Directory ##
* config
* hooks
* index
* object database
* references

!SLIDE bullets incremental transition=scrollUp
## object database ##
* content
* new_content = type + ' ' + content.size + \0
* sha = Digest::SHA1.digest(new_content)
* "b17b55b9f1a8e715db59a..."
* compressed = zlib::deflate(new_content)
* path = .git/objects/b1/7b55b9f1a8e...
* File.open(path, 'w') {|f| f.write(compressed)}

!SLIDE bullets incremental transition=fade
## object database ##
* "loose" format 

!SLIDE bullets smaller incremental transition=scrollUp
## object database ###
* gc (recolector de basura)
* mismo fichero con diferencias menores

*   .git/objects/5b/be38dff97fdc3f9db42539fa2eaf2993c24445
    .git/objects/81/5e06841b80897afd8fe5686dc610e045af1911
    .git/objects/dd/40e9ec9d8ccdd6d9b1f140992b947a657dd7a4
    .git/objects/fe/13dfa3393aaa7e9e0276067501f691df8ecda2


*   .git/objects/pack/pack-b916c14d0420eaaca7a2d9eeea2fd851d4e5b48a.pack
    .git/objects/pack/pack-b916c14d0420eaaca7a2d9eeea2fd851d4e5b48a.idx

!SLIDE bullets incremental transition=fade
## Object Database ##
* "packed" format

!SLIDE transition=scrollRight
## Object Database ##
![types](object-types.png)

!SLIDE bullets incremental transition=fade
## object database ##
* blob
* cada fichero/file es un blob
![tree2](tree2.png)

!SLIDE transition=fade
## object database ##
* blob
![blob](blob-detail.png)

!SLIDE bullets incremental transition=fade
## object database ##
* tree 
* cada directorio/carpeta se representa con un tree
![tree3](tree3.png)

!SLIDE bullets incremental transition=fade
## object database ##
* tree 
![tree](tree-detail.png)

!SLIDE bullets incremental transition=fade
## object database ##
* commit
* un puntero a un root tree + metadata commit (parent, autor, commiter, fecha, mensaje)
![commit](commit-detail.png)

!SLIDE bullets incremental transition=fade
## object database ##
* DAG
![dag](object-relationship.png)

!SLIDE transition=fade
## Object Database ##
![types](object-types.png)

!SLIDE bullets incremental transition=fade
## object database ##
![tag](tag-detail.png)

* .git/objects/20/c71174453dc760692cd...
* .git/refs/tags/v1.0

!SLIDE
## Object Database ##
![types](object-types.png)

!SLIDE transition=fade
## Object Database ##

![types](object-types-locked.png)

INMUTABLES !

!SLIDE bullets incremental 
## Muy importante! ##
* no se borra nada (bueno casi)
* es muy seguro (SHA1 crypto safe)
* no se borra la historia
* se escribe una historia alternativa

!SLIDE bullets incremental transition=scrollLeft
## references ##
* punteros "livianos", móviles a distintos commits
* guardados en .git/refs/*

!SLIDE bullets incremental
# references #

![ref](reference.png)

!SLIDE transition=fade
# Ejemplo #
![ref](scenario1.png)

!SLIDE transition=fade
# Ejemplo #
![ref](scenario2.png)

!SLIDE transition=fade
# Ejemplo #
![ref](scenario3.png)

!SLIDE transition=fade
# Ejemplo #
![ref](scenario4.png)


!SLIDE transition=fade
# Ejemplo #
![ref](scenario4b.png)


!SLIDE transition=fade
# Ejemplo #
![ref](scenario5.png)

!SLIDE transition=fade
# Ejemplo #
![ref](scenario6.png)

!SLIDE transition=fade
# Ejemplo #
![ref](scenario8.png)

!SLIDE transition=fade
# Ejemplo #
![ref](scenario7.png)

!SLIDE transition=scrollLeft
# El índice: 3 cabezas piensan mas que 2 #

!SLIDE bullets incremental 
## Index ##
### area intermedia (staging area) ###

!SLIDE transition=fade
### Index ###
![ref](index.png)

!SLIDE transition=fade
### Index ###
![ref](index1.png)

!SLIDE transition=fade
### Index ###
![ref](index2.png)

!SLIDE transition=fade
### Index ###
![ref](index3.png)

!SLIDE transition=fade
### Index ###
![ref](index4.png)

!SLIDE bullets incremental 
## Index ##
* no es necesario commitear todo de una 
* elegir las partes a commitear (git add --interactive)
* ayuda a hacer review de tus cambios
* permite tener una historia de cambios mas ordenada y entendible

!SLIDE
# Respositorios alienígenas o remotos #

!SLIDE
## Protocols ##
* ssh://
* http[s]://
* git://
* file://
* rsync:// <-- deprecated
* ftp:// <-- deprecated

!SLIDE

    Merging vs/y/o Rebasing

!SLIDE
# Conclusiones #
* poner puntos interesantes de Git, como :
* rápido
* simple pero potente
* mejora significativa en el workflow?
* etc 



