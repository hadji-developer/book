## Привет, мир!

Итак, когда Rust уже установлен можно приступать к написанию вашей первой программы. Общая традиция при изучении нового языка программирования - писать маленькую программу которая печатает в строке вывода `"Hello, world!"`. Давайте сделаем тоже самое.

> Обратите внимание: данная книга подразумевает, что читатель должен быть знаком с командной строкой. Однако, Rust не выдвигает каких-либо специальных требований к тому, как вы пишете и по какому принципу храните код своих программ. По этому, если вы предпочитаете использовать интегрированную среду разработки (IDE) взамен командной строки терминала, чувствуйте себя спокойно и пользуйтесь тем, чем вам удобно. Разные IDE имеют разный уровень поддержки Rust, по этому не забывайте проверять документацию к выбранной IDE. Однако, не так давно команда Rust сфокусировалась на задаче большей поддержки языка в разных IDE и однозначно сделала определённый прогресс в данном направлении!

### Создание папки проекта

Прежде всего начнём с создания директории, в которой будем сохранять наш код на языке Rust. На самом деле не важно, где сохранять наш код. Однако, для упражнений и проектов, обсуждаемых в данной книге, мы советуем создать директорию *projects* в вашем домашнем каталоге, там же и хранить в будущем код программ из книги.

Откройте терминал и введите следующие команды для того, чтобы создать директорию <em>projects</em> для хранения кода разных проектов, и, внутри неё, директорию <em>hello_world</em> для проекта “Hello, world!”.

Для Linux, macOS и PowerShell на Windows, введите:

```console
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

Для Windows в CMD, введите:

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

### Написание и запуск первой Rust программы

Теперь создадим новый файл, в котором сохраним исходный код программы, назовём его *main.rs*. Заметьте, что файлы с кодом на языке программирования Rust всегда заканчиваются расширением *.rs*. В случае, если вы захотите использовать более одного слова в названии файла, используйте знак подчёркивания в качестве разделителя. Например, возможно использовать именование *hello_world.rs*, но не рекомендуется использовать вариант *helloworld.rs*.

Теперь откроем файл *main.rs* для редактирования и введём следующие строки кода:

<span class="filename">Название файла: main.rs</span>

```rust
fn main() {
    println!("Hello, world!");
}
```

<span class="caption">Листинг 1-1: Программа которая печатает <code>Hello, world!</code></span>

Сохраните файл и вернитесь обратно в окно терминала, чтобы скомпилировать и запустить нашу первую программу. На Linux или macOS для этого введите следующие команды:

```console
$ rustc main.rs
$ ./main
Hello, world!
```

В Windows, введите команду `.\main.exe` вместо `./main`:

```powershell
> rustc main.rs
> .\main.exe
Hello, world!
```

Независимо от операционной системы, строка `Hello, world!` должна напечататься в окне вашего терминала. Если вы не увидели вывода, вернитесь в часть "Решение проблем" ["Troubleshooting"] раздела "Установка" для получения помощи.

Если напечаталось `Hello, world!`, то примите наши поздравления! Вы написали программу на Rust, что делает вас Rust программистом — добро пожаловать!

### Анатомия программы на Rust

Давайте рассмотрим в деталях, что происходит в программе “Hello, world!”. Вот первый кусок пазла:

```rust
fn main() {

}
```

Эти строки определяют функцию в Rust. Функция `main` имеет специальный смысл: она всегда является первым кодом, который запускается в исполняемой программе на Rust. Первая строка объявляет функцию с именем `main` у которой нет параметров и она ничего не возвращает. Если бы тут были параметры, они были бы записаны внутри круглых скобок, `()`.

Также заметим, что тело функции обёрнуто в фигурные скобки `{}` (curly brackets). В Rust тело любой функции оборачивается в фигурные скобки. Хорошим стилем является размещение открывающей скобки в строке объявления функции, оставляя пробел между ними.

Если вы хотите придерживаться единого стиля оформления кода во всех проектах Rust, вы можете использовать инструмент автоматического форматирования `rustfmt` для оформления вашего кода в определённом стиле. Команда Rust включила этот инструмент в стандартный дистрибутив Rust, как и `rustc`, поэтому он уже должен быть установлен на вашем компьютере! Более подробную информацию можно найти в онлайн-документации.

Содержимое функции `main`:

```rust
    println!("Hello, world!");
```

Эта строка делает всю работу в этой маленькой программе: печатает текст на экран. Можно заметить четыре важных детали.

Первая, не столь заметная, - в стиле Rust для отступа используются четыре пробела, а не знак табуляции.

Во-вторых, `println!` вызывает макрос Rust. Если бы вместо этого он вызывал функцию, она вводилась бы как `println` (без `!`). Мы обсудим макросы Rust более подробно в главе 19. На данный момент вам просто нужно знать, что использование `!` означает, что вы вызываете макрос вместо обычной функции, и что макросы не всегда следуют тем же правилам, что и функции.

Третья - вы видите строку `"Hello, world!"`. Мы передаём эту строку как аргумент в макрос `println!` и, благодаря этому, строка выводится макросом на экран.

Четвёртая - в конце строки стоит точка с запятой (`;`), которая означает, что выражение закончилось и следующее выражение можно начинать опять. Большая часть строк в Rust коде заканчивается точкой с запятой.

### Компиляция и выполнение кода являются отдельными шагами

Только что вы запустили вновь созданную программу, теперь изучим каждый шаг этого процесса.

Перед запуском программы, её необходимо скомпилировать компилятором Rust с помощью ввода команды `rustc` и передачи имени вашего файла с исходным кодом, например так:

```console
$ rustc main.rs
```

Если вы знакомы с C или C++, то заметили, что это весьма похоже на вызов компиляции при помощи `gcc` или `clang`. После успешной компиляции, Rust выдаст двоичный исполняемый файл.

Для того, чтобы посмотреть на исполняемый файл на Linux, macOS и в PowerShell на Windows достаточно выполнить команду `ls` в командной строке. На Linux или macOS будет отображено два файла. В PowerShell на Windows, как и в Windows CMD - три файла.

```console
$ ls
main  main.rs
```

В CMD на Windows следует ввести следующие команды:

```cmd
> dir /B %= the /B option says to only show the file names =%
main.exe
main.pdb
main.rs
```

В обоих случаях видно: файл исходного кода с расширением *.rs*, исполняемый двоичный файл (*main.exe* в Windows, но *main* на всех других платформах), а в случаем использования Windows, ещё и файл включающий отладочную информацию с расширением *.pdb*. <br><br>Отсюда мы можем запустить нашу программу (исполняемый двоичный файл) *main* или *main.exe* соответствующей командой для Windows или иных ОС:

```console
$ ./main # для Linux
> .\main.exe # для Windows
```

Если *main.rs* был с текстом “Hello, world!”, то строка `Hello, world` будет напечатана в терминале.

Если вам близки динамические языки, такие как Ruby, Python или JavaScript, вы, возможно, не привыкли к тому, что компиляция и выполнение программы - это отдельные шаги. Rust - это язык с предварительной компиляцией (*ahead-of-time compiled*), что означает, что, скомпилировав программу, вы можете передать исполняемый файл другому человеку и он сможет запустить её, даже не имея установленного Rust. А если вы дадите кому-то файл *.rb*, *.py* или *.js*, то  для его выполнения получателю понадобится установленный интерпретатор Ruby, Python или JavaScript (соответственно). Но в этих языках вам нужна всего одна команда для компиляции и запуска вашей программы. Что ж, всё является компромиссом в дизайне языков.

Простая компиляция с помощью `rustc` подходит только для простых программ, но по мере того, как ваши проекты становятся сложнее, вы захотите управлять всеми опциями и упростить обмен своим кодом с другими. Далее мы представим инструмент Cargo, который поможет в написании настоящих, а значит и более сложных, программ на Rust.


["Troubleshooting"]: ch01-01-installation.html#troubleshooting
