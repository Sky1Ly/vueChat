<template>
    <div class="col-sm-6">
        <div id="background">
            <p :style="{backgroundColor: colorChatPrincipal}">{{ chatPrincipal }}</p>
            <p :style="{backgroundColor: colorChatSecundario}" style="text-align: end;">{{ chatSecundario }}</p>
        </div>
    </div>
</template>
<script>
export default {
    props: ["chatPrincipal", "chatSecundario", "colorChatPrincipal", "colorChatSecundario"]
}
</script>
<style>
    #background {
        background-image: url('https://i.pinimg.com/736x/d2/a7/76/d2a77609f5d97b9081b117c8f699bd37.jpg');
        object-fit: cover;
        width: 100%;
        height: 600px;
    }
</style>