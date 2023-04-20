# <pre>                  IT314 - Software Engineering </pre>

#### Name       : Ranpariya Jatin Bharatbhai
#### Student ID  : 202001226
#### Date       : 20-04-2023

----

## Objective:
    The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.

----
1. Creating eclipse project named 'Lab8_202001226' and a package named 'myPackage' inside src folder in it.

![image](https://user-images.githubusercontent.com/72184476/233311235-7881fd44-dfc4-4cb2-bbbc-a20fc3a05a67.png)

2. Creating a class for a Boa with the given code snippet in the lab manual.
```
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	
	//returns true if this Boa constructor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	
	//returns true if the length of this Boa constructor is
	//less than the given cage length
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength;
	}
}	
```
![image](https://user-images.githubusercontent.com/72184476/233313045-c05a1630-6995-4cd7-8bf4-85bca4dee2fa.png)

3. Creating JUnit test file named 'BoaTest'.  

![image](https://user-images.githubusercontent.com/72184476/233318766-211d3835-654f-4a75-b799-20ea681b2bc8.png)

4. Initializing ken and jen as private Boa's.
```
import static org.junit.Assert.*;

import org.junit.After;
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen, ken;
	
	@Before
	public void setUp() throws Exception {
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa("Kenneth", 3, "granola bars");
	}
}
```
![image](https://user-images.githubusercontent.com/72184476/233319170-9afc79e4-78d7-4b47-b2b2-d216817f413e.png)

5. Implementing test cases for **isHealthy()** and **fitsInCage()** functions.
```
import static org.junit.Assert.*;

import org.junit.After;
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen, ken;
	
	@Before
	public void setUp() throws Exception {
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa("Kenneth", 3, "granola bars");
	}

	@After
	public void tearDown() throws Exception {
	}

	@Test
	public void testIsHealthy() {
		// IsHealthy testing for jen
		Assert.assertFalse(jen.isHealthy());
		
		// IsHealthy testing for ken
		Assert.assertTrue(ken.isHealthy());
	}
	
	@Test
	public void testFitsInCage() {
		// FitsInCage testing for jen
		Assert.assertFalse(jen.fitsInCage(1));
		Assert.assertFalse(jen.fitsInCage(2));
		Assert.assertTrue(jen.fitsInCage(3));
		
		// FitsInCage testing for ken
		Assert.assertFalse(ken.fitsInCage(2));
		Assert.assertFalse(ken.fitsInCage(3));
		Assert.assertTrue(ken.fitsInCage(4));
	}
}
```
![image](https://user-images.githubusercontent.com/72184476/233321589-6194f6da-c9e1-4904-8372-c16cc0bbbe0d.png)
For testing thee fitsInCage() function, there is no need to write tests for both jen and ken objects as the function is same for both and the output of test cases depends only whether the given lenght is greater than,less than or equal to actual length of object.The behaviour will be similar in both cases.

6. Running the tes cases. All test cases are passed and there is no red bars in the output. Both 2 test cases are passed.

![image](https://user-images.githubusercontent.com/72184476/233322692-b45bbadc-acb4-4dec-a910-6b76b9c10a0c.png)

7. Adding a new method to the Boa class with name lenghtInInches() to get the length in inches.
```
//returns the length of the Boa in inches
public int lenghtInInches() {
  return this.length * 12;
}
```
![image](https://user-images.githubusercontent.com/72184476/233324783-977920c2-f979-41ed-b9eb-96a547867f56.png)
As the length of the Boa is given in feet, to convert it into inches, We simply multiply length with 12 and return the value.

8. Adding another test case and running all 3 test cases together.
```
@Test
public void testLengthInInches() {
  // Length in inches of Boa-Jen should be 2*12=24
  assertEquals(24, jen.lenghtInInches());
        
  // Length in inches of Boa-Ken should be 3*12=36
  assertEquals(36, ken.lenghtInInches());
}
```
![image](https://user-images.githubusercontent.com/72184476/233325764-a1bac460-128a-4ba1-958e-6800e090de67.png)
As a result, test cases have been created for the specified Boa class, and the necessary Junit test cases have been used to test all three methods.
