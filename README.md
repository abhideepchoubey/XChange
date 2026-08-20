# Xchange 💱

A simple and responsive **Currency Converter** built with React. Xchange allows users to enter an amount, select source and target currencies, fetch exchange-rate information, convert currencies, and swap the selected currencies.

## 🚀 Live Demo

[Xchange — Live Demo](https://xchange-weld.vercel.app/?utm_source=chatgpt.com)

---

## 📌 Features

* 💱 Convert between different currencies
* 🔄 Swap source and target currencies
* 🌐 Fetch currency exchange-rate information dynamically
* ⚛️ Built with React functional components
* 🪝 Uses React Hooks and a custom currency hook
* 🧩 Reusable `InputBox` component
* 🎛️ Controlled input and select components
* 📱 Responsive UI
* 🎨 Styled with Tailwind CSS
* 🚀 Deployed on Vercel

---

## 🛠️ Tech Stack

### Frontend

* React
* JavaScript (ES6+)
* Tailwind CSS
* Vite

### React Concepts

* Functional Components
* `useState`
* Custom Hooks
* Props
* Controlled Components
* Event Handling
* Component Reusability
* State Management

---

## 📂 Project Structure

```text
Xchange/
│
├── public/
│
├── src/
│   │
│   ├── components/
│   │   ├── InputBox.jsx
│   │   └── index.js
│   │
│   ├── hooks/
│   │   └── useCurrencyInfo.js
│   │
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
│
├── .gitignore
├── README.md
├── eslint.config.js
├── index.html
├── package-lock.json
├── package.json
└── vite.config.js
```

---

## 🧠 How It Works

The application follows this flow:

```text
User enters amount
        ↓
Select source currency
        ↓
Select target currency
        ↓
Fetch exchange-rate information
        ↓
Calculate converted amount
        ↓
Display result
```

The main `App` component maintains the following state:

```js
const [amount, setAmount] = useState(0)
const [from, setFrom] = useState("usd")
const [to, setTo] = useState("inr")
const [convertedAmount, setConvertedAmount] = useState(0)
```

The application obtains currency information based on the selected source currency using the custom `useCurrencyInfo` hook.

```js
const currencyInfo = useCurrencyInfo(from)
const options = Object.keys(currencyInfo)
```

---

## 💱 Currency Conversion

The conversion is performed using the selected exchange rate:

```js
const convert = () => {
    setConvertedAmount(
        Number(amount) * currencyInfo[to]
    );
};
```

For example:

```text
Amount = 100
From   = USD
To     = INR
Rate   = 85

Converted Amount = 100 × 85
                 = 8500 INR
```

---

## 🔄 Currency Swap

The application provides a swap button to exchange the source and target currencies.

```js
const swap = () => {
    setFrom(to)
    setTo(from)
    setConvertedAmount(amount)
    setAmount(convertedAmount)
}
```

For example:

```text
Before:

USD → INR

After:

INR → USD
```

---

## 🧩 Reusable InputBox Component

The project uses a reusable `InputBox` component for both currency sections.

The component accepts props such as:

```js
{
    label,
    amount,
    onAmountChange,
    onCurrencyChange,
    currencyOptions,
    selectCurrency,
    amountDisable,
    currencyDisable
}
```

This allows the same component to be used for both the **From** and **To** sections.

### From Currency

```jsx
<InputBox
    label="From"
    amount={amount}
    currencyOptions={options}
    onCurrencyChange={(currency) => setFrom(currency)}
    selectCurrency={from}
    onAmountChange={(amount) => setAmount(amount)}
/>
```

### To Currency

```jsx
<InputBox
    label="To"
    amount={convertedAmount}
    currencyOptions={options}
    onCurrencyChange={(currency) => setTo(currency)}
    selectCurrency={to}
    amountDisable
/>
```

This demonstrates **component reusability and communication between components through props**.

---

## 🎛️ Controlled Components

The amount input is controlled by React state:

```jsx
<input
    type="number"
    value={amount}
    onChange={(e) =>
        onAmountChange && onAmountChange(e.target.value)
    }
/>
```

The selected currency is also controlled:

```jsx
<select
    value={selectCurrency}
    onChange={(e) =>
        onCurrencyChange &&
        onCurrencyChange(e.target.value)
    }
>
```

This means React state is the source of truth for the form values.

---

## 🪝 Custom Hook

The project uses a custom hook:

```js
useCurrencyInfo(from)
```

The hook is responsible for obtaining currency information based on the selected source currency.

This separates the **data-fetching logic** from the UI logic in `App.jsx`.

The returned currency information is then used to generate the available currency options:

```js
const currencyInfo = useCurrencyInfo(from)

const options = Object.keys(currencyInfo)
```

---

## 📋 Form Handling

The conversion form prevents the browser's default page reload:

```jsx
<form
    onSubmit={(e) => {
        e.preventDefault()
        convert()
    }}
>
```

This allows the conversion to be handled entirely by React.

---

## 🎨 Styling

The application uses **Tailwind CSS** for styling.

Tailwind is imported through:

```css
@import "tailwindcss";
```

The UI uses Tailwind utility classes for:

* Layout
* Spacing
* Colors
* Borders
* Buttons
* Responsive design
* Background styling

---

## ⚙️ Installation & Setup

### 1. Clone the repository

```bash
git clone <your-repository-url>
```

### 2. Navigate to the project

```bash
cd Xchange
```

### 3. Install dependencies

```bash
npm install
```

### 4. Start the development server

```bash
npm run dev
```

The application will be available at the local URL provided by Vite.

---

## 🏗️ Build for Production

```bash
npm run build
```

To preview the production build:

```bash
npm run preview
```

---

## 🌐 Deployment

The application is deployed using **Vercel**.

Live application:

[https://xchange-weld.vercel.app/](https://xchange-weld.vercel.app/?utm_source=chatgpt.com)

---

## 📚 Concepts Demonstrated

This project helped practice:

* React functional components
* `useState`
* Custom Hooks
* Props
* Controlled Components
* Event handling
* Form handling
* State management
* Component reusability
* API/data fetching
* Tailwind CSS
* Vite
* Deployment with Vercel

---

## 🔮 Future Improvements

Possible improvements include:

* Add loading indicators
* Add API error handling
* Add conversion history
* Store recent conversions using `localStorage`
* Add currency symbols
* Add conversion charts
* Add more currencies
* Add automatic conversion while typing
* Improve accessibility
* Add unit tests
* Migrate the project to TypeScript

---

