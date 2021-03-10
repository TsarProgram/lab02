## Лабораторная работа #2

## Part I

## Выполнение:
1. [x] Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
2. [x] Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
```sh
  $ mkdir workspace/projects/lab02 //создаем директорию с этой лабой
  $ cd workspace/projects/lab02   //перемещаемся в нее
  $ git init //создаем локальный репозиторий
  Вывод: Initialized empty Git repository in /home/vitaliy/workspace/projects/lab02/.git/
  $ git remote add origin https://github.com/TsarProgram/lab02.git  //устанавливаеv подключение к удаленному серверу и git репозиторию на нем
  $ touch README.md    //создаем файл 
  $ git add README.md  // добавляем его в локальный репозиторий
  $ git commit -m"added README.md"  //оставляем коммит
  $ git push origin master  //пушим его в удаленный репозиторий на ветку master
```
3. [x] Создайте файл `hello_world.cpp` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку `using namespace std;`.
```sh
  $ touch hello_world.cpp  //создаем файл
  $ cat > hello_world.cpp << EOF //прочитаем ввод и перенаправим его вместо вывода на экран в файл
  Ввод:  
  > #include <iostream>
  > 
  > using namespace std;
  > 
  > int main()
  > {
  >   cout<< "Hello world!"<< endl;
  > }
  > EOF
```
4. [x] Добавьте этот файл в локальную копию репозитория.
```sh
  $ git add hello_world.cpp //добавляет файл в локальную копию репозитория
```
5. [x] Закоммитьте изменения с *осмысленным* сообщением.
```sh
  $ git commit -m"added file.cpp" //коммитим изменения с *осмысленным* сообщением.
```
6. [x] Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.
```sh
  $ nano hello_world.cpp //изменяем код, согласно условию задания 
```
7. [x] Закоммитьте новую версию программы. Почему не надо добавлять файл повторно `git add`?
```sh
   $ git commit -m" updated file.cpp" -a // -a позволяет не добавлять файл повторно
```
8. [x] Запуште изменения в удалёный репозиторий.
```sh
  $ git push origin master //пушим изменения в удаленный репозиторий на ветку master
```
9. [x] Проверьте, что история коммитов доступна в удалёный репозитории.

## Part II
**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*

1. [x] В локальной копии репозитория создайте локальную ветку `patch1`.
```sh
  $ git сheckout -b patch1  //создаем новую ветку и переходим на нее
```
2. [x] Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.
```sh
  $ nano hello_world.cpp //изменяем код, согласно условию задания
```
3. [x] **commit**, **push** локальную ветку в удалённый репозиторий.
```sh
   $ git commit -m"updated file.cpp" -a
   $ git push origin patch1 //пушим изменения в удаленный репозиторий на ветку patch1
```
4. [x] Проверьте, что ветка `patch1` доступна в удалёный репозитории. 
5. [x] Cоздайте pull-request `patch1 -> master`.
6. [x] В локальной копии в ветке `patch1` добавьте в исходный код комментарии.
7. [x] **commit**, **push**.
```sh
  $ nano hello_world.cpp 
  $ git commit -m"updated file.cppX2" -a
  $ git push origin patch1 //ничего нового
```
8. [x] Проверьте, что новые изменения есть в созданном на **шаге 5** pull-request
9. [x] В удалённый репозитории выполните  слияние PR `patch1 -> master` и удалите ветку `patch1` в удаленном репозитории.
```sh
  $ git checkout master //перемещаемся на ветку master
  $ git merge patch1  //мержим ее и patch1
  $ git push origin master //заливаем изменения в удаленный репозиторий
  $ git push origin --delete patch1  //удаляем patch1 в удаленном репозитории
```
10. [x] Локально выполните **pull**.
```sh
   $ git pull origin master //загружаем файл в локальный репозиторий
```
11. [x] С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.
```sh
  $ git log //смотрим историю коммитов
  //нет возможности копировать с консоли, а писать вручную слишком долго, но они правда есть)
```
12. [x] Удалите локальную ветку `patch1`.
```sh
   $ git branch -d patch1 //удаляем ветку в локальном репозитории
```

### Part III
**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*

1. [x] Создайте новую локальную ветку `patch2`.
```sh
  $ git checkout -b patch2
```
2. [x] Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.
```sh
  $ sudo apt install clang-format
  $ clang-format -i -style=Mozilla hello_world.cpp //делаем то, о чем говорится в условии
```
3. [x] **commit**, **push**, создайте pull-request `patch2 -> master`.
```sh
  $ git commit -m"new style" -a
  $ git push origin patch2
```
4. [x] В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
5. [x] Убедитесь, что в pull-request появились *конфликтны*.
6. [x] Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.
```sh
  $ git checkout master 
  $ git pull origin master
  $ git checkout patch2
  $ git rebase master //пытаемся объединить изменения, сделанные в одной ветке, с другой веткой - видим конфликты
  $ nano hello_world.cpp //устраняем конфликты вручную 
  $ git add hello_world.cpp
  $ rebase --continue //объединяем изменения, сделанные в одной ветке, с другой веткой
```
7. [x] Сделайте *force push* в ветку `patch2`
```sh
  $ git push --force origin patch2 //пушим изменения в удаленный репозиторий
```
8. [x] Убедитесь, что в pull-request пропали конфликтны. 
9. [x] Вмержите pull-request `patch2 -> master`.
```sh
  $ git checkout master
  $ git merge patch2
```
  
