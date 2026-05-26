# Лабораторная работа №3. Обработка событий клика.
Выполнила: Тристан Владислава Дмитриевна ИНС-б-о-24-2 
# Цель работы 
Изучить механизм обработки событий в Android. Научиться обрабатывать нажатия на элементы интерфейса (кнопки) с помощью декларативного подхода (XML) и программного подхода (Java). Освоить работу с идентификаторами ресурсов и Toast-уведомления.
# Ход работы
Задание 1. Создание проекта и верстка экрана

1.1. Откройте Android Studio и создайте проект с шаблоном Empty Views Activity. Назовите проект ClickProcessingLab. 

1.2. Откройте файл activity_main.xml. Убедитесь, что корневым элементов является LinearLayout с вертикальной ориентацией. Если это не так, оберните существующий TextView в LinearLayout. 

1.3. Добавьте под стандартным TextView кнопку со следующими параметрами: 

  android:id="@+id/button1"
  
  android:layout_width="175dp"
  
  android:layout_height="75dp"
  
  android:text="Кнопка"

```java
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center_horizontal"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:textSize="18sp"
        android:layout_marginBottom="20dp" />

    <Button
        android:id="@+id/button1"
        android:layout_width="175dp"
        android:layout_height="75dp"
        android:text="Кнопка"
        android:textSize="16sp" />

</LinearLayout>
```

<img width="558" height="847" alt="Снимок экрана 2026-03-27 130257" src="https://github.com/user-attachments/assets/d3375cd7-a8e2-4a45-8b2b-b6e1f2b9c89c" />


Задание 2. Обработка клика через XML-атрибут onClick (Декларативный подход)

2.1. В файле activity_main.xml добавьте к нопке атрибут onClick 

```java

<Button
    ...
    android:onClick="onButtonClick" />
```
Задание 3: Обработка клика через setOnClickListener (Программный подход)

MainActivity.java

```java
package com.example.clickprocessinglab;

import android.os.Bundle;
import android.view.View;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void onButtonClick(View view) {
        Toast.makeText(this, "Триста", Toast.LENGTH_SHORT).show();
    }
}
```

<img width="381" height="806" alt="Снимок экрана 2026-05-27 003759" src="https://github.com/user-attachments/assets/4f3000d1-61b7-497c-a7c1-ff58138a3146" />

Задание 4: Использование аргумента View для изменения нажатой кнопки 

Задание 4: Использование аргумента View для изменения нажатой кнопки
Модифицирован код из задания 3: внутри метода onClick изменён текст самой нажатой кнопки.

```java
  myButton.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
      Button clickedButton = (Button) v;
      clickedButton.setText("Нажата!");
      // Или в одну строку: ((Button)v).setText("Нажата!");
      Toast.makeText(MainActivity.this, "Клик обработан в коде!", Toast.LENGTH_SHORT).show();
    }
  });
```

Задание 5: Работа с несколькими кнопками

activity_main.xml

```java
  <Button
      android:id="@+id/button1"
      android:layout_width="175dp"
      android:layout_height="75dp"
      android:text="Кнопка 1" />

  <Button
      android:id="@+id/button2"
      android:layout_width="175dp"
      android:layout_height="75dp"
      android:text="Кнопка 2" />

  <Button
      android:id="@+id/button3"
      android:layout_width="175dp"
      android:layout_height="75dp"
      android:text="Кнопка 3" />
```

MainActivity.java

```java
  Button button1 = findViewById(R.id.button1);
  Button button2 = findViewById(R.id.button2);
  Button button3 = findViewById(R.id.button3);

  button1.setOnClickListener(new View.OnClickListener() {
  @Override
  public void onClick(View v) {
      //Button clickedButton = (Button) v;
      //clickedButton.setText("Нажата!");
      // Или в одну строку: ((Button)v).setText("Нажата!");
      ((Button)v).setText("Нажата кнопка 1");
      Toast.makeText(MainActivity.this, "Нажата кнопка 1", Toast.LENGTH_SHORT).show();
    }
  });

  button2.setOnClickListener(new View.OnClickListener() {
  @Override
  public void onClick(View v) {
      ((Button)v).setText("Нажата кнопка 2");
      Toast.makeText(MainActivity.this, "Нажата кнопка 2", Toast.LENGTH_SHORT).show();
    }
  });

  button3.setOnClickListener(new View.OnClickListener() {
  @Override
  public void onClick(View v) {
      ((Button)v).setText("Нажата кнопка 3");
      Toast.makeText(MainActivity.this, "Нажата кнопка 3", Toast.LENGTH_SHORT).show();
    }
  });
```

<img width="376" height="828" alt="image_7 (1)" src="https://github.com/user-attachments/assets/a0b5cbd6-f23f-462c-9d2a-b92fc7bdaafe" />


# Контрольные вопросы

1. Что такое ViewBinding и в чем его преимущество перед findViewById()?
ViewBinding — это механизм генерации класса-привязки, который содержит прямые ссылки на все View с id из

XML-разметки.

Преимущества:

Безопасность типов — нет необходимости в приведении типов
Защита от NullPointerException — все ссылки гарантированно инициализированы
Удобство — автодополнение кода и проверка на этапе компиляции
Подключение: В build.gradle (модуль app):

```java
android {
    buildFeatures {
        viewBinding true
    }
}
```


2. В чем разница между декларативной (XML-атрибут onClick) и программной (setOnClickListener) подпиской на событие? Когда какой способ предпочтительнее?
3. 
Декларативный подход (android:onClick в XML) проще и быстрее для простых случаев, но менее гибкий — метод должен быть public в Activity. Программный подход (setOnClickListener в Java-коде) более гибкий, позволяет динамически менять обработчики, использовать анонимные классы и лямбда-выражения. Декларативный предпочтителен для простых UI, программный — для сложной логики, динамических интерфейсов и когда нужно менять поведение во время выполнения.

3.Что произойдет, если в методе-обработчике, указанном в XML, изменить сигнатуру (например, убрать параметр View v)? Почему?

Приложение упадет с ошибкой IllegalStateException при запуске или при нажатии на кнопку, потому что система Android через рефлексию ищет метод с точной сигнатурой: public void methodName(View v). Если сигнатура не совпадает (нет параметра View, другой тип возвращаемого значения или метод не public), система не сможет вызвать обработчик и выбросит исключение с сообщением о том, что метод не найден.

4. Опишите жизненный цикл Activity. В каком методе (onCreate, onStart, onResume) лучше всего инициализировать слушатели для кнопок и почему?
5. 
Жизненный цикл Activity: onCreate() → onStart() → onResume() → (Activity активна) → onPause() → onStop() → onDestroy(). Инициализировать слушатели лучше всего в onCreate(), потому что этот метод вызывается один раз при создании Activity, когда интерфейс уже загружен (после setContentView), но Activity еще не видна пользователю. Это обеспечивает однократную инициализацию, лучшую производительность и избегает повторной настройки при каждом возврате к Activity (что произошло бы в onResume()).

5.Что такое анонимный внутренний класс? Как он используется при установке слушателей событий в Java?
Анонимный внутренний класс — это класс без имени, который объявляется и создается в одном выражении, обычно для однократного использования. Он используется при установке слушателей событий для реализации интерфейсов (например, View.OnClickListener) без создания отдельного именованного класса. Это позволяет писать компактный код, логика которого находится непосредственно в месте использования, но может привести к дублированию кода при множественных обработчиках.
