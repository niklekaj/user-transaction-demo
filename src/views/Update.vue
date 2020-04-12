<template>
  <table>
    <thead>
        <tr>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Street address</th>
        <th>Postal code</th>
        <th>Locality</th>
        <th>Country name</th>
        </tr>
  </thead>
      <tbody>
        <tr v-for="address in this.objUserData.addresses" :key="address.id">
          <td> <input spellcheck="false" type="text" :value="address.firstName"> </td>
          <td> <input spellcheck="false" type="text" :value="address.lastName"> </td>
          <td> <input spellcheck="false" type="text" :value="address.streetAddress"> </td>
          <td> <input spellcheck="false" type="text" :value="address.postalCode"> </td>
          <td> <input spellcheck="false" type="text" :value="address.locality"> </td>
          <td> <input spellcheck="false" type="text" :value="address.countryName"> </td>
        </tr>
      </tbody>
  </table>
</template>

<script>
import UserData from './../../test.json';

export default {
    data() {
        return {
            objUserData: UserData
        };
    }
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
            // padding-left: 1rem;
            height: 3rem;
            box-sizing: border-box;
        }

        th {
            border: 2px solid black;
            padding-left: 1rem;
        }

        td:nth-child(1) {
            width: 25%;
        }
    }

    input {
        border: none;
        // width: calc(100% - 1rem);
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
