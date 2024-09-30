# Работа 1 - Компонент физики Rigidbody в Unity
Отчет по лабораторной работе #1 выполнил(а):
- Захаров Данил Андреевич
- РИ-320930
- АТ-01
# Цель работы: изучить свойства компонента Rigidbody, освоить реализацию игровых механик с применением свойств этого компонента

![image](https://github.com/user-attachments/assets/269a5c64-0d18-4b4e-be9e-59d721a95636)

Рекомендуемые источники для изучения:
1.	Rigidbody Unity Documentation
2.	Тема Rigidbogy в материалах лекции

# Задания к работе
1.1 Создайте сцену, изображенную на рисунке ниже:




## Создал сцену



2.2 Добавьте компонент Rigidbody на объекты CubeSid и CubeNancy. Запустите сцену, проверьте что кубики падают вниз и останавливаются на земле.
## Rigidbody для CubeSid

![image](https://github.com/user-attachments/assets/a62de6bc-c7d6-4cfd-96a1-3ef16d345c46)

## Rigidbody для CubeNancy

![image](https://github.com/user-attachments/assets/6d86ea09-ee97-4e69-94b3-f1591a5a3b2c)

2.3 Установите массу для объекта CubeSid = 1 кг, для объекта CubeNancy = 100 кг. Запустите сцену. Какой из двух кубов быстрее достигнет земли и почему? Дайте развернутый ответ:

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Два куба (CubeSid, масса – 1 кг; и CubeNancy, масса – 100 кг) упадут на CubeGround в одно время, так как параметр “Mass” компонента RigidBody не влияет на скорость падения объектов. Данный параметр влияет лишь на то, как тело взаимодействует с другими RigidBody.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.5 Измените значение свойства Drag внутри компонента Rigidbody так, чтобы CubeSid достигал земли быстрее чем CubeNancy.

2.6 Дополните сцену сферой и эстокадой, по которой будет скатываться сфера с компонентом физии твердого тела Rigidbody. Установите массу сферы равную 100 кг, размер оставьте по умолчанию. Поместите сферу в верхней части эстокады, а кубы Sid & Nancy будут помещаться в нижней части с целью тестирования механики:

![image](https://github.com/user-attachments/assets/5b0d9f54-7f04-4cd8-85c2-0f001ba458c6)

## Создал сцену

![image](https://github.com/user-attachments/assets/9e8d84e6-d79c-47bd-b063-558a2eeac7e9)

2.7 Протестируйте наезд сферы на кубы разной массы (1 и 100 кг). Опишите характер столкновения, влияет ли параметр Drag (если да, — то как?)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
При столкновении Sphere массой 100 кг с CubeSid массой 1 кг, сфера продолжает своё движение по начатой траектории, сдвигая при этом куб, пока не достигнет конца платформы. При столкновении Sphere массой 100 кг с CubeNancy массой 100 кг, сфера ударяется о куб, после чего отскакивает в обратном направлении, сдвигая при этом куб на пару сотых единиц (сам куб переваливается на дальнее ребро, после чего возвращается в исходное положение – лежит одной гранью на земле). При изменении параметра Drag (поставил для CubeNancy значения 1000, затем 10000), можно сказать, что взаимодействие сферы и куба поменялось – куб стал меньше наклоняться на дальнее ребро (Drag = 1000), а в конке просто начал скользить по земле (Drag = 10000).
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.8 Модифицируйте сцену для тестирования параметров Drag и Angular Drag:

![image](https://github.com/user-attachments/assets/327e3dda-6220-441c-a763-b6f90903c6c0)

## Модифицировал сцену

![image](https://github.com/user-attachments/assets/4f10b368-f6ea-4175-b5e9-38b2a63550c4)


2.9 Протестируйте, что произойдет если указать разные значения для Drag и Angular Drag. Имеет ли это какую-то практическую ценность? Почему по умолчанию значение Angular Drag близко к нулю, но не равно ему? Проверьте что произойдет, если указать значение Angular Drag = 0. Дайте развернутый ответ:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Если указать разные значения для Drag и Angular Drag, могу предположить, что Drag отвечает за сопротивление среде а Angular drag за вращение вокруг оси. С помощью этих параметров можно обыграть смену среды объекта, например, погружение в воду или добавить эффект при столкновении.
По умолчанию значение Angular Drag близко к нулю, но не равно ему, потому что Angular Drag влияет на замедление вращения объекта, а значение по умолчанию в 0,05 позволяет сделать физику более стабильной.
|Если указать значение Angular Drag = 0, то объект будет совершать больше оборотов в сравнении со значениями Angular Drag больших нуля, по сути, можно сказать, что на объект перестают действовать силы, препятствующие его вращению/пропадает сопротивление среды.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.10 Назначьте на платформу Stage компонент Rigidbody и отключите гравитацию (Use Gravity). Проверьте, что произойдет при запуске сцены.

## Назначил на платформу Stage компонент Rigidbody и отключил гравитацию

![image](https://github.com/user-attachments/assets/17c34d71-7c0f-4a7f-8ef2-6756dac9130f)

2.11 Во вкладке Project Settings - Physics увеличьте значение силы гравитации. Подберите такое значение силы, при котором скорость падения достаточно большая для того, чтобы движок не успел обработать столкновение кубов Sid & Nancy с платформами Stage и Ground. В некоторых случаях можно добавиться интересного эффекта:

![image](https://github.com/user-attachments/assets/25f89c9e-49d5-43ee-b91e-5d3b1d2b7060)

Напишите найденное значение и от чего оно зависит (по вашему мнению):
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Где-то после значения Physics -300 куб с массой 100 кг проходит сквозь Ground, после значения -7000 куб проходит через Stage т.к обработчик не успевает установить столкновение этих объектов.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.12 Верните значение гравитации к настройкам по умолчанию.

2.13 Для объекта Stage зафиксируйте свойство FreezePosition внутри компонента Rigidbody таким образом, чтобы объект вращался вокруг оси, не падая вниз. Укажите, как должна выглядеть настройка FreezePosition?

![image](https://github.com/user-attachments/assets/5b6e614b-e2fd-467f-a515-8cefdffe7036)

-------------------------------------------------------------------------------------------------------------------------------------------------------------
Чтобы Stage вращался вокруг своей оси, в параметре FreezePosition внутри компонента RigidBody нужно выбрать фиксацию положения по всем трём осям (X, Y, Z).
-------------------------------------------------------------------------------------------------------------------------------------------------------------

2.14 isKinematic позволяет сделать объект нефизическим. Если поставить галочку isKinematic, — то объект будет жестко стоять на месте. При этом управлять кинематическими свойствами объекта можно во время выполнения сцены. Запустите сцену повторно и активируйте свойство isKinematic на объекте Stage во время вращения. Что произойдет, если галочку вновь отключить при запущенной сцене? Продолжит ли платформа своё вращение?

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
При включении галочки на параметре isKinematic после запуска сцены вращение платформы Stage прекратится, при этом, если галочку вновь отключить, платформа не начнёт вращаться.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.15 Поднимете объект Biba на высоту 1000 метров и запустите сцену. Дождитесь момента, когда куб достигнет земли Ground при падении. По какой причине куб проскакивает землю, не останавливаясь? Какие могут быть способы решения этой проблемы?

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Куб проскакивает землю из-за долгого расчёта физики (не успевает сделать расчёты, чтобы куб, сталкиваясь с землёй, успел остановиться; не может успеть просчитать их взаимодействие). Данная проблема решается с помощью настройки коллизии (“Collision Detection”): “Позволяет настроить RigidBody для непрерывного обнаружения столкновений, которое используется для предотвращения прохождения быстро движущихся объектов через другие объекты без обнаружения столкновений. Для достижения наилучших результатов установите для этого значения значение CollisionDetectionMode.ContinuousDynamic. При столкновении двух быстро движущихся объектов (пули, машины) нужно установите значение CollisionDetectionMode.Continuous. Эти два параметра сильно влияют на производительность физики.”
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.16 В скрипт файле ниже приведён пример, в котором происходит управление свойствами компонента RigidBody при нажатии на кнопку Space. Для работы созданный скрипт-файл следует подключить к объекту, свойствами которого планируется управлять при нажатии на клавишу Space:

```C#

using UnityEngine;

public class RigidbodyMod : MonoBehaviour
{
    private Rigidbody _rb;

    void Start()
    {
        _rb = GetComponent<Rigidbody>();
    }

    void Update()
    {
        if(Input.GetKeyDown(KeyCode.Space)) 
        {
            //_rb.isKinematic = true;
            _rb.mass= 1.0f;
            _rb.drag = 0;
            _rb.angularDrag = 0.05f;
            _rb.useGravity= true;
        }
    }
}

```
2.17 Используя этот сценарий и знания, полученные в работе, доработайте игровую сцену и создайте “уникальный интерактив”. Часть действий на сцене должны запускаться при нажатии клавиш клавиатуры.

# Изменённый скрипт для сферы.

![image](https://github.com/user-attachments/assets/d12581f6-9438-4473-940d-c653d3481540)

# Изменённый скрипт для куба Boba.

![image](https://github.com/user-attachments/assets/c957775f-f5f7-4ea9-9f78-0d7b5e5ee3c8)

2.18 Напишите развернутый вывод по проделанной работе. Как знания свойств компонентов RigidBody помогут в создании интерактивных приложений, игр и симуляторов?

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
В ходе данной работы познакомился с таким физическим компонентом, как RigidBody; провёл различные эксперименты, изменяя параметры данного компонента (Mass, Drag. AngularDrag, UseGravity, isKinematic, FreezePosition, CollisiionDetection); настроил изменение некоторых параметров путём обработки события нажатия на клавишу. Знания свойств, изученныe и полученные в ходе данной работы, помогут в реализации различных игровых механик (эффект перехода из одной среды в другую; взаимодействие между объектами разной массы; эффект “заморозки” с помощью параметра isKinematic; наблюдение физических явлений по контакту двух тел
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
