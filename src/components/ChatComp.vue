<template>
    <div v-for="(mensaje, i) in mensajes" :key="i">
        <p :class="{chatEnd: chatEnd}" :style="{ backgroundColor: colorChat }">{{ mensaje }}</p>
    </div>
</template>
<script>
export default {
    props: ["mensajes", "colorChat", "chatEnd"]
}
//<p :style="{backgroundColor: colorChatSecundario}" style="text-align: end;">{{ chatSecundario }}</p>
</script>
<style>
.chatEnd {
    text-align: end;
}
</style>