[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8837416&assignment_repo_type=AssignmentRepo)

# Autocomplete, Cookie, Popup

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

<a href="https://bright-seahorse-dbfa48.netlify.app/">LIVE</a>

# Autocomplate component

### Props

|    Name     |   Type   |   Default   |  Binding Way  | Description |
| :---------: | :------: | :---------: | :-----------: | :---------: |
|   select    | `String` | _undefined_ | v-model:value |     ...     |
|   options   | `Array`  |    _[]_     |   :options    |     ...     |
| placeholder | `String` | _undefined_ | :placeholder  |     ...     |

# Popup component

### Props

|       Name        |      Type       |   Default   |   Binding Way   |                                                                    Description                                                                     |
| :---------------: | :-------------: | :---------: | :-------------: | :------------------------------------------------------------------------------------------------------------------------------------------------: |
|       title       |    `String`     | _undefined_ |     :title      |                                                                        ...                                                                         |
|       text        |    `String`     | _undefined_ |      :text      |                                                                        ...                                                                         |
|   negative-text   |    `String`     | _undefined_  | :negative-text  |                                     <sub>Cancel button text. Corresponding button won't show if not set.</sub>                                     |
|   positive-text   |    `String`     | _undefined_  | :positive-text  |                                    <sub>Confirm button text. Corresponding button won't show if not set.</sub>                                     |
|     closable      |    `Boolean`    |   _false_   |    :closable    |                                                      <sub>Whether to show close button.</sub>                                                      |
| on-positive-click | `() => boolean` |   _false_   | @positive-click | <sub>The default behavior is closing the confirm. Return `false` or resolve `false` or `Promise rejected` will prevent the default behavior.</sub> |
| on-negative-click | `() => boolean` |   _false_   | @negative-click | <sub>The default behavior is closing the confirm. Return `false` or resolve `false` or `Promise rejected` will prevent the default behavior.</sub> |

### Slots

|  Name   | Parameters | Description |
| :-----: | :--------: | :---------: |
| header  |    `()`    |     ...     |
| content |    `()`    |     ...     |
| action  |    `()`    |     ...     |

# Cookie component

### Props

|   Name   |   Type    |   Default   |   Binding Way    | Description |
| :------: | :-------: | :---------: | :--------------: | :---------: |
|  title   | `String`  | _undefined_ |      :title      |     ...     |
|   text   | `String`  | _undefined_ |      :text       |     ...     |
| feedback | `Boolean` |   _false_   | v-model:feedback |     ...     |

### Slots

|  Name   | Parameters | Description |
| :-----: | :--------: | :---------: |
| content |    `()`    |     ...     |
