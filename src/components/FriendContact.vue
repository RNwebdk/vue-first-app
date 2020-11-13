<template>
<li>
    <h2>{{ name }} {{ isFavorite ? "(Favorite)" : ""  }} </h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavorit">Favorite</button>
    <ul v-if="detailsAreVisible">
        <li><strong>Phone:</strong>{{ phoneNumber }}</li>
        <li><strong>Email:</strong>{{ emailAddress }}</li>
    </ul>
    <button @click="$emit('delete', id)">Delete Contact</button>
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
        id: {
            type: String,
            required: true
        },
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
    emits: ['toggle-favorite', 'delete'],
    // emits: {
    //     'toggle-favorite': function(id){
    //         if(id){
    //             return true;
    //         }else{
    //             console.warn('Id is missing!');
    //             return false;
    //         }
    //     }
    // },
    data(){
        return{
            detailsAreVisible: false
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
            this.$emit('toggle-favorite', this.id);
        }
    }
};
</script>