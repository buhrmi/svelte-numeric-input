<script>
  let { value = $bindable(0), decimals = 2, ...rest } = $props()

  function handleInput(e) {
    const oldValue = value.toString().replace(/,/g, '')
    const oldPosition = e.target.value.length - e.target.selectionStart
    let newValue = e.target.value

    // insert a decimal point at current position instead of comma
    if (e.data == ',') {
      const cursorPosition = e.target.selectionStart;
      const beforeCursor = newValue.slice(0, cursorPosition);
      const afterCursor = newValue.slice(cursorPosition);
      newValue = beforeCursor + '.' + afterCursor;
    }

    newValue = newValue.replace(/,/g, '')

    // Reset if we have more than one decimal point
    if ((newValue.match(/\./g) || []).length > 1) {
      newValue = oldValue;
    }

    // Trim to 2 decimal places
    let amountTrimmed = 0;
    if (newValue.includes('.')) {
      const [integerPart, decimalPart] = newValue.split('.');
      amountTrimmed = Math.max(0, decimalPart.length - decimals + Math.floor((decimalPart.length-1) / 3));
      newValue = integerPart + '.' + decimalPart.slice(0, decimals);
    }

    // Apply toLocaleString to the part before the decimal point
    if (newValue.includes('.')) {
      const [integerPart, decimalPart] = newValue.split('.');
      newValue = parseFloat(integerPart || '0').toLocaleString('en-US') + '.' + decimalPart;
    } else {
      newValue = parseFloat(newValue || '0').toLocaleString('en-US');
    }

    value = e.target.value = newValue

    const newPosition = Math.max(0, e.target.value.length - oldPosition + amountTrimmed)
    e.target.setSelectionRange(newPosition, newPosition)
  }

  function normalizeValue() {
    value = (parseFloat(value.replace(/,/g, '')) || 0).toLocaleString('en-US', {
      minimumFractionDigits: decimals,
      maximumFractionDigits: decimals,
    })
  }
</script>

<input oninput={handleInput} onblur={normalizeValue} {value} {...rest} />