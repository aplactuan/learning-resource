<template>
    <base-dialog v-if="inputIsInvalid" header="Invalid Input" @close="confirmError">
        <template #default>
            <p>The Input is Invalid</p>
            <p>Please check it again</p>
        </template>
        <template #actions>
            <base-button @click="confirmError">Okay</base-button>
        </template>
    </base-dialog>
    <base-card>
        <form @submit.prevent="submitResource(title, description, link)">
            <div class="form-control">
                <label for="title">Title</label>
                <input type="text" id="title" name="title" ref="titleInput" />
            </div>
            <div class="form-control">
                <label for="description">Description</label>
                <textarea name="description" id="description" rows="3" ref="descInput"></textarea>
            </div>
            <div class="form-control">
                <label for="link">Link</label>
                <input type="url" name="link" id="link" ref="linkInput" />
            </div>
            <div class="form-control">
                <base-button type="submit">Submit</base-button>
            </div>
        </form>
    </base-card>
</template>
<script>
export default {
    inject: ['addResource'],
    data() {
        return {
            inputIsInvalid: false
        }
    },
    methods: {
        submitResource() {
            const title = this.$refs.titleInput.value;
            const description = this.$refs.descInput.value;
            const link = this.$refs.linkInput.value;

            if (title.trim() === '' || description.trim() === '' || link.trim() === '') {
                this.inputIsInvalid = true;
                return;
            }

            this.addResource(title, description, link);
        },
        confirmError() {
            this.inputIsInvalid = false;
        }
    }
}
</script>
<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>