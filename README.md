# svelte-numeric-input

A numeric input component for Svelte 5.

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