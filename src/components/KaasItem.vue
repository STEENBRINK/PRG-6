<template>
    <div id="main">
        <button class="accordion" @click="toggle()">{{ kaas.name }} </button>
        <button class="edit" @click="toggle2()">Edit</button>
        <button @click="$emit('del-kaas', kaas._id)" class="del">Delete</button>

        <div id="info">
            <ul v-show="isOpen" class="list">
                <li><b>Name:</b> {{kaas.name}}</li>
                <li><b>Country:</b> {{kaas.country}}</li>
                <li><b>Region:</b> {{kaas.region}}</li>
                <li><b>Type:</b> {{kaas.type}}</li>
                <li><b>Family:</b> {{kaas.family}}</li>
                <li><b>colour:</b> {{kaas.colour}}</li>
                <li><b>fatDry:</b> {{kaas.fatDry}}</li>
                <li><b>calcium:</b> {{kaas.calcium}}</li>
                <li><b>vegitarian:</b> {{kaas.vegitarian}}</li>
            </ul>

            <form @submit="editKaas" v-show="isOpen2">
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
    </div>
</template>

<script>
export default {
    name:"KaasItem",
    props: ["kaas"],
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
        toggle() {
            this.isOpen = !this.isOpen
        },
        toggle2() {
            this.isOpen2 = !this.isOpen2
        },
        editKaas(entry) {
            entry.preventDefault();
            const editKaas = {
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
            this.$emit('edit-kaas', editKaas);
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

