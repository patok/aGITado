!SLIDE
    Cómo funciona?

!SLIDE
    Estructura del repositorio

!SLIDE fade
## git directory ##

!SLIDE fade
## git directory ##

.git

!SLIDE fade
## git directory ##

.git

GIT_DIR

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
## object database ##
* "packed" format

!SLIDE bullets incremental transition=scrollRight
## object database ##
* object types
* blob
* tree
* commit
* tag

!SLIDE bullets incremental transition=fade
## object database ##
* blob
* every file constitutes a blob

!SLIDE bullets incremental transition=fade
## object database ##
* tree 
* cada directorio se representa con un tree
* es una estructura reflexiva (un tree puede contener una referencia a un tree)

!SLIDE bullets incremental transition=fade
## object database ##
* commit
* un puntero a un root tree + metadata commit (parent, autor, commiter, fecha, mensaje)

!SLIDE bullets incremental transition=fade
## object database ##
* DAG

!SLIDE bullets incremental transition=fade
## object database ##
* tag
* puntero a un objeto en la base (x lo gral un commit)

!SLIDE bullets incremental transition=fade
## object database ##
* INMUTABLES !

!SLIDE bullets incremental transition=scrollLeft
## references ##
* lightweight, moveable pointers to a commit
* stored under .git/refs/*

!SLIDE

* workflow & structure sample: blobs, tree, commits, tags & refs, branches

!SLIDE
    Respositorios alienígenas o remotos
    
!SLIDE

    Merging vs/y/o Rebasing

!SLIDE
    Identificando al acusado

!SLIDE
    El índice: 3 cabezas piensan mas que 2


