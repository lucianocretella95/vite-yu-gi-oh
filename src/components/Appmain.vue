<script>
import axios from 'axios';
export default {
    data() {
        return {
            dek: [],
        }
    },

    methods: {
        getcards() {
            this.newmail = []
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php')
                .then(function (result) {
                    console.log(result.data);
                    this.dek.push(result.data);
                });
        },
    },
}
</script>

<template>
    <div class="container text-center">
        <div class="column justify-content-start" style="font-size: 0.8rem;">
            <button @click="getcards">Apri Dek</button>
            <div class="dekcards">
                <div v-for="cards in dek">
                    <p>{{ cards }}</p>
                </div>
            </div>
            <!-- <div class="col-4" v-for="carte in yugi">
                <p>{{ carte.name }} {{ carte.type }} {{ carte.desc }} {{ carte.archetype }}</p>
                <img style="width: 5rem;" :src="yugi[0].card_images[0].image_url">
            </div> -->
        </div>
    </div>

</template>

<style scoped></style>