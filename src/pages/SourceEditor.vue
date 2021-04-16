<template>
  <q-page class="flex flex-center">


  <div id="editor"></div>



  </q-page>
</template>

<script>
import ClassicEditor from '@ckeditor/ckeditor5-build-classic';


export default {
  name: 'PageIndex',

   mounted(){
     ClassicEditor.create( document.querySelector( '#editor' ) )
    .then( editor => {
        console.log( editor );
    } )
    .catch( error => {
        console.error( error );
    } );
   }



  }
</script>
