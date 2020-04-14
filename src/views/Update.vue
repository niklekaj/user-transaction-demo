<template>
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
          <td class="c-update__cells"> <input @focusout="updateExistingAddress($event, index, Object.keys(address)[14])"  spellcheck="false" type="text" :value="address.streetAddress"> </td>
          <td class="c-update__cells"> <input @focusout="updateExistingAddress($event, index, Object.keys(address)[12])" spellcheck="false" type="text" :value="address.postalCode"> </td>
          <td class="c-update__cells"> <input @focusout="updateExistingAddress($event, index, Object.keys(address)[11])" spellcheck="false" type="text" :value="address.locality"> </td>
          <td class="c-update__cells"> <input @focusout="updateExistingAddress($event, index, Object.keys(address)[4])" spellcheck="false" type="text" :value="address.countryName"> </td>
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
          <td class="c-update__cells"> <input @focusout="updateNewAddress($event, index, Object.keys(newAdd)[14])" spellcheck="false" type="text"></td>
          <td class="c-update__cells"> <input @focusout="updateNewAddress($event, index, Object.keys(newAdd)[12])" spellcheck="false" type="text"></td>
          <td class="c-update__cells"> <input @focusout="updateNewAddress($event, index, Object.keys(newAdd)[11])" spellcheck="false" type="text"></td>
          <td class="c-update__cells"> <input @focusout="updateNewAddress($event, index, Object.keys(newAdd)[4])" spellcheck="false" type="text"></td>
          <td class="c-update__cells c-update__cells--inactive" style="background: #e0e0e0;"></td>
        </tr>
      </tbody>
  </table>
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
        }
    },
};
</script>
    
<style scoped lang="scss">
    table {
        font-size: 2.5rem;
        color: black;
        background: white;
        margin: 2rem 1rem 0;
        border: 5px solid rgb(65, 125, 6);
        max-width: 100%;

        th,
        td {
            border: 1px solid black;
            text-align: left;
            height: 3rem;
            box-sizing: border-box;
        }

        th {
            border: 2px solid black;
            padding-left: 1rem;
        }

        .c-update__cells {
            &:nth-child(1) {
                width: 5%;
            }

            &:nth-child(2) {
                width: 22%;
            }

            &:nth-child(3) {
                width: 10%;
            }

            &--inactive {
                background: #e0e0e0;
                padding-left: 1rem;
            }

            &-button {
                padding: 0;
                height: 100%;
                width: 100%;
            }
        }
    }

    input {
        border: none;
        width: 100%;
        padding: 0;
        font-size: 2.5rem;
        margin-left: 0;
        padding-left: 1rem;
        height: 100%;
        box-sizing: border-box;

        &:focus {
            outline: none;
            background: #8bf0d5;
        }
    }
</style>
