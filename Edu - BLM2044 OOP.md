Alakalı sayfalar
[[CS - OOP]]

---
## Notlar

[[CS - OOP]]

---
Derste dinlediklerim
[[UML Diagrams#Class diagram]]
[[Assosicaton]]
[[Aggrigation]]
[[Inheritance]]
[[Encapculation]]
[[Polymorphism]]
[[Override]]
[[Virtual Method]]



---



# Çıkmışlardan notlar
## blm244_2020_mt

### **1-** **Programlama dillerinde thread kullanım amacını örnek bir C# veya Java kodu üzerinden açıklayınız**
![[Thread Using]]



### **2-** 2d array
![[Pasted image 20240418154731 1.png]]
**Java**
```java
public class multiDimArr {  
    public static void main(String[] args){  
        int[][] multiArr = new int[3][];  
  
        multiArr[0] = new int[2];  
        multiArr[1] = new int[1];  
        multiArr[2] = new int[3];  
		/*  
        multiArr[0][0]=1;        
        multiArr[0][1]=2;        
        multiArr[1][0]=0;        
        multiArr[2][0]=1;        
        multiArr[2][1]=2;        
        multiArr[2][2]=3;
        */  
        for (int i = 0; i< multiArr[0].length; i++){  
            multiArr[0][i]=i+1;  
        }  
  
        for (int i = 0; i< multiArr[1].length; i++){  
            multiArr[1][i]=i;
        }  
  
        for (int i = 0; i< multiArr[2].length; i++){  
            multiArr[2][i]=i+1;  
        }  
  
        for (int i = 0; i< multiArr.length;i++){  
            for (int j = 0; j < multiArr[i].length ;j++){  
                System.out.println(multiArr[i][j]);  
            }  
        }  
    }  
}
```
C#
```csharp
using System;

public class MultiDimArr
{
    public static void Main(string[] args)
    {
        int[][] multiArr = new int[3][];

        multiArr[0] = new int[2];
        multiArr[1] = new int[1];
        multiArr[2] = new int[3];

        // Initialize the first row
        for (int i = 0; i < multiArr[0].Length; i++)
        {
            multiArr[0][i] = i + 1;
        }

        // Initialize the second row
        for (int i = 0; i < multiArr[1].Length; i++)
        {
            multiArr[1][i] = i;
        }

        // Initialize the third row
        for (int i = 0; i < multiArr[2].Length; i++)
        {
            multiArr[2][i] = i + 1;
        }

        // Print the multi-dimensional array
        for (int i = 0; i < multiArr.Length; i++)
        {
            for (int j = 0; j < multiArr[i].Length; j++)
            {
                Console.WriteLine(multiArr[i][j]);
            }
        }
    }
}

```
### 3- Yukarıda verilen kodun çıktısının olması için main metodunu içeren sınıfın kodunu yazınız
```java
package cikmislar;  
  
public class Person {  
    private String name;  
    private int salary;  
    public Iperson k;  
  
    public Person(String n, int s) {  
        name = n;  
        salary = s;  
    }  
  
    public void setSalary(int salary) {  
        if ((this.salary-salary) != 0) {  
            if (k != null) {  
                k.salaryChange(this.salary, salary);  
            }  
            this.salary = salary;  
        }  
    }  
  
    public static void main(String[] args) {  
        Person per = new Person("Ali", 10);  

//----------------------------------
        per.k = new Iperson() {  
            @Override  
            public void salaryChange(int x, int y) {  
                System.out.println("initial sal "+x+"final salary "+y );  
            }  
        };  

		per.k = (x, y) -> System.out.println("initial sal "+x+"final salary "+y );
//----------------------------------
  
  
        per.setSalary(12);  
        per.setSalary(-14);  
    }  
}  
  
interface Iperson {  
    void salaryChange(int x, int y);  
}
```

### 4- Aşağıda verilen kodun çalışabilmesi için gerekli kodları içeren programı yzınız.
```csharp


public class aritClass {

    public static int mult(int x, int y){
        return x*y;
    }
    public static int addi(int x, int y){
        return x+y;
    }
//-----------------
    public delegate int del1(int x, int y); //fonksiyonun abtractı
    
    public static int Arit(int x, int y, del1 deloperator){
        return deloperator(x,y);
    }
//-----------------
    public static void Main(string[] args) {
        Console.WriteLine("add "+Arit(4, 5,addi));
        Console.WriteLine("mult "+Arit(4, 5,mult));
    }
    
}

```
### 5- Aşağıda verilen şekli gerçekleyecek C# veya Java kodunu yazınız.
![[Pasted image 20240421154855 1.png]]
```java
package cikmislar;  
  
public class AgCo {  
    public static void main(String[] args) {  
        Student student = new Student("John");  
        Department department = new Department("Computer Science", new Student("test2"));  
        University university = new University("Tech University", new Department("IE",new Student("test3")));  
        /*
        Student student = new Student("John");  
		Department department = new Department("Computer Science", student);  
		University university = new University("Tech University", department);
        */
  
  
        System.out.println("University: " + university.getName());  
        System.out.println("Department: " + department.getName()); 
        //-------
        System.out.println("Department: " + department.getName());  
		department.setStudent(student);
	    //------- 
        System.out.println("Enrolled Student: " + university.getDepartment().getEnrolledStudent().getName());  
    }  
}  
  
class Student {  
    private String name;  
  
    public Student(String name) {  
        this.name = name;  
    }  
  
    public String getName() {  
        return name;  
    }  
  
    public void setName(String name) {  
        this.name = name;  
    }  
}  
  
class Department {  
    private String name;  
    private Student enrolledStudent;  
  
    
  
	
	public Department(String name,Student enrolledStudent) {  
	    this.name = name;  
	    this.enrolledStudent = enrolledStudent;  
	  
	}  
	//burada aggregationnu constructor seçeneği vererek sağladık gibi. olsa iyi olur ama olmasa da olur 
	public Department(String name) {  
    this.name = name;  
    enrolledStudent = null;  
	}
    public Student getEnrolledStudent() {  
        return enrolledStudent;  
    } 
	public void setStudent(Student s){  
	    this.enrolledStudent = s;  
	} 
  
    public String getName() {  
        return name;  
    }  
  
     
  
    public void setName(String name) {  
        this.name = name;  
    }  
  
    public void setEnrolledStudent(Student enrolledStudent) {  
        this.enrolledStudent = enrolledStudent;  
    }  
}  
  
class University {  
    private String name;  
    private Department department;  
  
    public University(String name, Department department) {  
        this.name = name;  
        this.department = department;  
    }  
  
    public Department getDepartment() {  
        return department;  
    }  
  
    public String getName() {  
        return name;  
    }  
  
    public void setDepartment(Department department) {  
        this.department = department;  
    }  
  
    public void setName(String name) {  
        this.name = name;  
    }  
}
```

##  blm244_2021_mt
### 1- Tabloda, Person sınıfındaki name değişkenine erişilmek istenen yerler verilmiştir. Her bir durumda erişimi sağlayacak en az özelliğe sahip erişim belirleyiciyi ve gereken diğer işlemleri yazınız. (Not: Soruyu C# veya Java dillerinden biriyle açıklayabilirsiniz.
```java
public class Person {
… String name;
}
```

| aynı sınıf | aynı paket | farklı paket | farklı proje |
| ---------- | ---------- | ------------ | ------------ |
| private    | default    | public       | public       |
farklı proje için ``import project1.Person``  yazması lazım

bunun örneği intelljde var

### 2- C# dilinde; a. Person sınıfından oluşturulan nesnelerden 4 tanesini içerecek bir boyutlu dizide, b. Person sınıfından oluşturulan nesnelerden 4 tanesini 2’ye 2’lik matriste, tutacak değişkenleri tanımlayınız. Dizilerin veri girişini yapınız ve bir döngü yapısı kullanarak her bir dizi elemanını ekrana yazdırınız


 a. One-dimensional array to hold 4 objects of the Person class:

```csharp
using System;

class Program
{
    static void Main()
    {
        // Define a one-dimensional array to hold 4 objects of the Person class
        Person[] peopleArray = new Person[4];

        // Input data for the array
        peopleArray[0] = new Person("Alice", 25);
        peopleArray[1] = new Person("Bob", 30);
        peopleArray[2] = new Person("Charlie", 28);
        peopleArray[3] = new Person("David", 32);

        // Print each array element
        foreach (var person in peopleArray)
        {
            Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
        }
        //-----------
        for (int i = 0; i < peopleArray.Length; i++)
		{
		    var person = peopleArray[i];
		    Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
		}

		//-----------
    }
}

class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}
```

 b. 2x2 matrix to hold 4 objects of the Person class:

```csharp
using System;

class Program
{
    static void Main()
    {
        // Define a 2x2 matrix to hold 4 objects of the Person class
        Person[,] peopleMatrix = new Person[2, 2];

        // Input data for the matrix
        peopleMatrix[0, 0] = new Person("Alice", 25);
        peopleMatrix[0, 1] = new Person("Bob", 30);
        peopleMatrix[1, 0] = new Person("Charlie", 28);
        peopleMatrix[1, 1] = new Person("David", 32);

        // Print each matrix element
        for (int i = 0; i < 2; i++)
        {
            for (int j = 0; j < 2; j++)
            {
                Console.WriteLine($"Name: {peopleMatrix[i, j].Name}, Age: {peopleMatrix[i, j].Age}");
            }
        }
    }
}

class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}
```




### 3- a.Employee ee = new Engineer("Ayşe", 1); ee.showDetail(); b. IEmployee ie = new Engineer("Ali",2); ie.showDetail(); İşlemlerinin çıktıları nedir? c. Yukarıdaki kodları aynı sonucu verecek C# koduna çeviriniz.
![[#blm244_2023_mt#3- a.Employee ee = new Engineer("Ayşe", 1); ee.showDetail(); b. IEmployee ie = new Engineer("Ali",2); ie.showDetail(); İşlemlerinin çıktıları nedir? c. Yukarıdaki kodları aynı sonucu verecek C koduna çeviriniz.]]
### 4- C# dilinde oluşturulan her nesne System.Object sınıfını miras almaktadır. public class Person {String name; public Person(String n ){name=n;}} sınıfında Object sınıfından miras alınan Equals(Object o) ve ToString() metotlarını override edecek kodları Person sınıfı içerisine ekleyiniz.

official doc da bu şekilde
```csharp

public virtual bool Equals(object? obj)
        {
            return this == obj;
        }

        public static bool Equals(object? objA, object? objB)
        {
            if (objA == objB)
            {
                return true;
            }
            if (objA == null || objB == null)
            {
                return false;
            }
            return objA.Equals(objB);
        }
public virtual string? ToString()
        {
            // The default for an object is to return the fully qualified name of the class.
            return GetType().ToString();
        }
```
**ÇÖZÜM**
burada eğer override etmezsek 
false ve Person olarak döndürüyor
true ve person için p2= p1 yapmak lazım çünlü hashcodeları farklı
toString javada da var

```csharp
using System;

public class HelloWorld
{
    public static void Main(string[] args)
    {
        Person p1 = new Person("isim");
        Person p2 = new Person("isim");
        
        bool isEqual = p1.Equals(p2);
        Console.WriteLine(isEqual);  
        
        Console.WriteLine(p1.ToString()); 
    }
}

public class Person
{
    string name;
    
    public Person(string n)
    {
        name = n;
    }

    public override bool Equals(object obj)
    {
        if (obj == null || GetType() != obj.GetType())
        {
            return false;
        }

        Person other = (Person)obj;
        return name == other.name;
    }

    public override string ToString()
    {
        return $"Person Name: {name}";
    }
}
```

### 5- Matematikte karmaşık sayı gerçek ve sanal kısımdan oluşan bir nesnedir. a ve b sayıları gerçek olursa karmaşık sayılar;z=a+ib biçiminde gösterilirler. a. Karmaşık sayı nesnesinin Complex c = new Complex(2.0,3.0); biçiminde oluşturulabileceği Complex sınıfını C# veya Java dillerinden birisi ile yazınız. c. Complex sınıfında iki karmaşık sayının toplamını yaparak Complex veri tipinde geri döndürecek metodu yazınız.
intellj de var
```java
package cikmislar.blm244_2021_mt;

public class ComplexNum {

    private double real;  // Real part
    private double imaginary;  // Imaginary part

    // Constructor method
    public ComplexNum(double real, double imaginary) {
        this.real = real;
        this.imaginary = imaginary;
    }

    // Method to calculate the sum of two complex numbers
    public ComplexNum add(ComplexNum other) {
        double newReal = this.real + other.real;
        double newImaginary = this.imaginary + other.imaginary;
        return new ComplexNum(newReal, newImaginary);
    }

    // Method to return the complex number in a formatted string
    @Override
    public String toString() {
        return real + " + " + imaginary + "i";
    }

    // Main method for testing
    public static void main(String[] args) {
        ComplexNum c1 = new ComplexNum(2.0, 3.0);
        ComplexNum c2 = new ComplexNum(1.0, 4.0);

        // Calculate the sum of two complex numbers and print the result
        ComplexNum sum = c1.add(c2);
        System.out.println("Sum: " + sum.toString());
    }
}

```
## blm244_2021_final
### 1- Yukarıda verilen UML diyagramını gerçekleyecek C# veya Java kodunu yazınız. Herbir Log sınıfındaki logmesajı metodu ekrana kendi tipini yazsın. Örnek; EmaiLog sınıfında “email log” yazabilir. Logsınıf’ın uyarı metodu logmesajlarını aktif duruma getirecek. LogSınıf sınıfından bir nesne oluşturarak FileLog sınıfının mesajını ekrana yazdırın.

### 2- LogSınıf veri tipinde ve değerleri(nesneleri) EmailLog, SMSLog ve FileLog sınıflarından oluşturulan bir liste (List) oluşturun. Programınız liste değerlerini ekrana yazsın.
```java
package final_calisma;  
  
  
public class uml_loli {  
    public static void main(String[] args) {  
        Ilog emaillog = new emailLog();  
        Ilog smslog = new smsLog();  
        Ilog filelog = new fileLog();  
  
        logSinif lsm1 = new logSinif(emaillog);  
        lsm1.uyar();  
        logSinif lsm2 = new logSinif(smslog);  
        lsm2.uyar();  
        logSinif lsm3 = new logSinif(filelog);  
        lsm3.uyar();  

//2-------------------------
        logSinif[] arrLog = new logSinif[3];  
        arrLog[0] = new logSinif(emaillog);  
        arrLog[1] = new logSinif(smslog);  
        arrLog[2] = new logSinif(filelog);  
  
        for (logSinif log : arrLog) {  
            log.uyar();  
        }  
     }  
//2-------------------------
}  
  
class emailLog implements Ilog{  
    @Override  
    public void logMesaji(){  
        System.out.println("this is mail log");  
    }  
}  
  
class smsLog implements Ilog{  
    @Override  
    public void logMesaji() {  
        System.out.println("this is sms log");  
    }  
}  
  
class fileLog implements Ilog{  
    @Override  
    public void logMesaji() {  
        System.out.println("this is file log");  
    }  
}  
  
class logSinif{  
    Ilog ilog;  
  
    public logSinif(Ilog ilog){  
        this.ilog = ilog;  
    }  
  
    public void uyar(){  
        ilog.logMesaji();  
    }  
}
```

### 3- Verilen UML diyagramına uygun olan C# veya java kodlarını yazınız.
![[Pasted image 20240421161445 1.png]]
intelljde var
```java
package cikmislar.blm244_2021_final;  
  
public class memur_muhendis_calisan_uml {  
  
    public static void main(String[] args) {  
        calisan c1 = new calisan("ali");  
        c1.getInfo();  
  
        memur mem1 = new memur("veysel",5);  
        mem1.getInfo();  
  
        muhendis muh1 = new muhendis("kasım","bas");  
        muh1.getInfo();  
    }  
}  
  
class calisan{  
    String ad;  
  
    public calisan(String ad){  
        this.ad = ad;  
    }  
  
    public void getInfo(){  
        System.out.println("calisan info: "+ "isim: " + ad);  
    }  
}  
  
class memur extends calisan{  
  
    int derece;  
  
    public memur(String ad,int derece){  
        super(ad);  
        this.derece = derece;  
    }  
  
    @Override  
    public void getInfo(){  
        System.out.println("memur info: "+ "isim: " + ad+" derece: " +derece);  
    }  
}  
  
class muhendis extends calisan{  
  
    String unvan;  
  
    public muhendis(String ad, String unvan){  
        super(ad);  
        this.unvan=unvan;  
    }  
  
    @Override  
    public void getInfo(){  
        System.out.println("muhendis info: "+ "isim: " + ad+" unvan: " +unvan);  
    }  
}
```

### 4- Birinci satırında 2, ikinci satırında 1, üçüncü satırında 3 Calisan veri tipinde nesne bulunduran diziyi C# ve Java dillerinde yazınız. Bu soruda Calisan sınıfını oluşturmayın, yalnızca nesnesini oluşturun.
intellj de var
```java
package cikmislar.blm244_2021_final;  
  
public class twoDarrCalisanClass {  
  
    public static void main(String[] args) {  
        Calisan[][] calisanlar = new Calisan[3][];  
  
        calisanlar[0] = new Calisan[]{new Calisan("ali", 1), new Calisan("ayse", 2)};  
        calisanlar[1] = new Calisan[]{new Calisan("zeynep", 3)};  
        calisanlar[2] = new Calisan[]{new Calisan("veli", 4), new Calisan("zeki", 5), new Calisan("cigdem", 6)};  
    }  
}  
  
class Calisan {  
    String isim;  
    int yas;  
  
    public Calisan(String isim, int yas) {  
        this.isim = isim;  
        this.yas = yas;  
    }  
}
```
### 5- Yukarıda verilen şekle uygun C# kodunu yazınız.
![[#5- Aşağıda verilen şekli gerçekleyecek C veya Java kodunu yazınız.]]
### 5-Yukarıda verilen iki metot için veri tipi oluşturacak C# kodunu yazınız.
```csharp
using System;

public class Matematik
{
    // toplama metodu
    public int topla(int x, int y)
    {
        return x + y;
    }

    // çarpma metodu
    public int carp(int x, int y)
    {
        return x * y;
    }
}

class Program
{
    static void Main(string[] args)
    {
        Matematik matematik = new Matematik();
        
        // Örnek kullanımlar
        int toplamSonuc = matematik.topla(3, 4);
        int carpmaSonuc = matematik.carp(3, 4);
        
        Console.WriteLine("Toplam: " + toplamSonuc); // Output: Toplam: 7
        Console.WriteLine("Çarpma: " + carpmaSonuc); // Output: Çarpma: 12
    }
}

```

## blm244_2022_final
### 1,”Ali”, new Person() değerlerini birlikte tutacak bir boyutlu diziyi Java ve C# dillerinde tanımlayacak ve değerleri ekrana yazdıracak kodları yazınız
```java
class Person {
    @Override
    public String toString() {
        return "Person instance";
    }
}

public class Main {
    public static void main(String[] args) {
        Object[] array = new Object[3];
        array[0] = 1;
        array[1] = "Ali";
        array[2] = new Person();

        for (Object obj : array) {
            System.out.println(obj);
        }
    }
}

```

```csharp
using System;

class Person
{
    public override string ToString()
    {
        return "Person instance";
    }
}

class Program
{
    static void Main(string[] args)
    {
        object[] array = new object[3];
        array[0] = 1;
        array[1] = "Ali";
        array[2] = new Person();

        foreach (object obj in array)
        {
            Console.WriteLine(obj);
        }
    }
}

```
bu sorudaki trick "object" type olarak tanımlamak. object type arrayde farklı türleri destekler.

### Yukarıda verilen list değişkenine eklenen değerlerin number ve name değerleri üzerinden sıralanabilmesi için Student sınıfında ve list değişkeninin bulunduğu alanda olması gereken kodları yazınız.
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Student implements Comparable<Student> {
    int number;
    String name;

    public Student(int number, String name) {
        this.number = number;
        this.name = name;
    }

    @Override
    public String toString() {
        return number + " " + name;
    }
//*----------
    @Override
    public int compareTo(Student other) {
        // Önce number alanına göre karşılaştırma yap
        int numberCompare = Integer.compare(this.number, other.number);
        if (numberCompare != 0) {
            return numberCompare;
        }
        // number eşitse, name alanına göre karşılaştırma yap
        return this.name.compareTo(other.name);
    }
//----------*
    public static void main(String[] args) {
        List<Student> list = new ArrayList<>();
        list.add(new Student(1, "Ayşe"));
        list.add(new Student(3, "Fatma"));
        list.add(new Student(1, "Mehmet"));
        list.add(new Student(2, "Ali"));
//*----------
        // List'i sıralamak için Collections.sort metodunu kullan
        Collections.sort(list);

        // Sıralanmış listeyi yazdır
        for (Student student : list) {
            System.out.println(student);
        }
//----------*
    }
}

```
## blm244_2023_mt
### 1- Yukarıda verilen tabloyu Java’da kullanılan erişim belirleyicilere uygun olarak doldurunuz.****

|                             | Aynı Paket | Aynı Paket | Farklı Paket | Farklı Paket |
| --------------------------- | ---------- | ---------- | ------------ | ------------ |
|                             | Miras      | Nesne      | Miras        | Nesne        |
| Private(scope olarak düşün) | -          | +          | -            | -            |
| Default                     | +          | +          | -            | -            |
| Protected                   | +          | +          | +            | -            |
| Public                      | +          | +          | +            | +            |
==bunları dene==


### 2-C# dilinde; a. Person sınıfından oluşturulan nesnelerden 4 tanesini içerecek bir boyutlu dizide, b. Person sınıfından oluşturulan nesnelerden 4 tanesini 2’ye 2’lik matriste, tutacak değişkenleri tanımlayınız. Dizilerin veri girişini yapınız ve bir döngü yapısı kullanarak her bir dizi elemanını ekrana yazdırınız.
![[#2- C dilinde; a. Person sınıfından oluşturulan nesnelerden 4 tanesini içerecek bir boyutlu dizide, b. Person sınıfından oluşturulan nesnelerden 4 tanesini 2’ye 2’lik matriste, tutacak değişkenleri tanımlayınız. Dizilerin veri girişini yapınız ve bir döngü yapısı kullanarak her bir dizi elemanını ekrana yazdırınız]]
### 3- a.Employee ee = new Engineer("Ayşe", 1); ee.showDetail(); b. IEmployee ie = new Engineer("Ali",2); ie.showDetail(); İşlemlerinin çıktıları nedir? c. Yukarıdaki kodları aynı sonucu verecek C# koduna çeviriniz.
![[Pasted image 20240421172707 1.png]]
burada output engineer'a göre olur ikisinde de yani
```
output
Ayşe 1
Ali 2
```
çünkü java'da parent'ın tipinde de olsalar childin fonksiyonu kullanır
c# da ise eğer override yoksa fonksiyonlarda önce parent'ı kullanır.
c. c# da aynı output için
implements ve extends -> :
bir de employee ve engineer'ın showDetail fonksiyonlarına override ekle!
Console.WriteLine 
super(n) yerine : base(n) geliyor
```csharp
using System;


public class engEmp
{
    public static void Main(string[] args)
    {
        Employee ee = new Engineer("Ayşe", 1);
        ee.showDetail();

        IEmployee ie = new Engineer("Ali", 2);
        ie.showDetail();
    }
}

class Employee : IEmployee
{
    public string name;

    public Employee(string n)
    {
        name = n;
    }

    public virtual void showDetail()
    {
        Console.WriteLine(name);
    }
}

class Engineer : Employee
{
    public int dnumber;

    public Engineer(string n, int d) : base(n)
    {
        dnumber = d;
    }

    public override void showDetail()
    {
        Console.WriteLine(name + " " + dnumber);
    }
}

interface IEmployee
{
    void showDetail();
}

```

### 4- C# dilinde oluşturulan her nesne System.Object sınıfını miras almaktadır. public class Person {String name; public Person(String n ){name=n;}} sınıfında Object sınıfından miras alınan Equals(Object o) ve ToString() metotlarını override edecek kodları Person sınıfı içerisine ekleyiniz.
![[#4- C dilinde oluşturulan her nesne System.Object sınıfını miras almaktadır. public class Person {String name; public Person(String n ){name=n;}} sınıfında Object sınıfından miras alınan Equals(Object o) ve ToString() metotlarını override edecek kodları Person sınıfı içerisine ekleyiniz.]]
### 5- a. Java’da “super” ve “this” anahtar kelimelerini kullanan bir kod grubu yazınız. b. C# dilinde “base” ve “this” kullanacak bir kod grubu yazınız

```java
// Java code demonstrating the use of "super" and "this" keywords

class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    void display() {
        System.out.println("Name: " + name);
    }
}

class Dog extends Animal {
    String breed;

    Dog(String name, String breed) {
        super(name);  // Calls the constructor of the superclass
        this.breed = breed;  // Initializes the breed attribute of the subclass
    }

    void display() {
        super.display();  // Calls the display method of the superclass
        System.out.println("Breed: " + breed);
    }
}

public class Test {
    public static void main(String[] args) {
        Dog myDog = new Dog("Buddy", "Labrador");
        myDog.display();
    }
}

```

```csharp
// C# code demonstrating the use of "base" and "this" keywords

using System;

class Animal {
    protected string name;

    public Animal(string name) {
        this.name = name;
    }

    public virtual void Display() {
        Console.WriteLine($"Name: {name}");
    }
}

class Dog : Animal {
    private string breed;

    public Dog(string name, string breed) : base(name) {
        this.breed = breed;
    }

    public override void Display() {
        base.Display();  // Calls the Display method of the base class
        Console.WriteLine($"Breed: {breed}");
    }
}

class Program {
    static void Main() {
        Dog myDog = new Dog("Buddy", "Labrador");
        myDog.Display();
    }
}

```
# Hocanın mailden çıkanlar

## 1. 5 soru olacak, soruda belirtilen kısa kodları yazmanız gerekiyor. Syntax'ın tam doğru olması gerekmez  fakat abartmayın. En azından sınıf, metot, interface tanımlamayı düzgün yapmak gerekir.


### Java Examples

#### 1. Initializing a Class

```java
public class MyClass {
    private int myField;

    public MyClass(int myField) {
        this.myField = myField;
    }

    public void displayField() {
        System.out.println("My field value is: " + myField);
    }

    public static void main(String[] args) {
        MyClass myObject = new MyClass(10);
        myObject.displayField();
    }
}
```

#### 2. Initializing a Method

```java
public class MyMath {
    public int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        MyMath math = new MyMath();
        int result = math.add(5, 3);
        System.out.println("Result of addition: " + result);
    }
}
```

#### 3. Initializing an Interface

```java
public interface MyInterface {
    void myMethod();
}

public class MyClass implements MyInterface {
    @Override
    public void myMethod() {
        System.out.println("Implementation of myMethod");
    }

    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.myMethod();
    }
}
```

### C# Examples

#### 1. Initializing a Class

```csharp
public class MyClass
{
    private int myField;

    public MyClass(int myField)
    {
        this.myField = myField;
    }

    public void DisplayField()
    {
        Console.WriteLine("My field value is: " + myField);
    }

    public static void Main()
    {
        MyClass myObject = new MyClass(10);
        myObject.DisplayField();
    }
}
```

#### 2. Initializing a Method

```csharp
public class MyMath
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public static void Main()
    {
        MyMath math = new MyMath();
        int result = math.Add(5, 3);
        Console.WriteLine("Result of addition: " + result);
    }
}
```

#### 3. Initializing an Interface

```csharp
public interface IMyInterface
{
    void MyMethod();
}

public class MyClass : IMyInterface
{
    public void MyMethod()
    {
        Console.WriteLine("Implementation of MyMethod");
    }

    public static void Main()
    {
        MyClass obj = new MyClass();
        obj.MyMethod();
    }
}
```

These examples should give you a good starting point for initializing classes, methods, and interfaces in both Java and C#. Let me know if you have any questions or need further clarification on any of the examples!

## 4. 1 ve 2 boyutlu diziler her iki dildede önemlidir.
### 1D
**java**
```java
public class onedarr {  
  
    public static void main(String[] args) {  
        int[] arr = new int[5];  
  
        for (int i = 0; i< arr.length; i++){  
            arr[i] = i*15;  
        }  
  
        for (int i = 0;i < arr.length; i++){  
            System.out.println(arr[i]);  
        }  
    }  
}
```
C#
```csharp
using System;

public class OneDArray
{
    public static void Main(string[] args)
    {
        int[] arr = new int[5];

        for (int i = 0; i < arr.Length; i++)
        {
            arr[i] = i * 15;
        }

        for (int i = 0; i < arr.Length; i++)
        {
            Console.WriteLine(arr[i]);
        }
    }
}

```
- Changed `public static void main(String[] args)` to `public static void Main(string[] args)`
- Replaced `arr.length` with `arr.Length` for array length property
- Changed `System.out.println()` to `Console.WriteLine()` for outputting to the console
sadece sout i değiştir kafiii
### 2D
![[Pasted image 20240418154731 1.png]]
**Java**
```java
public class multiDimArr {  
    public static void main(String[] args){  
        int[][] multiArr = new int[3][];  
  
        multiArr[0] = new int[2];  
        multiArr[1] = new int[1];  
        multiArr[2] = new int[3];  
		/*  
        multiArr[0][0]=1;        
        multiArr[0][1]=2;        
        multiArr[1][0]=0;        
        multiArr[2][0]=1;        
        multiArr[2][1]=2;        
        multiArr[2][2]=3;
        */  
        for (int i = 0; i< multiArr[0].length; i++){  
            multiArr[0][i]=i+1;  
        }  
  
        for (int i = 0; i< multiArr[1].length; i++){  
            multiArr[1][i]=i;  
        }  
  
        for (int i = 0; i< multiArr[2].length; i++){  
            multiArr[2][i]=i+1;  
        }  
  
        for (int i = 0; i< multiArr.length;i++){  
            for (int j = 0; j < multiArr[i].length ;j++){  
                System.out.println(multiArr[i][j]);  
            }  
        }  
    }  
}
```
C#
```csharp
using System;

public class MultiDimArr
{
    public static void Main(string[] args)
    {
        int[][] multiArr = new int[3][];

        multiArr[0] = new int[2];
        multiArr[1] = new int[1];
        multiArr[2] = new int[3];

        // Initialize the first row
        for (int i = 0; i < multiArr[0].Length; i++)
        {
            multiArr[0][i] = i + 1;
        }

        // Initialize the second row
        for (int i = 0; i < multiArr[1].Length; i++)
        {
            multiArr[1][i] = i;
        }

        // Initialize the third row
        for (int i = 0; i < multiArr[2].Length; i++)
        {
            multiArr[2][i] = i + 1;
        }

        // Print the multi-dimensional array
        for (int i = 0; i < multiArr.Length; i++)
        {
            for (int j = 0; j < multiArr[i].Length; j++)
            {
                Console.WriteLine(multiArr[i][j]);
            }
        }
    }
}

```

## 5. Sınıflar arasındaki association, agregation, composition ilişkileri genelde sorgulanan kavramlardır.
[[UML Diagrams#4- Dependency (Aggregation & Composition)]]

## 6. Encapsulation (kapsülleme) erişim belirleyiciler java ve C# dillerinde farklılık gösterir.
[[Access Modifiers]]
![[Pasted image 20240420164246 1.png]]

https://www.youtube.com/watch?v=T632kAJ_9VA&t=32s&ab_channel=BroCode

bunun kodları pk1 pk2 olarak intellij de var protected olan kafa sikiyo ama geri kalanlar ok


## 7. İnheritance (kalıtım) nesne yönelimde bahsedince olmazsa olmazlar arasındadır.

burada override ederken overload yapmaman lazım fonk birebir aynı kalacak!

## 8. Kalıtım varsa polymorhism olmazsa olmaz kabul edilebilir.
bunun örneği intellj

## 9. Abstract sınıflar ve interface kullanımı bir çok tasarım deseninde kullanılırlar. En azından temel kullanımı bizim derse uyar.
- Bir class sadece bir abstract class implement edebilir.
- “new” ile oluşturulamaz.
- Abstract sınıfta metot ve değişkenler tanımlanabilir :
- abs class da access modifierslar aynı
## 10. C# dilinde delegate ve ona bağlı event kullanımı önem taşır.
https://www.tutorialsteacher.com/csharp/csharp-event
### delegate kullanımı
c++daki func pointera benziyor
```csharp
using System;

public delegate void delmsg(string msg);

public class HelloWorld
{
    public static void Main()
    {
        delmsg del1 = greet;
        del1("selam");
    }

    public static void greet(string msg)
    {
        Console.WriteLine(msg);
    }
}

```

```csharp
using System;

public delegate int MathOperation(int a, int b);

public class Calculator
{
    public int Add(int a, int b)
    {
        Console.WriteLine($"Adding {a} and {b}");
        return a + b;
    }

    public int Subtract(int a, int b)
    {
        Console.WriteLine($"Subtracting {b} from {a}");
        return a - b;
    }

    public int Multiply(int a, int b)
    {
        Console.WriteLine($"Multiplying {a} by {b}");
        return a * b;
    }
}

public class Program
{
    public static void Main()
    {
        // Create an instance of the Calculator class
        Calculator calculator = new Calculator();

        // Initialize a single delegate instance with the Add method
        MathOperation operation = calculator.Add;

        // Invoke the single delegate
        int result1 = operation(5, 3);
        Console.WriteLine($"Result from single delegate invocation: {result1}");

        // Initialize a multicast delegate with multiple methods
        operation += calculator.Subtract;
        operation += calculator.Multiply;

        // Invoke the multicast delegate
        int result2 = operation(10, 2);
        Console.WriteLine($"Result from multicast delegate invocation: {result2}");
    }
}
	
```




---

## **abstract class vs interface**
### Abstract Class

An abstract class is a class that cannot be instantiated directly. It serves as a base for other classes to inherit from. An abstract class can have both abstract (unimplemented) and concrete (implemented) methods.

#### Key Points:

- **Cannot be instantiated**: You cannot create an object of an abstract class directly.
  
- **Can have abstract methods**: These methods are declared without an implementation and must be implemented by any non-abstract subclass.
  
- **Can have concrete methods**: These methods have an implementation and can be used directly by subclasses.

#### Syntax:

```java
public abstract class Animal {
    
    // Abstract method (no implementation)
    public abstract void sound();
    
    // Concrete method
    public void breathe() {
        System.out.println("Breathing...");
    }
}
```

#### Example:

```java
public class Dog extends Animal {
    
    // Implementing the abstract method
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}
```

### Interface

An interface is like a blueprint of a class that contains only abstract methods, constants, and static methods. It provides a way to achieve abstraction and multiple inheritance in Java. A class implements an interface to become more specialized.

#### Key Points:

- **Cannot be instantiated**: Similar to abstract classes, you cannot create an object of an interface.
  
- **Contains only abstract methods**: All methods in an interface are abstract by default.
  
- **Can have constants**: You can declare constants (static final variables) in an interface.
  
- **Supports multiple inheritance**: A class can implement multiple interfaces.

#### Syntax:

```java
public interface Animal {
    
    // Abstract method (no implementation)
    void sound();
    
    // Constant
    String TYPE = "Animal";
    
    // Static method with implementation (Java 8+)
    static void info() {
        System.out.println("This is an Animal interface");
    }
}
```

#### Example:

```java
public class Dog implements Animal {
    
    // Implementing the abstract method from Animal interface
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}
```

### Comparison

- **Instantiation**: Abstract classes cannot be instantiated, while interfaces cannot be instantiated directly but can be implemented by classes.
  
- **Accessibility**: Abstract classes can have `public`, `protected`, or `default` access, while interfaces are `public` by default.
  
- **Multiple Inheritance**: A class can extend only one abstract class, but it can implement multiple interfaces.

### When to Use Which?

- **Use Abstract Class**:
    - When you want to share code among several closely related classes.
    - When you need to declare fields and provide default implementations for methods.
  
- **Use Interface**:
    - When you want to specify a contract for multiple classes to implement.
    - When you need to achieve multiple inheritance.

### Summary

- **Abstract Class**: 
    - A class that cannot be instantiated and may contain abstract methods and concrete methods.
  
- **Interface**: 
    - A blueprint of a class containing only abstract methods, constants, and static methods.


---

## **abstract method vs normal method**
The main difference between abstract methods and normal methods lies in their implementation and usage within classes. Here's a breakdown of their differences:

### Abstract Methods

1. **No Implementation**:
    - An abstract method is declared without providing an implementation in the abstract class or interface.
  
2. **Must Be Overridden**:
    - Any non-abstract subclass of an abstract class or any class implementing an interface containing abstract methods must provide an implementation for those abstract methods.
  
3. **Purpose**:
    - It serves as a declaration or contract, indicating that any subclass or implementing class must provide a concrete implementation.

#### Example:

```java
public abstract class Animal {
    
    // Abstract method
    public abstract void sound();
}
```

### Normal Methods (Concrete Methods)

1. **Has Implementation**:
    - A normal method has a complete implementation, providing the code that will be executed when the method is called.
  
2. **Optional to Override**:
    - Subclasses may choose to override a normal method, but it's not mandatory.
  
3. **Purpose**:
    - Provides the actual functionality or behavior of the class.

#### Example:

```java
public class Dog extends Animal {
    
    // Concrete method
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}
```

### Summary

- **Abstract Methods**:
    - Are declared without an implementation.
    - Must be overridden by non-abstract subclasses or implementing classes.
    - Serve as a contract or declaration that subclasses or implementing classes must fulfill.

- **Normal Methods**:
    - Have a complete implementation.
    - Can be optionally overridden by subclasses.
    - Provide the actual functionality or behavior of the class.

Understanding the difference between abstract methods and normal methods helps in designing classes with proper abstraction and inheritance, allowing for flexibility and code reusability in object-oriented programming.


## static -> nesne oluşturmadan şak şak kullan
Certainly! A static utility class is commonly used to group related methods that perform utility tasks and don't rely on instance-specific state. Below is an example of a static utility class named `MathUtils` that provides various mathematical operations.

### Static Utility Class: `MathUtils`

```java
public class MathUtils {
    
    // Private constructor to prevent instantiation
    private MathUtils() {
        throw new AssertionError("Utility class should not be instantiated");
    }

    // Static method to add two numbers
    public static int add(int a, int b) {
        return a + b;
    }

    // Static method to subtract two numbers
    public static int subtract(int a, int b) {
        return a - b;
    }

    // Static method to multiply two numbers
    public static int multiply(int a, int b) {
        return a * b;
    }

    // Static method to divide two numbers
    public static double divide(int a, int b) {
        if (b == 0) {
            throw new IllegalArgumentException("Cannot divide by zero");
        }
        return (double) a / b;
    }
}
```

### Usage in Main Class

Now, let's see how you can use the `MathUtils` class to perform mathematical operations without creating an instance of the class.

```java
public class Main {
    
    public static void main(String[] args) {
        
        // Calling static methods from MathUtils class
        int sum = MathUtils.add(5, 3);
        int difference = MathUtils.subtract(5, 3);
        int product = MathUtils.multiply(5, 3);
        double quotient = MathUtils.divide(10, 2);

        // Printing the results
        System.out.println("Sum: " + sum);
        System.out.println("Difference: " + difference);
        System.out.println("Product: " + product);
        System.out.println("Quotient: " + quotient);
    }
}
```

### Explanation

- **Private Constructor**: 
    - The `MathUtils` class has a private constructor to prevent instantiation of the class, ensuring that it's used only for static utility methods.

- **Static Methods**:
    - The `add`, `subtract`, `multiply`, and `divide` methods are static, allowing you to call them directly using the class name without creating an instance.

- **Utility Class Usage**:
    - In the `Main` class, we call the static methods of the `MathUtils` class to perform various mathematical operations, such as addition, subtraction, multiplication, and division.

This static utility class serves as a convenient way to organize related utility methods and makes it clear that these methods are standalone and don't rely on instance-specific state.




# ek not
![[#blm244_2021_final#5- Yukarıda verilen şekle uygun C kodunu yazınız.]]

agg ve comp 

![[#blm244_2023_mt#3- a.Employee ee = new Engineer("Ayşe", 1); ee.showDetail(); b. IEmployee ie = new Engineer("Ali",2); ie.showDetail(); İşlemlerinin çıktıları nedir? c. Yukarıdaki kodları aynı sonucu verecek C koduna çeviriniz.]]



## EVENT DELEGATE KENDİ NOTUM
### DELEGATE
delegate bir abstract aslında
tanımlarken bu obje bir method yerine geçecek ve attributeları bunlar olacak diye tanımlıyoruz
![[#blm244_2020_mt#4- Aşağıda verilen kodun çalışabilmesi için gerekli kodları içeren programı yzınız.]]
burada delegate kullanmamız gerektiğini arit methodunda iki farklı method girebildiğinden anlıyoruz.
delegate'in attr'lerini de üstteki mult ve addi nin attr'lerinde görüyoruz.
`public delegate int del1(int x, int y);` bu ifade "public scopeda delegate tipinde  ismi del1  olup int return eden içine x,y olarak 2 int variable alan bir func'un abstractı" demektir

`public static int Arit(int x, int y, del1 deloperator){ return deloperator(x,y); }` bu kısımda da o abtractlığı nasıl kullanacağımızı gördük

### EVENT
Publisher subscriber benzetmesi çok yaygın
1 publisher 1+ subscriber 
eventler delegate ile encapculate oluyorlar
```csharp
public delegate void Notify();  // delegate
                    
public class ProcessBusinessLogic
{
    public event Notify ProcessCompleted; // event

    public void StartProcess()
    {
        Console.WriteLine("Process Started!");
        // some code here..
        OnProcessCompleted();
    }

    protected virtual void OnProcessCompleted() //protected virtual method
    {
        //if ProcessCompleted is not null then call delegate
        ProcessCompleted?.Invoke(); 
    }
}
```

`public delegate void Notify();  // delegate` burada void döndüren bir delegate tanımlıyoruz

`public event Notify ProcessCompleted; // event`  burada Notify delegate'ini return eden bir event tanımlıyoruz

`protected virtual void OnProcessCompleted() //protected virtual method{ ProcessCompleted?.Invoke(); }` burada  PressCompleted eğer tetiklendiyse diye bir kontrol var. eğer tetiklendiyse pressCompleted çalışıyor çünkü press completed notify delegatinini refer ediyor. ? null değilse invoke'u çalıştır demek.

`public void StartProcess(){ Console.WriteLine("Process Started!"); OnProcessCompleted(); }` burası da düz method ama OnProgressCompleted'i çalıştırarak bir event var mı yok mu bakıyor.

Buraya kadarki kısmı daha temelleri halleden developer yapıyor. Buradan sonrası da yeni feature falan ekleyen developer yapıyor. Publisher subscriber benzetmesi. burada üstteki kod publisher alttaki subscriber.

```csharp
class Program
{
    public static void Main()
    {
        ProcessBusinessLogic bl = new ProcessBusinessLogic();
        bl.ProcessCompleted += bl_ProcessCompleted; // register with an event
        bl.StartProcess();
    }

    // event handler
    public static void bl_ProcessCompleted()
    {
        Console.WriteLine("Process Completed!");
    }
}
```

`ProcessBusinessLogic bl = new ProcessBusinessLogic();` üstteki classtan bir obj oluşturuyoruz.
`bl.ProcessCompleted += bl_ProcessCompleted;` bl'deki process completed notify delegate'ine bir func gönderiyoruz. ama burada += olduğuna bakma bir queue sistemi yok 

`bl.StartProcess();` üstteki classtaki startprocessi başlatıyoruz o OnProcessCompleted'a gidiyor o da delegate'i kontrol ediyor içinde bir method var mı yok mu diye. Bu kodda bl_ProcessCompleted methodu var.

```
output:
Process Started!  
Process Completed!
```

https://www.tutorialsteacher.com/csharp/csharp-event



```cs

using System;
using System.Data;
using System.Data.SqlClient;

class SqlDatabaseOperations
{
    private string connectionString;

    public SqlDatabaseOperations(string connectionString)
    {
        this.connectionString = connectionString;
    }

    public void InsertData(string tableName, string columns, string values)
    {
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            string query = $"INSERT INTO {tableName} ({columns}) VALUES ({values})";
            SqlCommand command = new SqlCommand(query, connection);

            connection.Open();
            command.ExecuteNonQuery();
            connection.Close();
        }
    }

    public void UpdateData(string tableName, string setClause, string whereClause)
    {
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            string query = $"UPDATE {tableName} SET {setClause} WHERE {whereClause}";
            SqlCommand command = new SqlCommand(query, connection);

            connection.Open();
            command.ExecuteNonQuery();
            connection.Close();
        }
    }

    public void DeleteData(string tableName, string whereClause)
    {
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            string query = $"DELETE FROM {tableName} WHERE {whereClause}";
            SqlCommand command = new SqlCommand(query, connection);

            connection.Open();
            command.ExecuteNonQuery();
            connection.Close();
        }
    }

    public DataTable SelectData(string tableName, string columns, string whereClause = "")
    {
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            string query = $"SELECT {columns} FROM {tableName}";
            if (!string.IsNullOrEmpty(whereClause))
            {
                query += $" WHERE {whereClause}";
            }

            SqlDataAdapter adapter = new SqlDataAdapter(query, connection);
            DataTable dataTable = new DataTable();
            adapter.Fill(dataTable);

            return dataTable;
        }
    }
}

class Program
{
    static void Main()
    {
        string connectionString = @"Server=your_server_name;Database=your_database_name;User Id=your_username;Password=your_password;";
        SqlDatabaseOperations dbOperations = new SqlDatabaseOperations(connectionString);

        // Insert example
        dbOperations.InsertData("TableName", "Column1, Column2", "'Value1', 'Value2'");

        // Update example
        dbOperations.UpdateData("TableName", "Column1='UpdatedValue'", "Column2='Value2'");

        // Delete example
        dbOperations.DeleteData("TableName", "Column1='UpdatedValue'");

        // Select example
        DataTable results = dbOperations.SelectData("TableName", "*");
        foreach (DataRow row in results.Rows)
        {
            foreach (var item in row.ItemArray)
            {
                Console.Write($"{item} ");
            }
            Console.WriteLine();
        }
    }
}


```

```cs

using System;
using System.Data;
using System.Data.OleDb;

class AccessDatabaseOperations
{
    private string connectionString;

    public AccessDatabaseOperations(string databasePath)
    {
        connectionString = $@"Provider=Microsoft.ACE.OLEDB.12.0;Data Source={databasePath};Persist Security Info=False;";
    }

    public void InsertData(string tableName, string columns, string values)
    {
        using (OleDbConnection connection = new OleDbConnection(connectionString))
        {
            string query = $"INSERT INTO {tableName} ({columns}) VALUES ({values})";
            OleDbCommand command = new OleDbCommand(query, connection);

            connection.Open();
            command.ExecuteNonQuery();
            connection.Close();
        }
    }

    public void UpdateData(string tableName, string setClause, string whereClause)
    {
        using (OleDbConnection connection = new OleDbConnection(connectionString))
        {
            string query = $"UPDATE {tableName} SET {setClause} WHERE {whereClause}";
            OleDbCommand command = new OleDbCommand(query, connection);

            connection.Open();
            command.ExecuteNonQuery();
            connection.Close();
        }
    }

    public void DeleteData(string tableName, string whereClause)
    {
        using (OleDbConnection connection = new OleDbConnection(connectionString))
        {
            string query = $"DELETE FROM {tableName} WHERE {whereClause}";
            OleDbCommand command = new OleDbCommand(query, connection);

            connection.Open();
            command.ExecuteNonQuery();
            connection.Close();
        }
    }

    public DataTable SelectData(string tableName, string columns, string whereClause = "")
    {
        using (OleDbConnection connection = new OleDbConnection(connectionString))
        {
            string query = $"SELECT {columns} FROM {tableName}";
            if (!string.IsNullOrEmpty(whereClause))
            {
                query += $" WHERE {whereClause}";
            }

            OleDbDataAdapter adapter = new OleDbDataAdapter(query, connection);
            DataTable dataTable = new DataTable();
            adapter.Fill(dataTable);

            return dataTable;
        }
    }
}

class Program
{
    static void Main()
    {
        string databasePath = @"C:\path\to\your\database.accdb";
        AccessDatabaseOperations dbOperations = new AccessDatabaseOperations(databasePath);

        // Insert example
        dbOperations.InsertData("TableName", "Column1, Column2", "'Value1', 'Value2'");

        // Update example
        dbOperations.UpdateData("TableName", "Column1='UpdatedValue'", "Column2='Value2'");

        // Delete example
        dbOperations.DeleteData("TableName", "Column1='UpdatedValue'");

        // Select example
        DataTable results = dbOperations.SelectData("TableName", "*");
        foreach (DataRow row in results.Rows)
        {
            foreach (var item in row.ItemArray)
            {
                Console.Write($"{item} ");
            }
            Console.WriteLine();
        }
    }
}


```