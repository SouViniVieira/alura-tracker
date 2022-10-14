<template>
    <div class="box has-text-weight-bold" :style="estilos">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BoxList',
    data() {
        return {
            estilos: {
                'background-color': '#F4F0CA'
            }
        }
    }
})
</script>