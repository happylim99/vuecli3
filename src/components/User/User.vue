<template>
    <div class="component">
        <h1>The User Component</h1>
        <p>I'm an awesome User!</p>
        <p>Name: {{ name }}</p>
        <p>Age: {{ age }}</p>
        <button @click="changeName">Change my name</button>
        <hr>
        <div class="row">
            <div class="col-xs-8 col-sm-6">
                <app-user-detail :name="name" @nameReset="name = $event" :resetFn='resetName' :userAge='age' />
            </div>
            <div class="col-xs-8 col-sm-6">
                <!-- <app-user-edit :userAge="age" @ageWasEdited='age = $event' /> -->
                <app-user-edit :userAge="age" @ageWasEdited='aa' />
            </div>
        </div>
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

    export default {
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit
        },

        data() {
            return {
                name: 'Sean',
                age: 27
            }
        },

        methods: {
            changeName() {
                this.name = 'Anna'
            },
            resetName(aa, bb) {
                this.name = bb
            },
            aa(age) {
                this.age = age
            }
        }
    }
</script>

<style scoped>
    div {
        background-color: lightblue;
    }
</style>
