<style>

body {
    counter-reset: h2counter;
}

/* H1 - No numbering */
h1 {
    /* No counter reset or increment */
}

/* H2 - Level 1 numbering */
h2 {
    counter-reset: h3counter;
}

h2::before {
    counter-increment: h2counter;
    content: counter(h2counter) ". ";
}

/* H3 - Level 2 numbering */
h3 {
    counter-reset: h4counter;
}

h3::before {
    counter-increment: h3counter;
    content: counter(h2counter) "." counter(h3counter) " ";
}

/* H4 - Level 3 numbering (optional) */
h4 {
    counter-reset: h5counter;
}

h4::before {
    counter-increment: h4counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) " ";
}

</style>

# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a *Competent* grade on this portfolio task.

## Required evidence

### Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Project Directory](C:/TAFE/C_RIOT_AT2_Part2/project_directory.png)
![Happy Smiley Face](C:/TAFE/C_RIOT_AT2_Part2/output_of_mainpy.png)

If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### Fundamental code comprehension

 Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide  an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name   | value                                         |
   | ----------              |--------|-----------------------------------------------|
   | built-in primitive type | dimmed | True                                          |
   | built-in composite type | Pixels | [O, Y, Y, Y, Y, Y, Y, O, ..., O, Y, Y, Y, Y, Y, Y, O] |
   | user-defined type       | WHITE  | (255, 255, 255)                               |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                   | Type     |
   | ------------             |----------|
   | self.pixels              | list     |
   | A member of self.pixels  | tuple    |
   | self                     | instance |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File      | First line | Line range |
   | ------------ |-----------| -------- |------------|
   |  sequence    | smiley.py | self.sense_hat = SenseHat()         | 13–26      |
   |  selection   | sad.py    | if wide_open:         | 26-29      |
   |  iteration   | happy.py  | for pixel in mouth:         | 21-22      |


4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type                    | Used? | Example |
   | ----------------------- |-------| --------|
   | int                     | YES   | WHITE = (255, 255, 255)        |
   | float                   | YES   | delay=0.25        |
   | str                     | NO    | _       |
   | bool                    | YES   | wide_open=True        |

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

> Class variable: YELLOW (YELLOW = (255, 255, 0)), while the Instance variable: pixels (self.pixels).
> 
>The major difference between the two is that the class variable is a variable that is shared across all instances of the class while the instance variable is only used in a specific instance of a class.
> In the smiley.py, YELLOW is defined as a constant colour that is used in all classes, while the pixels is a specific type of smiley which could be different as smiley faces can be many shapes.
>

6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:
   1. What is the purpose of a constructor (in general) and this one (in particular)?

   > In Python, a constructor (named __init __) is a special method in a class, which is automatically called when a new instance of the class is created.
   > The key purpose of a constructor is to initialize the attributes of the instance, and to set up any relevent and necessary default values and states.
   > 
   > In the happy.py case, it calls its parent classes of Smiley and Blinkable to initialize shared and inherited functionaliy, such as draw_mouth() and draw_eyes() 
   > to create a smiley face with a happy expression.
   >

   2. What statement(s) does it execute (consider the `super` call), and what is the result?

   > It executes super()__init __(), self.draw_mouth() and self.draw_eyes(), 
   > where super().__init __() calls the parent classes of Smiley and Blinkable to set up the basic face shape (pixels attrubute from the Smiley class);
   > then draw_mouth() and draw_eyes() to draw the specific mouth and eye shape to make a smiley face with a happy expression. 
   >

### Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:
   
> The code follows the Python Enhancement Proposal (PEP 8). 
> 
> The SenseHat primarily adheres to PEP 8, but some deviations are also included due to the library's specific needs or preferences. 
> The why: The SenseHat python library is written with a strong emphasis on PEP 8 compliance to ensure readability and maintainability.
> The why not: due to the uniqueness of SenseHat and the needs to meet specific project or performance needs, some deviations may occur.
> For example, SenseHat may use certain internal code for interfacing with sensors and hardware to prioritize efficiency.

2. List three aspects of this convention you see applied in the code.

> 1) Class names are written in PascalCase (Smiley, Happy and Sad);
> 2) Method names are written in snake_case (draw_mouth() and draw_eyes());
> 3) The 4 spaces per indentation level. These codes follow the 4 spaces per indentation rule to improve code readability, compatibility and consistency.
>

3. Give two examples of organizational documentation in the code.

> Example 1: "Provides a Smiley with a happy expression" from the happy.py.
> This is a class-level docstring that explains the purpose of this Happy class is to initiate a smiley face with a happy expression.
> 
> Example 2: "Draws the mouth feature on a smiley" from the sad.py.
> This is a method-level docstring that explains the purpose of this method is to draw eye shapes for the smiley.

### Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.
  
  Use the following table for your answers:

| Class Name | Super or Sub? | Direct parent(s)   |
|------------|---------------|--------------------|
| Smiley     | Super         | NA                 |
| Happy      | Sub           | Smiley & Blinkable |
| Sad        | Sub           | Smiley             |
| Blinkable  | Super         | NA                 |

2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

> Abstraction is a fundamental concept in Python programming that refers to the process of creating abstract classes and methods that provide a blueprint for other classes to inherit from.
> It involves hiding unnecessary details and exposing only the relevant information to the users, thus allows us to simplify complex concepts and focus on the essential details. 
> 
> Example: The Smiley class provides an abstraction for handling the Sense HAT's LED matrix.
> Simply call the method of show() to display the smiley face or dim_display(dimmed=True) to adjust brightness without needing to know the details of how the Sense HAT interacts with hardware to set pixel colors or control brightness.
> Furthermore, this abstraction allows Sad and Happy subclasses to focus on customizing pixel patterns for expressions without dealing with the low-level logic of interacting with the LED matrix.

3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

> This is called Inheritance.
> 
> In this project, the inheritance enables the Happy and Sad classes to extend the functionality of base classes (Smiley and Blinkable).
> The Smiley base class provides shared functionality for displaying a smiley face on the Sense HAT's LED matrix, while the Blinkable base class provides functionality for making the eyes blink.
> The inheritance promotes code reuse and modularity, as the Happy and Sad classes can reuse functionalities from base classes, and only need to add or modify specific features, like the mouth and eye patterns, to represent different facial expressions.

### Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > The key difference between the two classes is the shape of the face they draw (shapes of mouth and eyes),
   > that one makes a happy face and another makes a sad face
   >
2. What are the key similarities?
   > Both classes are inheriting same functionalities from base class (e.g. Smiley), and use the same methods (e.g. draw_mouth() and draw_eyes())
   >
3. What difference stands out the most to you and why?
   > The happy class has the function of blinking (base class of Blinkable), wihle the Sad class doesn't have it.
   >
4. How does this difference affect the functionality of these classes
   > This difference allows the happy face to blink in every 0.25s, but not available in the sad face.
   >

### Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > The Smiley class uses the SenseHat
   >
2. Which of these classes directly interact with the SenseHat functionalities?
   > Smiley class directly interact with the SenseHat functionalities
   >
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   > The encapsulation in OOP involves hiding the internal details of a class and exposing only the necessary functionalities through a public interface.
   > In this project, the SenseHAT is encapsulated within the Smiley class, effectively hiding its complexities from the subclasses (Happy, Sad) and external users.
   > 
   > For example, The Smiley class initializes the SenseHAT object (self.sense_hat = SenseHat()) and provides methods like show() and dim_display() to interact with it.
   > These methods abstract away the underlying hardware operations, like setting pixel values (set_pixels()) and adjusting brightness (low_light).
   > Thus, the subclasses of Happy and Sad only need to modify the pixels attribute (mouth and eyes) to produce different faces, without needing direct access to the SenseHat object or its methods.
   > 

### Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

> Yes, because the base class of Blinkable is inherited in the Happy class and displayed by blink() method.
>

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

> No, because the blink() method can be overrode in subclasses. For example, the blink() method has a parameter delay=0.25, this defines how frequent the eye blinks and can be changed if needed.
>

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

> In OOP, implementation is defined thata single interface (method or function) can behave differently based on the object or class that implements it.
> It allows methods with the same name to have different implementations depending on the specific class.
> Thus, Polymorphism provides flexibility and extensibility, allowing the same method to adapt to the unique requirements of each class while maintaining a common interface for calling the method.
>

4. How is inheritance used in the blink method, and why is it important for polymorphism?

> Both Happy and Sad classes inherit blink() method from base class of Smiley, however each subclass can override the blink() method to implement its own version of how the eyes should blink.
> 
> Polymorphism is important, because it allows the flexibility. It allows the blink() method to be implemented differently in Happy and Sad to fit they needs.
>
1. **Implement Blink in Sad Class:**

   - Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:

   ```python
   def blink(self, delay=0.25):
        self.draw_eyes(wide_open=False)
        self.show()
        time.sleep(delay)
        self.draw_eyes(wide_open=True)
        self.show()
   ```

2. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

3. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:

![MainPy For Sad Smiley](C:/TAFE/C_RIOT_AT2_Part2/mainPy_for_sad_smiley.png)
![Sad Smiley Blinking](C:/TAFE/C_RIOT_AT2_Part2/sad_smiley_blinking.png)

- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > The eyes blink once and the blinking stops.

  ### If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

     > Blinkable is a base class

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

  > The generic term for Blinkable is an Abstract Base Clas (ABC), which is designed to be inherited or extended by other classes such as Smiley, Happy and Sad, ensuring these subclasses will have a blink() method.

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

  > The OO principle represented by the Blinkable class is Inheritance.
  > 
  > The Blinkable class defines a common interface (the blink() method) that other classes can inherit.
  > Through inheriting from Blinkable, subclasses like Happy and Sad can provide their specific implementations of the blink() method,
  > which matches to the definition of Inheritance where subclasses inherit a behavior from a base class and can override or extend that behavior.

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

  > This is because of the dynamic typing and flexible method overriding in Python,
  > which allows flexibility in extending functionality while maintaining distinct behaviors for different subclasses.
  > This enables user to simply define a blink() method in the Sad class, even if no formal interface (Blinkable) is directly called.

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  > This is known as polymorphism.
  > This is called “Duck Typing”. Duck typing is a fundamental concept in Python, which allows Python to be very flexible in accepting different types of objects as arguments to functions or methods, as long as they support the required operations
  > 
  > In contrast, C# uses a different concept of “Strong Typing” in which the type of the object defines the operations that can be performed. This type method ensures compile-time safety, but compromises flexibility when compared to Python.

  ***

  ## Refactoring

  ### Does a Smiley Have to Be Yellow?

  While our current implementation predominantly features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(s)?
        > Five colours are defined, namely Green, Red, Yellow and Blank. They are defined in the class of Smiley.
     2. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
        > The colour variables are hold in Tuples.
     3. Add the color blue to the appropriate class using the appropriate format and values.

  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > These color variables are used in subclasses like Happy and Sad. These subclasses inherited colors from base clas of Smiley.

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > The easiest way to change this will be change the values of YELLOW from (255, 255, 0) to (0, 255, 0).

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

  2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

  3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.

  4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

  This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

  ### Flexible Colors – Step 2

  Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

  1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

  2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.

  3. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

  4. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`'s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.

  ![Bulk Rename](screenshots/bulk_rename.png)

  5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

  6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

  ### Flexible Colors – Step 3

  With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

  1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

     ```python
     super().__init__(complexion=self.BLUE)
     ```

  2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

  3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.

  4. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.

  ***
