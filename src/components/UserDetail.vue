<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User Name: {{ reverseName() }}</p>
        <p>User Age: {{ userAge }}</p>
        <button @click="resetName">Reset Name</button>
        <button @click="resetFn()">Reset Name from Parent</button>
    </div>
</template>

<script>
import { eventBus } from '../main';

export default {
    props: {
        name: {
            type: String,
            default: 'Rue'
        },
        reverse: Boolean,
        resetFn: Function,
        userAge: Number
    },
    methods: {
        reverseName() {
            return this.reverse == true ? this.name.split("").reverse().join("") : this.name;
        },
        resetName() {
            this.name = 'Rue';
            this.$emit("nameReset", this.name);
        }
    },
    created() {
        eventBus.$on('ageEdited', (age) => {
            this.userAge = age;
        });
    }
}
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
