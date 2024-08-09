# learn-ts

Chúng ta sẽ đi qua từng phần của lộ trình học TypeScript, cung cấp ví dụ cụ thể cho mỗi phần để bạn có thể hiểu rõ hơn. Hãy bắt đầu với phần đầu tiên:

---

### **1. Giới thiệu về TypeScript**

#### **1.1. Tổng quan về TypeScript**

-   **TypeScript là gì?**

    -   **Mô tả**: TypeScript là một ngôn ngữ lập trình được xây dựng trên JavaScript, cung cấp thêm các tính năng như kiểu tĩnh (static typing), classes, interfaces, và nhiều hơn nữa. TypeScript giúp bắt lỗi trong quá trình phát triển, giúp code dễ bảo trì và mở rộng.

-   **Cài đặt TypeScript**

    -   **Ví dụ**: Để cài đặt TypeScript, bạn có thể sử dụng npm (Node Package Manager) qua lệnh sau:

        ```bash
        npm install -g typescript
        ```

        Sau khi cài đặt, bạn có thể kiểm tra phiên bản TypeScript bằng lệnh:

        ```bash
        tsc --version
        ```

-   **Thiết lập môi trường phát triển**

    -   **Mô tả**: Chúng ta sẽ thiết lập môi trường làm việc với Visual Studio Code (VSCode) và cấu hình một dự án TypeScript cơ bản.

    -   **Ví dụ**: Tạo một file TypeScript đơn giản (`example.ts`) và biên dịch nó:

        ```typescript
        // example.ts
        const greet = (name: string): string => {
            return `Hello, ${name}!`;
        };

        console.log(greet("TypeScript"));
        ```

        Để biên dịch file này thành JavaScript, bạn sử dụng lệnh:

        ```bash
        tsc example.ts
        ```

        Sau khi biên dịch, bạn sẽ thấy file `example.js` được tạo ra và có thể chạy bằng Node.js:

        ```bash
        node example.js
        ```

---

### **2. Cơ bản về TypeScript**

#### **2.1. Kiểu dữ liệu cơ bản**

-   **Kiểu dữ liệu nguyên thủy**

    -   **Ví dụ**: Đây là một số kiểu dữ liệu cơ bản trong TypeScript:

        ```typescript
        let isDone: boolean = false;
        let count: number = 42;
        let userName: string = "John";

        let numbers: number[] = [1, 2, 3];
        let tuple: [string, number] = ["hello", 10];

        enum Color {
            Red,
            Green,
            Blue,
        }
        let color: Color = Color.Green;

        let notSure: any = 4;
        notSure = "Could be a string";
        notSure = false; // Okay
        ```

#### **2.2. Kiểu tùy chỉnh (Custom Types)**

-   **Union Types**

    -   **Ví dụ**: Bạn có thể khai báo biến với nhiều kiểu dữ liệu:

        ```typescript
        let value: string | number;
        value = "Hello"; // OK
        value = 123; // OK
        // value = true; // Error: Type 'boolean' is not assignable to type 'string | number'.
        ```

-   **Type Alias**

    -   **Ví dụ**: Tạo một kiểu tùy chỉnh:

        ```typescript
        type StringOrNumber = string | number;

        let value: StringOrNumber;
        value = "Hello"; // OK
        value = 123; // OK
        ```

-   **Interface**

    -   **Ví dụ**: Sử dụng `interface` để định nghĩa cấu trúc của một đối tượng:

        ```typescript
        interface User {
            name: string;
            age: number;
            isAdmin?: boolean; // optional property
        }

        let user: User = {
            name: "Alice",
            age: 25,
        };
        ```

---

### **3. Cấu trúc điều khiển và hàm**

#### **3.1. Câu lệnh điều kiện và vòng lặp**

-   **Câu lệnh điều kiện**

    -   **Ví dụ**: Sử dụng `if`, `else` và `switch`:

        ```typescript
        let age: number = 18;

        if (age >= 18) {
            console.log("You are an adult.");
        } else {
            console.log("You are a minor.");
        }

        let day: number = 3;
        switch (day) {
            case 1:
                console.log("Monday");
                break;
            case 2:
                console.log("Tuesday");
                break;
            case 3:
                console.log("Wednesday");
                break;
            default:
                console.log("Another day");
                break;
        }
        ```

-   **Vòng lặp**

    -   **Ví dụ**: Sử dụng `for`, `while` và `for...of`:

        ```typescript
        // For loop
        for (let i = 0; i < 5; i++) {
            console.log(i);
        }

        // While loop
        let i = 0;
        while (i < 5) {
            console.log(i);
            i++;
        }

        // For...of loop
        let arr = [10, 20, 30];
        for (let value of arr) {
            console.log(value);
        }
        ```

#### **3.2. Hàm trong TypeScript**

-   **Hàm cơ bản**

    -   **Ví dụ**: Định nghĩa hàm với kiểu trả về:

        ```typescript
        function add(a: number, b: number): number {
            return a + b;
        }

        console.log(add(2, 3)); // Output: 5
        ```

-   **Tham số tùy chọn và tham số mặc định**

    -   **Ví dụ**:

        ```typescript
        function greet(name: string, greeting: string = "Hello"): string {
            return `${greeting}, ${name}!`;
        }

        console.log(greet("Alice")); // Output: "Hello, Alice!"
        console.log(greet("Bob", "Hi")); // Output: "Hi, Bob!"
        ```

-   **Arrow functions**

    -   **Ví dụ**:

        ```typescript
        const multiply = (x: number, y: number): number => {
            return x * y;
        };

        console.log(multiply(4, 5)); // Output: 20
        ```

---

### **4. Lập trình hướng đối tượng trong TypeScript**

#### **4.1. Class và Object**

-   **Định nghĩa class**

    -   **Ví dụ**: Tạo một class đơn giản trong TypeScript với constructor và thuộc tính:

        ```typescript
        class Person {
            name: string;
            age: number;

            constructor(name: string, age: number) {
                this.name = name;
                this.age = age;
            }

            greet() {
                return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
            }
        }

        let person = new Person("Alice", 30);
        console.log(person.greet()); // Output: "Hello, my name is Alice and I am 30 years old."
        ```

-   **Phương thức (Methods)**

    -   **Ví dụ**: Thêm các phương thức vào class để thực hiện các hành động:

        ```typescript
        class Calculator {
            add(a: number, b: number): number {
                return a + b;
            }

            subtract(a: number, b: number): number {
                return a - b;
            }
        }

        let calc = new Calculator();
        console.log(calc.add(5, 3)); // Output: 8
        console.log(calc.subtract(5, 3)); // Output: 2
        ```

-   **Tính kế thừa (Inheritance)**

    -   **Ví dụ**: Tạo một class con kế thừa từ class cha:

        ```typescript
        class Animal {
            name: string;

            constructor(name: string) {
                this.name = name;
            }

            move(distance: number = 0) {
                console.log(`${this.name} moved ${distance} meters.`);
            }
        }

        class Dog extends Animal {
            bark() {
                console.log("Woof! Woof!");
            }
        }

        let dog = new Dog("Buddy");
        dog.bark(); // Output: "Woof! Woof!"
        dog.move(10); // Output: "Buddy moved 10 meters."
        ```

-   **Overriding và super()**

    -   **Ví dụ**: Ghi đè phương thức trong class con và sử dụng `super()` để gọi phương thức của class cha:

        ```typescript
        class Animal {
            name: string;

            constructor(name: string) {
                this.name = name;
            }

            move(distance: number = 0) {
                console.log(`${this.name} moved ${distance} meters.`);
            }
        }

        class Bird extends Animal {
            move(distance: number = 0) {
                console.log("Flying...");
                super.move(distance);
            }
        }

        let bird = new Bird("Sparrow");
        bird.move(20); // Output: "Flying... Sparrow moved 20 meters."
        ```

#### **4.2. Access Modifiers**

-   **public, private, protected**

    -   **Ví dụ**: Sử dụng các từ khóa `public`, `private`, và `protected` để điều chỉnh quyền truy cập:

        ```typescript
        class Vehicle {
            public brand: string;
            protected speed: number;
            private vin: string;

            constructor(brand: string, speed: number, vin: string) {
                this.brand = brand;
                this.speed = speed;
                this.vin = vin;
            }

            public accelerate() {
                this.speed += 10;
                console.log(`Accelerating... Speed is now ${this.speed}`);
            }

            protected checkSpeed() {
                console.log(`Speed is ${this.speed}`);
            }

            private checkVin() {
                console.log(`VIN is ${this.vin}`);
            }
        }

        class Car extends Vehicle {
            constructor(brand: string, speed: number, vin: string) {
                super(brand, speed, vin);
            }

            public boost() {
                this.speed += 50;
                console.log(`Boosting... Speed is now ${this.speed}`);
            }

            public showSpeed() {
                this.checkSpeed();
            }
        }

        let car = new Car("Toyota", 120, "1HGBH41JXMN109186");
        car.accelerate(); // OK, public method
        car.boost(); // OK, public method
        car.showSpeed(); // OK, protected method accessed through public method

        // car.checkVin(); // Error: Property 'checkVin' is private and only accessible within class 'Vehicle'.
        ```

-   **Readonly**

    -   **Ví dụ**: Sử dụng `readonly` để tạo thuộc tính chỉ có thể đọc:

        ```typescript
        class Book {
            readonly title: string;

            constructor(title: string) {
                this.title = title;
            }

            displayTitle() {
                console.log(`The book title is ${this.title}`);
            }
        }

        let book = new Book("TypeScript for Beginners");
        console.log(book.title); // Output: "TypeScript for Beginners"

        // book.title = "Advanced TypeScript"; // Error: Cannot assign to 'title' because it is a read-only property.
        ```

#### **4.3. Abstraction và Interface**

-   **Abstract class**

    -   **Ví dụ**: Sử dụng abstract class để tạo ra các lớp trừu tượng:

        ```typescript
        abstract class Shape {
            abstract area(): number;
            abstract perimeter(): number;

            describe(): string {
                return "This is a shape";
            }
        }

        class Circle extends Shape {
            radius: number;

            constructor(radius: number) {
                super();
                this.radius = radius;
            }

            area(): number {
                return Math.PI * this.radius ** 2;
            }

            perimeter(): number {
                return 2 * Math.PI * this.radius;
            }
        }

        let circle = new Circle(5);
        console.log(circle.area()); // Output: 78.53981633974483
        console.log(circle.perimeter()); // Output: 31.41592653589793
        console.log(circle.describe()); // Output: "This is a shape"
        ```

-   **Interface**

    -   **Ví dụ**: Sử dụng interface để định nghĩa cấu trúc của object:

        ```typescript
        interface Drawable {
            draw(): void;
        }

        interface Shape {
            area(): number;
        }

        class Rectangle implements Drawable, Shape {
            width: number;
            height: number;

            constructor(width: number, height: number) {
                this.width = width;
                this.height = height;
            }

            draw(): void {
                console.log("Drawing a rectangle...");
            }

            area(): number {
                return this.width * this.height;
            }
        }

        let rect = new Rectangle(10, 20);
        rect.draw(); // Output: "Drawing a rectangle..."
        console.log(rect.area()); // Output: 200
        ```

#### **4.4. Generics**

-   **Generics cơ bản**

    -   **Ví dụ**: Sử dụng Generics để tạo hàm và class linh hoạt hơn:

        ```typescript
        function identity<T>(arg: T): T {
            return arg;
        }

        console.log(identity<number>(42)); // Output: 42
        console.log(identity<string>("Hello")); // Output: "Hello"
        ```

-   **Generics Constraints**

    -   **Ví dụ**: Áp dụng ràng buộc lên Generics:

        ```typescript
        interface Lengthwise {
            length: number;
        }

        function loggingIdentity<T extends Lengthwise>(arg: T): T {
            console.log(arg.length); // OK
            return arg;
        }

        loggingIdentity({ length: 10, value: 3 }); // Output: 10
        // loggingIdentity(3); // Error: Argument of type '3' is not assignable to parameter of type 'Lengthwise'.
        ```

---

### **5. Module và Namespace trong TypeScript**

#### **5.1. Module trong TypeScript**

-   **Giới thiệu về Module**

    -   **Mô tả**: Module trong TypeScript là các file chứa code (class, function, interface, v.v.) và có thể được import/export giữa các file khác nhau. Module giúp chia nhỏ ứng dụng thành các phần có thể tái sử dụng và quản lý dễ dàng hơn.

-   **Export và Import**

    -   **Ví dụ**: Tạo và sử dụng module:

        **File: `mathUtils.ts`**

        ```typescript
        export function add(a: number, b: number): number {
            return a + b;
        }

        export function subtract(a: number, b: number): number {
            return a - b;
        }

        export class Calculator {
            multiply(a: number, b: number): number {
                return a * b;
            }
        }
        ```

        **File: `app.ts`**

        ```typescript
        import { add, subtract, Calculator } from "./mathUtils";

        console.log(add(5, 3)); // Output: 8
        console.log(subtract(5, 3)); // Output: 2

        let calc = new Calculator();
        console.log(calc.multiply(4, 5)); // Output: 20
        ```

-   **Export Default**

    -   **Ví dụ**: Sử dụng `export default` khi muốn export một thành phần duy nhất trong một file:

        **File: `greet.ts`**

        ```typescript
        export default function greet(name: string): string {
            return `Hello, ${name}!`;
        }
        ```

        **File: `app.ts`**

        ```typescript
        import greet from "./greet";

        console.log(greet("TypeScript")); // Output: "Hello, TypeScript!"
        ```

-   **Wildcard Import (`import * as`)**

    -   **Ví dụ**: Sử dụng `import * as` để import toàn bộ các thành phần từ một module:

        ```typescript
        import * as MathUtils from "./mathUtils";

        console.log(MathUtils.add(10, 5)); // Output: 15
        console.log(MathUtils.subtract(10, 5)); // Output: 5

        let calc = new MathUtils.Calculator();
        console.log(calc.multiply(3, 3)); // Output: 9
        ```

#### **5.2. Namespace**

-   **Giới thiệu về Namespace**

    -   **Mô tả**: Namespace là cách để nhóm các mã lại với nhau và tránh xung đột tên trong các ứng dụng lớn. Namespace thường được sử dụng khi bạn không cần tách code thành nhiều file riêng biệt như module.

-   **Định nghĩa và sử dụng Namespace**

    -   **Ví dụ**: Tạo và sử dụng Namespace:

        **File: `app.ts`**

        ```typescript
        namespace Geometry {
            export class Rectangle {
                constructor(public width: number, public height: number) {}

                area(): number {
                    return this.width * this.height;
                }
            }

            export class Circle {
                constructor(public radius: number) {}

                area(): number {
                    return Math.PI * this.radius ** 2;
                }
            }
        }

        let rect = new Geometry.Rectangle(10, 20);
        console.log(rect.area()); // Output: 200

        let circle = new Geometry.Circle(5);
        console.log(circle.area()); // Output: 78.53981633974483
        ```

-   **Nested Namespace**

    -   **Ví dụ**: Tạo Namespace lồng nhau để quản lý các nhóm mã liên quan:

        ```typescript
        namespace App {
            export namespace Utils {
                export function log(message: string): void {
                    console.log(message);
                }
            }

            export namespace Models {
                export class User {
                    constructor(public name: string, public age: number) {}
                }
            }
        }

        let user = new App.Models.User("Alice", 30);
        App.Utils.log(`User: ${user.name}, Age: ${user.age}`); // Output: "User: Alice, Age: 30"
        ```

-   **Sử dụng alias cho Namespace**

    -   **Ví dụ**: Sử dụng alias để rút gọn tên Namespace:

        ```typescript
        namespace Utilities {
            export function formatDate(date: Date): string {
                return date.toDateString();
            }

            export function formatNumber(number: number): string {
                return number.toFixed(2);
            }
        }

        import Utils = Utilities;

        console.log(Utils.formatDate(new Date())); // Output: "Sat Aug 10 2024"
        console.log(Utils.formatNumber(1234.56789)); // Output: "1234.57"
        ```

---

### **6. Cấu hình dự án TypeScript với `tsconfig.json`**

#### **6.1. Giới thiệu về `tsconfig.json`**

-   **Mô tả**: File `tsconfig.json` là nơi bạn định nghĩa các tùy chọn cấu hình cho trình biên dịch TypeScript (TypeScript compiler). Nó giúp bạn kiểm soát quá trình biên dịch mã TypeScript, từ việc chỉ định các file nguồn, thư mục output, đến việc bật/tắt các tính năng biên dịch cụ thể.

#### **6.2. Tạo file `tsconfig.json`**

-   **Ví dụ**: Bạn có thể khởi tạo file `tsconfig.json` cơ bản bằng lệnh:

    ```bash
    tsc --init
    ```

    Sau khi chạy lệnh này, một file `tsconfig.json` sẽ được tạo trong thư mục hiện tại với các cấu hình mặc định.

#### **6.3. Các tùy chọn cấu hình cơ bản trong `tsconfig.json`**

-   **`compilerOptions`**

    -   **Mô tả**: Đây là phần quan trọng nhất của `tsconfig.json`, nơi bạn cấu hình các tùy chọn cho trình biên dịch.

    -   **Ví dụ**:

        ```json
        {
            "compilerOptions": {
                "target": "es5", // Phiên bản JavaScript mà mã TypeScript sẽ được biên dịch thành.
                "module": "commonjs", // Kiểu module (CommonJS, ES6, AMD, v.v.).
                "strict": true, // Bật tất cả các kiểm tra chặt chẽ (strict mode).
                "esModuleInterop": true, // Đảm bảo khả năng tương thích với các module ES.
                "outDir": "./dist", // Thư mục output cho các file biên dịch.
                "rootDir": "./src", // Thư mục chứa các file nguồn.
                "sourceMap": true // Tạo file source map để debug.
            }
        }
        ```

    -   **Giải thích một số tùy chọn chính**:
        -   **`target`**: Định nghĩa phiên bản ECMAScript mà bạn muốn biên dịch TypeScript thành. Ví dụ: `"es5"`, `"es6"`, `"es2015"`, `"esnext"`.
        -   **`module`**: Định nghĩa loại module hệ thống được sử dụng, ví dụ: `"commonjs"` (dùng cho Node.js), `"es6"` (dùng cho các dự án web hiện đại).
        -   **`strict`**: Bật chế độ nghiêm ngặt, giúp kiểm tra chặt chẽ hơn các lỗi tiềm ẩn.
        -   **`outDir`**: Chỉ định thư mục nơi các file JavaScript sẽ được đặt sau khi biên dịch.
        -   **`rootDir`**: Chỉ định thư mục gốc của các file nguồn TypeScript.
        -   **`sourceMap`**: Tạo các file source map để dễ dàng debug mã TypeScript trong các công cụ phát triển web.

#### **6.4. Một số tùy chọn khác trong `tsconfig.json`**

-   **`include` và `exclude`**

    -   **Mô tả**: Sử dụng các tùy chọn này để chỉ định những file hoặc thư mục nào sẽ được (hoặc không được) trình biên dịch TypeScript biên dịch.

    -   **Ví dụ**:

        ```json
        {
            "compilerOptions": {
                "outDir": "./dist",
                "rootDir": "./src"
            },
            "include": ["src/**/*"], // Biên dịch tất cả các file trong thư mục src
            "exclude": ["node_modules", "**/*.spec.ts"] // Loại trừ thư mục node_modules và các file test
        }
        ```

-   **`lib`**

    -   **Mô tả**: Tùy chọn này cho phép bạn thêm các thư viện JavaScript chuẩn mà bạn muốn bao gồm trong dự án.

    -   **Ví dụ**:

        ```json
        {
            "compilerOptions": {
                "lib": ["es6", "dom"] // Bao gồm các thư viện ECMAScript 6 và DOM APIs
            }
        }
        ```

-   **`paths` và `baseUrl`**

    -   **Mô tả**: Sử dụng để cấu hình alias cho các đường dẫn, giúp bạn quản lý các module một cách dễ dàng hơn.

    -   **Ví dụ**:

        ```json
        {
            "compilerOptions": {
                "baseUrl": "./", // Đặt đường dẫn gốc
                "paths": {
                    "@models/*": ["src/models/*"], // Alias cho đường dẫn tới models
                    "@utils/*": ["src/utils/*"] // Alias cho đường dẫn tới utils
                }
            }
        }
        ```

        **Sử dụng trong mã TypeScript**:

        ```typescript
        import { User } from "@models/user";
        import { calculate } from "@utils/math";
        ```

-   **`experimentalDecorators` và `emitDecoratorMetadata`**

    -   **Mô tả**: Các tùy chọn này được sử dụng khi bạn làm việc với decorators trong TypeScript.

    -   **Ví dụ**:

        ```json
        {
            "compilerOptions": {
                "experimentalDecorators": true, // Cho phép sử dụng decorators
                "emitDecoratorMetadata": true // Phát sinh metadata cho các decorators
            }
        }
        ```

-   **`noImplicitAny`**

    -   **Mô tả**: Khi tùy chọn này được bật, trình biên dịch sẽ báo lỗi nếu không thể suy luận kiểu dữ liệu và sử dụng `any` ngầm định.

    -   **Ví dụ**:

        ```json
        {
            "compilerOptions": {
                "noImplicitAny": true // Báo lỗi khi sử dụng any ngầm định
            }
        }
        ```

        **Ví dụ về lỗi khi `noImplicitAny` được bật**:

        ```typescript
        function log(message) {
            console.log(message);
        }
        // Error: Parameter 'message' implicitly has an 'any' type.
        ```

---

### **7. Kỹ thuật nâng cao trong TypeScript**

#### **7.1. Union và Intersection Types**

-   **Union Types**

    -   **Mô tả**: Union Types cho phép một biến có thể là một trong nhiều kiểu dữ liệu khác nhau.
    -   **Ví dụ**:

        ```typescript
        function printValue(value: string | number) {
            if (typeof value === "string") {
                console.log(`String: ${value}`);
            } else {
                console.log(`Number: ${value}`);
            }
        }

        printValue("Hello"); // Output: String: Hello
        printValue(42); // Output: Number: 42
        ```

-   **Intersection Types**

    -   **Mô tả**: Intersection Types cho phép một biến phải thỏa mãn nhiều kiểu dữ liệu cùng lúc.
    -   **Ví dụ**:

        ```typescript
        interface Person {
            name: string;
            age: number;
        }

        interface Employee {
            employeeId: number;
        }

        type Worker = Person & Employee;

        const worker: Worker = {
            name: "Alice",
            age: 30,
            employeeId: 1234,
        };

        console.log(worker);
        // Output: { name: "Alice", age: 30, employeeId: 1234 }
        ```

#### **7.2. Type Guards**

-   **Mô tả**: Type Guards là các kỹ thuật giúp TypeScript nhận biết được kiểu dữ liệu cụ thể của một biến trong quá trình chạy, từ đó đưa ra các cảnh báo hoặc xử lý tương ứng.

-   **Ví dụ: Sử dụng `typeof` để kiểm tra kiểu dữ liệu**:

    ```typescript
    function printType(value: string | number) {
        if (typeof value === "string") {
            console.log(`It's a string: ${value}`);
        } else {
            console.log(`It's a number: ${value}`);
        }
    }

    printType("Hello"); // Output: It's a string: Hello
    printType(100); // Output: It's a number: 100
    ```

-   **Ví dụ: Sử dụng `instanceof` để kiểm tra kiểu dữ liệu**:

    ```typescript
    class Dog {
        bark() {
            console.log("Woof!");
        }
    }

    class Cat {
        meow() {
            console.log("Meow!");
        }
    }

    function makeSound(animal: Dog | Cat) {
        if (animal instanceof Dog) {
            animal.bark();
        } else if (animal instanceof Cat) {
            animal.meow();
        }
    }

    let dog = new Dog();
    let cat = new Cat();

    makeSound(dog); // Output: Woof!
    makeSound(cat); // Output: Meow!
    ```

#### **7.3. Type Assertion**

-   **Mô tả**: Type Assertion cho phép bạn thông báo với TypeScript về kiểu dữ liệu mà bạn chắc chắn, giúp trình biên dịch hiểu rõ hơn về biến và tránh báo lỗi không cần thiết.

-   **Ví dụ: Sử dụng cú pháp `as`**:

    ```typescript
    let someValue: any = "Hello, TypeScript";
    let strLength: number = (someValue as string).length;

    console.log(strLength); // Output: 16
    ```

-   **Ví dụ: Sử dụng cú pháp `<type>`**:

    ```typescript
    let someValue: any = "Hello, TypeScript";
    let strLength: number = (<string>someValue).length;

    console.log(strLength); // Output: 16
    ```

#### **7.4. Conditional Types**

-   **Mô tả**: Conditional Types trong TypeScript cho phép bạn định nghĩa các kiểu dữ liệu phức tạp dựa trên điều kiện.

-   **Ví dụ: Tạo conditional types đơn giản**:

    ```typescript
    type IsString<T> = T extends string ? "Yes" : "No";

    type Test1 = IsString<string>; // "Yes"
    type Test2 = IsString<number>; // "No"
    ```

#### **7.5. Utility Types**

-   **Mô tả**: TypeScript cung cấp các Utility Types để giúp bạn xử lý và biến đổi các kiểu dữ liệu một cách linh hoạt.

-   **Partial**

    -   **Ví dụ**: Sử dụng `Partial` để biến tất cả các thuộc tính của một kiểu dữ liệu thành tùy chọn (optional).

        ```typescript
        interface Person {
            name: string;
            age: number;
            address: string;
        }

        let partialPerson: Partial<Person> = {
            name: "Alice",
        };

        console.log(partialPerson); // Output: { name: "Alice" }
        ```

-   **Readonly**

    -   **Ví dụ**: Sử dụng `Readonly` để biến tất cả các thuộc tính của một kiểu dữ liệu thành chỉ đọc (readonly).

        ```typescript
        interface Person {
            name: string;
            age: number;
        }

        const person: Readonly<Person> = {
            name: "Alice",
            age: 30,
        };

        // person.age = 31; // Error: Cannot assign to 'age' because it is a read-only property.
        ```

-   **Pick**

    -   **Ví dụ**: Sử dụng `Pick` để chọn một tập hợp con của các thuộc tính từ một kiểu dữ liệu.

        ```typescript
        interface Person {
            name: string;
            age: number;
            address: string;
        }

        type NameAndAge = Pick<Person, "name" | "age">;

        let person: NameAndAge = {
            name: "Alice",
            age: 30,
        };

        console.log(person); // Output: { name: "Alice", age: 30 }
        ```

-   **Omit**

    -   **Ví dụ**: Sử dụng `Omit` để loại bỏ một tập hợp con của các thuộc tính từ một kiểu dữ liệu.

        ```typescript
        interface Person {
            name: string;
            age: number;
            address: string;
        }

        type NameOnly = Omit<Person, "age" | "address">;

        let person: NameOnly = {
            name: "Alice",
        };

        console.log(person); // Output: { name: "Alice" }
        ```

#### **7.6. Decorators**

-   **Mô tả**: Decorators là một tính năng mạnh mẽ của TypeScript, cho phép bạn thay đổi hành vi của class, phương thức, thuộc tính, và tham số. Decorators rất phổ biến trong các framework như Angular.

-   **Class Decorator**

    -   **Ví dụ**: Tạo một class decorator đơn giản:

        ```typescript
        function sealed(constructor: Function) {
            Object.seal(constructor);
            Object.seal(constructor.prototype);
        }

        @sealed
        class Greeter {
            greeting: string;

            constructor(message: string) {
                this.greeting = message;
            }

            greet() {
                return `Hello, ${this.greeting}`;
            }
        }

        const greeter = new Greeter("World");
        console.log(greeter.greet()); // Output: "Hello, World"
        ```

-   **Method Decorator**

    -   **Ví dụ**: Tạo một method decorator để log thông tin về phương thức được gọi:

        ```typescript
        function logMethod(
            target: any,
            propertyName: string,
            propertyDesciptor: PropertyDescriptor
        ): PropertyDescriptor {
            const method = propertyDesciptor.value;

            propertyDesciptor.value = function (...args: any[]) {
                console.log(`Calling ${propertyName} with arguments: ${JSON.stringify(args)}`);
                const result = method.apply(this, args);
                console.log(`Result: ${result}`);
                return result;
            };

            return propertyDesciptor;
        }

        class Calculator {
            @logMethod
            add(a: number, b: number): number {
                return a + b;
            }
        }

        const calc = new Calculator();
        calc.add(5, 3); // Output: Calling add with arguments: [5,3]
        // Output: Result: 8
        ```

#### **7.7. Advanced Generics**

-   **Mô tả**: Generics nâng cao giúp tạo ra các kiểu dữ liệu và hàm mạnh mẽ, linh hoạt hơn trong TypeScript.

-   **Mapped Types**

    -   **Ví dụ**: Tạo Mapped Types để biến đổi tất cả các thuộc tính của một kiểu:

        ```typescript
        type Person = {
            name: string;
            age: number;
            address: string;
        };

        type ReadonlyPerson = {
            readonly [K in keyof Person]: Person[K];
        };

        const person: ReadonlyPerson = {
            name: "Alice",
            age: 30,
            address: "123 Street",
        };

        // person.age = 31; // Error: Cannot assign to 'age' because it is a read-only property.
        ```

-   **Conditional Types**

    -   **Ví dụ**: Sử dụng Conditional Types để xử lý các trường hợp phức tạp:

        ```typescript
        type ExtractStringType<T> = T extends { [key: string]: infer U } ? U : never;

        type Person = {
            name: string;
            age: number;
        };

        type Result = ExtractStringType<Person>; // Result is string | number
        ```

---
### **8. Áp dụng TypeScript trong dự án thực tế**

#### **8.1. Tích hợp TypeScript vào một dự án Node.js**

- **Khởi tạo dự án Node.js với TypeScript**
  - **Bước 1**: Tạo một thư mục mới cho dự án và khởi tạo `package.json`.

    ```bash
    mkdir my-ts-project
    cd my-ts-project
    npm init -y
    ```

  - **Bước 2**: Cài đặt TypeScript và các công cụ cần thiết.

    ```bash
    npm install typescript ts-node @types/node --save-dev
    ```

  - **Bước 3**: Khởi tạo file `tsconfig.json`.

    ```bash
    npx tsc --init
    ```

  - **Bước 4**: Tạo một file TypeScript đầu tiên.

    **File: `src/index.ts`**

    ```typescript
    const greeting: string = "Hello, TypeScript!";
    console.log(greeting);
    ```

  - **Bước 5**: Thêm script để chạy dự án bằng TypeScript trong `package.json`.

    ```json
    {
      "scripts": {
        "start": "ts-node src/index.ts"
      }
    }
    ```

  - **Bước 6**: Chạy dự án.

    ```bash
    npm start
    ```

#### **8.2. Áp dụng TypeScript với React**

- **Khởi tạo dự án React với TypeScript**
  - **Bước 1**: Sử dụng `create-react-app` để khởi tạo dự án React với TypeScript.

    ```bash
    npx create-react-app my-react-app --template typescript
    cd my-react-app
    ```

  - **Bước 2**: Chạy ứng dụng React.

    ```bash
    npm start
    ```

  - **Bước 3**: Tạo một component React với TypeScript.

    **File: `src/components/Hello.tsx`**

    ```typescript
    import React from 'react';

    interface HelloProps {
        name: string;
    }

    const Hello: React.FC<HelloProps> = ({ name }) => {
        return <h1>Hello, {name}!</h1>;
    }

    export default Hello;
    ```

  - **Bước 4**: Sử dụng component trong ứng dụng.

    **File: `src/App.tsx`**

    ```typescript
    import React from 'react';
    import Hello from './components/Hello';

    function App() {
        return (
            <div>
                <Hello name="TypeScript" />
            </div>
        );
    }

    export default App;
    ```

#### **8.3. Sử dụng TypeScript với Express.js**

- **Khởi tạo dự án Express.js với TypeScript**
  - **Bước 1**: Tạo thư mục dự án và khởi tạo `package.json`.

    ```bash
    mkdir my-express-app
    cd my-express-app
    npm init -y
    ```

  - **Bước 2**: Cài đặt các thư viện cần thiết.

    ```bash
    npm install express
    npm install typescript ts-node @types/node @types/express --save-dev
    ```

  - **Bước 3**: Khởi tạo file `tsconfig.json`.

    ```bash
    npx tsc --init
    ```

  - **Bước 4**: Tạo file cấu trúc cơ bản cho ứng dụng Express.js.

    **File: `src/app.ts`**

    ```typescript
    import express, { Request, Response } from 'express';

    const app = express();
    const port = 3000;

    app.get('/', (req: Request, res: Response) => {
        res.send('Hello, TypeScript with Express!');
    });

    app.listen(port, () => {
        console.log(`Server is running on http://localhost:${port}`);
    });
    ```

  - **Bước 5**: Thêm script để chạy server bằng TypeScript trong `package.json`.

    ```json
    {
      "scripts": {
        "start": "ts-node src/app.ts"
      }
    }
    ```

  - **Bước 6**: Chạy server.

    ```bash
    npm start
    ```

#### **8.4. Kiểm thử mã TypeScript với Jest**

- **Cài đặt và cấu hình Jest cho TypeScript**
  - **Bước 1**: Cài đặt Jest và các thư viện hỗ trợ TypeScript.

    ```bash
    npm install jest ts-jest @types/jest --save-dev
    ```

  - **Bước 2**: Tạo file cấu hình cho Jest.

    **File: `jest.config.js`**

    ```javascript
    module.exports = {
        preset: 'ts-jest',
        testEnvironment: 'node',
    };
    ```

  - **Bước 3**: Viết một test case đơn giản.

    **File: `src/sum.ts`**

    ```typescript
    export function sum(a: number, b: number): number {
        return a + b;
    }
    ```

    **File: `src/sum.test.ts`**

    ```typescript
    import { sum } from './sum';

    test('adds 1 + 2 to equal 3', () => {
        expect(sum(1, 2)).toBe(3);
    });
    ```

  - **Bước 4**: Thêm script để chạy Jest trong `package.json`.

    ```json
    {
      "scripts": {
        "test": "jest"
      }
    }
    ```

  - **Bước 5**: Chạy các test case.

    ```bash
    npm test
    ```

#### **8.5. Sử dụng TypeScript với GraphQL**

- **Tạo dự án GraphQL với TypeScript**
  - **Bước 1**: Khởi tạo dự án Node.js.

    ```bash
    mkdir my-graphql-app
    cd my-graphql-app
    npm init -y
    ```

  - **Bước 2**: Cài đặt các thư viện cần thiết.

    ```bash
    npm install express express-graphql graphql
    npm install typescript ts-node @types/node @types/express @types/graphql --save-dev
    ```

  - **Bước 3**: Tạo file cấu trúc cơ bản cho GraphQL.

    **File: `src/schema.ts`**

    ```typescript
    import { GraphQLObjectType, GraphQLSchema, GraphQLString } from 'graphql';

    const RootQuery = new GraphQLObjectType({
        name: 'RootQueryType',
        fields: {
            hello: {
                type: GraphQLString,
                resolve() {
                    return 'Hello, GraphQL with TypeScript!';
                }
            }
        }
    });

    export const schema = new GraphQLSchema({
        query: RootQuery
    });
    ```

    **File: `src/app.ts`**

    ```typescript
    import express from 'express';
    import { graphqlHTTP } from 'express-graphql';
    import { schema } from './schema';

    const app = express();
    const port = 4000;

    app.use('/graphql', graphqlHTTP({
        schema: schema,
        graphiql: true,
    }));

    app.listen(port, () => {
        console.log(`GraphQL server running at http://localhost:${port}/graphql`);
    });
    ```

  - **Bước 4**: Thêm script để chạy server trong `package.json`.

    ```json
    {
      "scripts": {
        "start": "ts-node src/app.ts"
      }
    }
    ```

  - **Bước 5**: Chạy server.

    ```bash
    npm start
    ```

  - **Bước 6**: Truy cập vào http://localhost:4000/graphql và thử truy vấn:

    ```graphql
    {
      hello
    }
    ```

    **Output**:

    ```json
    {
      "data": {
        "hello": "Hello, GraphQL with TypeScript!"
      }
    }
    ```

#### **8.6. TypeScript với các thư viện và framework khác**

- **TypeScript với Angular**: Angular hỗ trợ TypeScript theo mặc định, bạn có thể sử dụng Angular CLI để tạo dự án với TypeScript.
- **TypeScript với Vue.js**: Bạn có thể sử dụng Vue CLI để tạo dự án Vue.js với TypeScript, hoặc tích hợp TypeScript vào dự án Vue.js hiện có.
- **TypeScript với Next.js**: Next.js hỗ trợ TypeScript một cách liền mạch, chỉ cần thêm một vài file cấu hình là có thể bắt đầu sử dụng.

---


### **9. Tài nguyên học tập TypeScript và lời khuyên cuối cùng**

#### **9.1. Tài nguyên học tập**

- **Sách**
  - **"TypeScript Handbook"**: Tài liệu chính thức của TypeScript, rất chi tiết và đầy đủ. Bạn có thể đọc online miễn phí trên trang web của TypeScript.
    - [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)

  - **"Pro TypeScript: Application-Scale JavaScript Development"** của Steve Fenton: Sách này cung cấp cái nhìn sâu sắc về TypeScript và cách áp dụng nó vào phát triển ứng dụng quy mô lớn.

  - **"Learning TypeScript 2.x"** của Remo H. Jansen: Hướng dẫn chi tiết cho những người mới bắt đầu với TypeScript và những người muốn nâng cao kỹ năng.

- **Khóa học online**
  - **Udemy**: Các khóa học như “Understanding TypeScript” của Maximilian Schwarzmüller cung cấp hướng dẫn chi tiết và bài tập thực hành.
    - [Understanding TypeScript on Udemy](https://www.udemy.com/course/understanding-typescript/)

  - **Pluralsight**: Có nhiều khóa học về TypeScript với các cấp độ khác nhau, từ cơ bản đến nâng cao.
    - [TypeScript Courses on Pluralsight](https://www.pluralsight.com/courses?query=typescript)

  - **Codecademy**: Cung cấp một khóa học TypeScript cơ bản với nhiều bài tập thực hành.
    - [Learn TypeScript on Codecademy](https://www.codecademy.com/learn/learn-typescript)

- **Video**
  - **YouTube**: Các kênh như Academind, Traversy Media, và The Net Ninja có nhiều video hướng dẫn về TypeScript.
    - [Academind TypeScript Playlist](https://www.youtube.com/playlist?list=PL55RiY5tL51pw7gEEn9MPs5xMtoZt9T8r)

- **Blog và tài liệu trực tuyến**
  - **TypeScript Blog**: Cung cấp các cập nhật và bài viết về các tính năng mới và tốt nhất về TypeScript.
    - [TypeScript Blog](https://devblogs.microsoft.com/typescript/)

  - **Medium**: Nhiều bài viết và hướng dẫn về TypeScript từ cộng đồng.
    - [Medium TypeScript Articles](https://medium.com/tag/typescript)

- **Cộng đồng**
  - **Stack Overflow**: Một nguồn tài nguyên hữu ích cho việc giải quyết các vấn đề cụ thể.
    - [TypeScript Questions on Stack Overflow](https://stackoverflow.com/questions/tagged/typescript)

  - **Reddit**: Subreddit như r/typescript cung cấp một nơi để thảo luận và hỏi đáp về TypeScript.
    - [r/typescript](https://www.reddit.com/r/typescript/)

#### **9.2. Lời khuyên cuối cùng**

- **Thực hành là chìa khóa**: Việc áp dụng những gì bạn học vào các dự án thực tế là cách hiệu quả nhất để củng cố kiến thức. Hãy thử tạo ra các dự án nhỏ hoặc đóng góp vào các dự án mã nguồn mở.

- **Đọc mã nguồn**: Xem và phân tích mã nguồn của các dự án TypeScript lớn có thể giúp bạn hiểu cách các nhà phát triển khác sử dụng TypeScript và các best practices.

- **Tham gia cộng đồng**: Tham gia các nhóm, diễn đàn và các cuộc thảo luận về TypeScript để cập nhật những thay đổi mới nhất và nhận được sự hỗ trợ từ cộng đồng.

- **Cập nhật thường xuyên**: TypeScript liên tục phát triển với các tính năng mới và cải tiến. Hãy chắc chắn rằng bạn theo dõi các bản phát hành mới và tài liệu chính thức để luôn cập nhật.

- **Sử dụng các công cụ và tiện ích**: Khám phá các công cụ và tiện ích hỗ trợ TypeScript, như các plugin IDE, công cụ kiểm thử, và các thư viện tiện ích, để tăng cường hiệu quả làm việc và bảo trì mã nguồn.

---
