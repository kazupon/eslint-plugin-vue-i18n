---
title: '@intlify/vue-i18n/no-raw-text'
description: disallow to string literal in template or JSX
since: v0.2.0
---

# @intlify/vue-i18n/no-raw-text

> disallow to string literal in template or JSX

- :star: The `"extends": "plugin:@intlify/vue-i18n/recommended"` property in a configuration file enables this rule.

This rule warns the usage of string literal.

This rule encourage i18n in about the application needs to be localized.

## :book: Rule Details

:-1: Examples of **incorrect** code for this rule:

`template` option:

<eslint-code-block language="javascript">

<!-- eslint-skip -->

```js
/* eslint @intlify/vue-i18n/no-raw-text: 'error' */
export default {
  // ✗ BAD
  template: '<p>hello</p>'
  // ...
}
```

</eslint-code-block>

`template` block of single-file components:

<eslint-code-block>

<!-- eslint-skip -->

```vue
<script>
/* eslint @intlify/vue-i18n/no-raw-text: 'error' */
</script>
<template>
  <!-- ✗ BAD -->
  <p>hello</p>
</template>
```

</eslint-code-block>

`JSX`:

<eslint-code-block language="javascript">

<!-- eslint-skip -->

```js
/* eslint @intlify/vue-i18n/no-raw-text: 'error' */
export default {
  // ✗ BAD
  render: h => <p>hello</p>
  // ...
}
```

</eslint-code-block>

:+1: Examples of **correct** code for this rule:

`template` option:

<eslint-code-block language="javascript">

<!-- eslint-skip -->

```js
/* eslint @intlify/vue-i18n/no-raw-text: 'error' */
export default {
  // ✓ GOOD
  template: `<p>{{ \$t('hello') }}</p>`
  // ...
}
```

</eslint-code-block>

`template` block of single-file components:

<eslint-code-block>

<!-- eslint-skip -->

```vue
<script>
/* eslint @intlify/vue-i18n/no-raw-text: 'error' */
</script>
<template>
  <!-- ✓ GOOD -->
  <p>{{ $t('hello') }}</p>
</template>
```

</eslint-code-block>

`JSX`:

<eslint-code-block language="javascript">

<!-- eslint-skip -->

```js
/* eslint @intlify/vue-i18n/no-raw-text: 'error' */
export default {
  // ✓ GOOD
  render: h => <p>{this.$t('hello')}</p>
  // ...
}
```

</eslint-code-block>

## :gear: Options

```json
{
  "@intlify/vue-i18n/no-raw-text": [
    "error",
    {
      "ignoreNodes": ["md-icon", "v-icon"],
      "ignorePattern": "^[-#:()&]+$",
      "ignoreText": ["EUR", "HKD", "USD"]
    }
  ]
}
```

- `ignoreNodes`: specify nodes to ignore such as icon components
- `ignorePattern`: specify a regexp pattern that matches strings to ignore
- `ignoreText`: specify an array of strings to ignore

## :rocket: Version

This rule was introduced in `@intlify/eslint-plugin-vue-i18n` v0.2.0

## :mag: Implementation

- [Rule source](https://github.com/intlify/eslint-plugin-vue-i18n/blob/master/lib/rules/no-raw-text.ts)
- [Test source](https://github.com/intlify/eslint-plugin-vue-i18n/tree/master/tests/lib/rules/no-raw-text.ts)
