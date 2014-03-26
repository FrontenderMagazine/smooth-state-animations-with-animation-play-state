# Красивые анимации состояний с помощью animation-play-state

Если CSS анимация применяется сразу, при загрузке страницы, все просто. Ты просто 
используешь css-свойство `animation` и все. Но что делать, если анимация 
применяется к определенному состоянию, например по :hover, :active, :focus или
просто изменению класса вызванного с помощью JavaScript?

Простое решение будет выглядеть приблизительно так:

<iframe src="http://dabblet.com/gist/9786900" width="100%" height="400"></iframe>

Однако, это значит, что когда вы уберете курсор с элемента он резко вернется в 
свое начальное состояние (в котором отсутствует вращение). В большинстве случаев
будет предпочтительно остановить анимацию на последнем показанном кадре, и оставить
в таком состоянии до того момента, как пользователь снова наведет курсор на элемент.
Что бы добиться такого эффекта мы можем применить анимацию изначально добавив 
`animation-play-state: paused;` и изменять значение этого свойства по :hover на
`animation-play-state: running;`. Вот что у нас получится:

<iframe src="http://dabblet.com/gist/9787052" width="100%" height="400"></iframe>

Я обнаружила это, когда помогала моему другу [Джулиану][1] (Julian) с его 
[одностраничником][2]. Когда ты наводишь курсор на элемент `figure` содержащий 
фотографию, она начинает скролится, но когда он выходит за границы элемента, 
то фотография не возвращается в свое начальное состояние, что смотрелось бы 
весьма скверно.


Но будьте осторожны, пока это все работает не слишком хорошо, например, есть баги 
с отрисовкой в Firefox и IE *(примечание переводчика: я таковых не заметил.)*, 
кроме того картину портят несколько css-свойств, которые пока не поддерживаются 
(например, `baseline-shift` в SVG), но все это проблемы, которые я буду решать
в следующий раз, когда столкнусь с ними выполняя очередную задачу и все это 
опять выльется в то, что работа займет намного больше, чем та пара часов, которые
я планировала на неё потратить. Кроме анимаций на этом одностраничке вас могут
заинтересовать пуговицы, сделанные на чистом css (видите, чего я понаделала?) или
тиснение на кожаной рамке вокруг фотографии. Твидовый фон и цветовая гамма — 
заслуга [Лауры Калбаг][3] (Laura Kalbag). Кроме того в процессе этого проекта
я экспериментировала с SASS и работать с ним оказалось намного приятнее, чем с 
LESS, так что в случаях, когда мне нужен препроцессор буду теперь использовать
его.


![Screenshot][4]

 [1]: http://twitter.com/juliancheal
 [2]: http://juliancheal.co.uk
 [3]: https://twitter.com/laurakalbag
 [4]: img/Screen-Shot-2014-01-09-at-14.45.40--1024x558.png