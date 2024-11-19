# Rent Management App

A modern mobile application built with React Native, Expo, and TypeScript for efficient property management.

## Features

- 🏢 **Property Management**
  - Track vacant and occupied units
  - Monitor unit maintenance status
  - Manage unit details and pricing

- 👥 **Tenant Management**
  - Store tenant information
  - Track lease agreements
  - Manage tenant documentation

- 💰 **Rent Collection**
  - Monthly rent tracking
  - Advance payment management
  - Maintenance charge collection

- 🔧 **Utility Management**
  - Electricity bill tracking
  - Water bill management
  - Government taxes
  - Miscellaneous charges

- 🅿️ **Parking Management**
  - Slot allocation
  - Vehicle type tracking
  - Occupancy status

- 📊 **Dashboard**
  - Occupancy statistics
  - Revenue overview
  - Payment status tracking

## Complete Setup Guide

### System Requirements

- Node.js (v16 or later)
- npm (v8 or later) or yarn
- Expo CLI (`npm install -g expo-cli`)
- Expo Go app on mobile device
- Git (for version control)

### Dependencies

```json
{
  "dependencies": {
    "@react-navigation/bottom-tabs": "^6.5.11",
    "@react-navigation/native": "^6.1.9",
    "@react-navigation/native-stack": "^6.9.17",
    "@reduxjs/toolkit": "^2.0.1",
    "expo": "~50.0.2",
    "expo-status-bar": "~1.11.1",
    "nativewind": "^2.0.11",
    "react": "18.2.0",
    "react-native": "0.73.2",
    "react-native-safe-area-context": "4.8.2",
    "react-native-screens": "~3.29.0",
    "react-redux": "^9.0.4",
    "@react-native-async-storage/async-storage": "1.21.0"
  },
  "devDependencies": {
    "@babel/core": "^7.20.0",
    "@types/react": "~18.2.45",
    "tailwindcss": "^3.3.2",
    "typescript": "^5.1.3"
  }
}
```

### Configuration Files

#### 1. TypeScript Configuration (tsconfig.json)
```json
{
  "extends": "expo/tsconfig.base",
  "compilerOptions": {
    "strict": true,
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "include": [
    "**/*.ts",
    "**/*.tsx"
  ]
}
```

#### 2. Babel Configuration (babel.config.js)
```javascript
module.exports = function(api) {
  api.cache(true);
  return {
    presets: ['babel-preset-expo'],
    plugins: ["nativewind/babel"]
  };
};
```

#### 3. TailwindCSS Configuration (tailwind.config.js)
```javascript
module.exports = {
  content: ["./App.{js,jsx,ts,tsx}", "./src/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

#### 4. Metro Configuration (metro.config.js)
```javascript
const { getDefaultConfig } = require('expo/metro-config');
const config = getDefaultConfig(__dirname);
module.exports = config;
```

### Project Structure

```
project/
├── src/
│   ├── components/
│   │   ├── forms/
│   │   │   ├── TenantForm.tsx
│   │   │   ├── UnitForm.tsx
│   │   │   └── RentForm.tsx
│   │   └── ui/
│   │       ├── Card.tsx
│   │       ├── Button.tsx
│   │       └── Input.tsx
│   ├── navigation/
│   │   └── AppNavigator.tsx
│   ├── screens/
│   │   ├── Dashboard.tsx
│   │   ├── TenantsScreen.tsx
│   │   ├── UnitsScreen.tsx
│   │   ├── RentCollectionsScreen.tsx
│   │   ├── UtilitiesScreen.tsx
│   │   └── ParkingScreen.tsx
│   ├── store/
│   │   ├── store.ts
│   │   └── slices/
│   │       ├── tenantsSlice.ts
│   │       ├── unitsSlice.ts
│   │       ├── rentCollectionsSlice.ts
│   │       ├── utilitiesSlice.ts
│   │       └── parkingSlice.ts
│   ├── types/
│   │   └── index.ts
│   └── utils/
│       ├── validation.ts
│       └── helpers.ts
├── App.tsx
├── app.json
├── babel.config.js
├── metro.config.js
├── package.json
├── tailwind.config.js
└── tsconfig.json
```

### Data Models

```typescript
// src/types/index.ts

interface Tenant {
  id: string;
  name: string;
  phone: string;
  email: string;
  joinDate: string;
  unitId: string;
}

interface RentCollection {
  id: string;
  tenantId: string;
  amount: number;
  date: string;
  type: 'RENT' | 'ADVANCE' | 'MAINTENANCE';
  status: 'PAID' | 'PENDING' | 'OVERDUE';
}

interface Unit {
  id: string;
  number: string;
  floor: string;
  status: 'VACANT' | 'OCCUPIED';
  rentAmount: number;
  maintenanceCharge: number;
  parkingSlots: string[];
}

interface Utility {
  id: string;
  unitId: string;
  type: 'ELECTRICITY' | 'WATER' | 'TAX' | 'MISC';
  amount: number;
  date: string;
  status: 'PAID' | 'PENDING';
  description?: string;
}

interface ParkingSlot {
  id: string;
  number: string;
  type: 'CAR' | 'BIKE';
  status: 'OCCUPIED' | 'VACANT';
  unitId?: string;
}
```

### Installation Steps

1. Clone the repository:
```bash
git clone <repository-url>
cd rent-management-app
```

2. Install dependencies:
```bash
npm install
```

3. Configure environment variables (if needed):
```bash
cp .env.example .env
```

4. Start the development server:
```bash
npm start
```

### Available Scripts

- `npm start` - Start Expo development server
- `npm run ios` - Run on iOS simulator
- `npm run android` - Run on Android emulator
- `npm run web` - Run in web browser
- `npm run lint` - Run ESLint
- `npm run typescript` - Run TypeScript compiler check

### State Management

The app uses Redux Toolkit for state management. Each feature has its own slice:

- `tenantsSlice` - Manages tenant data
- `unitsSlice` - Manages property units
- `rentCollectionsSlice` - Handles rent payments
- `utilitiesSlice` - Manages utility bills
- `parkingSlice` - Manages parking slots

### Styling

The app uses NativeWind (TailwindCSS for React Native) for styling:

1. Configure TailwindCSS:
```bash
npm install nativewind
npm install --dev tailwindcss
```

2. Use in components:
```tsx
<View className="p-4 bg-white rounded-lg shadow-md">
  <Text className="text-lg font-bold text-gray-800">
    Title
  </Text>
</View>
```

### Navigation

Using React Navigation with bottom tabs and stack navigation:

```tsx
const Tab = createBottomTabNavigator();
const Stack = createNativeStackNavigator();

// Tab Navigator
<Tab.Navigator>
  <Tab.Screen name="Dashboard" component={Dashboard} />
  <Tab.Screen name="Tenants" component={TenantsScreen} />
  // ... other screens
</Tab.Navigator>
```

### Development Guidelines

1. **Code Style**
   - Use TypeScript strictly
   - Follow ESLint rules
   - Use functional components
   - Implement proper error handling

2. **State Management**
   - Use Redux for global state
   - Local state for UI components
   - Implement proper loading states
   - Handle errors gracefully

3. **Performance**
   - Implement proper memoization
   - Optimize re-renders
   - Use proper list rendering
   - Implement proper data pagination

4. **Testing**
   - Write unit tests for utilities
   - Test Redux reducers
   - Test React components
   - Implement E2E tests

### Troubleshooting

Common issues and solutions:

1. **Metro bundler issues**
   ```bash
   npm start -- --reset-cache
   ```

2. **iOS build fails**
   ```bash
   cd ios && pod install && cd ..
   ```

3. **Android build issues**
   ```bash
   cd android && ./gradlew clean && cd ..
   ```

### Contributing

1. Fork the repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

### License

MIT License - feel free to use this project for your own purposes.

### Support

For issues and feature requests, please create an issue in the repository.