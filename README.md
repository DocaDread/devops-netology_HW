Домашние задания с 3.1

# 3.1. Работа в терминале, лекция 1

1.Какие ресурсы выделены по умолчанию для ВМ?
----------------------------------------------

   1 Гб оперативной памяти, 2 ядра процессора, 64 Гб VHDD (Динамический)

2.Как добавить оперативной памяти или ресурсов процессора виртуальной машине?
------------------------------------------------------------------------------

Добавить ресурсов можно с помощью VBoxManage через файл конфигурации Vagrant,а именно:
	  
	  config.vm.provider "virtualbox" do |vb|
	    v.memory = 1024
  	    v.cpus = 2
	  end

3.man bash
------------------------------------------------------------------------------------------------
   Какой переменной можно задать длину журнала history, и на какой строчке manual это описывается?
		
	- HISTFILESIZE (655) - Задает максимальное кол-во строк, содержащихся в файле истории
	- HISTSIZE (Line 658) - Задает кол-во сохраненных команд для журнала history

   Что делает директива ignoreboth в bash?

   	- ignoreboth - сокращение для значений ignorespace и ignoredups (значения для переменной HISTCONTROL, которые указывают как сохраняются команды в истории)
  	- ignorespace - нужен для игнорирования строк, начинающихся с пробела, 
   	- ingoredups -  не сохранять строки, которые совпадают с предыдущими записями в истории.

4.В каких сценариях использования применимы скобки {} и на какой строчке man bash это описано?
-----------------------------------------------------------------------------------------------
	
   Фигурные скобки используются для выполнения составных команд в окружении текущей оболочки (shell). Указание в man на строке 212 в разделе SHELL Grammar

5.Как создать однократным вызовом touch 100000 файлов? Получится ли аналогичным образом создать 300000? Если нет, то почему?
-----------------------------------------------------------------------------------------------------------------------------

   - 100000 файлов можно создать командой touch file{000001..100000}, указав больше разрядов у начала диапазона, чтобы не было ошибки по аргументам (как при указании {1..100000})
 
   - для создания 300000 файлов уже необходимо увеличить количество места, доступного для стека ulimit -s 65536 (указать значение больше стандартного 8192)

6.Что делает конструкция [[ -d /tmp ]]
--------------------------------------

   Данная конструкция является условным выражением, которое проверяет существует ли директория tmp в выводом в виде 0 или 1 (истина, ложь)

7.Добейтесь в выводе type -a bash в виртуальной машине наличия первым пунктом в списке:
--------------------------------------------------------------------------------------

export PATH=/tmp/new_path:$PATH
![2021-11-13_16-02-59](https://user-images.githubusercontent.com/93042634/141635041-378ddbee-d7ba-4312-b9f0-168328883da2.png)


8.Чем отличается планирование команд с помощью batch и at?
----------------------------------------------------------

at выполняет комманды из стандартного ввода в заданное время

batch выполняет комманды, когда средняя загрузка системы меньше 1.5

