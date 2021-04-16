<template>
  <q-page class="flex flex-center">

  <div ref="editor"></div>

  </q-page>
</template>

<script>
import ClassicEditor from '@ckeditor/ckeditor5-build-classic';

export default {
  name: 'PageIndex',

   mounted(){
      ClassicEditor.create(this.$refs['editor'])
       .then(editor => {})
        .catch(err => console.error(err));
   }

  }
</script>
