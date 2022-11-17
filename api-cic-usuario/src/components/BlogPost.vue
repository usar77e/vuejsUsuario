<script setup>
    defineProps([
        'title',
        'body',
        'id',
        'colorText',
    ])
</script>
<template>
    <div class="card">
        <div class="card-body"
        :class="`text-${colorText}`">
            <h5 class="card-title">{{ id }} - {{ title }}</h5>
            <p>{{ body}}</p>
        </div>
    </div>

</template>