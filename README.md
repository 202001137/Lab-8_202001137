# Lab-8_202001137


**Name: Kirtan D Makwana**  
**ID: 202001137**  

## Creating a new Eclipse project, and within the project create a package and defining the class

<img src="https://user-images.githubusercontent.com/95064151/233036757-48d69020-3270-44bc-9c8b-c8443862f8ff.png">

## Adding the Test Case

    public class BoaTest {
      Boa jen;
      Boa ken;

      @Before
      public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa ("Kenneth", 3, "granola bars");
      }

      @After
      public void tearDown() throws Exception {
      }

      @Test
        public void testIsHealthy() {
            assertTrue(ken.isHealthy()); // kens favourite food is granola bars
            assertFalse(jen.isHealthy());
        }

        @Test
        public void testFitsInCage() {
            assertFalse(ken.fitsInCage(2));
            assertFalse(ken.fitsInCage(3));
            assertTrue(ken.fitsInCage(5));

            assertFalse(jen.fitsInCage(1));
            assertFalse(jen.fitsInCage(2));
            assertTrue(jen.fitsInCage(3));
        }
    }

## Running the Test Case

<img src="https://user-images.githubusercontent.com/95064151/233039273-d00304f8-2deb-4061-af0c-b76a2254d573.png">

## Adding a new method to the Boa class

	public int lengthInInches(){
		// 1 foot is 12 inches
		return this.length*12;
	}

<img src="https://user-images.githubusercontent.com/95064151/233043524-77bdff56-2e7b-4f43-bd8a-0ca06593abf9.png">

## Adding new test cases to test lengthInInches()

    @Test
    public void testlengthInInches() {
    	assertEquals("error in lengthInInches()",  36, ken.lengthInInches());
    	assertNotEquals("error in lengthInInches()",  35, ken.lengthInInches());
        
    	assertEquals("error in lengthInInches()",  24, jen.lengthInInches());
    	assertNotEquals("error in lengthInInches()",  30, jen.lengthInInches());
    }
    
## Running the new Test Case

<img src="https://user-images.githubusercontent.com/95064151/233043180-b2f14800-de7b-4d43-a372-2e3cfdc44d44.png">
