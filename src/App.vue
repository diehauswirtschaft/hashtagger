<template>
    <v-app>
        <v-toolbar app>
            <v-toolbar-title class="headline">
                <img src="./assets/dhw-signet.svg" class="dhw-logo" alt="die HausWirtschaft">
                <span>Hash</span>
                <span class="font-weight-light">Tagger</span>
            </v-toolbar-title>
        </v-toolbar>

        <v-content class="pb-4">
            <HashTagChooser/>
        </v-content>
    </v-app>
</template>

<script>
    import HashTagChooser from './components/HashTagChooser'

    export default {
        name: 'App',
        components: {
            HashTagChooser
        },
        data() {
            return {
                //
            }
        }
    }
</script>

<style>
    .headline {
        display: flex;
    }

    .headline .dhw-logo {
        width: auto;
        height: 32px;
        margin-right: 2px;
    }

    .theme--light.v-toolbar {
        background: #003C71;
        color: #D7EAE2;
    }
</style>
