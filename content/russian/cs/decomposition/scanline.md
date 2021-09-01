---
title: Сканирующая прямая
---

## Сканлайн

Мы уже разбирали базовые задачи на сканлайн в теме С++.

## Повторение

Дано $n$ отрезков (задаются своим левым и правым концом) и $m$ точек,
требуется найти точку, которую покрывают наибольшее количество
отрезков.

## Идея

Мы могли бы для каждой точки, честно за $O(n)$ найти количество
отрезков, которые ее покрывают.

Но можно сделать это эффективнее, если обрабатывать отрезок, который мы
встречаем, сразу для всех точек, которые он покрывает.

## Решение

Сделаем события трех видов :

1\) Начинается новый отрезок в точке $x$

2\) Требуется ответить на запрос сколько отрезков покрывают данную точку
$x$.

3\) Закрывается отрезок в точке $x$.

Отсортируем запросу по координате и пройдемся по отсортированному списку
событий, поддерживая, сколько отрезков сейчас покрывают данную точку.

## Асимптотика

Сам проход работает за $O(n)$, но нам еще нужно отсортировать события,
поэтому суммарно решение работает за $O(n\\log(n))$

## Новая задача

Дано $n$ прямоугольников, требуется найти площадь их объединения.

## Идея

Пользуясь предыдущим подходом можно было бы создать события :

1\) прямоугольник начинается в точке $x$ и занимает отрезок с $y_{1}$
по $y_{2}$

2\) прямоугольник заканчивается в точке $x$ и занимает отрезок с
$y_{1}$ по $y_{2}$

Затем просто поддерживать массив для каждой точки по $y$-координате
сколько прямоугольников ее поддерживает и тогда для каждого
события, надо прибавить к ответу (разницу между $x$ этого события
и предыдущего) $\\cdot$ количество точек, которых покрывает хоть один
прямоугольник.

Это решение работает за $nY$, что достаточно долго, но теперь мы знаем
структуры, которая умеет такие запросы быстрее.