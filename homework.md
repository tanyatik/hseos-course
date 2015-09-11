#### Домашнее задание 1

 Написать скрипт, обходящий директорию в файловой системе. Должен печатать отступ, тип (файл/директория)  и название, и в директории спускаться рекурсивно.
Должен принимать один необязательный аргумент -- директорию, с которой начинать обход.

Вывод должен быть таким:

```
Directory: ATLAS
  Directory: CONFIG
    Directory: ARCHS
      File: AMD64K10h32SSE3.tar.bz2
      File: AMD64K10h64SSE3.tar.bz2
      File: AMDDOZER32AVXFMA4.tar.bz2
      File: AMDDOZER64AVXFMA4.tar.bz2
...
```

<!--
```
indent()
{
    j=0;
    while [ "$j" -lt "$1" ]; do
        echo "    \c"
        j=`expr $j + 1`
    done
}

traverse()
{
    cd "$1"

    ls | while read i; do
        indent $2
        if [ -d "$i" ]; then
            echo "Directory $i"
            (traverse "$i" `expr $2 + 1`)
        else
            echo "File $i"
        fi
    done
}

if [ -z $1 ]; then
    traverse . 0
else
    traverse $1 0
fi
```
-->

#### Домашнее задание 2

Настроить .bashrc.

1. Настроить доступ в Github по ssh ключу и сделать добавление ssh ключей для Github в ssh agent при старте системы.

Про генерацию ssh ключей можно прочитать здесь: https://help.github.com/articles/generating-ssh-keys/

2. Настроить переменные окружения EDITOR, PATH.

3. Настроить alias для часто используемых команд.

4. (По желанию) Настроить текст при запуске командной оболочки и приглашение (prompt).
