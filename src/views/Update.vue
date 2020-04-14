<template>
    <div class="c-update">
        <table>
            <thead>
                <tr>
                <th>ID</th>
                <th>First Name</th>
                <th>Last Name</th>
                <th>Street address</th>
                <th>Postal code</th>
                <th>Locality</th>
                <th>Country name</th>
                <th>Add</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(address, index) in this.objUserData.addresses" :key="address.id">
                    <td class="c-update__cells c-update__cells--inactive">{{ address.id }}</td>
                    <td class="c-update__cells c-update__cells--inactive">{{ address.firstName }}</td>
                    <td class="c-update__cells c-update__cells--inactive">{{ address.lastName }}</td>
                    <td class="c-update__cells"> <input class="c-update__cells-input" @focusout="updateExistingAddress($event, index, Object.keys(address)[14])"  spellcheck="false" type="text" :value="address.streetAddress"> </td>
                    <td class="c-update__cells"> <input class="c-update__cells-input" @focusout="updateExistingAddress($event, index, Object.keys(address)[12])" spellcheck="false" type="text" :value="address.postalCode"> </td>
                    <td class="c-update__cells"> <input class="c-update__cells-input" @focusout="updateExistingAddress($event, index, Object.keys(address)[11])" spellcheck="false" type="text" :value="address.locality"> </td>
                    <td class="c-update__cells"> <input class="c-update__cells-input" @focusout="updateExistingAddress($event, index, Object.keys(address)[4])" spellcheck="false" type="text" :value="address.countryName"> </td>
                    <td class="c-update__cells">
                        <button class="c-update__cells-button" @click="addRow(address)"> 
                                    Add Row 
                        </button>
                    </td>
                </tr>

                <tr v-if="this.newAddresses.length !== 0">
                    <td colspan="8"></td>
                </tr>
                <tr v-if="this.newAddresses.length !== 0">
                    <td colspan="9" style="text-align: center; background: #ebe99f;"> New Addresses </td>
                </tr>

                <tr v-for="(newAdd, index) in this.newAddresses" :key="index">
                    <td class="c-update__cells c-update__cells--inactive"></td>
                    <td class="c-update__cells c-update__cells--inactive">{{ newAdd.firstName }}</td>
                    <td class="c-update__cells c-update__cells--inactive">{{ newAdd.lastName }}</td>
                    <td class="c-update__cells"> <input class="c-update__cells-input" @focusout="updateNewAddress($event, index, Object.keys(newAdd)[13])" spellcheck="false" type="text"></td>
                    <td class="c-update__cells"> <input class="c-update__cells-input" @focusout="updateNewAddress($event, index, Object.keys(newAdd)[11])" spellcheck="false" type="text"></td>
                    <td class="c-update__cells"> <input class="c-update__cells-input" @focusout="updateNewAddress($event, index, Object.keys(newAdd)[10])" spellcheck="false" type="text"></td>
                    <td class="c-update__cells"> <input class="c-update__cells-input" @focusout="updateNewAddress($event, index, Object.keys(newAdd)[4])" spellcheck="false" type="text"></td>
                    <td class="c-update__cells c-update__cells--inactive" style="background: #e0e0e0;"></td>
                </tr>
            </tbody>
        </table>
        <button class="c-update--submit" @click="submit()">
            Submit
        </button>
    </div>
</template>

<script>
import UserData from './../../test.json';

export default {
    data() {
        return {
            objUserData: {},
            newAddresses: []
        };
    },
    created() {
        this.objUserData = UserData;
    },
    methods: {
        addRow(address) {
            let newAdd = {};
            // the beauty of javascript :') --> assigning the key - value pairs of the "origin" object in the
            // outer scope to a newly assigned object in order to avoid modifying the "origin" object
            // in the global scope a.k.a the respective "address" of the original json object
            for(let [key, value] of Object.entries(address)) {
                newAdd[key] = value;
            }
            delete newAdd.id; // removing id key from the newly created object (additional new address)
            this.newAddresses.push(newAdd);
        },
        updateExistingAddress(e, i, objKey) {
            this.objUserData.addresses[i][objKey] = e.target.value;
        },
        updateNewAddress(e, i, objKey) {
            this.newAddresses[i][objKey] = e.target.value;
        },
        // submitting the json 
        submit() {
            let req = new XMLHttpRequest();
            const url = '';
            req.open("POST", url);
            req.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
            req.send(JSON.stringify(this.objUserData, this.newAddresses));
        }
    },
};
</script>
    
<style scoped lang="scss">
    @import "./Update.scss";
</style>
