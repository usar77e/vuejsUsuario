<script setup>
    defineProps([
        'title',
        'body',
        'id',
        'colorText',
    ])

    const emit = defineEmits(['cambiarFavoritoNombre'])
</script>
<template>
    <div class="card">
        <div class="card-body"
        :class="`text-${colorText}`">
            <h5 class="card-title">{{ id }} - {{ title }}</h5>
            <p>{{ body}}</p>
            <button 
                @click="emit('cambiarFavoritoNombre', title)" 
                class="btn btn-outline-primary">
                Favorito
            </button>
        </div>
    </div>

</template>