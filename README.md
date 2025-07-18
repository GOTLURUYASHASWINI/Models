# Models
const mongoose = require('mongoose');

const TaskSchema = new mongoose.Schema({
  task_str_id: {
    type: String,
    required: true,
    unique: true
  },
  description: {
    type: String,
    required: true
  },
  estimated_time_minutes: {
    type: Number,
    required: true,
    min: [1, 'Estimated time must be greater than 0']
  },
  status: {
    type: String,
    enum: ['pending', 'in_progress', 'done'],
    default: 'pending'
  }
}, { timestamps: true });

module.exports = mongoose.model('Task', TaskSchema);
