# Notes

- Superscript of Javascript
- Statically-typed
- TS Compiler will catch type errors
- annotate varibale types
- Less errors at run-time
- Code completion and refactoring
- need to transpile

## Types

### JS:
- Number
- String
- Boolean
- Null
- Undefined
- Object

### TS:
- Any
- Unknown
- Never
- Enum
- Tuple

## Example

### Tuple
```ts
let user: [number, string] = [1, 'Mosh'];
```

### Enum
```ts
enum Size { Small = 1, Medium, Large }

let mySize: Size = Size.Medium;
//  => 2
```

### Function
```ts
function calculateTax(income: number, taxYear = 2022): number {
    if (taxYear < 2022)
        return income * 1.2;
    return income * 1.3
}

calculateTax(10_000);
```

### Object
```ts
let employee: {
    readonly id: number;
    name: string;
    retire: (date: Date) => void;
} = { 
    id: 1, 
    name: "Mosh", 
    retire: (date: Date) => {
        console.log(date);
    } 
};
```

### Type Alias
```ts
type Employee = {
    readonly id: number,
    name: string,
    retire: (date: Date) => void
}

let employee: Employee = {
    id: 1,
    name: "Stephen",
    retire: (date: Date) => {
        console.log(date);
    }
}
```

### Union Type
```ts
function kgToLbs(weight: number | string): number {
    // remember 'narrowing'
    if (typeof weight === 'number')
        return weight * 2.2;
    else
        return parseInt(weight) * 2.2;
}
kgToLbs(10);
kgToLbs('10kg');
```

### Intersection Type
```ts
type Draggable = {
    drag: () => void
};

type Resizable = {
    resize: () => void
};

// Intersection Type
type UIWidget = Draggable & Resizable;

let textBox: UIWidget = {
    drag: () => {},
    resize: () => {}
}
```

### Literal Type
```ts
type Quantity = 50 | 100;
let quantity: Quantity = 100;

// error
let bad: Quantity = 80;
```

### Nullable Types
```ts
function greet(name: string | null | undefined) {
    if (name)
        console.log(name.toUpperCase());
    else
        console.log('Hola!');
}

greet(null);
```

### Optional Chaining
```ts
type Customer = {
    // Optional property
    birthday?: Date;
};

function getCustomer(id: number): Customer | null | undefined {
    return id === 0 ? null : { birthday: new Date() };
}

let customer = getCustomer(0);
//  Optional property access operator
console.log(customer?.birthday?.getFullYear);

// Optional element access operator
// cutomers?.[0]

// Optional call
let log: any = null
log?.('a');
```