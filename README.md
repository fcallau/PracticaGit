# Práctica del curso de git, gitHub y Sourcetree



### *- ¿Qué comando utilizaste en el paso 11? ¿Por qué?*

**`git reset --hard HEAD~1`**

Con el `git reset HEAD~1` se deshace el último commit volviendo al commit padre (el numérico que acompaña la virgulilla indica los ancestros que se mueve el puntero HEAD dentro de la rama en la que se encuentra). Usando el modificador `--hard` se deshacen los cambios de la **working copy**, por lo que el estado de esta, será el que había antes de realizar el commit.


### *- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?*

**`git reflog`**

Muestra lo que ha pasado en el repositorio. Interesa rehacer el  commit desecho, con lo que se debe usar el hash asociado al commit al que se quiere apuntar (fef631f).

**`git reset --hard fef631f`**

Con el `git reset fef631f` el puntero HEAD apunta al commit que se le pasa en el comando. Usando el modificador `--hard` se recuperan los cambios de la **working copy**, por lo que el estado de esta, será el que había antes de deshacer el commit.


### *- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?*

Estando en la rama **styled** (la rama que absorbe) se usa el comando **`git merge master`** para absorber a la rama **master**. No genera ningún conflicto porque la rama que absorve ya tiene los commits de la rama que quiere absorver.


### *- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?*

Estando en la rama **styled** (la rama que absorbe) se usa el comando **`git merge htmlify`** para absorber a la rama **htmlify** (al no tratarse de dos ramas "en línea" se hace un commit no fast-forward, por lo que equivaldría a ejecutar el comando `git merge --no-ff htmlify`). Causa conflicto porque la rama que absorve y la rama que quiere absorver tienen como mínimo un fichero en común con una línea, como mínimo, en la que difieren. En este caso en particular, el fichero es el git-nuestro.md y las líneas que difieren son varias.


### *- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?*

Estando en la rama **master** (la rama que absorbe) se usa el comando **`git merge styled`** para absorber a la rama **styled**. Se trata del caso de dos ramas en línea, y en concreto de un workflow habitual, en el que una *feature* implementada y probada acaba siendo absorvida por la rama **master** (pasando préviamente por las ramas *develop* y *release*). Y no, no genera ningún conflicto porque se trata de un merge fast-forward (merge entre dos ramas "en línea").


### *- ¿Qué comando o comandos utilizaste en el paso 25?*

El comando **`git config alias.graph "log --graph --decorate --pretty=oneline"`** para crear un álias para posteriormente poder usarlo con el comando **`git graph`**.


### *- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?*

Sí, y es el que se habría realizado en el caso de no explicitar que fuese un no fast-forward. Puede ser fast-forward por tratarse de dos ramas que estan "en línea".


### *- ¿Qué comando o comandos utilizaste en el paso 27?*

Se usa el comando **`git reset HEAD~1`** para deshacer el merge. No se usa el modificador `--hard` para mantener los datos en la **working copy**.


### *- ¿Qué comando o comandos utilizaste en el paso 28?*

**`git checkout -- git-nuestro.md`** para descartar los cambios en la **working copy**.


### *- ¿Qué comando o comandos utilizaste en el paso 29?*

**`git branch -d title`** pero avisa que la rama no está "fully merged"; indica que hay algún commit de la rama que será inalcanzable en el caso del borrado. El comando por lo tanto ha informado de las consecuencias de realizar el borrado de la rama. Se procede al borrado de la rama con el comando **`git branch -D title`**.


### *- ¿Qué comando o comandos utilizaste en el paso 30?*

**`git reflog`** para localizar el identificador del commit al que queremos apuntar, posteriormente se ejecuta el comando **`git reset --hard 9d24081`**. Con el modificador `--hard` conseguimos que en la **working copy** esté la versión de git-nuestro con el título. Sin el `--hard` hubiéramos recibido un aviso de cambios detectados, por lo que se deberían descartar los cambios para conseguir el mismo estado que con el modificador `--hard`.


### *- ¿Qué comando o comandos usaste en el paso 32?*

**`git log`** para localizar el commit y posteriormente **`git checkout 65dea979e344eca3c06bafe950850cf88d853fe6`** para apuntar al commit.


### *- ¿Qué comando o comandos usaste en el punto 33?*

**`git reflog`** para localizar el commit (ahora no sirve el `git log` porque solo tenemos visibilidad del commit inicial) y posteriormente **`git checkout 9d24081`** para apuntar al commit donde la rama **master** absorvía a la rama **title**.