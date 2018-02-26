<template>
  <div class="hello-quill">
    <div class="quill-wrapper">
      <quill-editor ref="myTextEditor" v-model="content"> </quill-editor>
    </div>
    <div v-html="content"></div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        content: `<h2><span>Welcome to Quill..</span></h2>`,
        exportContent: ''
      }
    }
  }

</script>

<style>
.hello-quill{
  height: 100%;
  width: 100%;
  padding: 0 200px;
}
.quill-wrapper{
  height: 500px;
}
</style>
