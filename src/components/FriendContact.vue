<template>
    <li>
        <h2>{{ name }} {{ isFavorite ? "(Favorite)" : "" }}</h2>
        <button @click="toggleDetails">
            {{ detailsAreVisible ? "Hide" : "Show" }} Details
        </button>
        <button @click="toggleFavorite">Toggle Favorite</button>
        <button @click="deleteFriend">Delete</button>
        <ul v-if="detailsAreVisible">
            <li>
                <strong>Phone:</strong> {{ phoneNumber }}
            </li>
            <li>
                <strong>Email:</strong> {{ emailAddress }}
            </li>
        </ul>
        
    </li>
</template>

<script>
    export default {
        props: {
            id: {type: String, required: true},
            name: {type: String, required: true},
            phoneNumber: {type: String, required: true},
            emailAddress: {type: String, required: true},
            isFavorite: {type: Boolean, required: false, default: false},
        },
        emits: ["toggle-favorite", "deleted"],
        data() {
            return {
                detailsAreVisible: false,
            };
        },
        methods: {
            toggleDetails() {
                console.log(this.phoneNumber);
                console.log("Toggle button was clicked!");
                this.detailsAreVisible = !this.detailsAreVisible;
            },
            toggleFavorite() {
                this.$emit("toggle-favorite", this.id);
            },
            deleteFriend() {
                this.$emit("delete", this.id);
            }
        }
    }
</script>

<style></style>