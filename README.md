# Практическая работа №1. Знакомство с Android Studio
#### Цель работы: Изучение интерфейса Android studio и создание первого простого приложения.
Выполнил ИНС-б-о-24-1, Пузанов Александр Александрович

Ход выполнения:

#### 1. Скачанное приложение

![Рисунок1.png](%D0%BF%D0%B8%D0%BA%D1%87%D0%B8/%D0%BB%D0%B0%D0%B1%D0%B01/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BE%D0%BA1.png)
#### 2. Созданный проект:

![img.png](%D0%BF%D0%B8%D0%BA%D1%87%D0%B8/%D0%BB%D0%B0%D0%B1%D0%B01/img.png)
#### 3. Изменённое имя приложения:

![img_1.png](%D0%BF%D0%B8%D0%BA%D1%87%D0%B8/%D0%BB%D0%B0%D0%B1%D0%B01/img_1.png)
#### 4. Дата рождения:
Код:
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            AlexanderPusanovTheme {
                Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                    Box(
                        modifier = Modifier
                            .fillMaxSize()
                            .padding(innerPadding),
                        contentAlignment = Alignment.Center
                    ) {
                        Text(
                            text = "Дата рождения: 01.01.2000",
                            fontSize = 20.sp,
                            color = Color.Black
                        )
                    }
                }
            }
        }
    }
}
```
Результат:

![img_2.png](%D0%BF%D0%B8%D0%BA%D1%87%D0%B8/%D0%BB%D0%B0%D0%B1%D0%B01/img_2.png)
#### 5. Синий круг, занимающий половину площади экрана
Код:
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val circleView = CircleView(this)
        setContentView(circleView)
    }
}

class CircleView(context: Context) : View(context) {
    private val paint = Paint().apply {
        color = Color.BLUE
        isAntiAlias = true
    }

    override fun onDraw(canvas: Canvas) {
        super.onDraw(canvas)

        val width = width.toFloat()
        val height = height.toFloat()

        val radius = Math.sqrt((width * height / 2 / Math.PI)).toFloat()

        canvas.drawCircle(width / 2, height / 2, radius, paint)
    }
}
```
Результат:

![img_3.png](%D0%BF%D0%B8%D0%BA%D1%87%D0%B8/%D0%BB%D0%B0%D0%B1%D0%B01/img_3.png)
#### 6. Легковой автомобиль (вариант 2)
Код:
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContentView(CarView(this))
    }
}

class CarView(context: Context) : View(context) {

    private val paint = Paint().apply {
        isAntiAlias = true
        style = Paint.Style.FILL
    }

    override fun onDraw(canvas: Canvas) {
        super.onDraw(canvas)

        // Кузов (синий)
        paint.color = Color.BLUE
        canvas.drawRect(100f, 400f, 800f, 550f, paint)

        // Верх (ломаная линия)
        paint.color = Color.CYAN
        val path = Path()
        path.moveTo(200f, 400f)
        path.lineTo(300f, 300f)
        path.lineTo(600f, 300f)
        path.lineTo(700f, 400f)
        path.close()
        canvas.drawPath(path, paint)

        // Колеса (черные)
        paint.color = Color.BLACK
        canvas.drawCircle(250f, 550f, 80f, paint)
        canvas.drawCircle(650f, 550f, 80f, paint)

        // Окна (белые)
        paint.color = Color.WHITE
        val window = Path()
        window.moveTo(320f, 380f)
        window.lineTo(380f, 320f)
        window.lineTo(580f, 320f)
        window.lineTo(620f, 380f)
        window.close()
        canvas.drawPath(window, paint)
    }
}
```
Результат:

![img_4.png](%D0%BF%D0%B8%D0%BA%D1%87%D0%B8/%D0%BB%D0%B0%D0%B1%D0%B01/img_4.png)

### Вывод:

В ходе выполнения практической работы было освоено базовое взаимодействие с Android Studio и создано простое мобильное приложение на языке Kotlin. Были изучены основные элементы интерфейса (виджеты), принципы их размещения и настройки.

Также были получены навыки работы с пользовательскими компонентами: реализована отрисовка графических примитивов с помощью класса Canvas, создан собственный View с переопределением метода onDraw(). В рамках задания построены фигуры (круг и автомобиль), использованы цвета и ломаные линии.

### Контрольные вопросы:

1. Понятие виджета
Виджет - это элемент пользовательского интерфейса (например, кнопка, текстовое поле), используемый для отображения информации и взаимодействия с пользователем.

2. Графические примитивы
Графические примитивы - это базовые элементы для рисования (линии, круги, прямоугольники, пути), используемые при работе с Canvas.

3. Переопределение метода
Переопределение - это изменение реализации метода родительского класса в дочернем классе.

4. Наследование
Наследование - механизм ООП, при котором один класс получает свойства и методы другого класса.
