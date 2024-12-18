<template>
    <input type="text" @input="insertDataName($event.target.value)" placeholder="Name">
    <input type="password" v-model="userPass" placeholder="Password">
    <input type="email" v-model="userEmail" placeholder="Email">
    <button type="button" @click="sendData()">Send</button>
    <p className="error"> {{ error }}</p>

    

    <div v-if="users.length == 0">
        We do not have any users at this moment
    </div>
    <div v-else-if="users.length == 1">
        Users has 1 element
    </div>
    <div v-else>
        Users has more than 1 element
    </div>

    <User v-for="(el, index) in users" :key="index" :user="el" :index="index" :deleteUser="deleteUser"/>
</template>

<script>
    import User from './components/User.vue'

    export default {
        components: { User },
        data() {
            return {
                users: [],
                error:``,
                userName: ``,
                userPass: ``,
                userEmail: ``
            }
        },

        methods: {
            insertDataName(val) {
                this.userName = val
            },

            sendData() {
                if (this.userName == `` && this.userPass == `` && this.userEmail == ``) {
                    this.error = `Name, password and email are not defined`;
                    return;
                } else if (this.userName == `` && this.userPass == ``) {
                    this.error = `Name and password are not deifned`;
                    return;
                } else if (this.userName == `` && this.userEmail == ``) {
                    this.error = `Name and email are not defined`;
                    return;
                } else if (this.userPass == `` && this.userEmail == ``) {
                    this.error = `Password and email are not defined`;
                    return;
                } else if (this.userEmail == ``) {
                    this.error = `Email is not defined`;
                    return;
                } else if (this.userPass == ``) {
                    this.error = `Password is not defined`;
                    return;
                } else if (this.userName == ``) {
                    this.error = `Name is not defined`;
                    return;
                }

                this.error = ``;

                this.users.push ({
                    name: this.userName,
                    pass: this.userPass,
                    email: this.userEmail
                })
            },

            deleteUser (index) {
                this.users.splice(index, 1);
            }
        }
    }
</script>

<style scoped>
    input {
        display: block;
        margin-bottom: 10px;
        border-radius: 3px;
        border: 1px solid silver;
        outline: none;
        padding: 10px 15px;
        background: #fafafa;
        color: #333;
    }

    button {
        border: 0;
        border-radius: 5px;
        outline: none;
        padding: 10px 15px;
        background: #6cd670;
        color: #167f3d;
        font-weight: bold;
        cursor: pointer;
        transition: transform 500ms ease;
    }

    button:hover {
        transform: translateY(-5px);
    }

    .user {
        width: 500px;
        margin-top: 20px;
        border: 1px solid silver;
        background: #e3e3e3;
        color: #222;
        padding: 20px;
        border-radius: 5px;
    }
</style>