<template>
    <div class="component">
        <h1>The User Component</h1>
        <p>I'm an awesome User!</p>
        <p>Age: {{ age }}</p>
        <div class="row">
            <button @click="changeName" class="col">Change Name</button>
            <button @click="changeState" class="col">Reverse Name Letters</button>
        </div>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-6">
                <app-user-detail :name="name" :reverse="reverse" :resetFn="resetName" :userAge="age" @nameReset="name = $event"></app-user-detail>
            </div>
            <div class="col-xs-12 col-sm-6">
                <app-user-edit :userAge="age" @ageEdited="age = $event"></app-user-edit>
            </div>
        </div>
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

    export default {
        data() {
            return {
                name: 'Rue',
                age: 32,
                reverse: false
            };
        },
        methods: {
            changeName() {
                this.name = 'Lou';
            },
            changeState() {
                this.reverse = !this.reverse;
            },
            resetName() {
                this.name = 'Rue';
            }
        },
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit
        }
    }
</script>

<style scoped>
    div {
        background-color: lightblue;
    }
</style>
