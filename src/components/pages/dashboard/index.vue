<template lang="pug">
  v-layout(row wrap)
    v-flex(xs12)
      h1 Dashboard
    v-flex(xs12)
      v-layout(row wrap)
        v-flex(d-flex xs6 md3 v-for="row in summary" :key="row.title")
          v-card(color="grey lighten-4")
            v-card-text
              div.sm-title {{ row.title }}
              div.sm-value {{ row.value }}
    v-flex(xs12)
      h2 Transactions
      v-data-table(:headers="transactions.headers" :items="transactions.data" :items-per-page="2")
</template>

<script>
export default {
  data () {
    return {
      summary: [
        { title: 'Today Transaction Count', value: 1234 },
        { title: 'Weekly Transaction Count', value: 9999 },
        { title: 'Today Transaction Total Amount', value: 12340000 },
        { title: 'Weekly Transaction Total Amount', value: 99990000 }
      ],
      transactions: {
        headers: [
          { text: 'Order ID', value: 'order_id' },
          { text: 'Merchant', value: 'merchant' },
          { text: 'Store', value: 'store' },
          { text: 'Amount(¥)', value: 'amount' },
          { text: 'Status', value: 'status' },
          { text: 'Time', value: 'txn_date' }
        ],
        data: [
          {
            order_id: Math.random() * 10000000,
            merchant: 'SevenEleven',
            store: 'Tokyo Store',
            amount: 350,
            status: 'processing',
            txn_date: '2019/07/01 23:00:00'
          }, {
            order_id: Math.random() * 10000000,
            merchant: 'SevenEleven',
            store: 'Ginza Store',
            amount: 900,
            status: 'complete',
            txn_date: '2019/07/02 10:01:30'
          }, {
            order_id: Math.random() * 10000000,
            merchant: 'ABC mart',
            store: 'Shinjuku Store',
            amount: 9000,
            status: 'cancel',
            txn_date: '2019/07/03 13:42:09'
          }
        ]
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.sm-title {
  font-size: 11px;
  margin-bottom: 8px;
}
.sm-value {
  font-size: 18px;
  text-align: right;
}
</style>
