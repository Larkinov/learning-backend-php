## Синтаксис
IIFE (Immediately Invoked Function Expression)
IIFE (от англ. Immediately Invoked Function Expression «немедленно вызываемое функциональное выражение») — это идиома JavaScript, в которой функция выполняется сразу после её определения. Такие функции также известны как самовыполняющиеся анонимные функции.

```javascript
// Обычное IIFE
(function () {
  // инструкции…
})();

// Вариант с использованием стрелочной функции
(() => {
  // инструкции…
})();

// Асинхронное IIFE
(async () => {
  // инструкции…
})();
```

## Модули
Модуль используется только в скриптах типа «модуль»:
```html
<script type="module" src="index.js"></script>
```
Экспорт из модуля по имени:

```javascript
export class ClassName;
export function functionName;
export const constName;

or 

export {ClassName [as NewName], functionName() [as newFunctionName], constName [as newConstName]};
Экспорт из модуля по умолчанию:

export default name;
```
Импорт:
```javascript
import {ClassName [as NewName], functionName [as newName] } from "./misc.js";
```