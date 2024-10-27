using System;
using System.Collections.Generic;

namespace ScheduleMaker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Добро пожаловать в Schedule Maker!");

            // Создаем новое расписание
            Schedule schedule = new Schedule();

            // Добавляем занятия
            schedule.AddLesson("Математика", "10:00", "11:00", "Понедельник");
            schedule.AddLesson("Физика", "11:00", "12:00", "Понедельник");
            schedule.AddLesson("История", "10:00", "11:00", "Вторник");

            // Выводим расписание
            schedule.PrintSchedule();

            Console.ReadKey();
        }
    }

    // Класс для представления расписания
    class Schedule
    {
        private List<Lesson> lessons;

        public Schedule()
        {
            lessons = new List<Lesson>();
        }

        // Добавляем новое занятие
        public void AddLesson(string subject, string startTime, string endTime, string day)
        {
            lessons.Add(new Lesson(subject, startTime, endTime, day));
        }

        // Выводим расписание
        public void PrintSchedule()
        {
            Console.WriteLine("\nРасписание:");
            foreach (Lesson lesson in lessons)
            {
                Console.WriteLine($"{lesson.Day}: {lesson.Subject} ({lesson.StartTime} - {lesson.EndTime})");
            }
        }
    }

    // Класс для представления занятия
    class Lesson
    {
        public string Subject { get; set; }
        public string StartTime { get; set; }
        public string EndTime { get; set; }
        public string Day { get; set; }

        public Lesson(string subject, string startTime, string endTime, string day)
        {
            Subject = subject;
            StartTime = startTime;
            EndTime = endTime;
            Day = day;
        }
    }
}
