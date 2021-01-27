<template>
    <section id="insert-data">
        <div id="cont-form">
            <p id="title-form">Voeg een kaassoort toe</p>
            <hr>
            <form @submit="addCartoon">
                <input type="text" v-model="name" value="Name" name="name" placeholder="titel">
                <input type="text" v-model="country" name="" placeholder="country">
                <input type="text" v-model="region" name="" placeholder="region">
                <input type="text" v-model="type" name="" placeholder="type">
                <input type="text" v-model="family" name="" placeholder="family">
                <input type="text" v-model="colour" name="" placeholder="colour">
                <input type="text" v-model.number="fatDry" name="" placeholder="Dry Fat Percentage">
                <input type="text" v-model.number="calcium" name="" placeholder="omschrijving">
                <input type="checkbox" v-model="vegitarian" name="" >
                <input type="submit" value="Toevoegen" class="btn">
            </form>
        </div>
    </section>
</template>

<script>
// import uuid from 'uuid';
export default {
    name: "AddCartoon",
    data() {
        return {
            isOpen: false,
            isOpen2: false,
            name:'',
            country: undefined,
            region: undefined,
            type: undefined,
            family: undefined,
            colour: undefined,
            fatDry: undefined,
            calcium: undefined,
            vegitarian: undefined
        }
    },
    methods: {
        addKaas(entry) {
            entry.preventDefault();
            const addKaas = {
                name: this.name,
                country: this.country,
                region: this.region,
                type: this.type,
                family: this.family,
                colour: this.colour,
                fatDry: this.fatDry,
                calcium: this.calcium,
                vegitarian: this.vegitarian
            }
            this.$emit('add-kaas', addKaas);
            this.name = undefined;
            this.country = undefined;
            this.region = undefined;
            this.type = undefined;
            this.family = undefined;
            this.colour = undefined;
            this.fatDry = undefined;
            this.calcium = undefined;
            this.vegitarian = undefined;
        }
    }
}
</script>