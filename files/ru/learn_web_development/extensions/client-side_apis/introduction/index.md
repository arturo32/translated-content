---
title: Введение в web APIs
slug: Learn_web_development/Extensions/Client-side_APIs/Introduction
---

{{LearnSidebar}}{{NextMenu("Learn/JavaScript/Client-side_web_APIs/Manipulating_documents", "Learn/JavaScript/Client-side_web_APIs")}}

Начнём с рассмотрения того что представляют собой API на высоком уровне и выясним, как они работают, как их использовать в своих программах и как они структурированы. Также рассмотрим основные виды API и их применение.

| Необходимые знания: | Базовая компьютерная грамотность, понимание основ [HTML](/ru/docs/Learn_web_development/Core/Structuring_content) и [CSS](/ru/docs/Learn/CSS), основы JavaScript (см. [первые шаги](/ru/docs/conflicting/Learn_web_development/Core/Scripting), [building blocks](/ru/docs/Learn_web_development/Core/Scripting), [объекты JavaScript](/ru/docs/Learn_web_development/Extensions/Advanced_JavaScript_objects)). |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Цель:               | Познакомиться с API, выяснить что они могут делать и как их использовать.                                                                                                                                                                                                                                                                                                                                       |

## Что такое API?

Интерфейс прикладного программирования (Application Programming Interfaces, APIs) — это готовые конструкции языка программирования, позволяющие разработчику строить сложную функциональность с меньшими усилиями. Они "скрывают" более сложный код от программиста, обеспечивая простоту использования.

Для лучшего понимания рассмотрим аналогию с домашними электросетями. Когда вы хотите использовать какой-то электроприбор, вы просто подключаете его к розетке, и всё работает. Вы не пытаетесь подключить провода напрямую к источнику тока — делать это бесполезно и, если вы не электрик, сложно и опасно.

![Подключение к разетке](plug-socket.png)

_Image source: [Overloaded plug socket](https://www.flickr.com/photos/easy-pics/9518184890/in/photostream/lightbox/) by [The Clear Communication People](https://www.flickr.com/photos/easy-pics/), on Flickr._

Точно также, если мы хотим, например, программировать 3D графику, гораздо легче сделать это с использованием API, написанных на языках высокого уровня, таких как JavaScript или Python.

> [!NOTE]
> Смотрите также [API в словаре](/ru/docs/Glossary/API).

### API клиентской части JavaScript

Для JavaScript на стороне клиента, в частности, существует множество API. Они не являются частью языка, а построены с помощью встроенных функций JavaScript для того, чтобы увеличить ваши возможности при написании кода. Их можно разделить на две категории:

- **API браузера** встроены в веб-браузер и способны использовать данные браузера и компьютерной среды для осуществления более сложных действий с этими данными. К примеру, [Web Audio API](/ru/docs/Web/API/Web_Audio_API) предоставляет конструкции JavaScript для работы с аудио в браузере, например,можно взять звуковую дорожку, изменить её громкость или применить к ней эффекты. На самом деле, в браузере выполняется сложный низкоуровневый код (например, на C++ или Rust) для обработки звука, но, как было сказано выше, эти детали скрыты благодаря API.
- **Сторонние API** не встроены в браузер по умолчанию. Такие API и информацию о них обычно необходимо искать в интернете. Например, [Twitter API](https://dev.twitter.com/overview/documentation) позволяет размещать последние твиты (tweets) на вашем веб-сайте. В данном API определён набор конструкций, осуществляющих запросы к сервисам Twitter и возвращающих определённые данные.

![Схема, описывающая работу API браузера](browser.png)

### Взаимодействие JavaScript, API и других средств JavaScript

Итак, выше мы поговорили о том, что такое JavaScript API клиентской части и как они связаны с языком JavaScript. Давайте теперь тезисно запишем основные понятия и определим назначение других инструментов JavaScript:

- JavaScript — Язык программирования сценариев высокого уровня, встроенный в браузер, позволяющий создавать функциональность веб-страниц/приложений. Отметим, что JavaScript также доступен на других программных платформах, таких как [Node.js](/ru/docs/Learn_web_development/Extensions/Server-side/Express_Nodejs/Introduction). Но пока не будем останавливаться на этом.
- API браузера (Browser APIs) — конструкции, встроенные в браузер, построенные на основе языка JavaScript, предназначенные для облегчения разработки функциональности.
- Сторонние API (Third party APIs) — конструкции, встроенные в сторонние платформы (такие как Twitter, Facebook) позволяющие вам использовать часть функциональности этих платформ в своих собственных веб-страницах/приложениях (например, показывать последние Твиты на вашей странице).
- Библиотеки JavaScript — Обычно один или несколько файлов, содержащих [пользовательские (custom) функции](/ru/docs/Learn_web_development/Core/Scripting/Functions#custom_functions). Такие файлы можно прикрепить к веб-странице, чтобы ускорить или предоставить инструменты для написания общего функциональности. Примеры: jQuery, Mootools и React.
- JavaScript фреймворки (frameworks) — cледующий шаг в развитии разработки после библиотек. Фреймворки JavaScript (такие как Angular и Ember) стремятся к тому, чтобы быть набором HTML, CSS, JavaScript и других технологий, после установки которого можно "писать" веб-приложение с нуля. Главное различие между фреймворками и библиотеками — "обратное направление управления" ( "Inversion of Control" ). Вызов метода из библиотеки происходит по требованию разработчика. При использовании фреймворка — наоборот, фреймворк производит вызов кода разработчика.

## На что способны API?

Широкое разнообразие API в современных браузерах позволяет наделить ваше приложение большими возможностями. Достаточно посмотреть список на странице [MDN APIs index page](/ru/docs/Web/API).

### Распространённые API браузера

В частности, к наиболее часто используемым категориям API (и которые мы рассмотрим далее в этом модуле) относятся :

- **API для работы с документами**, загруженными в браузер. Явный пример — [DOM (Document Object Model) API](/ru/docs/Web/API/Document_Object_Model), позволяющий работать с HTML и CSS — создавать, удалять и изменять HTML, динамически изменять вид страницы и т.д. Любое всплывающее окно на странице или появляющееся "на ходу" содержимое — всё это благодаря DOM. Узнайте больше об этой категории API на странице [Работа с документами](/ru/docs/Learn_web_development/Core/Scripting/DOM_scripting).
- **API, принимающие данные от сервера**, часто используются, чтобы обновить небольшие части веб-страницы. Эта, казалось бы, малая деталь оказывает огромное влияние на производительность и поведение сайтов, так как нет необходимости перезагружать всю страницу целиком, если вам нужно просто обновить список товаров или новых доступных историй. Это также сделает приложение или сайт более отзывчивым и "живым". Список API, благодаря которым это возможно, включает: [`XMLHttpRequest`](/ru/docs/Web/API/XMLHttpRequest) и [Fetch API](/ru/docs/Web/API/Fetch_API). Вы также могли встретить термин **Ajax**, описывающий эту технологию. Узнать больше об этой категории API на странице [Получение данных от сервера](/ru/docs/Learn_web_development/Core/Scripting/Network_requests).
- **API для работы с графикой** широко поддерживаются браузерами, самые популярные: [Canvas](/ru/docs/Web/API/Canvas_API) и [WebGL](/ru/docs/Web/API/WebGL_API), позволяющие программно изменять данные о пикселях, содержащиеся в элементе HTML {{htmlelement("canvas")}} для создания 2D и 3D изображений. Например, вы можете нарисовать фигуры, скажем, прямоугольники или круги, импортировать изображение в canvas и применить к нему фильтры, такие как сепия или оттенки серого с помощью Canvas API, или создать сложное 3D-изображение с освещением и текстурами, используя WebGL. Такие API часто используют в сочетании с API создания анимационных циклов (таких как {{domxref("window.requestAnimationFrame()")}}) и другими для создания постоянно меняющегося изображения на экране, как в мультфильмах или играх .
- **[Аудио и Видео API](/ru/docs/Apps/Fundamentals/Audio_and_video_delivery)** как {{domxref("HTMLMediaElement")}}, [Web Audio API](/ru/docs/Web/API/Web_Audio_API), и [WebRTC](/ru/docs/Web/API/WebRTC_API) позволяют делать действительно интересные вещи с мультимедиа. Например, создать собственный пользовательский интерфейс (User Interface, UI) для проигрывания аудио/видео, вывод на экран субтитров, записывать видео с веб-камеры для обработки в canvas (см. выше) или для передачи на другой компьютер в видео-конференции, применять звуковые эффекты к аудио-файлам (такие как gain, distortion, panning и т.д.).
- **API устройств** — в основном, это API для обработки и считывания данных с современных устройств удобным для работы веб-приложений образом. Например, [Geolocation API](/ru/docs/Web/API/Geolocation_API) позволяет считать данные о местоположении устройства. Другие примеры включают уведомление пользователя о появившемся обновлении для веб-приложения с помощью системных уведомлений (см. [Notifications API](/ru/docs/Web/API/Notifications_API)) или вибрации (см. [Vibration API](/ru/docs/Web/API/Vibration_API)).
- **API хранения данных на стороне пользователя** приобретают всё большее распространение в веб-браузерах — возможность хранить информацию на стороне клиента очень полезна, когда необходимо создать приложение, которое будет сохранять своё состояние между перезагрузками страницы, или даже работать, когда устройство не в сети. В данный момент доступно немало таких API. Например, простое хранилище данных в формате имя/значение (name/value) [Web Storage API](/ru/docs/Web/API/Web_Storage_API) или хранилище данных в формате таблиц [IndexedDB API](/ru/docs/Web/API/IndexedDB_API).

### Распространённые сторонние API

Существует множество сторонних API; некоторые из наиболее популярных, которые вы рано или поздно будете использовать, включают:

- [Twitter API](https://dev.twitter.com/overview/documentation) для добавления такой функциональности, как показ последних твитов на сайте.
- [Google Maps API](https://developers.google.com/maps/) для работы с картами на веб-странице (интересно, что Google Maps также использует этот API). Теперь это целый набор API, который может справляться с широким спектром задач, как свидетельствует [Google Maps API Picker](https://developers.google.com/maps/documentation/api-picker).
- [Набор Facebook API](https://developers.facebook.com/docs/) позволяет использовать различные части платформы Facebook в вашем приложении, предоставляя, например, возможность входа в систему с логином Facebook, оплаты покупок в приложении, демонстрация целевой рекламы и т.д.
- [YouTube API](https://developers.google.com/youtube/), предоставляющий возможность встраивать видео с YouTube на вашем сайте, производить поиск, создавать плейлисты и т.д.
- [Twilio API](https://www.twilio.com/) — фреймворк для встраивания функциональности голосовой и видео связи в вашем приложении, отправки SMS/MMS из приложения и т.д.

> [!NOTE]
> Вы можете найти информацию о гораздо большем количестве сторонних API в [Каталоге Web API](http://www.programmableweb.com/category/all/apis).

## Как работает API?

Работа разных JavaScript API немного отличается, но, в основном, у них похожие функции и принцип работы.

### Они основаны на объектах

Взаимодействие с API в коде происходит через один или больше [объектов JavaScript](/ru/docs/Learn_web_development/Extensions/Advanced_JavaScript_objects), которые служат контейнерами для информации, с которой работает API (содержится в свойствах объекта), и реализуют функциональность, которую предоставляет API (содержится в методах объекта).

> [!NOTE]
> Если вам ещё не известно как работают объекты, советуем вернуться назад и изучить модуль [Основы объектов JavaScript](/ru/docs/Learn_web_development/Extensions/Advanced_JavaScript_objects) прежде чем продолжать.

Вернёмся к примеру с Web Audio API — это довольно сложный API, состоящий из ряда объектов. Наиболее очевидные из них

- {{domxref("AudioContext")}}, представляющий [аудиограф](/ru/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_graphs), который содержит ряд полезных свойств и методов для управления воспроизведением звука в браузере.
- {{domxref("MediaElementAudioSourceNode")}} представляет элемент {{htmlelement("audio")}}, включающий в себя звук, которым можно управлять внутри аудиоконтекста или воспроизвести.
- {{domxref("AudioDestinationNode")}} представляет место назначения звука, то есть устройство вашего компьютера, которые фактически выводит его. Обычно это динамики или наушники.

Так как же эти объекты взаимодействуют? Если вы посмотрите на наш пример [simple web audio example](https://github.com/mdn/learning-area/blob/main/javascript/apis/introduction/web-audio/index.html) ([see it live also](https://mdn.github.io/learning-area/javascript/apis/introduction/web-audio/)), вы увидите следующий код:

```html
<audio src="outfoxing.mp3"></audio>

<button class="paused">Play</button>
<br />
<input type="range" min="0" max="1" step="0.01" value="1" class="volume" />
```

Прежде всего, добавляем элемент `audio`, с помощью которого встраиваем MP3 на страницу. Мы не включаем какие-либо элементы управления по умолчанию. Далее добавляем элемент {{htmlelement("button")}}, который будем использовать для воспроизведения и остановки музыки, и элемент {{htmlelement("input")}} с типом range, он понадобится для регулировки громкости трека во время его воспроизведения.</p>

Взглянем на JavaScript код этого примера.

Начнём с того, что создадим экземпляр конструктора `AudioContext`, с помощью которого будет манипулировать нашим треком.

```js
const AudioContext = window.AudioContext || window.webkitAudioContext;
const audioCtx = new AudioContext();
```

Далее создадим константы для наших `<audio>`, `<button>` и `<input>` элементов и воспользуемся методом {{domxref("AudioContext.createMediaElementSource()")}} для создания `MediaElementAudioSourceNode`, представляющий источник аудио, с которым будет воспроизводиться элемент `audio`.

```js
const audioElement = document.querySelector("audio");
const playBtn = document.querySelector("button");
const volumeSlider = document.querySelector(".volume");

const audioSource = audioCtx.createMediaElementSource(audioElement);
```

Затем включим пару обработчиков событий для переключения между воспроизведением и паузой при нажании на кнопку и сброса воспроизведения в начало, когда песня закончится:

```js
playBtn.addEventListener("click", () => {
  // проверить, находится ли контекст в приостановленном состоянии
  if (audioCtx.state === "suspended") {
    audioCtx.resume();
  }

  // если трек остановлен, то начать его проигрывать
  if (playBtn.getAttribute("class") === "paused") {
    audioElement.play();
    playBtn.setAttribute("class", "playing");
    playBtn.textContent = "Pause";
    // если трек воспроизводится, приостановить проигрывание
  } else if (playBtn.getAttribute("class") === "playing") {
    audioElement.pause();
    playBtn.setAttribute("class", "paused");
    playBtn.textContent = "Play";
  }
});

// если трек закончился
audioElement.addEventListener("ended", () => {
  playBtn.setAttribute("class", "paused");
  playBtn.textContent = "Play";
});
```

> [!NOTE]
> Обратите внимание, что методы `play()` и `pause()`, используемые для воспроизведения и приостановки дорожки, не являются частью Web Audio API. Они являются частью {{domxref("HTMLMediaElement")}} API, который отличается от Web Audio API, но тесно с ним связан.

Далее создадим объект {{domxref("GainNode")}} с помощью метода {{domxref("BaseAudioContext/createGain", "AudioContext.createGain()")}}, который можно использовать для регулировки громкости звука, и еще один обработчик событий, с помощью которого будем менять значение усиления (громкости) в зависимости от значения `<input type="range">`.

```js
// volume
const gainNode = audioCtx.createGain();

volumeSlider.addEventListener("input", () => {
  gainNode.gain.value = volumeSlider.value;
});
```

Наконец, чтобы всё заработало, соединим различные узлы в аудиографе с помощью метода {{domxref("AudioNode.connect()")}}, доступном на каждом узле этого типа:

```js
audioSource.connect(gainNode).connect(audioCtx.destination);
```

Звук начинается в источнике, который затем подключаетя к узлу усиления, чтобы можно было регулировать громкость звука. Затем узел усиления подключается к узлу назначения звука, чтобы его можно было воспроизвести на компьютере (по умолчанию свойство {{domxref("BaseAudioContext/destination", "AudioContext.destination")}} равно значению {{domxref(" AudioDestinationNode")}}, которое имеет доступ к аудио-оборудованию компьютера, например, к динамикам).

### У них узнаваемые точки входа

При использовании API убедитесь, что вы знаете где точка входа для API. В Web Audio API это довольно просто — экземпляр констуктора {{domxref("AudioContext")}}, возвращает объект, внутри которого доступны все полезные методы и свойства для манипуляции звуком.

Найти точку входа Document Object Model (DOM) API ещё проще — при применении этого API используется объект {{domxref("Document")}}, или экземпляр элемента HTML, с которым вы хотите каким-либо образом взаимодействовать, к примеру:

```js
const em = document.createElement("em"); // создаёт новый элемент em
const para = document.querySelector("p"); // ссылка на существующий элемент p
em.textContent = "Hello there!"; // присвоение текстового содержимого
para.appendChild(em); // встроить em внутрь para
```

Точки входа других API немного сложнее, часто подразумевается создание особого контекста, в котором будет написан код API. Например, объект контекста Canvas API создаётся получением ссылки на элемент {{htmlelement("canvas")}}, на котором вы хотите рисовать. Затем необходимо вызвать метод {{domxref("HTMLCanvasElement.getContext()")}}:

```js
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");
```

Всё, что мы хотим сделать с canvas после этого, достигается вызовом свойств и методов объекта содержимого (content) (который является экземпляром {{domxref("CanvasRenderingContext2D")}}), например:

```js
Ball.prototype.draw = function () {
  ctx.beginPath();
  ctx.fillStyle = this.color;
  ctx.arc(this.x, this.y, this.size, 0, 2 * Math.PI);
  ctx.fill();
};
```

> [!NOTE]
> Вы можете увидеть этот код в действии в нашем [bouncing balls demo](https://github.com/mdn/learning-area/blob/master/javascript/apis/introduction/bouncing-balls.html) (see it [running live](https://mdn.github.io/learning-area/javascript/apis/introduction/bouncing-balls.html) also).

### Они используют события для управления состоянием

Мы уже обсуждали события ранее в этом курсе, в нашей статье [Введение в события](/ru/docs/Learn_web_development/Core/Scripting/Events) — в ней детально описываются события на стороне клиента и их применение. Если вы ещё не знакомы с тем, как работают события клиентской части, рекомендуем прочитать эту статью прежде, чем продолжить.

В некоторых API содержится ряд различных событий, в некоторых — событий нет. Свойства обработчика, позволяющие запускать функции при совершении какого-либо события по большей части перечислены в нашем материале отдельного раздела "Обработчики событий (Event handlers)".

Мы уже видели несколько обработчиков событий, используемых в нашем примере с Web Audio API выше:

```js
// play/pause audio
playBtn.addEventListener("click", () => {
  // check if context is in suspended state (autoplay policy)
  if (audioCtx.state === "suspended") {
    audioCtx.resume();
  }

  // if track is stopped, play it
  if (playBtn.getAttribute("class") === "paused") {
    audioElement.play();
    playBtn.setAttribute("class", "playing");
    playBtn.textContent = "Pause";
    // if track is playing, stop it
  } else if (playBtn.getAttribute("class") === "playing") {
    audioElement.pause();
    playBtn.setAttribute("class", "paused");
    playBtn.textContent = "Play";
  }
});

// if track ends
audioElement.addEventListener("ended", () => {
  playBtn.setAttribute("class", "paused");
  playBtn.textContent = "Play";
});
```

### У них есть дополнительные средства безопасности там, где это необходимо

Функциональность WebAPI подвержена тем же соображениям безопасности, что и JavaScript или другие веб-технологии (например, [same-origin policy](/ru/docs/Web/Security/Same-origin_policy)), но иногда они содержат дополнительные механизмы защиты. К примеру, некоторые из наиболее современных WebAPI работают только со страницами, обслуживаемыми через HTTPS в связи с передачей конфиденциальных данных (примеры: [Service Workers](/ru/docs/Web/API/Service_Worker_API) и [Push](/ru/docs/Web/API/Push_API)).

К тому же, некоторые WebAPI запрашивают разрешение от пользователя, как только к ним происходит вызов в коде. Например, [Notifications API](/ru/docs/Web/API/Notifications_API) запрашивает разрешение для показа диалогого окна:

![Запрос разрешения на показ уведомлений](notification-permission.png)

Web Audio и HTMLMediaElement API подчиняются механизму безопасности, который называется [политикой автозапуска](/ru/docs/Web/API/Web_Audio_API/Best_practices#autoplay_policy). Это означает, что вы не можете автоматически воспроизводить звук при загрузки страницы — вы должны разрешить своим пользователям инициировать воспроизведения звука с помощью какого-либо элемента управления, например, кнопки. Сделано это, потому что автовоспроизведение звука обычно очень раздражает, и мы не должны подвергать этому наших пользователей.

## Итоги

На данном этапе, у вас должно сформироваться представление о том, что такое API, как они работают и как вы можете применить их в своём JavaScript-коде. Вам наверняка не терпится начать делать по-настоящему интересные вещи с конкретными API, так вперёд! В следующий раз мы рассмотрим работу с документом с помощью Document Object Model (DOM).

{{NextMenu("Learn/JavaScript/Client-side_web_APIs/Manipulating_documents", "Learn/JavaScript/Client-side_web_APIs")}}
