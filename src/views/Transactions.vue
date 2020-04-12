<template>
  <table>
    <thead>
        <tr>
        <th>Customer ID</th>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Email</th>
        <th>Ammount paid</th>
        <th>Currency</th>
        </tr>
  </thead>
      <tbody>
          <tr v-for="subscription in this.objUserData.paymentMethods[0].subscriptions" :key="subscription.id">
          <td> {{ subscription.transactions[0].customer.id }} </td>
          <td> {{ subscription.transactions[0].customer.firstName }} </td>
          <td> {{ subscription.transactions[0].customer.lastName }} </td>
          <td> {{ subscription.transactions[0].customer.email }} </td>
          <td> {{ subscription.transactions[0].amount }} </td>
          <td> {{ subscription.transactions[0].currencyIsoCode }} </td>
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
