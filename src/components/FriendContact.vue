<template>
<li>
    <h2>{{ name }} {{ friendIsFavorite ? "(Favorite)" : ""  }} </h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavorit">Favorite</button>
    <ul v-if="detailsAreVisible">
        <li><strong>Phone:</strong>{{ phoneNumber }}</li>
        <li><strong>Email:</strong>{{ emailAddress }}</li>
    </ul>
</li>  
</template>

<script>
export default {
    // First way
    // props: [
    //     "name",
    //     "phoneNumber",
    //     "emailAddress",
    //     "isFavorite"
    // ],
    // Second way
    // props: {
    //     name: String,
    //     phoneNumber: String,
    //     emailAddress: String,
    //     isFavorite: String,
    // },
    // Thrid way
    props: {
        name: {
            type: String,
            required: true
        },
        phoneNumber: {
            type: String,
            required: true
        },
        emailAddress: {
            type: String,
            required: true
        },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false,
            // validator: function(value){
            //     return value === '1' || value === '0';
            // }
        },
    },
    data(){
        return{
            detailsAreVisible: false,
            friendIsFavorite: this.isFavorite
        }
    },
    computed: {
        detailButtonCaption(){
            return this.detailsAreVisible ? "Hide" : "Show";
        }
    },
    methods: {
        toggleDetails(){
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavorit(){
            this.friendIsFavorite = !this.friendIsFavorite;
        }
    }
};
</script>