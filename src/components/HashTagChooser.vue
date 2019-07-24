<template>
    <v-container>
        <v-layout text-xs-center wrap>
            <v-flex xs12 v-if="hashtags.length > 30">
                <v-alert
                    :value="true"
                    class="mt-4"
                    type="warning"
                >
                    <strong>Instagram Hashtag-Limit überschritten!</strong><br>
                    {{ hashtags.length }} Hashtags statt maximal 30, die Liste wurde automatisch gekürzt.
                </v-alert>
            </v-flex>
            <v-flex xs12>
                <v-layout wrap>
                    <v-flex xs12 sm4>
                        <v-checkbox :color="checkColor" hide-details v-model="standard" label="Standard-Tags"></v-checkbox>
                        <v-checkbox :color="checkColor" hide-details v-model="stadtentwicklung" label="Stadtentwicklung"></v-checkbox>
                        <v-checkbox :color="checkColor" hide-details v-model="wien" label="Wien"></v-checkbox>
                    </v-flex>
                    <v-flex xs12 sm4>
                        <v-checkbox :color="checkColor" hide-details v-model="baugruppe" label="Baugruppe"></v-checkbox>
                        <v-checkbox :color="checkColor" hide-details v-model="leopoldstadt" label="Leopoldstadt"></v-checkbox>
                        <v-checkbox :color="checkColor" hide-details v-model="nordbahnviertel" label="Nordbahnviertel"></v-checkbox>
                    </v-flex>
                    <v-flex xs12 sm4>
                        <v-checkbox :color="checkColor" hide-details v-model="architektur" label="Architektur"></v-checkbox>
                        <v-checkbox :color="checkColor" hide-details v-model="nutzungsmischung" label="Nutzungsmischung"></v-checkbox>
                        <v-checkbox :color="checkColor" hide-details v-model="openhauswirtschaft" label="OPENhauswirtschaft"></v-checkbox>
                    </v-flex>
                </v-layout>
            </v-flex>
            <v-flex xs12>
                <v-textarea
                    class="mt-4 pb-5"
                    filled
                    box
                    name="hashtags"
                    label="Hashtags"
                    :value="hashtagString"
                ></v-textarea>
            </v-flex>
            <v-flex xs12>
                <v-btn
                    class="copyButton"
                    :color="checkColor"
                    v-clipboard:copy="hashtagString"
                    v-clipboard:success="onCopy"
                    v-clipboard:error="onError"
                >Hashtags kopieren</v-btn>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    export default {
        data: () => ({
            checkColor: "#003C71",
            standard: true,
            stadtentwicklung: false,
            wien: false,
            leopoldstadt: false,
            nordbahnviertel: false,
            architektur: false,
            nutzungsmischung: false,
            baugruppe: false,
            openhauswirtschaft: false
        }),
        computed: {
            hashtags: function () {
                const tags = new Set();

                if (this.standard === true) {
                    tags.add("dieHausWirtschaft")
                        .add("igersaustria")
                        .add("genossenschaft");
                }

                if (this.baugruppe === true) {
                    tags.add("baugruppe")
                        .add("cohousing")
                        .add("genossenschaft")
                        .add("genossenschaftlichwohnen")
                        .add("wohnprojekt");
                }

                if (this.stadtentwicklung === true) {
                    tags.add("stadtentwicklung")
                        .add("stadtplanung")
                        .add("städtebau")
                        .add("baukultur")
                        .add("urban");
                }

                if (this.wien === true) {
                    tags.add("wienstagram")
                        .add("welovevienna")
                        .add("igersvienna")
                        .add("wien")
                        .add("urban");
                }

                if (this.leopoldstadt === true) {
                    tags.add("1020wien")
                        .add("leopoldstadt")
                        .add("wien1020")
                        .add("1020")
                        .add("wien")
                        .add("urban");
                }

                if (this.nordbahnviertel === true) {
                    tags.add("wien")
                        .add("leopoldstadt")
                        .add("nordbahnviertel")
                        .add("nordbahnhof")
                        .add("stadtentwicklung")
                        .add("urban");
                }

                if (this.architektur === true) {
                    tags.add("architektur")
                        .add("architecture")
                        .add("austrianarchitecture")
                        .add("archilover")
                        .add("architecturegram")
                        .add("architecturelover")
                        .add("urbanism");
                }

                if (this.nutzungsmischung === true) {
                    tags.add("mixeduse")
                        .add("wohnen")
                        .add("arbeiten")
                        .add("nachhaltigwohnen")
                        .add("nutzungsmischung")
                        .add("urbanemischung");
                }

                if (this.openhauswirtschaft === true) {
                    tags.add("OPENhauswirtschaft")
                        .add("SmartCities")
                        .add("SmartCity")
                        .add("Research")
                        .add("Forschungsprojekt")
                        .add("poweredByKlimafonds");
                }

                return [...tags];
            },
            hashtagString: function () {
                return this.hashtags.slice(0, 30).map(tag => `#${tag}`).join(" ");
            }
        },
        methods: {
            onError: function (e) {
                alert("Text konnte nicht kopiert werden!");
                window.console.error(e);
            }
        }
    }
</script>

<style>
    .copyButton {
        color: #D7EAE2 !important;
    }
</style>
