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
          <td> <input type="text" :value="address.firstName"> </td>
          <td> <input type="text" :value="address.lastName"> </td>
          <td> <input type="text" :value="address.streetAddress"> </td>
          <td> <input type="text" :value="address.postalCode"> </td>
          <td> <input type="text" :value="address.locality"> </td>
          <td> <input type="text" :value="address.countryName"> </td>
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
        font-size: 3rem;
        color: black;
        background: white;
        margin: 2rem 1rem 0;
        border: 5px solid rgb(65, 125, 6);

        th,
        td {
            border: 1px solid black;
            text-align: left;
            padding-left: 1rem;
            height: 2rem;
        }

        th {
            border: 2px solid black;
        }
    }

    input {
        display: block;
        border: none;
        width: 100%;
        height: 100%;
        padding: 0;
        font-size: 2rem;

        &:focus {
            outline: none;
        }
    }
</style>
