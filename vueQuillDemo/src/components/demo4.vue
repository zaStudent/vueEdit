<template>
  <div class="demo4-page">
    <quill-editor ref="quillTextEditor" v-model="content" 
                  :options="editorOption"
                  @blur="onEditorBlur($event)"
                  @focus="onEditorFocus($event)"
                  @ready="onEditorReady($event)">
      <div id="toolbar"></div>
    </quill-editor>

    <div class="ql-snow">
      <div class="quill-code ql-editor">
        <div v-html="content"></div>
      </div>
    </div>

    <div>
      <code>
        {{content}}
      </code>
    </div>

  </div>
</template>

<script>

  let quillEditorOption = {
                            container:[
                              ['bold', 'italic', 'underline', 'strike'],
                              ['blockquote', 'code-block'],
                              [{ 'header': 1 }, { 'header': 2 }],
                              [{ 'list': 'ordered' }, { 'list': 'bullet' }],
                              [{ 'script': 'sub' }, { 'script': 'super' }],
                              [{ 'indent': '-1' }, { 'indent': '+1' }],
                              [{ 'direction': 'rtl' }],
                              [{ 'size': ['small', false, 'large', 'huge'] }],
                              [{ 'header': [1, 2, 3, 4, 5, 6, false] }],
                              [{ 'font': ['test1','test2'] }],
                              [{ 'color': [] }, { 'background': [] }],
                              [{ 'align': [] }],
                              ['clean'],
                              ['link', 'image', 'video'],
                              ['emoji']
                            ],
                            handlers: {'emoji': function() {}}
                          }
  export default {
    data() {
      return {
        name: 'register-modules-example',
        content: `<h1 class="ql-align-center">
                    <span class="ql-font-serif" style="background-color: rgb(240, 102, 102); color: rgb(255, 255, 255);"> I am Example 4! </span>
                  </h1>`,
        editorOption: {
          modules: {
            toolbar: quillEditorOption,
            toolbar_emoji: true,
          }
        }
      }
    },
    methods: {
      onEditorBlur(editor) {
        // console.log('editor blur!', editor)
      },
      onEditorFocus(editor) {
        // console.log('editor focus!', editor)
      },
      onEditorReady(editor) {
        // console.log('editor ready!', editor)
      }
    }
  }
</script>

<style>
  .demo4-page{
    padding: 0 200px; 
  }
  .demo4-page .quill-code {
    border: none;
    height: auto;
  }
</style>