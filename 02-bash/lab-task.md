### 1. Hello World

Написать программу печатающую Hello World

<!--
```
#!/bin/sh
echo Hello World
```
-->

### 2. Аргументы

Написать скрипт печатающий свои аргументы. Что будет, если выполнить ваш скрипт с опцией -n?

<!--
#!/bin/sh
echo $@
-->

### 3. Скачивание

Написать скрипт, скачивающий файл если он еще не скачан. Имя файла и url должны быть экспортированы в переменных FILE, URL.

Если скрипт называется `downloader.sh`, то **запускать** ваш скрипт вы должны так:

```
export FILE=yandex.html
export URL=http://ya.ru
./downloader.sh
```

<!---
```
#!/bin/sh

set -e

FILE=yandex.html
URL=http://ya.ru

if [[ ! -f $FILE ]]; then
    wget $URL -o $FILE
fi
```
-->

### 4. Скрипт, запускающий команду каждые 5 секунд. 

Пример запуска: `watch.sh ls -lah`.
При запуске без аргументов должен выводиться usage.

**Note**. usage --- строка, объясняющая, как использовать программу. Пример usage можно увидеть, если запустить команду `grep` без аргументов:

```
➜  ~  grep
usage: grep [-abcDEFGHhIiJLlmnOoqRSsUVvwxZ] [-A num] [-B num] [-C[num]]
	[-e pattern] [-f file] [--binary-files=value] [--color=when]
	[--context[=num]] [--directories=action] [--label] [--line-buffered]
	[--null] [pattern] [file ...]
```

<!--
```
#!/bin/sh

set -e

if [[ $# == "0" ]]; then
    echo "usage: watch.sh CMD [ARGS...]"
    exit 1
fi

while true; do
    $@
    sleep 5
done
```
-->

### 5. Что делает данный скрипт? Как остановить его после запуска?

```
#!/bin/sh
(
    while true; do
        touch file.txt
    done
) > /dev/null 2> /dev/null &
```

### 6. Fortune

Установите программу fortune. Добавьте её в .bashrc (.zshrc) и наполняйтесь мудростью и просветлением при каждом запуске командной оболочки.

Установите программу cowsay и сделайте так, чтобы при каждом запуске командной оболочки мудрость изрекала ASCII-корова.

### 7. Перепишите команды в более короткой форме.

```
mv reallylongfilename_reallyreallylong_iamnotkidding.txt reallylongfilename_reallyreallylong_iamnotkidding.old
```
<!-- # mv reallylongfilename_reallyreallylong_iamnotkidding.{txt,old} -->

**Note**. Хотелось бы печатать `really...kidding` только один раз.

```
cd /home/myuser
```
<!-- # cd -->

```
rm film.avi film.avi.part01 film.avi.part02 film.avi.part03
```
**Note**. Других файлов с расширением `.avi` в папке нет.

<!-- # rm file.avi* -->

```
mkdir src
mkdir src/myproject
mkdir src/myproject/java
mkdir src/myproject/java/com
mkdir src/myproject/java/com/hse
mkdir src/myproject/java/com/hse/myproject
```
<!-- # mkdir -p src/myproject/java/com/hse/myproject -->

```
cat /tmp/myfile | grep "mystring"  # Useless Use of Cat Award
```

**Note**. Можно ли обойтись одной командой (а не двумя, как сейчас)?

<!-- # grep mystring /tmp/myfile -->

### 8. Что делают эти однострочники? 

Как можно переписать их в более короткой форме?

```
ls | grep "[.]txt$"
```
<!--  # ls *.txt -->

```
(cd /tmp && ls)
```
<!-- # ls /tmp -->

```
for file in $(ls); do ./process.sh $file; done
```
**Note**. man xargs
<!-- # ls | xargs ./process.sh -->

```
find . -type f -iname '*.txt' -maxdepth 1 | xargs sed 's/ /\n/g' | grep -v "^$" | wc -l
```
<!-- # cat *.txt | wc -w -->

```
sort file1 > tmp1 && sort file2 > tmp2 && diff tmp1 tmp2 && rm tmp1 tmp2
```
<!-- # diff <(sort file1) <(sort file2) -->
