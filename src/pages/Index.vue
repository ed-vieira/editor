<template>
  <q-page class="row  justify-evenly" >




<div class="document-editor">
    <div ref="toolbar-container" class="document-editor__toolbar"></div>
    <div class="document-editor__editable-container">
      <div class="row">
        <div class="col-12 col-md-12">
             <div ref="editor" class="document-editor__editable"></div>
        </div>
      </div>
    </div>
</div>




    <button class="btn btn-success" @click.prevent="getInput" id="btn-edit">
        get
    </button>


    {{editorData}}


  </q-page>
</template>

<script>
// import ClassicEditor from '@ckeditor/ckeditor5-build-classic';
//import CKFinder from '@ckeditor/ckeditor5-ckfinder/src/ckfinder';

import DecoupledEditor from '@ckeditor/ckeditor5-build-decoupled-document';
import {CkEditorToolbarItems} from '../ck-editor'

export default {
  name: 'PageIndex',
  data(){
    return{
      editorData: "",
      editor: null,
    }
  },

  methods:{
     getInput(){
       this.editorData = this.editor.getData();
     },
  },

   mounted(){

        DecoupledEditor.create(this.$refs['editor'],{
          toolbar: {
            items: CkEditorToolbarItems,
            shouldNotGroupWhenFull: true
          },
          ckfinder: {
              uploadUrl: 'https://example.com/ckfinder/core/connector/php/connector.php?command=QuickUpload&type=Images&responseType=json'
          },
        }).then(editor => {
	        this.$refs['toolbar-container'].appendChild(editor.ui.view.toolbar.element);
	    	  this.editor = editor;
	      }).catch( error => {
      		console.error( 'There was a problem initializing the editor.', error );
	      });


   }

  }
</script>

<style>
  @import '../css/ckeditor/style.css';
</style>
