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
          <td> {{ address.firstName }} </td>
          <td> {{ address.lastName }} </td>
          <td> {{ address.streetAddress }} </td>
          <td> {{ address.postalCode }} </td>
          <td> {{ address.locality }} </td>
          <td> {{ address.countryName}} </td>
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

        th,
        td {
            border: 1px solid black;
            text-align: left;
            padding-left: 1rem;
        }

        th {
            border: 2px solid black;
        }
    }
</style>
