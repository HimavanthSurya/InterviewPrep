### ❓1. What is the C#? What is the difference between C# and .NET ?

**Answer:**

- C# is a modern, object oriented programming language which is developed by microsoft. It is primarily used for developing aplications on .NET platform --- such as Web Applications, Desktop Applications, APIs, Mobile Applications using .NET MAUI or Xamarin.
- .NET Framework, on the other hand is the complete development platform which consists of CLR(Common Language Runtime), Class Libraries and tools required to build and run applications which are written in C#, F# and other .NET Supported languages

<p align="center"><img src="./images/.NET_arch.png" alt=".NET Architecture" width="50%" /></p>

---

### ❓2. What are the main concepts of OOPS ?

**Answer:**

- Object oriented programming is a programming paradim which is based on the concept of objects, which contain data(properties, fields) and methods(functions).
- OOPS principles helps us to build the scalable, reusable, modular and maintainable code.
- The four pillars of OOP in C#:

  - **Inheritance** - Enables a class to reuse the code of another class.
  - **Polymorphism** - Allows methods to behave differently based on the object.
  - **Abstraction** - Shows only essential features and hides the complexity.
  - **Encapsulation** - Binds every programming component into a single unit called as Class, hides internal details and protect data.

  <p align="center"><img src="./images/OOPs.png" alt="OOPs" width="40%" /></p>

---

### ❓3. What are the limitations of OOPs ?

**Answer:**

- OOPs is not suitable for small scale and immediate applications as building application with OOPs requires proper planning and requirement gathering which takes time and resources.

---

### ❓4. What are Classes and Objects ?

**Answer:**

- Classes are the **logical unit or blueprint**. It contains fields, properties, methods.

  - Class members are:
    1. A constructor is a method in the class which gets executed whenever a object of the class is created.
    2. A field is a variable of any type which stores the data.
    3. A property is a member that provides flexible mechanism to read and write the private field.
    4. A method is a code block which contains series of statements.

- Objects are the instance of the Class.

---

### ❓5. What are the types of the class ?

**Answer:**

- The different types of classes are :
  - Abstract Class
  - Static Class
  - Partial Class
  - Sealed Class

<p align="center"><img src="./images/classtypes.png" alt="class types" width="45%" /></p>

---

### ❓6. Is it possible to prevent object creation of a class in C# ?

**Answer:**

- **Abstract Class, Static Class, Private Class** for these class types object creation is not possible.

---

### ❓7. What are the difference between Property and Functions ?

**Answer:**

- Property is a specialized function but can only get and set the field values.

---

### ❓8. What are the differenct types of inheritance ?

**Answer:**

<p align="center"><img src="./images/InheritanceTypes.png" alt="Inheritance Types"/></p>

---

### ❓9. How to prevent class from being inherited ?

**Answer:**

- By using **SEALED** keyword in class
- By using **STATIC** keyword in class

```csharp

public sealed class Employee1
{

}

public static class Employee2
{

}

public class PermanentEmployee : Employee1 ❌❌❌
{

}

public class PermanentEmployee : Employee2 ❌❌❌
{

}
```

---

### ❓10. What is the difference between Abstraction and Encapsulation ?

**Answer:**

**Abstraction**

- Abstraction means showing only essential things and hide the complexity or Implentations
- Abstraction is the Concept of hiding programming components

```csharp
public abstract class EmployeeSalary
{
  public inte CalculateSalary()
  {
    return 10*300000;
  }
}

public class Employee : EmployeeSalary
{

}

public class SalarySection
{
  Employee employee =  new Employee();
  int sal = employee.CalculateSalary();
}

```

**Encapsulation**

- Wrapping of data and methods into a single unit is called Encapsulation.\
- Encapsulation is the implementation of the hiding of data.

```csharp
public class Employee
{
  private int empExperience;
  public int EmpExperience
  {
    get{return empExperience;}
    set{empExperience = value;}
  }
}
```
