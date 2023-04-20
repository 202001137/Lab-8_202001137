# Lab-8_202001137


**Name: Kirtan D Makwana**  
**ID: 202001137**  



# Lab Exercises
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
   
    @Test
    public void testIsHealthy() {
        Boa boa1 = new Boa("Sneaky", 6, "granola bars");
        assertTrue(boa1.isHealthy());
       
        Boa boa2 = new Boa("Slithery", 8, "pizza");
        assertFalse(boa2.isHealthy());
    }
   
    @Test
    public void testFitsInCage() {
        Boa boa1 = new Boa("Slinky", 4, "mice");
        assertTrue(boa1.fitsInCage(5));
        assertFalse(boa1.fitsInCage(3));
       
        Boa boa2 = new Boa("Curly", 10, "rabbits");
        assertTrue(boa2.fitsInCage(12));
        assertFalse(boa2.fitsInCage(9));
    }
}


The isHealthy method of the Boa class is being tested in the first test case. In order to confirm that isHealthy returns true for the first object and false for the second, we construct two Boa objects with distinct favourite foods.

The fitsInCage method of the Boa class is being tested in the second test scenario. Two Boa objects are made, and their compatibility with various-sized cages is tested. The first boa should fit in a cage that is 5 inches long but not 3, and the second boa should fit in a cage that is 12 inches long but not 9.


import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
   
    private Boa jen;
    private Boa ken;
   
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
   
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
   
    @Test
    public void testFitsInCage() {
        assertTrue(jen.fitsInCage(3));
        assertFalse(ken.fitsInCage(2));
    }
}

To the BoaTest class, we added private fields for Jen and Ken, and we initialised them in the setUp function. In order to use these Boa objects for testing, we also changed the testIsHealthy and testFitsInCage methods.

Any changes made to the Boa objects during a test will not affect the objects used in other tests because the setUp function will be called prior to each test procedure.

import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
   
    private Boa jen;
    private Boa ken;
   
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
   
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
   
    @Test
    public void testFitsInCage() {
        assertTrue(jen.fitsInCage(3));
        assertFalse(ken.fitsInCage(2));
    }
}
To ensure that the isHealthy method returns true for both Boa objects, we added assertions to the testIsHealthy method. To ensure that the fitsInCage method produces the anticipated outcomes for the Boa objects, we also added assertions to the testFitsInCage method.

import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
   
    private Boa jen;
    private Boa ken;
   
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
   
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
   
    @Test
    public void testFitsInCage() {
        assertFalse(jen.fitsInCage(1)); // cage length less than boa length
        assertTrue(jen.fitsInCage(2)); // cage length equal to boa length
        assertTrue(jen.fitsInCage(3)); // cage length greater than boa length
       
        assertFalse(ken.fitsInCage(2)); // cage length less than boa length
        assertTrue(ken.fitsInCage(3)); // cage length equal to boa length
        assertTrue(ken.fitsInCage(4)); // cage length greater than boa length
    }
}
To ensure that the fitsInCage method delivers the anticipated results for both Jen and Ken when the cage length is less than, equal to, and more than the length of the boa, we added assertions to the testFitsInCage method in this example.

Because it tests the fitsInCage method's behaviour for various input values, it should be noted that the testFitsInCage method is now more reliable.


public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;

    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }

    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }

    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }

    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}


Here is the updated code for the BoaTest class with the new testLengthInInches() method:

import static org.junit.Assert.*;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {
    private Boa jen;
    private Boa ken;

    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }

    @Test
    public void testIsHealthy() {
        assertFalse(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }

    @Test
    public void testFitsInCage() {
        assertTrue(jen.fitsInCage(24));
        assertFalse(jen.fitsInCage(16));
        assertTrue(ken.fitsInCage(36));
        assertTrue(ken.fitsInCage(24));
        assertFalse(ken.fitsInCage(18));
    }

    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
