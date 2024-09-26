# svelte-numeric-input

A numeric input component for Svelte 5.

[Demo](https://svelte-5-preview.vercel.app/#H4sIAAAAAAAAE1WNMQrDMAxFr2K0ZGnIbkKgY5deoOlQHBkEsS1kuVBC7h6bQKDj-4_H38DTihnsa4P4CQgW7sxwA_1xg_zFVbFyTkVcW8bshFinORpDgZOoeZaAQu4RuajxkoLpzq6Pp-mpqW6O43DVFf66YaovIS3kCRewKgX3934AkkUoMKAAAAA=)

## Installation

```bash
npm install --save svelte-numeric-input
```

## Usage

```html
<script>
  import NumericInput from 'svelte-numeric-input';
</script>

<NumericInput />
```

## Props

| Name       | Type     | Default | Description |
| ---------- | -------- | ------- | ----------- |
| value      | number   | 0       | The value of the input. |
| decimals   | number   | 2       | The number of decimal places. |

All other props are passed to the underlying `<input>` element.

## License

MIT