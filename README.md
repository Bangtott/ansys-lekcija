## Конспект
# FEM Solver
Метод конечных элементов (FEM) вычисляет распределение полей внутри заданного объема, ограниченного границами моделируемой области.  
При анализе поля в дальней зоне расстояние от антенны не учитывается в расчетах. Электромагнитное поле измеряется в вольтах на метр (В/м). В дальней зоне поле зависит от направления, что отражается в таких параметрах, как коэффициент усиления, направленность и напряженность поля.  

# IE Solver
Решатель интегральных уравнений (IE) не выполняет расчеты внутри объема. Вместо этого он строит 2D сетку на поверхностях и вычисляет распределение токов на них.  
IE-решатель применяется для анализа полей в ближней зоне. Расчет полей выполняется на заданном расстоянии, а визуализация токов возможна только на поверхностях с сеткой.  

# FEM + IE: Моделирование промежуточной области без сетки
Гибридный метод FE-BI (Finite Element – Boundary Integral) расширяет расчетную область FEM за счет интегрального преобразования полей.  
Отражатели и другие элементы могут моделироваться с помощью решателя IE. 
 
# SBR+: Альтернативный метод моделирования промежуточной области без сетки
Решатель HFSS SBR+ использует лучевой подход и может работать совместно с FEM, исключая необходимость построения сетки в промежуточной области.  

## Рефлексия
# Метод конечных элементов (FEM)
FEM — это мощный инструмент для расчета электромагнитных полей внутри заданного объема. Здесь всё просто: задаем границы, разбиваем пространство на элементы — и получаем точное распределение полей. А если нужно рассчитать дальнюю зону? Легко! Расстояние от антенны уже не играет роли, а поле измеряется в классических В/м. Причем в дальней зоне всё становится "направленным" — усиление, КНД и напряженность поля зависят от угла.  
# Решатель интегральных уравнений (IE)
Здесь другой подход — никаких объемных расчетов, только поверхности. IE строит 2D-сетку и смотрит, как текут токи по металлу. Идеально для анализа ближнего поля: можно детально изучить, что происходит прямо рядом с антенной. Но есть нюанс — токи и поля считаются только там, где есть сетка.  
# Гибридный подход: FEM + IE (FE-BI)
Зачем выбирать, если можно объединить? FE-BI — это когда FEM считает поле внутри объема, а IE подхватывает его на границе и переносит дальше без лишних сеток. Особенно круто для отражателей и сложных структур, где нужно и точность FEM, и эффективность IE.  
# Лучевой метод: SBR+
Если не хочется возиться с сетками вообще — есть SBR+. Это как трассировка лучей в 3D-графике, только для электромагнитных полей. Работает в паре с FEM, позволяя быстро считать промежуточные зоны без лишних расчетов. Быстро, гибко, без головной боли с сетками.  
# Если коротко:
FEM — для точных объемных расчетов.  
IE — для поверхностных токов и ближнего поля.  
FE-BI — лучший гибрид без лишних сеток.  
SBR+ — скорость и простота в лучевом подходе.  

## Постановка задачи
Модель автомобиля: car_model.step. Материал тела автомобиля – Perfect E. При расчёте колёса модели не учитываются.
Вариант 115 – частота 1115 МГц. Источник излучения: Plan e (Incident Wave).
