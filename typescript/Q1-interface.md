# Interface

## object 타입 지정
```typescript
interface Square {
   width: number;
   height: number;
}

let square: Square = { width: 100, height: 100 };
```

## extends
```typescript
interface Square {
   width: number;
   height: number;
}
interface ColorSquare extends Square {
   backgroundColor: string;
}

let square: Square = { width: 100, height: 100 };
let colorSquare: ColorSquare = { width: 100, height: 100, backgroundColor: "blue" };
```

## intersection type(&)
- `type`도 가능
```typescript
interface Square {
   width: number;
   height: number;
}
interface ColorSquare {
   backgroundColor: string;
} & Square
```

## 중복 선언 가능
```typescript
interface Square {
   width: number;
}
interface Square {
   height: number;
}
let square: Square = { width: 100, height: 100 };
```
