---
{"dg-publish":true,"permalink":"/dotnet/lab/dotnet-labs-code/","noteIcon":"","dg-note-properties":{}}
---

# .NET Lab Codes — Concise (Paper-Writing Style)

---

## Lab 1: BankAccount (Basic)

```csharp
using System;
using System.Collections.Generic;

enum AccType { Generic, Current, Saving, Business }

class BankAccount
{
    public static string BankName;
    static BankAccount() { BankName = "Global Trust Bank"; }

    public string AccountName { get; set; }
    public long AccountNumber { get; }
    protected decimal Balance { get; set; }
    public AccType AccountType { get; set; } = AccType.Generic;
    public bool IsActive { get; private set; } = true;
    private List<string> history = new List<string>();
    public IReadOnlyList<string> TransactionHistory => history;

    public BankAccount(string accountName, long accountNumber)
    {
        AccountName = accountName; AccountNumber = accountNumber; Balance = 0;
        history.Add("Account created: " + accountName);
    }

    public void Deposit(double amt)
    {
        if (amt <= 0) { Console.WriteLine("Invalid amount"); return; }
        Balance += (decimal)amt; history.Add("Deposited " + amt);
    }

    public void Withdrawal(double amt)
    {
        if (amt <= 0 || (decimal)amt > Balance) { Console.WriteLine("Invalid withdrawal"); return; }
        Balance -= (decimal)amt; history.Add("Withdrew " + amt);
    }

    public virtual void DisplayAccountInfo()
    {
        Console.WriteLine($"{AccountName} | {AccountNumber} | {AccountType} | Bal: {Balance}");
        foreach (var h in history) Console.WriteLine(h);
    }
}

class Program1
{
    static void Main()
    {
        var a = new BankAccount("Ram", 101);
        a.Deposit(1000);
        a.Withdrawal(300);
        a.DisplayAccountInfo();
    }
}
```

---

## Lab 2: Inheritance & Polymorphism (SavingsAccount)

```csharp
class SavingsAccount : BankAccount
{
    public const double InterestRate = 0.04;
    public SavingsAccount(string name, long num) : base(name, num) { }

    public void ApplyInterest()
    {
        double interest = (double)Balance * InterestRate;
        base.Deposit(interest);
    }

    public override void DisplayAccountInfo()
    {
        base.DisplayAccountInfo();
        Console.WriteLine($"Interest Rate: {InterestRate * 100}%");
    }
}

class Program2
{
    static void Main()
    {
        BankAccount a = new SavingsAccount("Sita", 202);
        a.Deposit(5000);
        a.Withdrawal(1000);
        ((SavingsAccount)a).ApplyInterest();
        a.DisplayAccountInfo();
    }
}
```

---

## Lab 3: Delegates (Single & Multicast)

```csharp
using System;

public delegate void MessageHandler();

class Program3
{
    static void ShowWelcome() => Console.WriteLine("Welcome!");
    static void ShowGoodbye() => Console.WriteLine("Goodbye!");

    static void Main()
    {
        MessageHandler mh = ShowWelcome;
        mh();                       // single-cast

        mh += ShowGoodbye;
        mh();                       // multi-cast: both

        mh -= ShowWelcome;
        mh();                       // only Goodbye
    }
}
```

---

## Lab 4: Action, Func, Predicate

```csharp
using System;
using System.Collections.Generic;

class Program4
{
    static void Main()
    {
        Action<List<string>> printAll = list => list.ForEach(Console.WriteLine);
        printAll(new List<string> { "A", "B", "C" });

        Func<int, bool> isEven = n => n % 2 == 0;
        Console.WriteLine(isEven(4));

        Predicate<int> isMultipleOf5 = n => n % 5 == 0;
        Console.WriteLine(isMultipleOf5(10));
    }
}
```

---

## Lab 5: LINQ with Employee

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Employee
{
    public string Name { get; set; }
    public double Salary { get; set; }
    public string Department { get; set; }
    public bool IsResigned { get; set; }
    public int Experience { get; set; }
}

class Program5
{
    static void Main()
    {
        List<Employee> emps = new List<Employee> {
            new Employee{Name="A",Salary=50000,Department="IT",IsResigned=false,Experience=2},
            new Employee{Name="B",Salary=70000,Department="HR",IsResigned=true,Experience=0},
            new Employee{Name="C",Salary=60000,Department="IT",IsResigned=false,Experience=3},
        };

        // 1. Active employees
        var active1 = from e in emps where !e.IsResigned select e;
        var active2 = emps.Where(e => !e.IsResigned);

        // 2. Sort by salary desc
        var sorted1 = from e in emps orderby e.Salary descending select e;
        var sorted2 = emps.OrderByDescending(e => e.Salary);

        // 3. Distinct departments
        var dept1 = (from e in emps select e.Department).Distinct();
        var dept2 = emps.Select(e => e.Department).Distinct();

        // 4. Any zero experience
        bool any1 = (from e in emps where e.Experience == 0 select e).Any();
        bool any2 = emps.Any(e => e.Experience == 0);

        // 5. Project Name & Salary
        var proj1 = from e in emps select new { e.Name, e.Salary };
        var proj2 = emps.Select(e => new { e.Name, e.Salary });

        foreach (var e in active2) Console.WriteLine(e.Name);
    }
}
```

---

## Lab 6: File I/O — NoteManagerApp

```csharp
using System;
using System.IO;

class NoteManagerApp
{
    static string dir = @"D:\NotesApp";

    static void SetupNoteDirectory()
    {
        if (!Directory.Exists(dir)) Directory.CreateDirectory(dir);
    }

    static void CreateNote(string title, string content)
    {
        string path = Path.Combine(dir, title + ".txt");
        if (File.Exists(path))
        {
            Console.Write("File exists. Overwrite? (y/n): ");
            if (Console.ReadLine().ToLower() != "y") return;
        }
        File.WriteAllText(path, content);
    }

    static void ReadNote(string title) =>
        Console.WriteLine(File.ReadAllText(Path.Combine(dir, title + ".txt")));

    static void ListAllNotes()
    {
        foreach (var f in Directory.GetFiles(dir))
            Console.WriteLine(Path.GetFileNameWithoutExtension(f));
    }

    static void CopyNote(string oldT, string newT) =>
        File.Copy(Path.Combine(dir, oldT + ".txt"), Path.Combine(dir, newT + ".txt"), true);

    static void MoveNote(string oldT, string newT) =>
        File.Move(Path.Combine(dir, oldT + ".txt"), Path.Combine(dir, newT + ".txt"));

    static void DeleteNote(string title)
    {
        Console.Write("Confirm delete? (y/n): ");
        if (Console.ReadLine().ToLower() == "y")
            File.Delete(Path.Combine(dir, title + ".txt"));
    }

    static void ReadNoteLineByLine(string title)
    {
        int i = 1;
        foreach (var line in File.ReadLines(Path.Combine(dir, title + ".txt")))
            Console.WriteLine($"{i++}: {line}");
    }

    static void Main()
    {
        SetupNoteDirectory();
        CreateNote("test", "Hello World");
        ReadNote("test");
        ListAllNotes();
        CopyNote("test", "test_copy");
        MoveNote("test_copy", "test_renamed");
        ReadNoteLineByLine("test");
        DeleteNote("test_renamed");
    }
}
```

---

## Lab 7: ASP.NET Core MVC Setup

**CLI commands:**
```bash
dotnet new mvc -n MyMvcApp
dotnet new webapi -n MyApiApp
cd MyMvcApp
dotnet run
```
Project structure: `Controllers/`, `Views/`, `Models/`, `wwwroot/`, `Program.cs`.

---

## Lab 8: ProductController — ActionResult Types

```csharp
using Microsoft.AspNetCore.Mvc;

public class ProductController : Controller
{
    public IActionResult Index()
    {
        var products = new[] { "Pen", "Book", "Bag" };
        return View(products);
    }

    public JsonResult GetProductInfo() =>
        Json(new { Name = "Pen", Price = 20 });

    public RedirectResult RedirectToHome() =>
        Redirect("/Home/Index");

    public FileResult DownloadProductFile()
    {
        byte[] bytes = System.Text.Encoding.UTF8.GetBytes("Product data");
        return File(bytes, "text/plain", "product.txt");
    }

    public ContentResult DisplayMessage() =>
        Content("This is a product message");

    public StatusCodeResult ReturnStatusCode() =>
        StatusCode(204);
}
```

---

## Lab 9: Razor Syntax, Tag Helpers, Custom Tag Helper

**Controller:**
```csharp
public class RazorDemoController : Controller
{
    public IActionResult Index()
    {
        ViewBag.Message = "Hello from ViewBag";
        ViewData["Numbers"] = new List<int> { 5, 12, 8, 20 };
        return View();
    }
}
```

**Index.cshtml:**
```html
<p>@ViewBag.Message</p>
@foreach (var n in (List<int>)ViewData["Numbers"])
{
    if (n > 10) { <p>@n : Number is large</p> }
    else { <p>@n : Number is small</p> }
}

<form asp-action="Index" method="post">
    <input asp-for="Name" /> <span asp-validation-for="Name"></span>
    <input asp-for="Email" /> <span asp-validation-for="Email"></span>
    <button type="submit">Submit</button>
</form>

<display-date date="DateTime.Now"></display-date>
```

**Custom Tag Helper:**
```csharp
using Microsoft.AspNetCore.Razor.TagHelpers;

[HtmlTargetElement("display-date")]
public class DisplayDateTagHelper : TagHelper
{
    public DateTime Date { get; set; }
    public override void Process(TagHelperContext context, TagHelperOutput output)
    {
        output.TagName = "span";
        output.Content.SetContent(Date.ToString("MM/dd/yyyy"));
    }
}
```

---

## Lab 10: Model Binding & Validation

**Model:**
```csharp
using System.ComponentModel.DataAnnotations;

public class Person
{
    [Required, MaxLength(50)]
    public string Name { get; set; }

    [Required, EmailAddress]
    public string Email { get; set; }

    [Required, Range(18, 100)]
    public int Age { get; set; }
}
```

**Controller:**
```csharp
public class ModelBindingController : Controller
{
    public IActionResult Index() => View();

    [HttpPost]
    public IActionResult Create(Person p)
    {
        if (!ModelState.IsValid) return View("Index", p);
        return Content("Created: " + p.Name);
    }
}
```

**Index.cshtml:**
```html
<form asp-action="Create" method="post">
    <input asp-for="Name" /> <span asp-validation-for="Name"></span>
    <input asp-for="Email" /> <span asp-validation-for="Email"></span>
    <input asp-for="Age" /> <span asp-validation-for="Age"></span>
    <button type="submit">Submit</button>
</form>
```

---

## Lab 11: ADO.NET — SqlCommand & SqlDataReader

```csharp
using System;
using System.Data.SqlClient;

class AdoDemo
{
    static string conStr = "Server=.;Database=CompanyDB;Trusted_Connection=True;";

    static void ReadEmployees()
    {
        using var con = new SqlConnection(conStr);
        con.Open();
        var cmd = new SqlCommand("SELECT Name, Salary FROM Employee WHERE IsResigned=0", con);
        using var reader = cmd.ExecuteReader();
        while (reader.Read())
            Console.WriteLine($"{reader["Name"]} - {reader["Salary"]}");
    }

    static void InsertEmployee(string name, decimal salary, string dept, bool resigned, int exp)
    {
        using var con = new SqlConnection(conStr);
        con.Open();
        var cmd = new SqlCommand(
            "INSERT INTO Employee (Name,Salary,Department,IsResigned,Experience) VALUES (@n,@s,@d,@r,@e)", con);
        cmd.Parameters.AddWithValue("@n", name);
        cmd.Parameters.AddWithValue("@s", salary);
        cmd.Parameters.AddWithValue("@d", dept);
        cmd.Parameters.AddWithValue("@r", resigned);
        cmd.Parameters.AddWithValue("@e", exp);
        cmd.ExecuteNonQuery();
    }

    static void Main()
    {
        ReadEmployees();
        InsertEmployee("D", 45000, "IT", false, 1);
    }
}
```

---

## Lab 12: Entity Framework — DbContext CRUD

```csharp
using System;
using System.Linq;
using Microsoft.EntityFrameworkCore;

public class Employee
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Salary { get; set; }
    public string Department { get; set; }
    public bool IsResigned { get; set; }
    public int Experience { get; set; }
}

public class AppDbContext : DbContext
{
    public DbSet<Employee> Employees { get; set; }
    protected override void OnConfiguring(DbContextOptionsBuilder o) =>
        o.UseSqlServer("Server=.;Database=CompanyDB;Trusted_Connection=True;");
}

class EfDemo
{
    static void Main()
    {
        using var ctx = new AppDbContext();

        // Read
        foreach (var e in ctx.Employees.Where(e => !e.IsResigned))
            Console.WriteLine($"{e.Name} - {e.Salary}");

        // Create
        var emp = new Employee { Name = "E", Salary = 40000, Department = "HR", IsResigned = false, Experience = 1 };
        ctx.Employees.Add(emp);
        ctx.SaveChanges();

        // Update
        var found = ctx.Employees.FirstOrDefault(e => e.Name == "E");
        if (found != null) { found.Experience += 1; ctx.SaveChanges(); }

        // Delete
        var toDelete = ctx.Employees.Find(1);
        if (toDelete != null) { ctx.Employees.Remove(toDelete); ctx.SaveChanges(); }
    }
}
```

---

## Lab 13: Session, TempData, Cookies

**Program.cs setup:**
```csharp
builder.Services.AddSession();
// ...
app.UseSession();
```

**Controller:**
```csharp
public class StateController : Controller
{
    [HttpPost]
    public IActionResult SetSession(string name, string email)
    {
        HttpContext.Session.SetString("Name", name);
        HttpContext.Session.SetString("Email", email);
        return RedirectToAction("ShowSession");
    }

    public IActionResult ShowSession()
    {
        ViewBag.Name = HttpContext.Session.GetString("Name");
        ViewBag.Email = HttpContext.Session.GetString("Email");
        return View();
    }

    public IActionResult ClearSession()
    {
        HttpContext.Session.Clear();
        return RedirectToAction("ShowSession");
    }

    public IActionResult AddEmployee()
    {
        TempData["Message"] = "Employee added successfully!";
        return RedirectToAction("ShowMessage");
    }

    public IActionResult ShowMessage()
    {
        ViewBag.Msg = TempData["Message"];
        return View();
    }

    [HttpPost]
    public IActionResult SetTheme(string theme)
    {
        Response.Cookies.Append("Theme", theme, new CookieOptions { Expires = DateTimeOffset.Now.AddDays(1) });
        return RedirectToAction("ShowSession");
    }

    public IActionResult DeleteTheme()
    {
        Response.Cookies.Delete("Theme");
        return RedirectToAction("ShowSession");
    }
}
```

---

## Lab 14: Authentication & Authorization (HttpContext)

**Login/Logout:**
```csharp
using Microsoft.AspNetCore.Authentication;
using Microsoft.AspNetCore.Authentication.Cookies;
using System.Security.Claims;

public class AccountController : Controller
{
    [HttpPost]
    public async Task<IActionResult> Login(string username, string password)
    {
        if (username == "admin" && password == "123")
        {
            var claims = new List<Claim> {
                new Claim(ClaimTypes.Name, username),
                new Claim(ClaimTypes.Role, "Admin"),
                new Claim("Experience", "3")
            };
            var identity = new ClaimsIdentity(claims, CookieAuthenticationDefaults.AuthenticationScheme);
            await HttpContext.SignInAsync(new ClaimsPrincipal(identity));
            return RedirectToAction("Index", "Home");
        }
        return Unauthorized();
    }

    public async Task<IActionResult> Logout()
    {
        await HttpContext.SignOutAsync();
        return RedirectToAction("Login");
    }
}
```

**Program.cs:**
```csharp
builder.Services.AddAuthentication(CookieAuthenticationDefaults.AuthenticationScheme)
    .AddCookie();
builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("RequireExperience", policy =>
        policy.RequireAssertion(ctx =>
            ctx.User.HasClaim(c => c.Type == "Experience" && int.Parse(c.Value) >= 2)));
});
// ...
app.UseAuthentication();
app.UseAuthorization();
```

**Protected controllers:**
```csharp
[Authorize]
public class DashboardController : Controller
{
    public IActionResult Index() => View();
}

[Authorize(Roles = "Admin")]
public class AdminController : Controller
{
    public IActionResult Index() => View();
}

[Authorize(Policy = "RequireExperience")]
public class SeniorController : Controller
{
    public IActionResult Index() => View();
}
```
</file_text>