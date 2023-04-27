fun main() {
    // product of all the numbers
    val numbers = listOf(2, 3, 4, 5, 6)
    val product = numbers.reduce { acc, num -> acc * num }
    println("Tich cua tat ca cac so la: $product")
    println()
    // sum of all the numbers
    var sum = 0
    for (number in numbers) {
        sum += number
    }
    println("Sum = $sum")
    println()
    // length greater than 5
    val strings = arrayOf("apple", "durian", "elephant", "pineapple", "dog", "duck")
    val filteredStrings = filterStrings(strings)
    println(filteredStrings.contentToString())
    println()
    // even numbers
    val randomNumbers = List(10) { (1..100).random() }
    val evenNumbers = randomNumbers.filter { it % 2 == 0 }
    println("Random numbers: $randomNumbers")
    println("Even numbers: $evenNumbers")
    println()
    // only the unique values
    val inputArray = arrayOf(1, 2, 3, 4, 4, 4, 5, 1, 3, 6)
    val uniqueArray = getUniqueValues(inputArray)
    println(uniqueArray.contentToString())
    println()
    // average score
    val scores = mapOf(
        "T.Nguyen" to 8.5,
        "T.Kien" to 8.0,
        "N.Anh" to 9.5,
        "B.Thao" to 10.0
    )
    val sumScores = scores.values.sum()
    val average = sumScores / scores.size
    println("Average score: $average")
    println()
    // sort by length (1)
    val sortStrings = listOf("apple", "durian", "elephant", "pineapple", "dog", "duck")
    val sortByLength = sortStringsByLength(sortStrings)
    println("Strings sort by length: $sortByLength")
    println()
    // sort strings by group
    val groupStrings = listOf("apple", "banana", "car", "dog", "elephant")
    val grouped = groupStrings.groupBy { it.length }
    println(grouped)
    println()
    // sort by length (2)
    val sorting = listOf("apple", "banana", "car", "dog", "elephant")
    val sortedString = sorting.sortedBy { it.length }
    println("Strings sort by length: $sortedString")
    println()
    // divisible by three
    val inputList = listOf(1, 2, 3, 4, 5, 6, 9, 12, 13, 15, 16, 21)
    val outputList = divisibleByThree(inputList)
    println(outputList)
    println()
    // employees are salary more than 50000
    val employees = mapOf(
        "Nguyen" to 75000,
        "Kien" to 60000,
        "Anh" to 45000,
        "Thao" to 50000,
        "Han" to 55000
    )
    val highEarners = filterBySalary(employees)
    println(highEarners)
    println()
    // class GPA (person, student, teacher)
    val person = Person("T.Kien", 30, "Q.2")
    val student = Student("Nguyen", 23, "Q.Binh Thanh", "Developer App", 7.5)
    val teacher = Teacher("G.Linh", 25, "Q.Binh Thanh", "Leader Sale")
    println(person.name + ", " + person.age + " year old")
    println(student.name + ", " + student.age + " year old, " + student.major)
    println(teacher.name + ", " + teacher.age + " year old, " + teacher.subject)
    println()
    // Area and Perimeter of Shape
    val rectangle = Rectangle(5.0, 6.0)
    val circle = Circle(7.0)
    val triangle = Triangle(5.0, 4.0)
    println("Area of Rec: ${rectangle.area}")
    println("Perimeter of Rec: ${rectangle.perimeter}")
    println("Area of Cir: ${circle.area}")
    println("Perimeter of Cir: ${circle.perimeter}")
    println("Area of Tri: ${triangle.area}")
    println("Perimeter of Tri: ${triangle.perimeter}")
    println()
    val rectangledrawable = rectangleDrawable(rectangle)
    rectangledrawable.draw()
    val circledrawable = circleDrawable(circle)
    circledrawable.draw()
    val triangledrawable = triangleDrawable(triangle)
    triangledrawable.draw()
    println()
    // bank account
    val checkingAccount = CheckingAccount(5.5, 2206, "Nguyen", 0.5)
    val savingsAccount = SavingsAccount(5.5, 2206, "Nguyen", 1.5)
    println("Withdraw: ${checkingAccount.withdraw()}")
    println("Interest: ${savingsAccount.addInterest()}")
    println()
    // class zoo: dog, cat, bird
    val zoo = Zoo()
    val dog = Dog("Buddy", 3, "Golden Retriever")
    val cat = Cat("Smokey", 2, "Gray")
    val bird = Bird("Tweety", 1, 12.5)
    // print dog
    zoo.addAnimal(dog)
    zoo.listAnimals()
    dog.makeSound()
    dog.fetch()
    println()
    // print cat
    zoo.removeAnimal(dog)
    zoo.addAnimal(cat)
    zoo.listAnimals()
    cat.makeSound()
    cat.scratch()
    println()
    // print bird
    zoo.removeAnimal(cat)
    zoo.addAnimal(bird)
    zoo.listAnimals()
    bird.makeSound()
    bird.fly()
    println()
}


// length greater than 5
fun filterStrings(array: Array<String>): Array<String> {
    return array.filter { it.length > 5 }.toTypedArray()
}

// only the unique values
fun getUniqueValues(inputArray: Array<Int>): Array<Int> {
    val uniqueValues = mutableListOf<Int>()
    for (element in inputArray) {
        if (!uniqueValues.contains(element)) {
            uniqueValues.add(element)
        }
    }
    return uniqueValues.toTypedArray()
}

// sorted by length
fun sortStringsByLength(strings: List<String>): List<String> {
    return strings.sortedBy { it.length }
}

// divisible by three
fun divisibleByThree(numbers: List<Int>): List<Int> {
    return numbers.filter { it % 3 == 0 }
}

// employees are salary more than 50000
fun filterBySalary(employees: Map<String, Int>): Map<String, Int> {
    return employees.filterValues { salary -> salary > 50000 }
}

// class GPA
// khai bao class me Person
open class Person(val name: String, val age: Int, address: String)

// khai bao class con Student
class Student(name: String, age: Int, address: String, val major: String, var gpa: Double) :
    Person(name, age, address)

// khai bao class con Teacher
class Teacher(name: String, age: Int, address: String, val subject: String) :
    Person(name, age, address)

// Bai 7
// khai bao class me: Shape
abstract class Shape {
    abstract val area: Double
    abstract val perimeter: Double
}

// khai bao class con: Rectangle
class Rectangle(val length: Double, val width: Double) : Shape() {
    override val area: Double
get() = length * width
    override val perimeter: Double
        get() = 2 * (length + width)
}

// khai bao class con: Circle
class Circle(val radius: Double) : Shape() {
    override val area: Double
        get() = Math.PI * radius * radius
    override val perimeter: Double
        get() = 2 * Math.PI * radius
}

// khai bao class con: Triangle
class Triangle(val length: Double, val height: Double) : Shape() {
    override val area: Double
        get() = 0.5 * length * height
    override val perimeter: Double
        get() = length + height + length
}

// khai bao interface cua Drawable
interface Drawable {
    fun draw()
}

class rectangleDrawable(val rectangle: Rectangle) : Drawable {
    override fun draw() {
        println("Rectangle are four angle")
    }
}

class circleDrawable(val circle: Circle) : Drawable {
    override fun draw() {
        println("Circle are three angle")
    }
}

class triangleDrawable(val triangle: Triangle) : Drawable {
    override fun draw() {
        println("Triangle are no angle but it is radius")
    }
}

// khai bao class me: Bank Account
open class BankAccount(
    var balance: Double,
    val accountNumber: Int,
    val ownerName: String
)

// khai bao class con: Checking Account
class CheckingAccount(
    balance: Double,
    accountNumber: Int,
    ownerName: String,
    val monthlyFee: Double
) : BankAccount(balance, accountNumber, ownerName) {
    fun withdraw(amount: Double = 4.5): Boolean {
        val totalAmount: Double = amount + monthlyFee
        if (totalAmount > balance) {
            return false
        }
        balance -= totalAmount
        return true
    }
}

// khai bao class con: Savings Account
class SavingsAccount(
    balance: Double,
    accountNumber: Int,
    ownerName: String,
    val interestRate: Double
) : BankAccount(balance, accountNumber, ownerName) {
    fun addInterest(): Double {
        val interest:Double = balance * interestRate
        balance += interest
        return interest
    }
}
// Class Animal
abstract class Animal(val name: String, val age: Int, val species: String) {
    abstract fun makeSound()
}

class Dog(name: String, age: Int, val breed: String) : Animal(name, age, "Dog") {
    override fun makeSound() {
        println("Woof!")
    }

    fun fetch() {
        println("$name is fetching.")
    }
}

class Cat(name: String, age: Int, val color: String) : Animal(name, age, "Cat") {
    override fun makeSound() {
        println("Meow!")
    }

    fun scratch() {
        println("$name is scratching.")
    }
}

class Bird(name: String, age: Int, val wingspan: Double) : Animal(name, age, "Bird") {
    override fun makeSound() {
        println("Chirp!")
    }

    fun fly() {
        println("$name is flying.")
    }
}
class Zoo {
    private val animals = mutableListOf<Animal>()

    fun addAnimal(animal: Animal) {
        animals.add(animal)
    }

    fun removeAnimal(animal: Animal) {
        animals.remove(animal)
    }
  fun listAnimals() {
        for (animal in animals) {
            println("${animal.name} (${animal.species}), ${animal.age} years old")
        }
    }
}
// class Vehicle
open class Vehicle(val color: String, val weight: Double, val manufacturer: String)

class Car(color: String, weight: Double, manufacturer: String, val numDoors: Int) : Vehicle(color, weight, manufacturer)

class Bike(color: String, weight: Double, manufacturer: String, val numWheels: Int) : Vehicle(color, weight, manufacturer)
class VehicleCatalog {
    private val vehicles = mutableListOf<Vehicle>()

    fun addVehicle(vehicle: Vehicle) {
        vehicles.add(vehicle)
    }

    fun displayCatalog() {
        for (vehicle in vehicles) {
            println("Manufacturer: ${vehicle.manufacturer}, Color: ${vehicle.color}, Weight: ${vehicle.weight}")
            when (vehicle) {
                is Car -> println("Type: Car, Number of Doors: ${vehicle.numDoors}")
                is Bike -> println("Type: Bike, Number of Wheels: ${vehicle.numWheels}")
            }
            println()
        }
    }
}
