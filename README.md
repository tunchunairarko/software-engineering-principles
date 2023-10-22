# software-engineering-principles



### 1. DRY (Don't Repeat Yourself)

**Explanation:** 
"Don't repeat yourself" (DRY) is a principle of software development aimed at reducing repetition of information which is likely to change, replacing it with abstractions that are less likely to change, or using data normalization which avoids redundancy in the first place.[Wikipedia][1]
The DRY principle is all about avoiding redundancy in your code. Imagine if you had to change something that's repeated in 10 places in your code. You'd have to remember all those places and make sure you change each one correctly. By following DRY, you centralize the code so that any changes only need to be made in one place. This makes your code more maintainable and less error-prone.

**React & TypeScript Examples:**

1. **Reusable Components:** If you find yourself using the same UI elements with slight variations, it's a sign you need a reusable component.
   ```tsx
   type ButtonProps = {
     label: string;
     onClick: () => void;
   };

   const Button: React.FC<ButtonProps> = ({ label, onClick }) => {
     return <button onClick={onClick}>{label}</button>;
   };
   ```

2. **Centralized Types:** If multiple components or functions use the same data structure, define that structure once and reuse it.
   ```typescript
   type User = {
     id: number;
     name: string;
     email: string;
   };
   ```

### 2. KISS (Keep It Simple, Stupid)

**Explanation:** 
Keep it simple, stupid (KISS) is a design principle which states that designs and/or systems should be as simple as possible. Wherever possible, complexity should be avoided in a system—as simplicity guarantees the greatest levels of user acceptance and interaction. KISS is used in a variety of disciplines, such as interface design, product design, and software development[interaction-design.org][1]. KISS is a reminder that most systems work best if they are kept simple rather than made complex. Complexity can introduce errors and make the system harder to understand and maintain. By striving for simplicity, you make your code more readable and easier to debug.

**React & TypeScript Examples:**

1. **Focused Components:** Instead of creating a mega-component that handles multiple tasks, break it down. Each component should have a single responsibility.
   ```tsx
   // Instead of:
   const UserProfileWithPosts: React.FC = () => { /* ... */ }

   // Do:
   const UserProfile: React.FC = () => { /* ... */ }
   const UserPosts: React.FC = () => { /* ... */ }
   ```

2. **Clear Naming:** Use descriptive names for variables, functions, and types. It might seem trivial, but clear naming can significantly improve code readability.
   ```typescript
   // Instead of:
   const uD = (id: number) => { /* ... */ }

   // Do:
   const getUserDetails = (userId: number) => { /* ... */ }
   ```

### 3. SOLID

**Explanation:** 
SOLID is a popular set of design principles that are used in object-oriented software development. SOLID is an acronym that stands for five key design principles: single responsibility principle, open-closed principle, Liskov substitution principle, interface segregation principle, and dependency inversion principle. All five are commonly used by software engineers and provide some important benefits for developers [bmc.com][3]. SOLID is a set of five design principles that guide developers in creating maintainable and scalable systems. Let's break them down:

- **S - Single Responsibility Principle (SRP):** A class or component should have only one reason to change. This means it should only have one job or responsibility.

- **O - Open/Closed Principle:** Software entities should be open for extension but closed for modification. This means you should be able to add new functionality without changing existing code.

- **L - Liskov Substitution Principle:** Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

- **I - Interface Segregation Principle:** Clients should not be forced to depend on interfaces they don't use. This means creating specific interfaces for different tasks rather than one general-purpose interface.

- **D - Dependency Inversion Principle:** High-level modules should not depend on low-level modules. Both should depend on abstractions. This means, for instance, that business logic should not depend directly on data access code but rather on an abstract interface.

**React & TypeScript Examples:**

1. **SRP in React:** Each component should handle one piece of functionality. For instance, if you have a component that fetches user data and displays both a profile and posts, consider splitting it.
   ```tsx
   const UserProfile: React.FC = () => { /* Fetch and display user profile */ }
   const UserPosts: React.FC = () => { /* Fetch and display user posts */ }
   ```

2. **OCP with TypeScript:** By using interfaces, you can ensure that your classes are open for extension but closed for modification.
   ```typescript
   interface Shape {
     area(): number;
   }

   class Circle implements Shape {
     radius: number;
     area() {
       return Math.PI * this.radius * this.radius;
     }
   }

   class Square implements Shape {
     side: number;
     area() {
       return this.side * this.side;
     }
   }
   ```



## References
[1]: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
[2]: https://www.interaction-design.org/literature/topics/keep-it-simple-stupid#:~:text=Keep%20it%20simple%2C%20stupid%20(KISS)%20is%20a%20design%20principle,of%20user%20acceptance%20and%20interaction
[3]: https://www.bmc.com/blogs/solid-design-principles/#:~:text=SOLID%20is%20an%20acronym%20that,some%20important%20benefits%20for%20developers
