[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8837416&assignment_repo_type=AssignmentRepo)

# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)

# Autocomplate component

### Props

|    Name     |   Type   |   Default   |  Binding Way  | Description |
| :---------: | :------: | :---------: | :-----------: | :---------: |
|    value    | `String` | _undefined_ | v-model:value |     ...     |
|   options   | `Array`  |    _[]_     |   :options    |     ...     |
| placeholder | `String` | _undefined_ | :placeholder  |     ...     |

# Popup component

### Props

|       Name        |      Type       |   Default   |   Binding Way   |                                                                      Description                                                                       |
| :---------------: | :-------------: | :---------: | :-------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------: |
|       title       |    `String`     | _undefined_ |     :title      |                                                                          ...                                                                           |
|       text        |    `String`     | _undefined_ |      :text      |                                                                          ...                                                                           |
|   negative-text   |    `String`     | _'Reject'_  | :negative-text  |                                    <small>Cancel button text. Corresponding button won't show if not set.</small>                                     |
|   positive-text   |    `String`     | _'Accept'_  | :positive-text  |                                   <small>Confirm button text. Corresponding button won't show if not set.</small>                                    |
|     closable      |    `Boolean`    |   _false_   |    :closable    |                                                      <small>Whether to show close button.</small>                                                      |
| on-positive-click | `() => boolean` |   _false_   | @positive-click | <small>The default behavior is closing the confirm. Return `false` or resolve `false` or `Promise rejected` will prevent the default behavior.</small> |
| on-negative-click | `() => boolean` |   _false_   | @negative-click | <small>The default behavior is closing the confirm. Return `false` or resolve `false` or `Promise rejected` will prevent the default behavior.</small> |

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

# Notification component

### Props

|   Name    |   Type    |    Default    | Binding Way | Description |
| :-------: | :-------: | :-----------: | :---------: | :---------: |
| placement | `String`  | _'top-right'_ | :placement  |     ...     |
|  content  | `String`  |  _undefined_  |  :content   |     ...     |
|   icon    | `String`  |  _'message'_  |    :icon    |     ...     |
|  variant  | `String`  |  _'default_   |  :variant   |     ...     |
| closable  | `Boolean` |    _false_    |  :closable  |     ...     |
