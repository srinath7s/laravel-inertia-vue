<script setup>
import Footer from '@/Components/partials/Footer.vue';
import NavBar from '@/Components/partials/NavBar.vue';
import SettingsPanel from '@/Components/partials/SettingsPanel.vue';
import SideBar from '@/Components/partials/SideBar.vue';
</script>
<style>
@import url('../../../assets/vendors/feather/feather.css');
</style>
<template>
    <div class="container-scroller">
        <NavBar></NavBar>
        <div class="container-fluid page-body-wrapper">
            <SettingsPanel></SettingsPanel>
            <div class="side-bar">
                <SideBar></SideBar>
            </div>
            <div class="main-panel">
                <div class="content-wrapper">
                    <main class="main">
                        <slot />
                    </main>
                </div>
            </div>
        </div>
        <div class="footer">
            <Footer></Footer>
        </div>
    </div>
</template>
<script setup>
import '../../../assets/js/hoverable-collapse.js';
</script>