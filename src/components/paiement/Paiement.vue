<template>
  <div class="container-fluid p-5">
    <!-- Titre principal -->
    <h1 class="h4 font-sans fw-semibold text-dark mb-4">Payment Dashboard</h1>

    <!-- Solde par défaut -->
    <div class="d-flex justify-content-between align-items-center mb-4">
      <h2>
        <span>Account Balance : </span>
        <span class="h3 text-dark medium-text"> {{ accountBalance }}</span>
      </h2>

      <button class="btn btn-success" @click="initiateTransfer">
        Initiate Transfer
      </button>
    </div>

    <!-- Filtrage avancé -->
    <div class="d-flex justify-content-between align-items-center mb-4">
      <div class="d-flex">
        <input
          type="date"
          class="form-control me-2"
          v-model="filter.date"
          placeholder="Filter by Date"
        />
        <select class="form-select me-2" v-model="filter.paymentMethod">
          <option value="">All Payment Methods</option>
          <option value="momo">Mobile Money</option>
          <option value="moov-money">Moov Money</option>
        </select>
        <select class="form-select me-2" v-model="filter.status">
          <option value="">All Statuses</option>
          <option value="completed">Completed</option>
          <option value="pending">Pending</option>
          <option value="failed">Failed</option>
        </select>
        <button class="btn btn-outline-primary me-2" @click="resetFilters">
          Reset Filters
        </button>
      </div>
      <button class="btn btn-primary" @click="exportData">
        Export to PDF/CSV
      </button>
    </div>

    <!-- Tableau des Transactions avec Pagination -->
    <div class="table-responsive bg-white rounded shadow-sm p-3 mb-4">
      <table class="table table-hover text-dark">
        <thead>
          <tr>
            <th>Date</th>
            <th>Transaction ID</th>
            <th>Payment Method</th>
            <th>Amount</th>
            <th>Status</th>
            <th>Details</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="transaction in paginatedTransactions"
            :key="transaction.id"
          >
            <td>{{ transaction.date }}</td>
            <td>{{ transaction.id }}</td>
            <td>{{ transaction.paymentMethod }}</td>
            <td>{{ transaction.amount }}</td>
            <td :class="statusClass(transaction.status)">
              {{ transaction.status }}
            </td>
            <td>
              <button
                class="btn btn-link text-primary"
                @click="viewDetails(transaction)"
              >
                View Details
              </button>
            </td>
          </tr>
        </tbody>
      </table>
      <div class="d-flex justify-content-between align-items-center">
        <button
          class="btn btn-outline-primary"
          :disabled="currentPage === 1"
          @click="prevPage"
        >
          Previous
        </button>
        <span>Page {{ currentPage }} of {{ totalPages }}</span>
        <button
          class="btn btn-outline-primary"
          :disabled="currentPage === totalPages"
          @click="nextPage"
        >
          Next
        </button>
      </div>
    </div>

    <!-- Notifications en temps réel -->
    <div>
      <h2 class="h5 text-dark">Real-Time Notifications</h2>
      <div class="table-responsive bg-white rounded shadow-sm p-3">
        <table class="table table-hover text-dark">
          <thead>
            <tr>
              <th>#</th>
              <th>Notification</th>
              <th>Time</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="(notification, index) in limitedNotifications"
              :key="notification.id"
            >
              <td>{{ index + 1 }}</td>
              <td>{{ notification.message }}</td>
              <td>{{ notification.time }}</td>
            </tr>
          </tbody>
        </table>
      </div>
      <button class="btn btn-secondary mt-2" @click="downloadAllNotifications">
        Download All Notifications
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      accountBalance: ' 7 748 540 FCFA', // Montant par défaut
      filter: {
        date: '',
        paymentMethod: '',
        status: '',
      },
      transactions: [
        // Exemple de données fictives pour les transactions
        {
          id: 'TX12345',
          date: '2024-10-15',
          paymentMethod: 'PayPal',
          amount: '$150.00',
          status: 'completed',
        },
        {
          id: 'TX67890',
          date: '2024-10-14',
          paymentMethod: 'Credit Card',
          amount: '$200.00',
          status: 'pending',
        },
        {
          id: 'TX67890',
          date: '2024-10-14',
          paymentMethod: 'Credit Card',
          amount: '$200.00',
          status: 'pending',
        },
      ],
      notifications: [], // Notifications en temps réel
      currentPage: 1,
      itemsPerPage: 5,
    };
  },
  computed: {
    filteredTransactions() {
      return this.transactions.filter((transaction) => {
        const matchesDate =
          !this.filter.date || transaction.date === this.filter.date;
        const matchesMethod =
          !this.filter.paymentMethod ||
          transaction.paymentMethod === this.filter.paymentMethod;
        const matchesStatus =
          !this.filter.status || transaction.status === this.filter.status;
        return matchesDate && matchesMethod && matchesStatus;
      });
    },
    paginatedTransactions() {
      const start = (this.currentPage - 1) * this.itemsPerPage;
      return this.filteredTransactions.slice(start, start + this.itemsPerPage);
    },
    totalPages() {
      return Math.ceil(this.filteredTransactions.length / this.itemsPerPage);
    },
    limitedNotifications() {
      return this.notifications.slice(-5);
    },
  },
  methods: {
    statusClass(status) {
      return status === 'completed'
        ? 'text-primary'
        : status === 'pending'
        ? 'text-secondary'
        : 'text-danger';
    },
    viewDetails(transaction) {
      alert(`Viewing details for transaction: ${transaction.id}`);
    },
    exportData() {
      alert('Exporting data to PDF or CSV...');
    },
    resetFilters() {
      this.filter.date = '';
      this.filter.paymentMethod = '';
      this.filter.status = '';
    },
    prevPage() {
      if (this.currentPage > 1) this.currentPage--;
    },
    nextPage() {
      if (this.currentPage < this.totalPages) this.currentPage++;
    },
    initiateTransfer() {
      alert('Initiating transfer...');
    },
    downloadAllNotifications() {
      alert('Downloading all notifications...');
    },
  },
  mounted() {
    // Simulation des notifications en temps réel
    setInterval(() => {
      const now = new Date();
      const newNotification = {
        id: this.notifications.length + 1,
        message: `New transaction completed: TX${Math.floor(
          Math.random() * 100000
        )}`,
        time: now.toLocaleTimeString(),
      };
      this.notifications.push(newNotification);
    }, 10000);
  },
};
</script>

<style scoped>
.table-responsive {
  max-height: 400px;
  overflow-y: auto;
}

.text-primary {
  color: #007bff !important;
}

.text-secondary {
  color: #6c757d !important;
}

.text-danger {
  color: #dc3545 !important;
}
</style>
