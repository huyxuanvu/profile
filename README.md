# Các Khái niệm OOP Cốt lõi trong Java

Lập trình hướng đối tượng (OOP - Object-Oriented Programming) là một mô hình lập trình mạnh mẽ, tập trung vào khái niệm "đối tượng" thay vì chỉ là các hàm hoặc logic đơn thuần. Trong Java, OOP là nền tảng cơ bản. Hiểu rõ các khái niệm này là chìa khóa để xây dựng các ứng dụng có cấu trúc tốt, dễ bảo trì và mở rộng.

## I. Khái niệm Cốt lõi Cơ bản (Các Trụ cột của OOP)

Đây là 6 khái niệm nền tảng mà mọi lập trình viên Java đều cần nắm vững.

### 1. Class (Lớp)

*   **Khái niệm:** Lớp là một *bản thiết kế*, *khuôn mẫu* hoặc *nguyên mẫu* để tạo ra các đối tượng. Nó không phải là một thực thể vật lý, mà chỉ là một định nghĩa trừu tượng về cấu trúc và hành vi chung của một tập hợp các đối tượng có cùng đặc điểm.
*   **Nội dung của Class:**
    *   **Thuộc tính (Attributes / Fields / Member Variables):** Biểu diễn trạng thái (state) của các đối tượng được tạo ra từ lớp đó. Chúng là các biến lưu trữ dữ liệu.
    *   **Phương thức (Methods / Member Functions):** Biểu diễn hành vi (behavior) hoặc các thao tác mà đối tượng có thể thực hiện. Chúng là các hàm.
*   **Mục đích:** Cung cấp một cấu trúc để định nghĩa các loại đối tượng trong hệ thống.
*   **Trong Java:** Được khai báo bằng từ khóa `class`.

```java
// Ví dụ về Class
class Dog {
    // Thuộc tính (State)
    String name;
    String breed;
    int age;

    // Constructor (Phương thức đặc biệt để khởi tạo đối tượng)
    public Dog(String name, String breed, int age) {
        this.name = name; // 'this' tham chiếu đến đối tượng hiện tại
        this.breed = breed;
        this.age = age;
    }

    // Phương thức (Behavior)
    void bark() {
        System.out.println(this.name + " says Woof Woof!");
    }

    void eat() {
        System.out.println(this.name + " is eating.");
    }

    // Getter cho thuộc tính age (ví dụ)
    public int getAge() {
        return this.age;
    }
}
Use code with caution.
Markdown
2. Object (Đối tượng)
Khái niệm: Đối tượng là một thể hiện (instance) cụ thể của một lớp. Nó là một thực thể tồn tại trong bộ nhớ khi chương trình chạy và có trạng thái (các giá trị cụ thể cho các thuộc tính) và có thể thực hiện hành vi (gọi các phương thức của lớp).
Mục đích: Biểu diễn các thực thể cụ thể trong thế giới thực hoặc trong bài toán đang giải quyết, dựa trên bản thiết kế của lớp.
Trong Java: Được tạo ra bằng từ khóa new, theo sau là tên lớp và dấu ngoặc đơn (()) (gọi constructor của lớp).
// Ví dụ về Object
public class Main {
    public static void main(String[] args) {
        // Tạo một đối tượng Dog từ lớp Dog
        Dog myDog = new Dog("Buddy", "Golden Retriever", 3);

        // Truy cập thuộc tính của đối tượng
        System.out.println("My dog's name is: " + myDog.name);
        System.out.println("My dog's breed is: " + myDog.breed);
        System.out.println("My dog's age is: " + myDog.getAge()); // Sử dụng getter

        // Gọi phương thức của đối tượng
        myDog.bark();
        myDog.eat();

        // Tạo đối tượng khác
        Dog yourDog = new Dog("Lucy", "Poodle", 5);
        yourDog.bark();
    }
}
Use code with caution.
Java
3. Encapsulation (Tính Đóng gói)
Khái niệm: Là quá trình gói gọn dữ liệu (thuộc tính) và các phương thức xử lý dữ liệu đó vào trong một đơn vị duy nhất (là lớp). Đồng thời, nó ẩn đi chi tiết cài đặt bên trong của lớp và chỉ cho phép truy cập dữ liệu thông qua giao diện công khai (thường là các phương thức get và set).
Nguyên tắc: "Che giấu thông tin" (Information Hiding).
Mục đích:
Bảo vệ dữ liệu: Ngăn chặn truy cập và sửa đổi dữ liệu trực tiếp từ bên ngoài một cách trái phép.
Kiểm soát truy cập: Cho phép bạn kiểm soát cách dữ liệu được đọc (qua getter) và ghi (qua setter), có thể thêm logic kiểm tra hoặc xử lý dữ liệu trước khi lưu.
Tăng tính linh hoạt: Dễ dàng thay đổi cài đặt bên trong của lớp mà không ảnh hưởng đến mã bên ngoài đang sử dụng lớp đó (miễn là giao diện công khai không thay đổi).
Đơn giản hóa: Người sử dụng lớp chỉ cần biết các phương thức công khai, không cần quan tâm chi tiết cài đặt phức tạp bên trong.
Trong Java: Đạt được chủ yếu bằng cách sử dụng các từ khóa kiểm soát truy cập (private, protected, public, default/package-private) cho các thành viên của lớp (thuộc tính và phương thức). Thông thường, các thuộc tính được để private, và các phương thức get (để đọc giá trị) và set (để ghi giá trị) được để public.
// Ví dụ về Encapsulation
class Account {
    // Thuộc tính private - chỉ có thể truy cập từ bên trong lớp
    private double balance;

    // Constructor
    public Account(double initialBalance) {
        if (initialBalance >= 0) {
            this.balance = initialBalance;
        } else {
            System.out.println("Initial balance cannot be negative. Setting to 0.");
            this.balance = 0;
        }
    }

    // Public getter - cho phép đọc giá trị balance
    public double getBalance() {
        return balance;
    }

    // Public setter - cho phép thay đổi balance, có thể thêm logic kiểm tra
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: " + amount);
        } else {
            System.out.println("Deposit amount must be positive.");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrew: " + amount);
        } else {
            System.out.println("Invalid withdrawal amount or insufficient balance.");
        }
    }
}

// Cách sử dụng
// Account myAccount = new Account(1000);
// System.out.println("Current balance: " + myAccount.getBalance()); // OK, using getter
// // myAccount.balance = 2000; // ERROR! Cannot access private field directly
// myAccount.deposit(500); // OK, using public method
// myAccount.withdraw(200); // OK, using public method
// System.out.println("Final balance: " + myAccount.getBalance());
Use code with caution.
Java
4. Inheritance (Tính Kế thừa)
Khái niệm: Là một cơ chế cho phép một lớp mới (lớp con, lớp dẫn xuất, subclass) thừa hưởng các thuộc tính và phương thức từ một lớp hiện có (lớp cha, lớp cơ sở, superclass). Lớp con có thể sử dụng lại các thành phần của lớp cha (thuộc tính và phương thức public/protected) và có thể thêm các thành viên mới hoặc thay đổi (ghi đè - override) hành vi của lớp cha.
Mối quan hệ: Thể hiện mối quan hệ "là một loại của" (is-a relationship). Ví dụ: Dog là một loại Animal.
Mục đích:
Tái sử dụng mã: Tránh lặp lại code bằng cách định nghĩa các thuộc tính và phương thức chung trong lớp cha.
Tạo hệ thống phân cấp: Tổ chức các lớp thành một cấu trúc cây, thể hiện mối quan hệ tổng quát/đặc thù.
Duy trì mã: Việc thay đổi code chung chỉ cần thực hiện ở một nơi (lớp cha).
Trong Java: Sử dụng từ khóa extends. Java chỉ hỗ trợ đơn kế thừa lớp (một lớp con chỉ có thể kế thừa trực tiếp từ một lớp cha duy nhất). Tuy nhiên, một lớp có thể cài đặt (implements) nhiều giao diện (interface) để đạt được một dạng "đa kế thừa hành vi".
// Ví dụ về Inheritance

// Lớp cha (Superclass)
class Animal {
    String name;

    public Animal(String name) {
        this.name = name;
    }

    void eat() {
        System.out.println(this.name + " is eating.");
    }

    void sleep() {
        System.out.println(this.name + " is sleeping.");
    }
}

// Lớp con (Subclass) kế thừa từ Animal
class Cat extends Animal {
    String color;

    // Constructor của lớp con gọi constructor của lớp cha bằng super()
    public Cat(String name, String color) {
        super(name); // super() phải là lệnh đầu tiên
        this.color = color;
    }

    // Phương thức riêng của lớp Cat
    void meow() {
        System.out.println(this.name + " says Meow!");
    }

    // Ghi đè (Override) phương thức eat của lớp cha (ví dụ sẽ chi tiết hơn ở Polymorphism)
    @Override
    void eat() {
        System.out.println(this.name + " (a " + this.color + " cat) is eating fish.");
    }
}

// Cách sử dụng
// Cat myCat = new Cat("Whiskers", "black");
// System.out.println("Cat's name: " + myCat.name); // Kế thừa thuộc tính 'name'
// myCat.eat();   // Gọi phương thức bị ghi đè
// myCat.sleep(); // Kế thừa phương thức 'sleep'
// myCat.meow();  // Gọi phương thức riêng của Cat
Use code with caution.
Java
5. Polymorphism (Tính Đa hình)
Khái niệm: "Đa hình" có nghĩa là "nhiều hình dạng". Trong OOP, đa hình cho phép một đối tượng có thể được coi là có nhiều kiểu khác nhau (thường là kiểu của lớp cha hoặc giao diện mà nó cài đặt) hoặc cho phép một hành động (phương thức) có thể được thực hiện theo nhiều cách khác nhau tùy thuộc vào đối tượng gọi nó.
Mục đích: Tăng tính linh hoạt và khả năng mở rộng của mã. Cho phép viết mã tổng quát hơn để làm việc với các đối tượng thuộc các lớp khác nhau trong cùng một hệ thống phân cấp.
Trong Java: Đa hình được thể hiện qua hai cơ chế chính:
Compile-time Polymorphism (Đa hình lúc biên dịch) - Method Overloading (Nạp chồng phương thức): Xảy ra khi có nhiều phương thức trong cùng một lớp có cùng tên nhưng khác nhau về danh sách tham số (số lượng, kiểu dữ liệu hoặc thứ tự của tham số). Trình biên dịch xác định phương thức nào sẽ được gọi dựa trên signature của phương thức được sử dụng.
// Ví dụ Overloading
class Calculator {
    // Phương thức add với 2 số nguyên
    int add(int a, int b) {
        return a + b;
    }

    // Phương thức add nạp chồng với 3 số nguyên
    int add(int a, int b, int c) {
        return a + b + c;
    }

    // Phương thức add nạp chồng với 2 số thực
    double add(double a, double b) {
        return a + b;
    }
}

// Cách sử dụng
// Calculator calc = new Calculator();
// System.out.println(calc.add(2, 3));      // Gọi add(int, int)
// System.out.println(calc.add(2, 3, 4));   // Gọi add(int, int, int)
// System.out.println(calc.add(2.5, 3.5));  // Gọi add(double, double)
Use code with caution.
Java
Runtime Polymorphism (Đa hình lúc chạy) - Method Overriding (Ghi đè phương thức): Xảy ra khi một lớp con cung cấp một cài đặt cụ thể cho một phương thức đã được định nghĩa trong lớp cha với cùng signature (tên, danh sách tham số và kiểu trả về). Quyết định phương thức nào sẽ được thực thi được đưa ra tại thời điểm chạy chương trình (JVM dựa vào kiểu đối tượng thực tế). Để ghi đè, phương thức trong lớp con phải có mức độ truy cập bằng hoặc rộng hơn lớp cha. Annotation @Override được khuyến khích sử dụng để kiểm tra lúc biên dịch.
// Ví dụ Overriding và Runtime Polymorphism

// Lớp cha
class Vehicle {
    void move() {
        System.out.println("Vehicle moves");
    }
}

// Lớp con ghi đè phương thức move
class Car extends Vehicle {
    @Override // Annotation giúp kiểm tra lúc biên dịch
    void move() {
        System.out.println("Car drives on the road");
    }
}

// Lớp con khác ghi đè phương thức move
class Bicycle extends Vehicle {
    @Override
    void move() {
        System.out.println("Bicycle pedals");
    }
}

// Cách sử dụng Runtime Polymorphism
public class PolymorphismDemo {
    public static void main(String[] args) {
        // Một biến tham chiếu kiểu lớp cha có thể trỏ tới đối tượng lớp con
        Vehicle myVehicle1 = new Car();
        Vehicle myVehicle2 = new Bicycle();
        Vehicle myVehicle3 = new Vehicle();

        // Khi gọi phương thức move(), JVM sẽ gọi phương thức của đối tượng thực tế
        myVehicle1.move(); // Output: Car drives on the road
        myVehicle2.move(); // Output: Bicycle pedals
        myVehicle3.move(); // Output: Vehicle moves

        // Đây là đa hình: Cùng một lời gọi myVehicle.move()
        // cho kết quả khác nhau tùy thuộc vào đối tượng thực tế mà myVehicle đang tham chiếu.
    }
}
Use code with caution.
Java
6. Abstraction (Tính Trừu tượng)
Khái niệm: Là quá trình ẩn đi những chi tiết cài đặt phức tạp và chỉ hiển thị những tính năng hoặc giao diện cần thiết cho người sử dụng. Tập trung vào "cái gì" (what) một đối tượng hoặc hệ thống làm, thay vì "làm như thế nào" (how).
Mục đích:
Giảm độ phức tạp: Đơn giản hóa cách nhìn về hệ thống bằng cách chỉ expose những thông tin quan trọng.
Tăng tính bảo trì: Dễ dàng thay đổi chi tiết cài đặt bên trong mà không ảnh hưởng đến người sử dụng interface trừu tượng.
Thiết kế hệ thống: Cung cấp một cấu trúc tổng quát cho các lớp con hoặc các lớp cài đặt tuân theo.
Trong Java: Đạt được thông qua:
Abstract Classes (Lớp trừu tượng):
Được khai báo bằng từ khóa abstract.
Không thể tạo đối tượng trực tiếp (không thể dùng new).
Có thể chứa cả phương thức trừu tượng (không có phần thân, chỉ có khai báo, kết thúc bằng ;, khai báo với từ khóa abstract) và phương thức cụ thể (có phần thân).
Nếu một lớp chứa ít nhất một phương thức trừu tượng, nó phải được khai báo là lớp trừu tượng.
Lớp con kế thừa một lớp trừu tượng phải cài đặt tất cả các phương thức trừu tượng của lớp cha (trừ khi lớp con đó cũng là lớp trừu tượng).
Có thể có constructor, và constructor này được gọi khi lớp con tạo đối tượng (qua super()).
// Ví dụ Abstract Class

// Lớp trừu tượng Shape
abstract class Shape {
    String color;

    // Constructor của lớp trừu tượng
    public Shape(String color) {
        this.color = color;
        System.out.println("Creating Shape with color: " + color);
    }

    // Phương thức trừu tượng - Bắt buộc lớp con phải cài đặt
    abstract double area();

    // Phương thức cụ thể - Có thể được kế thừa và sử dụng hoặc ghi đè
    void display() {
        System.out.println("This is a " + color + " shape.");
    }
}

// Lớp con kế thừa từ Shape và cài đặt phương thức trừu tượng area()
class Rectangle extends Shape {
    double width;
    double height;

    public Rectangle(String color, double width, double height) {
        super(color); // Gọi constructor của lớp cha
        this.width = width;
        this.height = height;
    }

    // Cài đặt phương thức trừu tượng area()
    @Override
    double area() {
        return width * height;
    }
}

// Cách sử dụng
// Shape myRectangle = new Rectangle("Red", 5.0, 4.0);
// myRectangle.display(); // Sử dụng phương thức cụ thể kế thừa
// System.out.println("Area: " + myRectangle.area()); // Gọi phương thức trừu tượng đã được cài đặt

// Shape s = new Shape("Blue"); // ERROR! Cannot instantiate abstract class Shape
Use code with caution.
Java
Interfaces (Giao diện):
Được khai báo bằng từ khóa interface.
Định nghĩa một hợp đồng (contract) về hành vi. Một lớp cài đặt giao diện cam kết sẽ cung cấp cài đặt cho tất cả các phương thức trừu tượng trong giao diện đó.
Thể hiện khả năng "có thể làm gì" (can-do) hoặc "có hành vi gì" (has-a behavior).
Trước Java 8, giao diện chỉ có thể chứa các hằng số (public static final ngầm định) và các phương thức trừu tượng (public abstract ngầm định).
Từ Java 8 trở đi, giao diện có thể chứa thêm phương thức default (có phần thân, cho phép thêm phương thức mới vào giao diện mà không phá vỡ các lớp đã cài đặt nó) và phương thức static.
Một lớp có thể cài đặt (implements) nhiều giao diện. Một giao diện có thể kế thừa (extends) nhiều giao diện khác.
Không có constructor.
// Ví dụ Interface

// Giao diện Drawabl - Định nghĩa khả năng vẽ
interface Drawable {
    // Phương thức trừu tượng (mặc định là public abstract)
    void draw();

    // Phương thức default (có thân - từ Java 8)
    default void redraw() {
        System.out.println("Redrawing the shape.");
        draw(); // Có thể gọi phương thức trừu tượng khác trong giao diện
    }

    // Phương thức static (từ Java 8)
    static void showUsage() {
        System.out.println("This interface defines drawing capabilities.");
    }
}

// Lớp Circle cài đặt giao diện Drawable
class Circle implements Drawable {
    // Phải cài đặt phương thức draw()
    @Override
    public void draw() {
        System.out.println("Drawing a circle.");
    }

    // Có thể ghi đè phương thức default nếu cần
    // @Override
    // public void redraw() { ... }
}

// Lớp Square cài đặt giao diện Drawable
class Square implements Drawable {
     // Phải cài đặt phương thức draw()
    @Override
    public void draw() {
        System.out.println("Drawing a square.");
    }
}

// Cách sử dụng Abstraction với Interface
public class AbstractionDemo {
    public static void main(String[] args) {
        // Biến tham chiếu kiểu Interface có thể trỏ đến đối tượng cài đặt Interface đó
        Drawable obj1 = new Circle();
        Drawable obj2 = new Square();

        obj1.draw();      // Drawing a circle.
        obj1.redraw();    // Redrawing the shape. Drawing a circle.

        obj2.draw();      // Drawing a square.
        obj2.redraw();    // Redrawing the shape. Drawing a square.

        Drawable.showUsage(); // Gọi phương thức static của interface
    }
}
Use code with caution.
Java
II. Khái niệm Cấp cao / Quan trọng khác trong Java OOP
Những khái niệm này giúp bạn thiết kế và cấu trúc các hệ thống OOP phức tạp và hiệu quả hơn.
1. Relationships between Objects (Các mối quan hệ giữa các Đối tượng)
Ngoài kế thừa (Inheritance - is-a), các đối tượng trong hệ thống có thể liên kết với nhau theo nhiều cách khác:
Association (Kết hợp): Mối quan hệ tổng quát, yếu giữa hai lớp độc lập. Một lớp "sử dụng" hoặc "liên kết" với lớp khác. Không có sự sở hữu mạnh mẽ. Các đối tượng có thể tồn tại độc lập. Ví dụ: Student và Course. Một Student có thể liên kết với nhiều Course, và một Course có nhiều Student. Student và Course tồn tại độc lập.
Trong Java: Thường được biểu diễn bằng cách một lớp chứa một tham chiếu đến một hoặc nhiều đối tượng của lớp khác như một thuộc tính, hoặc các phương thức của lớp này nhận đối tượng của lớp kia làm tham số.
class Student {
    private String name;
    // Association: Student liên kết với Course (thông qua danh sách các Course)
    private List<Course> enrolledCourses; 
    // ... constructor, getters, setters ...
}

class Course {
    private String title;
    // Association: Course liên kết với Student
    // ... constructor, getters, setters ...
}
Use code with caution.
Java
Aggregation (Kết tập): Một dạng đặc biệt của Association, thể hiện mối quan hệ "có chứa" (has-a), nhưng các thành phần (parts) có thể tồn tại độc lập với toàn bộ (whole). Mối quan hệ "toàn bộ-một phần" (whole-part), nhưng yếu. Ví dụ: Department và Professor. Một Department có nhiều Professor. Professor có thể tồn tại (và làm việc ở Department khác) ngay cả khi Department bị giải thể.
Trong Java: Tương tự Association, biểu diễn bằng cách một lớp chứa tham chiếu đến đối tượng lớp khác. Điểm khác biệt là ý nghĩa của mối quan hệ: phần có thể tồn tại độc lập.
class Professor {
    private String name;
    // ... constructor, methods ...
}

class Department {
    private String name;
    // Aggregation: Department "có chứa" nhiều Professor.
    // Professor có thể tồn tại độc lập.
    private List<Professor> professors;

    public Department(String name) {
        this.name = name;
        this.professors = new ArrayList<>(); // Khởi tạo danh sách
    }

    public void addProfessor(Professor prof) {
        this.professors.add(prof);
    }
    // ... other methods ...
}
Use code with caution.
Java
Composition (Thành phần): Một dạng đặc biệt và mạnh mẽ hơn của Aggregation. Cũng thể hiện mối quan hệ "có chứa" (has-a), nhưng các thành phần (parts) không thể tồn tại độc lập với toàn bộ (whole). Nếu toàn bộ bị hủy, các thành phần cũng bị hủy. Mối quan hệ "toàn bộ-một phần" mạnh. Ví dụ: House và Room. Một House được tạo thành từ Room. Room thường không tồn tại mà không có House (nó là một phần của House). Car và Engine (thường Engine được tạo ra và quản lý bởi Car).
Trong Java: Thường biểu diễn bằng cách một lớp chứa tham chiếu đến đối tượng lớp khác, và đối tượng thành phần thường được tạo bên trong hoặc quản lý chặt chẽ bởi đối tượng toàn bộ. Vòng đời của thành phần phụ thuộc vào toàn bộ.
// Ví dụ Composition: Engine là một phần của Car, không tồn tại độc lập
class Engine {
    private String type;

    public Engine(String type) {
        this.type = type;
        System.out.println("Engine (" + type + ") created.");
    }

    // Phương thức hủy (ví dụ để minh họa vòng đời)
    // Trong thực tế Java không có destructor rõ ràng như C++, dùng Garbage Collector
    // Nhưng ý tưởng là khi Car biến mất, Engine cũng không còn liên quan.
    // public void finalize() { System.out.println("Engine destroyed."); }
}

class Car {
    private String model;
    private Engine engine; // Composition: Car "có chứa" một Engine

    // Engine được tạo cùng lúc với Car
    public Car(String model, String engineType) {
        this.model = model;
        this.engine = new Engine(engineType); // Tạo Engine bên trong Car
        System.out.println("Car (" + model + ") created with its engine.");
    }

    public void start() {
        // Car sử dụng Engine
        System.out.println(model + " starting its " + engine.type + " engine.");
        // Giả sử Engine có phương thức start()
        // engine.start();
    }

    // Khi đối tượng Car bị thu hồi bởi Garbage Collector, đối tượng Engine bên trong nó cũng sẽ bị thu hồi
}
Use code with caution.
Java
Lưu ý: Phân biệt Aggregation và Composition đôi khi mang tính ngữ nghĩa dựa trên bài toán cụ thể và mức độ ràng buộc về vòng đời.
2. Abstract Class vs Interface (So sánh Lớp trừu tượng và Giao diện)
Đây là hai công cụ chính để đạt được Abstraction trong Java, nhưng chúng có sự khác biệt quan trọng:
Đặc điểm	Abstract Class	Interface
Mục đích	Định nghĩa một lớp cơ sở chung với code chung và các phương thức cần cài đặt bởi lớp con (is-a relationship).	Định nghĩa một hợp đồng về hành vi (can-do relationship).
Instantiability	Không thể tạo đối tượng (new).	Không thể tạo đối tượng (new).
Khai báo	Sử dụng từ khóa abstract class.	Sử dụng từ khóa interface.
Thành viên	Có thể có thuộc tính (biến instance).	Chỉ có thể có hằng số (public static final).
Methods	Có thể có phương thức trừu tượng (abstract) và phương thức cụ thể (có thân).	Chỉ có phương thức trừu tượng (trước Java 8). Từ Java 8 có thêm default và static methods.
Constructor	Có thể có constructor.	Không có constructor.
Tính kế thừa	Lớp con kế thừa bằng từ khóa extends. Một lớp chỉ có thể kế thừa một lớp trừu tượng.	Lớp cài đặt bằng từ khóa implements. Một lớp có thể cài đặt nhiều giao diện.
Đa kế thừa	Không hỗ trợ đa kế thừa lớp.	Hỗ trợ đa kế thừa giao diện (một interface kế thừa nhiều interface).
Mức truy cập	Có thể có bất kỳ mức truy cập nào (public, protected, private, default).	Tất cả các thành viên (trừ default/static methods) mặc định là public.
Khi nào sử dụng:
Sử dụng Abstract Class khi:
Bạn muốn chia sẻ code chung (các phương thức cụ thể, thuộc tính trạng thái) giữa các lớp con.
Các lớp con có mối quan hệ "là một loại của" nhau.
Bạn muốn định nghĩa một template method pattern (một phương thức cụ thể trong lớp trừu tượng gọi các phương thức trừu tượng để tạo ra một thuật toán).
Sử dụng Interface khi:
Bạn muốn định nghĩa một tập hợp các hành vi mà nhiều lớp không liên quan trong hệ thống phân cấp kế thừa có thể thực hiện.
Bạn muốn hỗ trợ đa kế thừa hành vi.
Bạn muốn tách biệt hoàn toàn định nghĩa hợp đồng (interface) với cài đặt cụ thể (lớp implement).
3. Inner Classes (Lớp lồng)
Khái niệm: Là một lớp được định nghĩa bên trong một lớp khác (outer class). Lớp bên trong (inner class) có thể truy cập tất cả các thành viên (bao gồm cả private) của lớp bên ngoài.
Mục đích:
Tăng tính đóng gói: Nhóm các lớp có mối quan hệ chặt chẽ lại với nhau.
Code dễ đọc và bảo trì hơn: Khi một lớp chỉ được sử dụng bởi một lớp khác, việc lồng nó vào giúp tổ chức code tốt hơn.
Tạo các lớp callback, adapter: Đặc biệt là sử dụng Anonymous Inner Class.
Các loại Inner Class trong Java:
Member Inner Class: Lớp được định nghĩa trực tiếp bên trong lớp ngoài, ngang hàng với các thuộc tính và phương thức của lớp ngoài. Cần một đối tượng của lớp ngoài để tạo đối tượng của lớp bên trong.
Local Inner Class: Lớp được định nghĩa bên trong một phương thức, constructor hoặc block scope. Nó chỉ hiển thị và chỉ có thể được sử dụng trong phạm vi mà nó được định nghĩa.
Anonymous Inner Class (Lớp vô danh): Một inner class không có tên. Thường được tạo và sử dụng ngay lập tức để cung cấp cài đặt cho một giao diện hoặc kế thừa một lớp (thường là abstract class) một cách ngắn gọn. Rất phổ biến trong việc xử lý sự kiện (event listeners).
Static Nested Class: Giống như inner class nhưng được khai báo với từ khóa static. Nó không có tham chiếu đến đối tượng của lớp ngoài và không thể truy cập trực tiếp các thành viên không phải static của lớp ngoài. Nó giống như một lớp độc lập nhưng được lồng vào lớp ngoài để tổ chức code. Cần tên lớp ngoài để truy cập.
// Ví dụ Inner Classes

class OuterClass {
    private int outerData = 10;

    // Member Inner Class
    class InnerClass {
        void display() {
            // Inner class có thể truy cập private members của outer class
            System.out.println("Inside InnerClass, outerData = " + outerData);
        }
    }

    void outerMethod() {
        // Local Inner Class bên trong phương thức
        class LocalInnerClass {
            void display() {
                System.out.println("Inside LocalInnerClass within outerMethod.");
                // Local inner class có thể truy cập biến final hoặc effectively final của phương thức
            }
        }
        LocalInnerClass local = new LocalInnerClass();
        local.display();
    }

    void demonstrateAnonymousInnerClass() {
        Runnable runner = new Runnable() { // Anonymous Inner Class implement interface Runnable
            @Override
            public void run() {
                System.out.println("Running inside Anonymous Inner Class.");
            }
        };
        new Thread(runner).start();
    }

    // Static Nested Class
    static class StaticNestedClass {
        void display() {
            System.out.println("Inside StaticNestedClass.");
            // Không thể truy cập outerData vì nó không phải static
            // System.out.println(outerData); // Compile error
        }
    }
}

// Cách sử dụng
// OuterClass outer = new OuterClass();
// OuterClass.InnerClass inner = outer.new InnerClass(); // Cần đối tượng outer để tạo member inner
// inner.display();

// outer.outerMethod(); // Chạy phương thức có local inner class

// outer.demonstrateAnonymousInnerClass(); // Chạy phương thức có anonymous inner class

// OuterClass.StaticNestedClass staticNested = new OuterClass.StaticNestedClass(); // Không cần đối tượng outer
// staticNested.display();
Use code with caution.
Java
4. final Keyword (Từ khóa final)
Khi áp dụng cho Biến: Biến trở thành một hằng số. Giá trị của nó chỉ được gán một lần (lúc khai báo hoặc trong constructor) và không thể thay đổi sau đó.
final int MAX_VALUE = 100;
// MAX_VALUE = 200; // Compile error
final Person person; // Tham chiếu là final, nhưng đối tượng mà nó trỏ tới CÓ THỂ thay đổi trạng thái
person = new Person("Alice");
// person = new Person("Bob"); // Compile error, không thể gán lại tham chiếu
person.setName("Alicia"); // OK, trạng thái của đối tượng có thể thay đổi
Use code with caution.
Java
Khi áp dụng cho Phương thức: Phương thức đó không thể bị ghi đè (override) bởi bất kỳ lớp con nào. Hữu ích khi bạn muốn đảm bảo hành vi của một phương thức là nhất quán trong toàn bộ hệ thống phân cấp kế thừa.
class Base {
    final void cannotOverride() {
        System.out.println("This method cannot be overridden.");
    }
}
class Derived extends Base {
    // void cannotOverride() { } // Compile error: cannot override final method
}
Use code with caution.
Java
Khi áp dụng cho Lớp: Lớp đó không thể bị kế thừa bởi bất kỳ lớp nào khác. Hữu ích khi bạn muốn ngăn chặn việc mở rộng lớp hoặc đảm bảo tính bất biến của lớp (ví dụ: lớp String, Integer, System trong Java là final).
final class ImmutableClass {
    // ... nội dung lớp ...
}
// class MyClass extends ImmutableClass { } // Compile error: cannot inherit from final class
Use code with caution.
Java
5. super Keyword (Từ khóa super)
Khái niệm: Một từ khóa tham chiếu đến thể hiện của lớp cha ngay lập tức (immediate parent class).
Công dụng:
Truy cập thành viên (thuộc tính, phương thức) của lớp cha: Khi lớp con có thành viên cùng tên với lớp cha, bạn có thể sử dụng super. để truy cập thành viên của lớp cha.
class Parent {
    String message = "From Parent";
    void display() { System.out.println(message); }
}
class Child extends Parent {
    String message = "From Child"; // Cùng tên với lớp cha
    void display() {
        System.out.println(message);       // Truy cập thuộc tính của lớp con
        System.out.println(super.message); // Truy cập thuộc tính của lớp cha
        super.display();                   // Gọi phương thức display() của lớp cha
    }
}
Use code with caution.
Java
Gọi constructor của lớp cha: Trong constructor của lớp con, bạn có thể sử dụng super() để gọi một trong các constructor của lớp cha. Nếu lớp cha không có constructor mặc định (no-arg constructor), lớp con bắt buộc phải gọi tường minh một constructor của lớp cha bằng super(). Lời gọi super() phải là dòng lệnh đầu tiên trong constructor của lớp con.
class Animal {
    String type;
    Animal(String type) { this.type = type; } // Constructor có tham số
}
class Dog extends Animal {
    String breed;
    Dog(String type, String breed) {
        super(type); // Gọi constructor của lớp cha Animal(String)
        this.breed = breed;
    }
    // Nếu Animal không có Animal() {}, lớp Dog không thể có constructor Dog() {}
    // mà không gọi super() hoặc super(...)
}
Use code with caution.
Java
6. this Keyword (Từ khóa this)
Khái niệm: Một từ khóa tham chiếu đến thể hiện (đối tượng) hiện tại của lớp.
Công dụng:
Tham chiếu đến thành viên (thuộc tính, phương thức) của đối tượng hiện tại: Đặc biệt hữu ích khi tên tham số của phương thức hoặc constructor trùng với tên thuộc tính của lớp, để phân biệt giữa biến cục bộ/tham số và thuộc tính của đối tượng.
class Person {
    String name; // Thuộc tính của lớp
    int age;

    Person(String name, int age) { // Tham số có cùng tên
        this.name = name; // this.name là thuộc tính, name là tham số
        this.age = age;   // this.age là thuộc tính, age là tham số
    }

    void display() {
        System.out.println("Name: " + this.name + ", Age: " + this.age); // Có thể dùng this.name hoặc name đều được
        this.greet(); // Có thể dùng this.greet() hoặc greet()
    }

    void greet() {
         System.out.println("Hello!");
    }
}
Use code with caution.
Java
Gọi constructor khác của cùng lớp: Bạn có thể sử dụng this() để gọi một constructor khác của cùng lớp từ một constructor khác. Điều này hữu ích để tránh lặp lại code khởi tạo. Lời gọi this() phải là dòng lệnh đầu tiên trong constructor.
class Box {
    int width;
    int height;
    int depth;

    // Constructor 1
    Box(int width, int height, int depth) {
        this.width = width;
        this.height = height;
        this.depth = depth;
    }

    // Constructor 2: Gọi Constructor 1
    Box(int size) {
        this(size, size, size); // Gọi Box(int, int, int)
    }

    // Constructor 3: Gọi Constructor 2
    Box() {
        this(0); // Gọi Box(int size)
    }
}
Use code with caution.
Java
7. Enum (Enumeration)
Khái niệm: enum là một kiểu dữ liệu đặc biệt (thực chất là một dạng lớp trong Java) được sử dụng để định nghĩa một tập hợp cố định các hằng số được đặt tên.
Mục đích:
Biểu diễn một tập hợp các giá trị có giới hạn và biết trước (ví dụ: các ngày trong tuần, các mùa, các trạng thái của một đối tượng, các loại thẻ bài...).
Cung cấp kiểu an toàn hơn so với việc sử dụng các hằng số int hoặc String truyền thống (tránh lỗi chính tả, đảm bảo giá trị hợp lệ).
Mã dễ đọc và dễ bảo trì hơn.
Trong Java: Khai báo bằng từ khóa enum. Các hằng số của enum được viết hoa theo quy ước. Enum có thể có thuộc tính, constructor (luôn là private hoặc package-private), và phương thức.
// Ví dụ Enum

enum Status {
    PENDING,   // Tự động là public static final Status PENDING = new Status();
    PROCESSING,
    COMPLETED,
    CANCELLED
}

enum Day {
    SUNDAY("Weekend"),
    MONDAY("Weekday"),
    TUESDAY("Weekday"),
    WEDNESDAY("Weekday"),
    THURSDAY("Weekday"),
    FRIDAY("Weekday"),
    SATURDAY("Weekend");

    // Enum có thể có thuộc tính
    private final String type;

    // Constructor của Enum (luôn private hoặc package-private)
    Day(String type) {
        this.type = type;
    }

    // Enum có thể có phương thức
    public String getType() {
        return type;
    }
}

// Cách sử dụng
public class EnumDemo {
    public static void main(String[] args) {
        Status currentStatus = Status.PROCESSING;

        if (currentStatus == Status.COMPLETED) {
            System.out.println("Task finished.");
        } else {
            System.out.println("Task is not finished.");
        }

        Day today = Day.MONDAY;
        System.out.println("Today is " + today + ", it's a " + today.getType()); // Output: Today is MONDAY, it's a Weekday

        for (Day d : Day.values()) { // values() là phương thức static được thêm tự động
             System.out.println(d + " is a " + d.getType() + ". Ordinal: " + d.ordinal()); // ordinal() trả về vị trí
        }
    }
}
