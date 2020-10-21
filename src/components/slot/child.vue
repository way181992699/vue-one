
<template>
  <div>
    子组件的非插槽内的文本
    <slot>
      <p>如果父组件没有内容插入的话，我将作为默认内容出现</p>
    </slot>
  </div>
</template>
<script>
export default {};
</script>