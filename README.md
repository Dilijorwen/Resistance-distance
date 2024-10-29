# Случайные блуждания: связь с резистивным расстоянием

Алгоритм вычисления эффективного сопротивления и моделирование случайных блужданий в электрических сетях. Вычисление эффективного сопротивления.

# Описание
Этот проект представляет собой программную реализацию алгоритма вычисления случайных блужданий на произвольном связном графе. Основной метод использует алгоритм на основе законов Кирхгофа для электрических цепей. Также включена программа для моделирования случайных блужданий.

# Структура проекта

Makefile -- файл для автоматизации сборки проекта,

one_file_report.w -- ключевой файл, из которого создаются octave скрипты и pdf версия отчета,

one_file_report.w,v -- rcs версия основного .w файла,	
moscow.dat -- матрица смежности мос метро,
442.dat -- матрица смежности линейного графа с 442 вершинами,
generator.m -- скрипт генерации произвольного графа и его матрицы смежности,
rpz.bib -- список литературы,
Остальные файлы -- стилевые файлы для ГОСТ 7-32.

# Требования
Для запуска проекта необходимы следующие утилиты:
	nuweb -- генерация tex файла для дальнейшей компиляции в pdf,
	pdflatex -- компиляция tex файла в pdf,
	bibtex -- генерация списка литературы,
	octave -- для выполнения рассчётов с помощью программ, которые будут сгенерированы nuweb-ом,
	rcs -- система контроля версий.

# Установка и запуск
## Сборка проекта
Откройте терминал и перейдите в директорию проекта. Выполните команду: "make".
Это запустит скрипт автоматической сборки проекта. В результате будут созданы:
	one_file_report.pdf -- файл отчёта,
	mainKirg.m -- octave скрипт для вычисления эффективного сопротивления в переданном графе,
	random_walk.m -- octave скрипт для выполнения случайного блуждания в переданном графе (не используется как самостоятельный скрипт),
	run_random_walk.m -- octave скрипт для запуска random_walk.m,
	theoretical_random_walk.m -- octave скрипт для теоретического рассчета значений для сравнения со значениями,полученными в run_random_walk.m.
Для очистки временных файлов, которые появляются в результате компиляции pdf, следует выполнить команду: "make clean".
		
# Использование
## Генерация графов
Для генерации тестовых графов выполните команду: "make auto-generate". 
В результате выполнения будут получены матрицы смежности для 9 графов:
	0.dat -- граф с 4 вершинами,
	1.dat -- граф с 100 вершинами,
	3.dat -- граф с 300 вершинами,
	6.dat -- граф с 600 вершинами,
	10.dat -- граф с 1000 вершинами,
	15.dat -- граф с 1500 вершинами,
	20.dat -- граф с 2000 вершинами,
	25.dat -- граф с 2500 вершинами,
	30.dat -- граф с 3000 вершинами.
		
Для генерации графа с другим параметрами выполните команду:
	"make generate NUM_VERTICES=<int> MAX_DEGREE=<int> FILE_NAME=<string>.dat", где
		NUM_VERTICES -- количество вершин, 
		MAX_DEGREE -- максимальная степень вершины, 
		FILE_NAME -- имя файла для сохранения.
	
## Выполнения программ:
Каждая из программ ("mainKirg.m", "run_random_walk.m", "theoretical_random_walk.m") запускаются по одному сценарию:
	"octave <PROGRAM_NAME.m> <FILE_NAME.dat> <V1> <V2>", где
		PROGRAM_NAME.m -- имя программы,
		FILE_NAME.dat -- имя файла с матрицей смежности,
		V1 -- номер начальной вершины,
		V2 -- номер конечной вершины.
