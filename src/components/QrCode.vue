<template>
  <div class="container-fluid min-vh-100 bg-white p-4">
    <!-- Titre -->
    <h1 class="h4 text-dark mb-4">QR Code Management</h1>

    <!-- Tabs -->
    <ul class="nav nav-tabs mb-4" id="qrCodeTabs" role="tablist">
      <li class="nav-item" role="presentation">
        <button
          class="nav-link active"
          id="list-tab"
          data-bs-toggle="tab"
          data-bs-target="#list"
          type="button"
          role="tab"
          aria-controls="list"
          aria-selected="true"
        >
          QR Code List
        </button>
      </li>
      <li class="nav-item" role="presentation">
        <button
          class="nav-link"
          id="new-tab"
          data-bs-toggle="tab"
          data-bs-target="#new"
          type="button"
          role="tab"
          aria-controls="new"
          aria-selected="false"
        >
          Generate New QR Code
        </button>
      </li>
      <li class="nav-item" role="presentation">
        <button
          class="nav-link"
          id="stats-tab"
          data-bs-toggle="tab"
          data-bs-target="#stats"
          type="button"
          role="tab"
          aria-controls="stats"
          aria-selected="false"
        >
          Statistics
        </button>
      </li>
    </ul>

    <!-- Tab Content -->
    <div class="tab-content" id="qrCodeTabsContent">
      <!-- Tab: QR Code List -->
      <div
        class="tab-pane fade show active"
        id="list"
        role="tabpanel"
        aria-labelledby="list-tab"
      >
        <h2 class="h6 text-dark mb-3">Existing QR Codes</h2>
        <p v-if="qrCodes.length === 0" class="text-muted">No QR Codes found.</p>
        <table v-if="qrCodes.length > 0" class="table table-hover">
          <thead class="table-light">
            <tr>
              <th>Name</th>
              <th>Amount</th>
              <th>Status</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="qr in qrCodes" :key="qr.id">
              <td>{{ qr.name }}</td>
              <td>{{ qr.amount || 'N/A' }}</td>
              <td>{{ qr.status }}</td>
              <td>
                <button
                  class="btn btn-sm btn-info me-2"
                  @click="viewQRCode(qr)"
                >
                  View
                </button>
                <button
                  class="btn btn-sm btn-danger"
                  @click="deleteQRCode(qr.id)"
                >
                  Delete
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <!-- Tab: Generate New QR Code -->
      <div
        class="tab-pane fade"
        id="new"
        role="tabpanel"
        aria-labelledby="new-tab"
      >
        <h2 class="h6 text-dark mb-3">Generate a New QR Code</h2>
        <form @submit.prevent="generateQRCode">
          <div class="mb-3">
            <label for="qrName" class="form-label">QR Code Name</label>
            <input
              type="text"
              id="qrName"
              v-model="newQRCode.name"
              class="form-control"
              placeholder="Enter name"
              required
            />
          </div>
          <div class="mb-3">
            <label for="qrAmount" class="form-label">Amount</label>
            <input
              type="number"
              id="qrAmount"
              v-model="newQRCode.amount"
              class="form-control"
              placeholder="Enter amount"
              required
            />
          </div>
          <button type="submit" class="btn btn-primary">
            Generate QR Code
          </button>
        </form>
      </div>

      <!-- Tab: Statistics -->
      <div
        class="tab-pane fade"
        id="stats"
        role="tabpanel"
        aria-labelledby="stats-tab"
      >
        <h2 class="h6 text-dark mb-3">QR Code Statistics</h2>
        <p class="text-muted">Statistics functionality coming soon...</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      qrCodes: [
        { id: 1, name: 'Event QR', amount: 200, status: 'Active' },
        { id: 2, name: 'Promo QR', amount: 500, status: 'Inactive' },
      ],
      newQRCode: {
        name: '',
        amount: null,
      },
    };
  },
  methods: {
    generateQRCode() {
      alert('New QR Code Generated!');
      // Add logic to generate and save the new QR Code
    },
    viewQRCode(qr) {
      alert(`Viewing QR Code: ${qr.name}`);
    },
    deleteQRCode(id) {
      this.qrCodes = this.qrCodes.filter((qr) => qr.id !== id);
    },
  },
};
</script>

<style scoped>
.container-fluid {
  font-family: 'Open Sans', sans-serif;
}

.nav-tabs .nav-link {
  border: 1px solid #ddd;
  border-radius: 5px 5px 0 0;
}

.nav-tabs .nav-link.active {
  background-color: #3490dc;
  color: white;
  border-color: #3490dc #3490dc #fff;
}

.table th,
.table td {
  vertical-align: middle;
}

.table-hover tbody tr:hover {
  background-color: rgba(52, 144, 220, 0.1);
}

.btn-primary {
  background-color: #3490dc;
  border: none;
}

.btn-primary:hover {
  background-color: #1e7bcf;
}
</style>
