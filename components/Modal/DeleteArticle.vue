<template>
    <b-modal id="bv-modal-delete" hide-footer>
    <template #modal-title>
      Delete
    </template>
    <div class="d-block text-center text-dark">
      <h4>Are you sure to delete this article?</h4>
      <b-button variant="danger">Delete</b-button>
    </div>
    <b-button class="mt-3" block @click="$bvModal.hide('bv-modal-delete')">Close Me</b-button>
  </b-modal>
</template>