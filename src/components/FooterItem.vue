<template>
    <footer v-bind:style="{ backgroundColor: styleFooter.footerColor}">
            
    </footer>
</template>

<script>
    export default {
        name: 'FooterItem',
        props: {
            styleFooter: {}
        }   
    }
</script>