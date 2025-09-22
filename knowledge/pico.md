# Pico CSS

Супер простая CSS библиотека для создания более менее красивых страниц

## Официальная документация

[Pico CSS](https://picocss.com/)

## Установка стандартных стилей

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.min.css"
/>
```

## Установка дополнительных стилей - цвета

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.colors.min.css"
/>
```

## Быстрые решения

Убрать лишние пробелы:

```css
--pico-typography-spacing-vertical: 0 rem;
--pico-spacing: 0.2rem;
--pico-form-element-spacing-vertical: 0.2rem;
--pico-form-element-spacing-horizontal: 0.5rem;
--pico-line-height: 1.2;
```

Правка шрифтов:

```css
@media (min-width: 576px) {
  :host,
  :root {
    --pico-font-size: 100%;
  }
}

@media (min-width: 768px) {
  :host,
  :root {
    --pico-font-size: 105%;
  }
}

@media (min-width: 1024px) {
  :host,
  :root {
    --pico-font-size: 110%;
  }
}

@media (min-width: 1280px) {
  :host,
  :root {
    --pico-font-size: 115%;
  }
}
```
