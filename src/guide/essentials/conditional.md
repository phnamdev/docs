# Hiển thị có điều kiện

<script setup>
import { ref } from 'vue'
const awesome = ref(true)
</script>

## `v-if`

Directive `v-if` dùng để hiển thị một khối có điều kiện. Khối chỉ được hiển thị nếu biểu thức của directive trả về một giá trị truthy.

```vue-html
<h1 v-if="awesome">Vue is awesome!</h1>
```

## `v-else`

Bạn có thể sử dụng directive `v-else` để chỉ ra một "khối else" cho `v-if`:

```vue-html
<button @click="awesome = !awesome">Toggle</button>

<h1 v-if="awesome">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>
```

<div class="demo">
  <button @click="awesome = !awesome">Toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
</div>

<div class="composition-api">

[Thử nó trong Playground](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdCBzZXR1cD5cbmltcG9ydCB7IHJlZiB9IGZyb20gJ3Z1ZSdcblxuY29uc3QgYXdlc29tZSA9IHJlZih0cnVlKVxuPC9zY3JpcHQ+XG5cbjx0ZW1wbGF0ZT5cbiAgPGJ1dHRvbiBAY2xpY2s9XCJhd2Vzb21lID0gIWF3ZXNvbWVcIj50b2dnbGU8L2J1dHRvbj5cblxuXHQ8aDEgdi1pZj1cImF3ZXNvbWVcIj5WdWUgaXMgYXdlc29tZSE8L2gxPlxuXHQ8aDEgdi1lbHNlPk9oIG5vIPCfmKI8L2gxPlxuPC90ZW1wbGF0ZT4iLCJpbXBvcnQtbWFwLmpzb24iOiJ7XG4gIFwiaW1wb3J0c1wiOiB7XG4gICAgXCJ2dWVcIjogXCJodHRwczovL3NmYy52dWVqcy5vcmcvdnVlLnJ1bnRpbWUuZXNtLWJyb3dzZXIuanNcIlxuICB9XG59In0=)

</div>
<div class="options-api">

[Thử nó trong Playground](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdD5cbmV4cG9ydCBkZWZhdWx0IHtcbiAgZGF0YSgpIHtcbiAgXHRyZXR1cm4ge1xuXHQgICAgYXdlc29tZTogdHJ1ZVxuICBcdH1cblx0fVxufVxuPC9zY3JpcHQ+XG5cbjx0ZW1wbGF0ZT5cbiAgPGJ1dHRvbiBAY2xpY2s9XCJhd2Vzb21lID0gIWF3ZXNvbWVcIj50b2dnbGU8L2J1dHRvbj5cblxuXHQ8aDEgdi1pZj1cImF3ZXNvbWVcIj5WdWUgaXMgYXdlc29tZSE8L2gxPlxuXHQ8aDEgdi1lbHNlPk9oIG5vIPCfmKI8L2gxPlxuPC90ZW1wbGF0ZT4iLCJpbXBvcnQtbWFwLmpzb24iOiJ7XG4gIFwiaW1wb3J0c1wiOiB7XG4gICAgXCJ2dWVcIjogXCJodHRwczovL3NmYy52dWVqcy5vcmcvdnVlLnJ1bnRpbWUuZXNtLWJyb3dzZXIuanNcIlxuICB9XG59In0=)

</div>

Một phần tử `v-else` phải ngay lập tức theo sau một `v-if` hoặc một phần tử `v-else-if` nếu không nó sẽ không được công nhận.

## `v-else-if`

Như cái tên của nó, `v-else-if` đóng vai trò là một "khối else if" cho `v-if`. Nó có thể nối tiếp nhau nhiều lần:

```vue-html
<div v-if="type === 'A'">
  A
</div>
<div v-else-if="type === 'B'">
  B
</div>
<div v-else-if="type === 'C'">
  C
</div>
<div v-else>
  Not A/B/C
</div>
```

Cũng giống như `v-else`, một phần tử `v-else-if` phải ngay lập tức theo sau `v-if` hoặc một phần tử `v-else-if`.

## `v-if` trên `<template>`

Bởi vì `v-if` là một directive, nó chỉ được gắn với một phần tử duy nhất. Nhưng điều gì sẽ xảy ra nếu chúng ta muốn chuyển đổi nhiều hơn một phần tử? Trong trường hợp này chúng ta có thể sử dụng `v-if` trên một phần tử `<template>`, cái mà đóng vai trò như một bao bọc vô hình. Kết quả hiển thị cuối cùng sẽ không bao gồm phần tử `<template>`.

```vue-html
<template v-if="ok">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
```

`v-else` và `v-else-if` cũng có thể sử dụng trên `<template>`.

## `v-show`

Một lựa chọn khác cho hiển thị một phần tử có điều kiện đó là directive `v-show`. Cách sử dụng phần lớn là giống nhau:

```vue-html
<h1 v-show="ok">Hello!</h1>
```

Sự khác nhau đó là một phần tử với `v-show` sẽ luôn hiển thị và ở trong DOM; `v-show` chỉ chuyển đổi thuộc tính CSS `display` của phần tử.

`v-show` không hỗ trợ phần tử `<template>`, `v-else` cũng vậy.

## `v-if` vs `v-show`

`v-if` là hiển thị có điều kiện "thực(real)" vì nó đảm bảo rằng các xử lý sự kiện và các thành phần con bên trong khối điều kiện được hủy và tạo lại trong quá trình chuyển đổi.

`v-if` cũng **lazy**: nếu điều kiện là sai khi hiển thị lần đầu, nó sẽ không làm gì cả - khối điều kiện sẽ không được hiển thị cho đến khi điều kiện đúng lần đầu tiên.

Trong khi đó, `v-show` đơn giản hơn nhiều - phần tử luôn được hiển thị bất kể điều kiện ban đầu và nó được chuyển đổi việc hiển thị dựa trên CSS.

Nói tóm lại, `v-if` có chi phí chuyển đổi cao hơn trong `v-show` có chi phí hiển thị lần đầu cao hơn. Vì vậy `v-show` phù hợp nếu bạn cần chuyển đổi một cái gì đó thường xuyên, và `v-if` phù hợp nếu điều kiện gần như không thay đổi trong quá trình chạy(runtime).

## `v-if` with `v-for`

::: warning Chú ý
Bạn **không nên** sử dụng `v-if` và `v-for` trên cùng một phần tử do sự ưu tiên ngầm định. Tham khảo [style guide](/style-guide/rules-essential.html#avoid-v-if-with-v-for) để biết thêm chi tiết.
:::

Khi `v-if` và `v-for` đều được sử dụng trên cùng một phần tử, `v-if` sẽ được đánh giá trước. Xem [hướng dẫn hiển thị danh sách](list#v-for-with-v-if) để biết thêm chi tiết.
