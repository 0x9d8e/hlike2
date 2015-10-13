<p>Минималистичная библиотека для кастомизации социальных кнопок. Предназначена для сайтов не требующих особо сложной интеграции с соцсетями. Расчитана на разработчиков.
Надоело каждый раз добавлять кучу апишек и мучаться с катомизацией каждой кнопки, не нашел удовлетворительного инструмента, написал этот. 
</p>
 - Не зависит от jQuery;
 - Вёрстку кнопок определяете только вы (clickjackig);
 - Сама подключает нужные api (некоторые сервисы требуют ключи);
 
 <p>Общая идея в том, чтобы динамически создать внутри свёрстанного элемента с нужным внешним видом прозрачный абсолютно спозиционированный блок на всю ширину и высоту элемента (или указанные в стилях) после чего инициализировать внутри виджет соцсети. Таким образом мы получаем какой угодно внешний вид социальных кнопок, при этом они будут реагировать на наведение и т.п. Кликая по ним пользователь кликает по прозрачному виджету поверх. 
 </p>

<h2>Доступны соцсети:</h2>
 - vk;
 - facebook;
 - goole+;
 - pinterest;

<h2>Пример:</h2>

    hlike.set({//Указываем нужные параметры
      vkKey: '5100067',
      fbKey: '1550284425231361',
      url: document.location.href,
      style: hlike.defaultStyle
    }).vk.like('.hLike.vk')//Инициализируем во всех нужных элементах соответствующие виджеты
      .fb.like('.hLike.facebook');

Можно указать собственные стили:

    hlike.set({
      style: {
        widget: {
          width: '1em',
          height: '1em'
        },
        widget_iframe: {
          position: 'absolute',
          opacity: 0,
          overflow: 'hidden',
          top: '0px',
          left: '0px',
          width: '100%',
          height: '100%'
        }
      }
    });

Или дефолтные:

    hlike.set({
      style: hlike.defaultStyle
    });

Или никаких.

**Если стили не указаны вообще, то никаких стилей не применится, включая дефолтные**. 
Разумеется любые стили всегда можно указать в css (дублировать их в js не нужно).

Любые свойства можно либо прямо присвоить:

    hlike.url = 'http://expample.com';

Либо передать объектом в метод `set`:

    hlike.set({
      vkKey: '11111111',
      fbKey: '0000000000000000',
      url: document.location.href,
      style: hlike.defaultStyle
    });

Метод возвращает `this`.

Далее вызываем методы соцсетей с css-селектором в единственном аттрибуте:

    hlike.fb.like('.fbLike')
         .vk.like('.vkLike');

Если нужно вызывать их с какими-либо разными параметрами сначала вызываем `set`:

    hlike.set({url: document.location.href+'?sn=vk'}).vk.like('.vkLike')
         .set({url: document.location.href+'?sn=fb'}).fb.like('.fbLike');

На момент написания этого текста доступны только лайки.

<h2>Свойства:</h2>
<ul>
  <li><b>vkKey:</b>&nbsp;api-ключ вконтакте;</li>
  <li><b>fbKey:</b>&nbsp;api-ключ facebook;</li>
  <li><b>style:</b>&nbsp;объект стилей;</li>
  <li><b>url:</b>&nbsp;адрес к которому применяется лайк <i>(если сеть поддерживает url отличный от текущего)</i>;</li>
</ul>

<h2>Методы:[устарело, см. код]</h2>
<ul>
  <li><b>set:</b>&nbsp;пакетно устанавливает свойства (принимает объект) и возвращает hlike;</li>
  <li><b>vk:</b>&nbsp;принимает css-селектор для элементов, которые нужно сделать vk-лайками и возвращает hlike;</li>
  <li><b>fb:</b>&nbsp;принимает css-селектор для элементов, которые нужно сделать facebook-лайками и возвращает hlike;</li>
  <li><b>gp:</b>&nbsp;принимает css-селектор для элементов, которые нужно сделать gplus-лайками и возвращает hlike;</li>
  <li><b>pin:</b>&nbsp;принимает css-селектор для элементов, которые нужно сделать pinterest-кнопкой и возвращает hlike;</li>
  <li><b><i>_приватные методы</i></b>&nbsp;см. в коде;</li>
</ul>

<h2>Ближайшие планы:</h2>
<ul>
  <li>Вторым аттрибутом добавить селектор либо коллбек для счётчика лайков и каким-либо образом его заполнять;</li>
  <li>Помимо селекоторов принимать массивы и коллекции элементов;</li>
  <li>Добавить поддержку других (сейчас только vk и facebook, g+, pinterest);</li>
  <li>Добавить поддержку шейров (сейчас только лайки);</li>
</ul>
