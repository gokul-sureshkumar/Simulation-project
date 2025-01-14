# TITTLE:

Door locking system with 4 digit Pincode

## ABSTRACT:

This project presents the design and implementation of an Arduino-based door locking system that utilizes a 4-digit Pincode for secure access control. The system aims to enhance the traditional door locking mechanisms by incorporating digital technology, providing a cost-effective and customizable solution for both residential and commercial applications. The core components of the system include an Arduino microcontroller, a keypad for user input, an electronic locking mechanism, and supporting circuitry. The user interface is established through a 4x4 keypad, allowing users to input a personalized 4-digit Pincode for door access. The Arduino microcontroller processes the entered Pincode and triggers the locking or unlocking mechanism accordingly.



## INTRODUCTION:

This Arduino-based door locking system offers a balance between security and user convenience, making it suitable for various environments where controlled access is desired. The flexibility and programmability of the Arduino platform make it easy to adapt the system to specific user requirements and integrate additional features for future enhancements.The Arduino-based door locking system with a 4-digit Pincode represents a modern and secure approach to access control. This system utilizes the Arduino microcontroller and a 4x4 keypad to enable users to input a personalized Pincode for door access. By seamlessly integrating digital technology, the system enhances security while eliminating the need for traditional keys. The 4-digit Pincode serves as a user-friendly and customizable credential, striking a balance between simplicity and security. The project's modular design allows for easy adaptation to specific user requirements and future enhancements, making it an accessible and versatile solution for residential and commercial applications. Through the combination of Arduino's open-source platform and a personalized Pincode system, this project aims to redefine door security with efficiency and cost-effectiveness at its core.


## LITERATURE REVIEW:

The literature review for an Arduino door locking system with a 4-digit Pincode encompasses an exploration of electronic access control systems, including their architectures and authentication methods, with a focus on the evolution from traditional key-based to digital solutions. Additionally, studies on the application of Arduino microcontrollers in security systems are examined, highlighting the versatility and adaptability of Arduino-based projects. Research on PIN-based access systems contributes insights into authentication principles and usability factors, while discussions on biometric and multifactor authentication systems provide a broader context. Literature on user experience and human-computer interaction in electronic door locking systems informs considerations for interface design. Security aspects, such as encryption and protection against common threats, are addressed, and the integration of IoT and home automation into door locking systems is explored. The review also encompasses the role of open-source hardware and software, examining their benefits and challenges. Real-world case studies and implementations offer practical insights and lessons learned, contributing to a comprehensive understanding of the state-of-the-art in Arduino-based door locking systems.


## PROPOSED METHODLOGY:

Define Objectives:
Clearly articulate the goals and functionalities of the Arduino-based door locking system.

Component Assembly:
Gather and connect the necessary components, including Arduino, keypad, and locking mechanism.

Code Development:
Write Arduino code for Pincode validation, user feedback, and control of the locking mechanism.

Testing:
Conduct rigorous testing to ensure proper functionality in different scenarios.

Security Implementation:
Integrate security measures, such as delay features, to enhance system robustness.

User Interface Refinement:
Design an intuitive user interface for effective interaction and feedback.

Documentation:
Prepare clear documentation covering system architecture, circuit diagrams, and user instructions.

User Training:
Train end-users on Pincode entry, system operation, and basic troubleshooting.

Installation:
Mount the system securely in the desired location, ensuring stability and proper connections.

Final Checks:
Perform a comprehensive check to verify overall system functionality before deployment.

Deployment:
Roll out the system for regular use, monitoring its performance in the real-world environment.

Maintenance Plan:
Establish a maintenance schedule and procedures for addressing any issues that may arise.

Feedback and Iteration:
Gather user feedback and consider improvements or additional features for future iterations
## CIRCUIT DIAGRAM:

![image](https://github.com/gokul-sureshkumar/Simulation-project/assets/121148715/6eb92823-6dc6-466d-82f9-8a2028ea0ebf)

## PROGRAM:
```
#include <Keypad.h>
#include <Servo.h>

const int servoPin = 9; // Pin for the servo motor
Servo myServo;

const int ROW_NUM    = 4; // four rows
const int COLUMN_NUM = 4; // four columns

char keys[ROW_NUM][COLUMN_NUM] = {
  {'1','2','3','A'},
  {'4','5','6','B'},
  {'7','8','9','C'},
  {'*','0','#','D'}
};
byte pin_rows[ROW_NUM] = {5, 4, 3, 2}; // connect to the row pinouts of the keypad
byte pin_column[COLUMN_NUM] = {8, 7, 6, A0}; // connect to the column pinouts of the keypad
Keypad keypad = Keypad(makeKeymap(keys), pin_rows, pin_column, ROW_NUM, COLUMN_NUM);
String enteredCode = "";
String correctCode = "1234"; // Change this to your desired 4-digit Pincode
void setup() {
  Serial.begin(9600);
  myServo.attach(servoPin);
  myServo.write(0); // Initialize the servo in the unlocked position
}
void loop() {
  char key = keypad.getKey();
  if (key) {
    if (key == '#') {
      // Check the entered Pincode
      if (enteredCode == correctCode) {
        unlockDoor();
      } else {
        Serial.println("Incorrect Pincode. Try again.");
        delay(2000); // Add a delay to discourage brute-force attacks
      }
      enteredCode = ""; // Clear the entered code after each attempt
    } else {
      // Append the pressed key to the entered code
      enteredCode += key;
    }
  }
}
void unlockDoor() {
  Serial.println("Door unlocked!");
  myServo.write(90); // Rotate the servo to lock position
  delay(2000); // Keep the door locked for 2 seconds (adjust as needed)
  myServo.write(0); // Rotate the servo back to unlock position
}
```
## RESULTS:

![image](https://github.com/gokul-sureshkumar/Simulation-project/assets/121148715/0e6450c0-6221-4338-b54e-4d0337f49dd1)

![image](https://github.com/gokul-sureshkumar/Simulation-project/assets/121148715/fdc432bb-132f-4e5f-baed-eaed1505cc69)

![image](https://github.com/gokul-sureshkumar/Simulation-project/assets/121148715/bc61a841-ddf5-48e5-8055-4e86a5dd8493)

![image](https://github.com/gokul-sureshkumar/Simulation-project/assets/121148715/9fe723ca-b24f-4720-a67f-50bcb541f4cc)


![image](https://github.com/gokul-sureshkumar/Simulation-project/assets/121148715/c30e3767-3333-4070-bdb9-00765a6eb057)

![image](https://github.com/gokul-sureshkumar/Simulation-project/assets/121148715/319b2ef3-6db7-4405-9f23-7bfda45df5b9)

![image](https://github.com/gokul-sureshkumar/Simulation-project/assets/121148715/edea6398-99dc-45af-8d91-5cd0377fbbce)

## CONCLUSION:

In conclusion, the Arduino door locking system with a 4-digit Pincode seamlessly merges user-friendly features with heightened security. The 4x4 keypad provides an intuitive interface for users to input a personalized Pincode, while the Arduino efficiently processes and controls the electronic locking mechanism. This system offers a cost-effective and customizable alternative to traditional access control methods.

The 4-digit Pincode enhances security, replacing or complementing physical keys. The Arduino's programmability allows for easy customization, and the electronic locking mechanism adds sophistication. This balance between security and user convenience makes the system suitable for diverse applications.

Future improvements could include additional security features or remote access capabilities. Regular maintenance and updates should be considered to address evolving security needs. In summary, the Arduino door locking system offers a practical, affordable, and secure solution for controlled entry in various environments.


## REFERENCE:

www.chat.openai.com www.youtube.com
