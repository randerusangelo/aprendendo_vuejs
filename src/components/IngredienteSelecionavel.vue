<script lang="ts">

import Tag from './Tag.vue';

export default{
    components: { Tag },
    props: {
        ingrediente: {type: String, required: true}
    },
    data(){
        return {
            selecionado: false
        }
    },
    methods: {
        aoClickar(){
            this.selecionado = !this.selecionado

            if(this.selecionado){
                this.$emit('adicionarIngrediente', this.ingrediente);
            } else {
                this.$emit('removerIngrediente', this.ingrediente);
            }
        }
    },
    emits: ['adicionarIngrediente', 'removerIngrediente']
}

</script>


<template>
    <button
        class="ingrediente"
        @click="aoClickar"
        :aria-pressed="selecionado"
    >
        <Tag :texto="ingrediente" :ativa="selecionado" />
    </button>
</template>


<style scoped>
.ingrediente {
    cursor: pointer;
}
</style>