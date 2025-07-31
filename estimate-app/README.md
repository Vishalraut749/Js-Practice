# Estimate Management System

A modern, responsive Vue.js application for creating and managing project estimates with an editable table interface.

## Features

- ✨ **Editable Table**: Double-click any cell to edit in-place
- ➕ **Add Items**: Easily add new estimate items
- 🗑️ **Delete Items**: Remove unwanted items with confirmation
- 💰 **Automatic Calculations**: Real-time total calculations
- ✅ **Input Validation**: Ensures data integrity
- 📱 **Responsive Design**: Works on desktop and mobile devices
- 🎨 **Modern UI**: Clean, professional interface with smooth animations

## Technologies Used

- **Vue.js 3** - Progressive JavaScript framework
- **TypeScript** - Type-safe JavaScript
- **Vite** - Fast build tool and development server
- **Composition API** - Modern Vue.js development approach

## Getting Started

### Prerequisites

- Node.js (version 16 or higher)
- npm or yarn package manager

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd estimate-app
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

## Usage

### Adding Items
- Click the "Add Item" button to create a new estimate item
- Fill in the description, quantity, and unit price
- Press Enter or click outside the input to save

### Editing Items
- Double-click any cell in the table to edit it
- Use the edit button (✏️) to enter edit mode
- Save changes with the checkmark (✓) or cancel with the X (✕)

### Deleting Items
- Click the delete button (🗑️) to remove an item
- Confirm the deletion in the popup dialog

### Validation
- Description is required and cannot be empty
- Quantity must be greater than 0
- Unit price cannot be negative

## Project Structure

```
estimate-app/
├── src/
│   ├── components/
│   │   └── EstimateTable.vue    # Main editable table component
│   ├── App.vue                  # Root component
│   └── main.ts                  # Application entry point
├── public/                      # Static assets
├── package.json                 # Dependencies and scripts
└── README.md                    # This file
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run type-check` - Run TypeScript type checking
- `npm run lint` - Run ESLint
- `npm run format` - Format code with Prettier

## Component Features

### EstimateTable.vue

The main component includes:

- **Reactive Data**: Uses Vue's Composition API for state management
- **TypeScript Interface**: Strongly typed estimate items
- **Inline Editing**: Toggle between view and edit modes
- **Data Persistence**: Maintains original data for cancel functionality
- **Input Validation**: Client-side validation with user feedback
- **Responsive Design**: Mobile-friendly table layout

### Key Methods

- `addNewItem()` - Adds a new estimate item in edit mode
- `editItem()` - Switches an item to edit mode
- `saveItem()` - Validates and saves changes
- `cancelEdit()` - Reverts changes and exits edit mode
- `deleteItem()` - Removes an item with confirmation

## Customization

### Styling
The application uses scoped CSS with:
- CSS Grid and Flexbox for layout
- CSS custom properties for theming
- Responsive breakpoints for mobile devices
- Smooth transitions and hover effects

### Data Structure
Each estimate item contains:
```typescript
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
```

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Commit your changes: `git commit -am 'Add feature'`
4. Push to the branch: `git push origin feature-name`
5. Submit a pull request

## License

This project is open source and available under the [MIT License](LICENSE).

## Future Enhancements

- 💾 Data persistence with localStorage or backend API
- 📊 Export to PDF/Excel functionality
- 🔍 Search and filter capabilities
- 📈 Charts and analytics
- 👥 Multi-user collaboration
- 🌙 Dark mode theme
- 📋 Estimate templates
