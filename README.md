## Лабораторная работа #2

##Part I

## Выполнение:
[*] 1.Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).

```bash
Command:
  $ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
  //скачивает файл, находящийся по данному адресу
```
```sh

2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0

Command:
  $ tar -xf boost_1_69_0.tar.gz
  // разархивирывает данный файл
```
```sh

3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.

Command:
  $ tree -L 1 //отображает все файлы и директории в искомой директории
  OR 
  $ find . -maxdepth 1 -type f | wc //отображает все файлы в искомой директории
  OR
  $ ls. -l | grep "^-" | wc //отображает все файлы в искомой директории
  

Result: 12;
```
```sh

4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.

Command:
  $ tree //отображает все файлы и директории рекурсивно, начиная с текущей директории
  OR
  $ find.  -type f | wc //отображает все файлы рекурсивно, начиная с текущей директории
  OR
  $ ls. -lR | grep "^-" | wc //отображает все файлы рекурсивно, начиная с текущей директории
  
Result: 61192;
```
```sh

5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).

For ".cpp":
     Result == 13774;
     Command: 
       $ find. -type f -name "*.cpp" | wc
For ".h":
     Result == 96; 
     Command: 
       $ find. -type f -name "*.h" | wc
For !".h" and !".cpp": 
     Result == 47122;
     Command:
       $ find. -type f -not -name "*.cpp" -not -name "*.h" | wc
       
       // find. -type f -name ищет файлы по данному имени (find. -type f -not -name  ищет все файлы, не свзанные с заданным именем)
```
```sh

6. Найдите полный путь до файла any.hpp внутри библиотеки boost.

Command: 
  $ find `pwd` -name "any.hpp" //find `pwd` выводит путь до файла с данным именем

Part of the result: 
/home/vitaliy/boost_1_69_0/boost/fusion/include/any.hpp
/home/vitaliy/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/vitaliy/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/vitaliy/boost_1_69_0/boost/type_erasure/any.hpp
/home/vitaliy/boost_1_69_0/boost/hana/any.hpp
/home/vitaliy/boost_1_69_0/boost/hana/fwd/any.hpp
```
```sh

7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.

Command: 
  $ grep -lR "boost::asio" // grep выводит все файлы, содержащие данную строку

Part of the result:
boost_output/include/boost/process/io.hpp
boost_output/include/boost/process/spawn.hpp
boost_output/include/boost/process/async.hpp
boost_output/include/boost/process/system.hpp
boost_output/include/boost/process/async_pipe.hpp
boost_output/include/boost/process/detail/windows/async_in.hpp
boost_output/include/boost/process/detail/windows/async_out.hpp
boost_output/include/boost/process/detail/windows/io_context_ref.hpp
```
```sh

8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.

Commands:
  $ sudo apt install libicu-dev
  $ ./bootstrap.sh --prefix=boost_output
  $ ./b2 install
  $ ./b2 install -j 8
```
```sh

9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.

Command:
  $ mv ~/boost_1_69_0/boost_output/lib/* ~/boost-lib/ 
  // mv перемещает все файлы из первой директории во вторую
```
```sh

10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.

Command: 
  $ du -ah // du выводит размер всех файлов в заданной директории

Part of the result: 
460K	./lib/libboost_math_tr1.so.1.69.0
120K	./lib/libboost_math_c99l.so.1.69.0
3,1M	./lib/libboost_math_tr1l.a
76K	./lib/libboost_stacktrace_backtrace.so.1.69.0
4,7M	./lib/libboost_wave.a
104K	./lib/libboost_date_time.so.1.69.0

OR

  $ sudo apt install ncdu
  $ ncdu // ncdu выводит размер всех файлов в заданной директории и располагает их от большего размера к меньшему
```
```sh

11. Найдите топ10 самых "тяжёлых".

Command: 
  $ du -ah | sort -rh | head -10 // sort -rh head -10 сортирует и находит размер 10 наибольших файлов в заданной директории

Result:
54M	./lib
4,7M	./lib/libboost_wave.a
4,5M	./lib/libboost_log.a
3,5M	./lib/libboost_locale.a
3,2M	./lib/libboost_regex.a
3,1M	./lib/libboost_math_tr1l.a
3,1M	./lib/libboost_math_tr1f.a
3,1M	./lib/libboost_math_tr1.a
2,7M	./lib/libboost_log_setup.a
2,4M	./lib/libboost_unit_test_framework.a
```
```sh

12. Составить отчет и отправить ссылку личным сообщением в **Slack**
 
 that's my report
 ```
