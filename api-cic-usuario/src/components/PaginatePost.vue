<script setup>
    defineProps(["inicio", "fin", "maxLength"])
    const emit = defineEmits(['next', 'preview'])
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button 
            @click="emit('preview')" 
            type="button" 
            class="btn btn-outline-primary"
            :disabled="inicio <=  0">previo</button>
        <button 
            @click="emit('next')" 
            type="button" 
            class="btn btn-outline-primary"
            :disabled="fin >= maxLength">Siguiente</button>
    </div>
</template>