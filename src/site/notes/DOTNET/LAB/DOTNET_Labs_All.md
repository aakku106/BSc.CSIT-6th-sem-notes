---
{"dg-publish":true,"permalink":"/dotnet/lab/dotnet-labs-all/","noteIcon":"","dg-note-properties":{}}
---

# CSIT .NET Lab Tasks — All Labs

---

## Lab Task 1: Bank Account Management System (Basic)

**Objective:** Create a basic bank account system with the ability to perform deposits, withdrawals, and maintain a transaction history. The task will help you understand object-oriented programming concepts such as classes, properties, and methods in C#.

### Instructions

**1. Create a BankAccount Class:**

- **Static Property:**
  - `BankName`: A static property representing the bank's name. It should be initialized to `"Global Trust Bank"` using a static constructor.

- **Instance Properties:**
  - `AccountName` (String): The name of the account holder (read/write).
  - `AccountNumber` (long): The unique account number (read-only).
  - `Balance` (decimal): The account balance (protected and modifiable only within the class).
  - `AccountType` (Enum): Type of account (e.g., `"Current, Saving, Business"`) (read/write, default value: `"Generic"`).
  - `IsActive` (Boolean): The account's status (read-only, default value `true`).
  - `TransactionHistory`: A list of strings that stores the transaction history (read-only outside the class).

**2. Constructor:**

- Accepts `accountName` and `accountNumber` as parameters.
- Initialize the balance to `0.0` and add a log entry for account creation to the `TransactionHistory`.

**3. Methods:**

- `Deposit(double amount)`: Increases the balance and logs the deposit in the transaction history. Ensure the deposit amount is positive.
- `Withdrawal(double amount)`: Decreases the balance and logs the withdrawal. Ensure the withdrawal amount is positive and there are sufficient funds.
- `DisplayAccountInfo()`: Displays all the account details, including the balance and transaction history.

**4. Properties:**

- For properties that should be protected or read-only, you will define getter and setter logic.
- `AccountName`: Should be get and set by default.
- `AccountNumber`: Should be a read-only property with a get method only.
- `Balance`: Should be a protected property, and you can define methods to modify it internally.
- `TransactionHistory`: This list should only be accessed in a read-only manner outside the class.

**5. Test the Class:**

- Create an instance of `BankAccount` in your `Main` method and perform the following actions:
  - Deposit some money into the account.
  - Make a withdrawal from the account.
  - Display account information including the transaction history.

---

## Lab Task 2: Bank Account Management System with Inheritance and Polymorphism

**Objective:** Extend the concepts from Lab Task 1 to enhance the system by adding multiple types of bank accounts (e.g., Savings, Checking) using Inheritance and Polymorphism. This will give you a deeper understanding of object-oriented programming (OOP) concepts in C#, such as class inheritance, method overriding, and polymorphic behavior.

### Instructions

**1. Extend the BankAccount Class:**

- You should use the `BankAccount` class from Lab 1 as the base class.
- Create two new derived classes: `SavingsAccount` and `CheckingAccount`.

**2. Derived Classes:**

- **SavingsAccount Class:**
  - **Instance Properties:**
    - `InterestRate` = 4% (`Const`)
  - This class should inherit from `BankAccount`.
  - It should override the `DisplayAccountInfo()` method to show additional information, like the interest rate.
  - It should have a method to apply interest to the balance (`ApplyInterest()`). Use `base.Deposit()` to deposit interest amount.

**3. Test the Bank Accounts:**

- Create instances of `SavingsAccount` in your `Main` method and perform operations like deposits, withdrawals, `ApplyInterest`, and displaying account information.
- Use a base class reference to call overridden methods of the derived classes.

---

## Lab Task 3: Understanding Single-cast and Multi-cast Delegates

### Questions

**1. Define a Delegate:**

- Create a delegate `public delegate void MessageHandler();`

**2. Create Two Methods:**

- Define two methods `ShowWelcome()` and `ShowGoodbye()` that print welcome and goodbye messages.

**3. Single-cast Delegate:**

- Create a delegate instance pointing only to `ShowWelcome()`.
- Invoke the delegate and observe the result.

**4. Multi-cast Delegate:**

- Add `ShowGoodbye()` to the same delegate using `+=`.
- Invoke the delegate again and observe both messages are displayed.

**5. Remove a Method:**

- Use `-=` to remove `ShowWelcome()` from the delegate.
- Invoke the delegate and observe only `ShowGoodbye()` is called.

---

## Lab Task 4: Using Lambda Expressions with Action, Func, and Predicate

**Objective:** Practice creating and using lambda expressions with `Action`, `Func`, and `Predicate` delegates in C#.

### Tasks

1. Define an `Action<List<string>>` delegate using a lambda expression that prints each element of a given list on a new line.

2. Define a `Func<int, bool>` delegate using a lambda expression that determines whether a given integer is even.

3. Define a `Predicate<int>` delegate using a lambda expression that checks whether a given integer is a multiple of 5.

---

## Lab Task 5: Working with LINQ in C# using Arrays and Collections

**Objective:** To practice LINQ operations using both query syntax and method syntax on arrays and generic collections such as `List<T>`, with a custom class `Employee`.

### Employee Class

```csharp
public class Employee
{
    public string Name { get; set; }
    public double Salary { get; set; }
    public string Department { get; set; }
    public bool IsResigned { get; set; }
    public int Experience { get; set; }
}
```

Given a list/array of employees, perform the following operations using both query syntax and method syntax:

### Tasks

1. **Filter active employees** — Retrieve only the employees who are currently working (i.e., `IsResigned == false`).

2. **Sort by salary descending** — Return the list of employees sorted in descending order of salary.

3. **Get distinct departments** — Extract a list of unique department names from the list.

4. **Check if any employee has zero experience** — Return `true` if any employee has `Experience == 0`.

5. **Project only Name and Salary** — Create a new list of objects that contains only the Name and Salary of each employee.

---

## Lab Task 6: C# File I/O – Note Management System

**Objective:** Design and implement a C# console application named `NoteManagerApp` that allows the user to manage personal text-based notes. The application should store all notes inside a specific directory on the D: drive and provide options to create, read, list, copy, move, and delete notes.

### Methods

1. **`SetupNoteDirectory()`** — Create a folder named `D:\NotesApp` if it does not already exist.

2. **`CreateNote(string title, string content)`** — Create a text file named `<title>.txt` inside `NotesApp`. If it exists, prompt for overwrite.

3. **`ReadNote(string title)`** — Display the full contents of the note using `File.ReadAllText`.

4. **`ListAllNotes()`** — List all note titles (i.e., file names without extensions) inside `NotesApp`.

5. **`CopyNote(string originalTitle, string copyTitle)`** — Copy the contents of one note to a new file using `File.Copy`.

6. **`MoveNote(string oldTitle, string newTitle)`** — Rename or move a note using `File.Move`.

7. **`DeleteNote(string title)`** — Delete a note file using `File.Delete`. Confirm with the user before deletion.

8. **`ReadNoteLineByLine(string title)`** — Display each line of the note with line numbers using `File.ReadLines`.

---

## Lab Work 7: Setting up a Basic ASP.NET Core MVC Application

**Objective:** Learn how to set up an ASP.NET Core MVC application and understand the project structure.

### Lab Instructions

- Create a new ASP.NET Core MVC & ASP.NET API project using Visual Studio or .NET CLI.
- Write different commands for creating projects.

---

## Lab Work 8: Understanding Controllers and ActionResult in ASP.NET Core

**Objective:** Understand how to create controllers in ASP.NET Core MVC and work with different types of `ActionResult` return types to handle different HTTP responses such as views, redirects, JSON data, and file downloads.

### Tasks

Create a new controller named `ProductController`.

1. In the `Index` action of the `ProductController`, return a View that displays a list of products.

2. Add a new action `GetProductInfo` in `ProductController` that returns product information in JSON format.

3. Add a new action `RedirectToHome` in `ProductController` that returns a `RedirectResult` to the home page (i.e., `Home/Index`).

4. Add a new action `DownloadProductFile` in `ProductController` that returns a file for download. You can use a simple text file or image as the content. `[File]`

5. Add a new action `DisplayMessage` in `ProductController` that returns a simple string message using `ContentResult`.

6. Add a new action `ReturnStatusCode` in `ProductController` that returns a custom HTTP status code (e.g., 204 No Content). `[StatusCodeResult]`

---

## Lab Work 9: Razor Syntax, Tag Helpers, and Custom Tag Helpers in ASP.NET Core MVC

**Objective:** Understand how to use Razor syntax, apply Tag Helpers in ASP.NET Core MVC, and create Custom Tag Helpers to enhance the functionality and maintainability of views.

### Task 1: Razor Syntax, ViewBag, and ViewData

**Controller:**

- Create `RazorDemoController` with an `Index` action.
- In the action, assign:
  - A string message to `ViewBag.Message`.
  - A list of integers to `ViewData["Numbers"]`.

**View (Index.cshtml):**

- Display `ViewBag.Message`.
- Use `@foreach` to loop through `ViewData["Numbers"]` and display each number.
- Add a conditional statement:
  - If the number is greater than 10, display `"Number is large"`.
  - Otherwise, display `"Number is small"`.

### Task 2: Tag Helper and Custom Tag Helper

1. **Built-in Tag Helpers:**
   - Create a simple form in `Index.cshtml` that uses `asp-for` tag helpers for input fields (Name, Email).
   - Use the `asp-validation-for` tag helper to display validation errors for these fields.
   - Add a submit button using `asp-button` tag helper.

2. **Custom Tag Helper:**
   - Create a custom Tag Helper `DisplayDateTagHelper` that takes a date parameter and formats it as `"MM/dd/yyyy"`.
   - In the view, use the custom tag helper to display the current date using `<display-date date="DateTime.Now"></display-date>`.

---

## Lab Work 10: Model Binding & Validations in ASP.NET Core MVC

**Objective:** To understand and implement Model Binding and Data Validation in ASP.NET Core MVC, including how to bind form data to models and apply validation using data annotations.

### Task 1: Model Binding

1. **Create a Model:**
   - Create a `Person` model with the following properties:
     - `Name` (string)
     - `Email` (string)
     - `Age` (int)

2. **Create a Controller (`ModelBindingController`):**
   - Add an `Index` action to render a form for creating a `Person` object.
   - Add a `Create` action to handle the form submission and bind the form data to a `Person` model using Model Binding.

3. **Create a View (Index.cshtml):**
   - Create a form that uses `asp-for` tag helpers to bind input fields for Name, Email, and Age to the `Person` model.
   - Use the `asp-action` attribute to submit the form to the `Create` action.

### Task 2: Data Validation with Annotations

1. **Add Data Annotations to the Person Model:**
   - `Name`: `[Required]`, `[MaxLength(50)]`.
   - `Email`: `[Required]`, `[EmailAddress]`.
   - `Age`: `[Required]`, `[Range(18, 100)]`.

2. **Update the Controller (`Create` action):**
   - In the `Create` action, check if the model is valid using `ModelState.IsValid`. If it is not valid, return to the form with validation errors.

3. **Display Validation Errors in the View:**
   - Use `asp-validation-for` tag helpers in the view to display validation messages for Name, Email, and Age.

4. **Submit the Form:**
   - Test the form by submitting invalid data (e.g., empty fields, invalid email, or age out of range).
   - Ensure the validation messages are displayed when invalid data is submitted.

---

## Lab Task 11: Working with ADO.NET using SqlCommand and SqlDataReader

**Objective:** Use `SqlConnection`, `SqlCommand`, and `SqlDataReader` to retrieve and insert data into the Employee table.

### Tasks

1. **Retrieve Data (Read):**
   - Use `SqlCommand.ExecuteReader()` to select all employees where `IsResigned = 0`.
   - Display the Name and Salary of each employee in the console.

2. **Insert Data (Write):**
   - Use `SqlCommand.ExecuteNonQuery()` to insert a new employee into the Employee table.
   - Use parameterized queries to pass values: Name, Salary, Department, IsResigned, and Experience.

---

## Lab Task 12: Working with Entity Framework using DbContext

**Objective:** Use Entity Framework (Code First or Database First) to perform CRUD operations on the Employee table using `DbContext`.

### Tasks

**1. Setup DbContext and Entity Class**

Create an `Employee` entity class with properties:

- `Id` (int, primary key)
- `Name` (string)
- `Salary` (decimal)
- `Department` (string)
- `IsResigned` (bool)
- `Experience` (int)

Create an `AppDbContext` class inheriting from `DbContext`. Add a `DbSet<Employee>` property named `Employees`.

**2. Retrieve Data (Read)**

- Using LINQ with `DbContext`, select all employees where `IsResigned = false`.
- Display each employee's Name and Salary in the console.

**3. Insert Data (Create)**

- Create a new `Employee` object.
- Assign values for Name, Salary, Department, IsResigned, and Experience.
- Add the object to the context using `context.Employees.Add()`.
- Save changes with `context.SaveChanges()`.

**4. Update Data (Update)**

- Retrieve a specific employee by Name.
- Increase their Experience by 1.
- Save changes back to the database using `context.SaveChanges()`.

**5. Delete Data (Delete)**

- Retrieve an employee by Id.
- Remove them using `context.Employees.Remove()`.
- Save changes with `context.SaveChanges()`.

---

## Lab Task 13: Working with Session, TempData, and Cookies

**Objective:** Understand and implement state management in ASP.NET Core using Session, TempData, and Cookies.

### Tasks

**1. Session**

- Configure session in `Startup.cs` (or `Program.cs` in .NET 6/7+).
- Create a form to take user's Name and Email.
- Store the values in Session.
- Retrieve and display the stored session values on another page.
- Add a button to clear session.

**2. TempData**

- Create an action that sets a TempData message (e.g., `"Employee added successfully!"`).
- Redirect to another action/view where the message is displayed once.
- Demonstrate that TempData persists only for a single request.

**3. Cookies**

- Create a form to enter Theme Preference (e.g., Light or Dark).
- Store the preference in a Cookie with expiration of 1 day.
- Retrieve the cookie value and apply it to the page (e.g., change background color based on theme).
- Add a button to delete the cookie.

---

## Lab Task 14: Authentication and Authorization (with HttpContext)

**Objective:** Implement manual authentication (using cookies + HttpContext) and role-based authorization without ASP.NET Core Identity.

### Tasks

**1. Authentication (Login/Logout with Cookies)**

- Create a simple Login form with Username and Password.
- On successful login:
  - Create a `ClaimsPrincipal` with claims (Name, Role).
  - Use `HttpContext.SignInAsync()` to issue an authentication cookie.
- On logout:
  - Call `HttpContext.SignOutAsync()` to clear the cookie.

**2. Authorization (Role-based)**

- Use the `[Authorize]` attribute to protect controllers/actions.
- Restrict access:
  - `[Authorize]` → Any authenticated user.
  - `[Authorize(Roles = "Admin")]` → Only Admin users.
  - `[Authorize(Roles = "User")]` → Only User role.

**3. Custom Policy Example**

- Create a custom requirement: e.g., user must have claim `"Experience"` >= 2.
- Register a policy in `Program.cs` using `AddAuthorization()`.
- Apply it using `[Authorize(Policy = "RequireExperience")]`.

**4. Demonstration Flow**

- Login as Admin → Can access Admin-only pages.
- Login as User → Denied when accessing Admin pages.
- Apply policy-based restriction on experience → Users with less than 2 years cannot access.
