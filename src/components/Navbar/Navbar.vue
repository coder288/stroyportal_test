<template>
    <div class="navbar">
        <div class="navbar__location">Волгоградская область</div>
        <div class="navbar__navs">
            <div class="navbar__nav">Тендеры</div>
            <div class="navbar__nav">База подрядчиков</div>
            <div class="navbar__nav navbar__nav--tick">Другие сервисы</div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Navbar"
    }
</script>

<style lang="scss">
    .navbar { background: #FAFBFC; padding: 0 89px 0 87px; height: 32px; display: flex; justify-content: space-between; align-items: center; font: 400 12px/19px 'open sans'; color: #708598; margin: 0 18px 0 0; }
    .navbar__location { position: relative; cursor: pointer; margin: 0 0 0 20px; }
    .navbar__location:hover { text-decoration: underline; }
    .navbar__location:before { content: ''; width: 14px; height: 16px; background: url(i/location.svg) no-repeat 50%; position: absolute; top: 0; bottom: 0; margin: auto 0 auto -20px; left: 0; }
    .navbar__navs { display: flex; }
    .navbar__nav + .navbar__nav { margin-left: 24px; }
    .navbar__nav { cursor: pointer; }
    .navbar__nav:hover { text-decoration: underline; }
    .navbar__nav--tick { position: relative; }
    .navbar__nav--tick:after { content: ''; width: 10px; height: 10px; position: absolute; background: url(i/tick.svg) no-repeat 50%; top: 0; bottom: 0; margin: auto 0 auto 7px; }
</style>