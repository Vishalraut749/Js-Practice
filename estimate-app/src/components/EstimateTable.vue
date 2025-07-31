<template>
  <div class="estimate-container">
    <div class="header">
      <h2>Project Estimates</h2>
      <button @click="addNewItem" class="btn btn-primary">
        <span class="icon">+</span>
        Add Item
      </button>
    </div>

    <div class="table-container">
      <table class="estimate-table">
        <thead>
          <tr>
            <th>Item Description</th>
            <th>Quantity</th>
            <th>Unit Price</th>
            <th>Total</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in estimates" :key="item.id" class="table-row">
            <td>
              <input
                v-if="item.isEditing"
                v-model="item.description"
                @blur="saveItem(item)"
                @keyup.enter="saveItem(item)"
                class="input-field"
                placeholder="Enter description"
                ref="descriptionInput"
              />
              <span v-else @dblclick="editItem(item)" class="editable-cell">
                {{ item.description || 'Click to edit' }}
              </span>
            </td>
            <td>
              <input
                v-if="item.isEditing"
                v-model.number="item.quantity"
                @blur="saveItem(item)"
                @keyup.enter="saveItem(item)"
                type="number"
                min="0"
                step="1"
                class="input-field number-input"
              />
              <span v-else @dblclick="editItem(item)" class="editable-cell">
                {{ item.quantity }}
              </span>
            </td>
            <td>
              <input
                v-if="item.isEditing"
                v-model.number="item.unitPrice"
                @blur="saveItem(item)"
                @keyup.enter="saveItem(item)"
                type="number"
                min="0"
                step="0.01"
                class="input-field number-input"
              />
              <span v-else @dblclick="editItem(item)" class="editable-cell">
                ${{ formatCurrency(item.unitPrice) }}
              </span>
            </td>
            <td class="total-cell">
              ${{ formatCurrency(item.quantity * item.unitPrice) }}
            </td>
            <td class="actions-cell">
              <button
                v-if="item.isEditing"
                @click="saveItem(item)"
                class="btn btn-success btn-sm"
                title="Save"
              >
                ✓
              </button>
              <button
                v-if="item.isEditing"
                @click="cancelEdit(item)"
                class="btn btn-secondary btn-sm"
                title="Cancel"
              >
                ✕
              </button>
              <button
                v-if="!item.isEditing"
                @click="editItem(item)"
                class="btn btn-info btn-sm"
                title="Edit"
              >
                ✏️
              </button>
              <button
                @click="deleteItem(index)"
                class="btn btn-danger btn-sm"
                title="Delete"
              >
                🗑️
              </button>
            </td>
          </tr>
        </tbody>
        <tfoot>
          <tr class="total-row">
            <td colspan="3"><strong>Total Estimate:</strong></td>
            <td class="total-cell"><strong>${{ formatCurrency(totalEstimate) }}</strong></td>
            <td></td>
          </tr>
        </tfoot>
      </table>
    </div>

    <div v-if="estimates.length === 0" class="empty-state">
      <p>No estimate items yet. Click "Add Item" to get started!</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, nextTick } from 'vue'

interface EstimateItem {
  id: number
  description: string
  quantity: number
  unitPrice: number
  isEditing: boolean
  originalData?: {
    description: string
    quantity: number
    unitPrice: number
  }
}

const estimates = ref<EstimateItem[]>([
  {
    id: 1,
    description: 'Frontend Development',
    quantity: 40,
    unitPrice: 75,
    isEditing: false
  },
  {
    id: 2,
    description: 'Backend API Development',
    quantity: 30,
    unitPrice: 85,
    isEditing: false
  },
  {
    id: 3,
    description: 'Database Design',
    quantity: 15,
    unitPrice: 90,
    isEditing: false
  }
])

const descriptionInput = ref<HTMLInputElement[]>([])

const totalEstimate = computed(() => {
  return estimates.value.reduce((total, item) => {
    return total + (item.quantity * item.unitPrice)
  }, 0)
})

const formatCurrency = (amount: number): string => {
  return amount.toFixed(2)
}

const addNewItem = () => {
  const newItem: EstimateItem = {
    id: Date.now(),
    description: '',
    quantity: 1,
    unitPrice: 0,
    isEditing: true
  }
  estimates.value.push(newItem)
  
  nextTick(() => {
    const inputs = descriptionInput.value
    if (inputs && inputs.length > 0) {
      inputs[inputs.length - 1]?.focus()
    }
  })
}

const editItem = (item: EstimateItem) => {
  // Store original data for cancel functionality
  item.originalData = {
    description: item.description,
    quantity: item.quantity,
    unitPrice: item.unitPrice
  }
  item.isEditing = true
  
  nextTick(() => {
    const inputs = descriptionInput.value
    const index = estimates.value.findIndex(est => est.id === item.id)
    inputs[index]?.focus()
  })
}

const saveItem = (item: EstimateItem) => {
  // Validate data
  if (!item.description.trim()) {
    alert('Description is required')
    return
  }
  if (item.quantity <= 0) {
    alert('Quantity must be greater than 0')
    return
  }
  if (item.unitPrice < 0) {
    alert('Unit price cannot be negative')
    return
  }
  
  item.isEditing = false
  delete item.originalData
}

const cancelEdit = (item: EstimateItem) => {
  if (item.originalData) {
    item.description = item.originalData.description
    item.quantity = item.originalData.quantity
    item.unitPrice = item.originalData.unitPrice
    delete item.originalData
  }
  item.isEditing = false
}

const deleteItem = (index: number) => {
  if (confirm('Are you sure you want to delete this item?')) {
    estimates.value.splice(index, 1)
  }
}
</script>

<style scoped>
.estimate-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 30px;
  padding-bottom: 15px;
  border-bottom: 2px solid #e0e0e0;
}

.header h2 {
  color: #333;
  margin: 0;
  font-size: 28px;
  font-weight: 600;
}

.table-container {
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  margin-bottom: 20px;
}

.estimate-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}

.estimate-table th {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 15px 12px;
  text-align: left;
  font-weight: 600;
  font-size: 14px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.estimate-table td {
  padding: 12px;
  border-bottom: 1px solid #f0f0f0;
  vertical-align: middle;
}

.table-row:hover {
  background-color: #f8f9ff;
}

.table-row:last-child td {
  border-bottom: none;
}

.input-field {
  width: 100%;
  padding: 8px 12px;
  border: 2px solid #e0e0e0;
  border-radius: 6px;
  font-size: 14px;
  transition: border-color 0.3s ease;
  background: white;
}

.input-field:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

.number-input {
  text-align: right;
}

.editable-cell {
  cursor: pointer;
  padding: 8px 12px;
  border-radius: 4px;
  transition: background-color 0.2s ease;
  display: block;
  min-height: 20px;
}

.editable-cell:hover {
  background-color: #f0f0f0;
}

.total-cell {
  font-weight: 600;
  color: #2c5aa0;
  text-align: right;
}

.actions-cell {
  text-align: center;
  white-space: nowrap;
}

.btn {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  margin: 2px;
}

.btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

.btn-primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.btn-success {
  background: #28a745;
  color: white;
}

.btn-secondary {
  background: #6c757d;
  color: white;
}

.btn-info {
  background: #17a2b8;
  color: white;
}

.btn-danger {
  background: #dc3545;
  color: white;
}

.btn-sm {
  padding: 6px 10px;
  font-size: 12px;
}

.icon {
  font-size: 16px;
  font-weight: bold;
}

.total-row {
  background: #f8f9fa;
  font-size: 16px;
}

.total-row td {
  padding: 15px 12px;
  border-top: 2px solid #e0e0e0;
}

.empty-state {
  text-align: center;
  padding: 60px 20px;
  color: #666;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.empty-state p {
  font-size: 18px;
  margin: 0;
}

@media (max-width: 768px) {
  .estimate-container {
    padding: 10px;
  }
  
  .header {
    flex-direction: column;
    gap: 15px;
    text-align: center;
  }
  
  .estimate-table {
    font-size: 12px;
  }
  
  .estimate-table th,
  .estimate-table td {
    padding: 8px 6px;
  }
  
  .btn {
    padding: 6px 12px;
    font-size: 12px;
  }
}
</style>