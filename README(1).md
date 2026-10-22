# PractiseWorkVar15

**Вариант 15.** Промышленный плавильный ковш металлургического завода (SmeltingLadle)

```csharp

using System;

class SmeltingLadle
{
    // Поля ковша
    private double _steelMass;
    private int _temperature;
    private double _wear;
    private int _minutes;

    // Масса стали
    public double SteelMass
    {
        get { return _steelMass; }
        set
        {
            if (value >= 0)
                _steelMass = value;
            else
                _steelMass = 0;
        }
    }

    // Температура металла
    public int Temperature
    {
        get { return _temperature; }
        set
        {
            if (value < 1200)
                _temperature = 1200;
            else if (value > 1750)
                _temperature = 1750;
            else
                _temperature = value;
        }
    }

    // Износ футеровки в процентах
    public double Wear
    {
        get { return _wear; }
        set
        {
            if (value < 0)
                _wear = 0;
            else if (value > 100)
                _wear = 100;
            else
                _wear = value;
        }
    }

    // Время после выпуска стали
    public int Minutes
    {
        get { return _minutes; }
        set
        {
            if (value >= 0)
                _minutes = value;
            else
                _minutes = 0;
        }
    }

    // Проверка износа футеровки
    public bool RefractoryBreachRisk
    {
        get { return Wear > 85; }
    }

    // Начальные значения ковша
    public SmeltingLadle()
    {
        SteelMass = 50;
        Temperature = 1500;
        Wear = 10;
        Minutes = 0;
    }

    // Создание ковша с заданными параметрами
    public SmeltingLadle(double steelMass, int temperature,
                         double wear, int minutes)
    {
        SteelMass = steelMass;
        Temperature = temperature;
        Wear = wear;
        Minutes = minutes;
    }

    // Выпуск стали из ковша
    public void PourSteel(double tons)
    {
        if (tons > 0 && tons <= SteelMass)
        {
            SteelMass -= tons;
            Wear += 2;
            Console.WriteLine("Выпущено стали: " + tons + " т");
        }
        else
        {
            Console.WriteLine("Нельзя выпустить столько стали!");
        }
    }

    // Нагрев металла
    public void HeatMetal(int degrees)
    {
        if (degrees > 0)
        {
            Temperature += degrees;
            Console.WriteLine("Металл нагрет на " + degrees + " градусов");
        }
    }

    // Вывод информации о ковше
    public void PrintStatus()
    {
        Console.WriteLine("Масса стали: " + SteelMass + " т");
        Console.WriteLine("Температура: " + Temperature + " °C");
        Console.WriteLine("Износ футеровки: " + Wear + "%");
        Console.WriteLine("Время после выпуска: " + Minutes + " мин");
        Console.WriteLine("Риск повреждения футеровки: " +
                          RefractoryBreachRisk);
        Console.WriteLine("----------------------------");
    }
}

class Program
{
    static void Main()
    {
        // Создаем три ковша с разными параметрами
        SmeltingLadle[] ladles =
        {
            new SmeltingLadle(),
            new SmeltingLadle(70, 1600, 40, 5),
            new SmeltingLadle(90, 1700, 90, 10)
        };

        // Четыре шага работы
        for (int step = 1; step <= 4; step++)
        {
            Console.WriteLine("ШАГ " + step);

            // Обрабатываем каждый ковш
            foreach (SmeltingLadle ladle in ladles)
            {
                ladle.Minutes += 10;
                ladle.HeatMetal(20);
                ladle.PourSteel(5);
            }

            Console.WriteLine();
        }

        // Выводим результаты
        Console.WriteLine("ИТОГОВОЕ СОСТОЯНИЕ");

        foreach (SmeltingLadle ladle in ladles)
        {
            ladle.PrintStatus();
        }
    }
}

```
<img width="979" height="512" alt="изображение" src="https://github.com/user-attachments/assets/35d717a6-fc95-4b09-9c07-f2459217f070" />
<img width="979" height="512" alt="изображение" src="https://github.com/user-attachments/assets/de14c926-21aa-44ef-ab24-36541eef5969" />
<img width="979" height="512" alt="изображение" src="https://github.com/user-attachments/assets/f83719ca-038e-431a-bf7b-2473d48c6fcd" />


