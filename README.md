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



