<template>
  <div class="demo2-page">
    <quill-editor v-model="content"
                  :options="editorOption"
                  @blur="onEditorBlur($event)"
                  @focus="onEditorFocus($event)"
                  @ready="onEditorReady($event)">
      <div id="toolbar" slot="toolbar">
        <!-- 添加工具栏按钮 -->
        <button class="ql-bold">Bold</button>
        <button class="ql-italic">Italic</button>
        
        <select class="ql-size">
          <!-- 默认title -->
          <option value="small"></option>
          <option selected></option>
          <option value="large"></option>
          <option value="huge"></option>
        </select>
        <select class="ql-font">
          <option selected="selected"></option>
          <option value="serif"></option>
          <option value="monospace"></option>
        </select>
        
        <button class="ql-script" value="sub"></button>
        <button class="ql-script" value="super"></button>
        <!-- custom-button -->
        <button id="custom-button" @click="customButtonClick">[ Click me ]</button>
      </div>
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
  export default {
    data() {
      return {
        name: 'register-modules-example',
        content: `<h1 class="ql-align-center">
                    <span class="ql-font-serif"><span class="ql-cursor">﻿</span>I am Example 2!</span></span>
                  </h1>
                  <p><br></p>
                  <p><strong class="ql-font-serif">Whenever you play the game of thrones, you either win or die. There is no middle ground.</strong></p>
                  <p><br></p>
                  <p><u class="ql-font-serif">Some war against sword and spear to win, and the others the crow and the paper to win.</u></p>
                  <p><br></p>
                  <p><em class="ql-font-serif">Dead history is write in ink, the living sort in blood.</em></p>
                  <p><br></p>
                  <p><span class="ql-font-serif" style="color: rgb(0, 102, 204);">They're only numbers. Numbers on paper. Once you understand that, it's easy to make them behave.</span></p>
                  <p><br></p>
                  <p><span class="ql-font-serif">Every time we deal with an enemy, we create two more.</span></p>
                  <p><br></p>
                  <p><span class="ql-font-serif">So the king has decreed. The small council consents.</span></p>
                  <p><br></p>
                  <p><span class="ql-font-serif">Chaos not is a pit, chaos is a ladder.</span></p>
                  <p><br></p>
                  <p><span class="ql-font-serif">A chain needs all sorts of metals, and a land needs all sorts of people.</span></p>
                  <p><br></p>
                  <p><span class="ql-font-serif">When the snows fall and the white winds blow, the lone wolf dies, but the pack survives.</p>
                  `,
        editorOption: {
          modules: {
            toolbar: '#toolbar'
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
      },
      customButtonClick() {
        alert(`你可以定义一些自定义按钮做你想做的事，如上传图片至第三方存储再插入内容区...等等`)
      }
    }
  }
</script>

<style>
  .demo2-page{
    padding: 0 200px; 
  }
  .demo2-page .quill-code {
    border: none;
    height: auto;
  }
  .demo2-page #custom-button{
    width: 100px;
  }
  .split-line:before{
    content: '';
    display: block;
    border-top: 1px solid #eee;
  }
</style>