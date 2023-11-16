<template>
  <h3>History</h3>
  <ul
    id="list"
    class="list"
  >
    <li
      v-for="transaction in transactions"
      :key="transaction.id"
      :class="transaction.amount < 0 ? 'minus' : 'plus'"
    >
      {{ transaction.text }} <span>Rs. {{ transaction.amount }}</span>
      <button
        @click="deleteTransaction(transaction.id)"
        class="delete-btn"
      >
        x
      </button>
    </li>
  </ul>
</template>

<script setup>
import { defineProps } from "vue";

const emit = defineEmits(["deleteTransaction"]);

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

const deleteTransaction = (id) => {
  emit("deleteTransaction", id);
  // emitting the deleteTransaction custom event
};
</script>

<!-- "Options API"  -->
<!-- <script>
export default {
  data() {
    return {
      transactions: [
        { id: 1, text: "Flower", amount: -19.99 },
        { id: 2, text: "Salary", amount: 299.97 },
        { id: 3, text: "Book", amount: -10 },
        { id: 4, text: "Camera", amount: 150 },
      ],
    };
  },
  methods: {},
};
</script> -->

<!-- "Composition API"  -->
<!-- <script>
export default {
  setup() {
    const transactions = [
      { id: 1, text: "Flower", amount: -19.99 },
      { id: 2, text: "Salary", amount: 299.97 },
      { id: 3, text: "Book", amount: -10 },
      { id: 4, text: "Camera", amount: 150 },
    ];
    myFunction = () => {
      console.log("myFunction");
    };

    return { transactions, myFunction };
  },
};
</script> -->

<!-- "Composition API" but better with the usage of 'setup' in the script tag -->
<!-- <script setup>
const transactions = [
  { id: 1, text: "Flower", amount: -19.99 },
  { id: 2, text: "Salary", amount: 299.97 },
  { id: 3, text: "Book", amount: -10 },
  { id: 4, text: "Camera", amount: 150 },
];
</script> -->

<!-- transactions moved to App.vue as it is used in multiple components (global state) -->
