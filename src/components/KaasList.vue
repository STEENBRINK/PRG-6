  
<template>
    <div>
        <section id="list-data">
            <div id="cont-list">
                <p id="title-form">Lijst van alle kaassoorten</p>
                <hr>
                <div v-bind:key="kaas.name" v-for="kaas in kaasList">
                    <KaasItem v-bind:kaas="kaas" v-on:del-kaas="$emit('del-kaas', kaas._id)" />
                </div>
            </div>
        </section>
    </div>
</template>

<script>
import KaasItem from './KaasItem.vue';
export default {
    name: "KaasList",
    components: {
        KaasItem
    },
    props: ["kaasList"]
}
console.log("POOP")
</script>