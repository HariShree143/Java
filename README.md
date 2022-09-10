# Java
package exceptionkeyword;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.Serializable;

class Dog implements Serializable{
	String name;
	String breed;
public Dog(String name, String breed) {
	this.name = name;
	this.breed = breed;
}
}
public class Main1 {
	public static void main(String args[]) {
		Dog dog = new Dog("Tyson", "Labrodor");
		try {
			FileOutputStream file = new FileOutputStream("file.txt");
			ObjectOutputStream output = new ObjectOutputStream(file);
			output.writeObject(dog);
			FileInputStream filestream = new FileInputStream("file.txt");
			ObjectInputStream input = new ObjectInputStream(filestream);
			Dog newDog = (Dog) input.readObject();
					System.out.println("The Dog Name is : " + newDog.name);
			System.out.println("Breed is: " + newDog.breed);
			output.close();
			input.close();
		}catch (Exception e) {
			e.getStackTrace();
		}
	}
}
