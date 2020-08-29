<template>
<v-card
:to="destination"
dark
class="mt-5"
>
<div class="d-flex flex-no-wrap justify-space-between">
<div>
<v-card-title

class="subheading"
v-text="'Go Back'"
></v-card-title>

<!-- <v-card-subtitle v-text="item.link"></v-card-subtitle> -->
</div>


</div>
</v-card>
</template>

<script>
export default {

    props: ['destination'],

}
</script>

<style>

</style>
