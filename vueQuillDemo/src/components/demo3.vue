<template>
  <div class="demo2-page">
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

  let quillEditorOption = [
              ['bold', 'italic', 'underline', 'strike'],
              ['blockquote', 'code-block'],
              [{ 'header': 1 }, { 'header': 2 }],
              [{ 'list': 'ordered' }, { 'list': 'bullet' }],
              [{ 'script': 'sub' }, { 'script': 'super' }],
              [{ 'indent': '-1' }, { 'indent': '+1' }],
              [{ 'direction': 'rtl' }],
              [{ 'size': ['small', false, 'large', 'huge'] }],
              [{ 'header': [1, 2, 3, 4, 5, 6, false] }],
              [{ 'font': [] }],
              [{ 'color': [] }, { 'background': [] }],
              [{ 'align': [] }],
              ['clean'],
              ['link', 'image', 'video']
            ]

  export default {
    data() {
      return {
        name: 'register-modules-example',
        content: `<p><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSvvpo2no-0Onr5Cwpuc0XncC0G3ecVb8Zjxe11sGcxOGepKLUc" width="500"></p>
                  <br>`,
        editorOption: {
          modules: {
            toolbar: quillEditorOption
          }
        }
      }
    },
    mounted () {
      this.$refs.quillTextEditor.quill.getModule('toolbar').addHandler('image', () => {
        this.selectLocalImage();
      });
    },
    methods: {
      // 富文本上传图片
      selectLocalImage () {
        const input = document.createElement('input');
        input.setAttribute('type', 'file');
        input.click();

        // 监听上传事件
        input.onchange = () => {
          const file = input.files[0];

          // 判断文件类型只能为图片
          if (/^image\//.test(file.type)) {
            this.saveToServer(file);
          } else {
            this.$Message.warning('只能上传图片');
          }
        };
      },

      saveToServer (file) {
        // TODO
        let callback = ()=>{
          return new Promise((resolve, reject)=>{
            resolve('http://pic.pc6.com/up/2017-5/201752314425762151772.jpg')
          })
        }
        callback().then((res)=>{
          this.insertToEditor(res);
        })
      },

      insertToEditor (url) {
        const range = this.$refs.quillTextEditor.quill.getSelection();
        this.$refs.quillTextEditor.quill.insertEmbed(range.index, 'image', url);
      },

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