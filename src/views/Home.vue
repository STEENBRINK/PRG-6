<template>
  <div id="app">
    <AddKaas v-on:add-kaas="addKaas"/>
    <KaasList v-bind:kaasList="kaasList" v-on:del-kaas="deleteKaas" v-on:edit-kaas="editKaas"/>
  </div>
</template>

<script>
import KaasList from '../components/KaasList';
import AddKaas from '../components/AddKaas';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    KaasList,
    AddKaas,
    },
  data() {
    return {
      kaasList: []
    }
  },
    created(){
        this.getAmount(0,5);
    },
    methods: {
        deleteKaas(id){
            axios
                .delete(`http://localhost:5000/api/kaas/deleteKaas/${id}`)
                .then(() => this.kaasList = this.kaasList.filter(kaas => kaas._id != id))
                .catch(err => console.error(err));
        },
        addKaas(newKaas){
            const { name, country, region, type, family, colour, fatDry, calcium, vegitarian } = newKaas;

            axios.post(`http://localhost:5000/api/kaas/createKaas`, {
                name,
                country,
                region,
                type,
                family,
                colour,
                fatDry,
                calcium,
                vegitarian
            })
            .then(res => this.kaasList = [...this.kaasList, res.data])
            .catch(err => console.error(err));
        },
        editKaas(editKaas){
            const { name, country, region, type, family, colour, fatDry, calcium, vegitarian } = editKaas;

            axios.patch(`http://localhost:5000/api/kaas/editKaas/${editKaas}`, {
                name,
                country,
                region,
                type,
                family,
                colour,
                fatDry,
                calcium,
                vegitarian
            })
            .then(res => this.kaasList = [...this.kaasList, res.data])
            .catch(err => console.error(err));
        },
        getAmount(start, amount){
            axios.get(`http://localhost:5000/api/kaas/${start, (amount + start)}`)
            .then(res => {
                this.kaasList = res.data.items
                console.log("POOPERS")
                console.log(res.data.items)
            })
            .catch(err => console.error(err))
        }
    }
}
</script>