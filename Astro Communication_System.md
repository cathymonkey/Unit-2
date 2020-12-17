# Astro Communication System 
### Created by Kien Le Trung, Timur Garifullin, Chengyu Fan


## Criteria A: Planning
### Context of the product
We are creating a communication system that could send and receive messages between Earth and arguably any planet. In our case, we are designing our system for austronauts on the moon. The system lets austronaut push buttons to send their messages in English. The system will then convert this into Morse code to show these message through a LED light. Morse-English translating system created by other developers could then be used to read the messages the austronat sent from our system.


#### Sketches of Ideas
![](https://github.com/BrightChanges/Unit-2/blob/main/IMG_1067.JPG)
Fig.1 Our sketch for how our system looks like


## Criteria B: Design
#### System Diagram
Image...
Fig.2 The system diagram of our program

#### Flow Diagram
![](https://github.com/BrightChanges/Unit-2/blob/main/Astro%20Commun%20Syst%20Flow%20chart.png)
Fig.3 Flow diagram of our complete system
(Link to our Flow Diagram online: https://app.lucidchart.com/lucidchart/invitations/accept/c567ebac-a171-4df8-b23b-e091a7f7a6d5)


## Criteria C: Development
1st development story:....

#### Codes (so far):

```.py

// include the library code:
#include <LiquidCrystal.h>

const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 10, d7 = 9;
const int but_A = 2;
const int but_B = 3;

int ButB_status = 0;
int row_changed = 0;

String letters[] = {"a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"};
String numbers[] = {"0","1","2","3","4","5","6","7","8","9"};
String commands[] = {"_","D","S"}; 

int letter_showing = 0;
int number_showing = 0;


//Mode 2 var
int ButB_status2 = 0;
int reset = 0;
int command_showing = 0;
int mode = 1; //0 - mode 1, 1 - mode 2
//


LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
String msg = "";


//Custom character - arrow
byte arrow[8] = {
  0b00000,
  0b00100,
  0b01110,
  0b10101,
  0b00100,
  0b00100,
  0b00100,
  0b00000
};


void setup() {
  Serial.begin(9600);

  //Setup message:
  lcd.begin(16, 2);
  lcd.print("Initializing...");
  delay(800);
  lcd.setCursor(0,1);
  lcd.print("Welcome");
  delay(1000);
  lcd.clear();

  //Setup interruptions
  attachInterrupt(0,buttonA, RISING); //Pin 2
  attachInterrupt(1,buttonB, RISING); //Pin 3
  
  lcd.createChar(0,arrow);
  lcd.setCursor(0, 1);  

  //For mode 2
  lcd.setCursor(3,1); //ButB_status2 = 0
  lcd.print("_"); // show space function
}

void loop(){

  lcd.setCursor(0,1);
  lcd.write(arrow[0]);  
  lcd.setCursor(1,1);
  lcd.print("C");
  lcd.setCursor(2,1);
  lcd.print(":");
  lcd.setCursor(4,1);
  lcd.print(":");
 

  
 //Normally scrolling through the alphabet
 if(ButB_status == 0){
    //Selector scrolling
   	lcd.setCursor(0,0);
    lcd.print(letters[letter_showing]);
   
    //Rest of the alphabet
    lcd.setCursor(2,0);
    for(int i=letter_showing+1; i<26;i++){
         lcd.print(letters[i]);
    }
  }
  
  
  
  //First press of the button
  //Go to letter "O"
  if(ButB_status == 1){
    Serial.println("ButB_Status = 1");  
    
    //Selector scrolling
    lcd.setCursor(0,0);
    lcd.print(letters[letter_showing]);
    
    //Rest of the alphabet
    lcd.setCursor(2,0);
    for(int i=letter_showing+1; i<26;i++){
         lcd.print(letters[i]);
    }

  }
  
  
  //Second press
  //Show and scroll through the numbers
  if(ButB_status == 2){
    //Selector scrolling
    
    lcd.setCursor(0,0);
   
    lcd.print(numbers[number_showing]);
    
    //Rest of the numbers
    lcd.setCursor(2,0);
    for(int n = number_showing+1; n < 10; n++){
      	lcd.print(numbers[n]);
    }
  }
  
  
    //print next character
    letter_showing++; 
    number_showing++;
  //Serial.print("Letter showing = ");
  //Serial.println(letter_showing);
  
   //reset the alphabet(letter array)
   if(letter_showing == 27){
      letter_showing = 0;
   } 
  
   //reset numbers(numbers array)
   if (number_showing > 10){
        number_showing = 0;
    }

  if(ButB_status == 1&& letter_showing >27){
    letter_showing = 14; 
   }

  
// Button B Mode 1
    //Make a delay if the row changed
    if(row_changed == 1){
        delay(2000);
        row_changed = 0;
    }


    //time between each character
    delay(1000);
 
   lcd.clear();
 
  
    //show the current message
    lcd.setCursor(5,1);
    Serial.println(msg);
    lcd.print(msg);
   

// Codes for BUTTON B IN MODE 2 
  // Changing the commands per click of Button B in mode 2
 if(mode == 1){
   if(ButB_status2 == 0 && reset == 1){
      lcd.clear();
      reset = 0;
  	  command_showing = 0; 
      Serial.println("command_showing = _ ");
      Serial.println(command_showing); 
      lcd.setCursor(3,1);
      lcd.print(commands[command_showing]); //show space function
  }
}   
 Serial.println(ButB_status2); 
}


//Functions:

void buttonA(){
  
  if(mode == 0){
   Serial.println("ButtonA in mode 1 was pressed");
  
    if(ButB_status == 2){
    	 msg += numbers[number_showing-1];
   } 
   else{
    msg += letters[letter_showing-1];
 	lcd.setCursor(5,1);
  	Serial.println(msg);
  	lcd.print(msg);
    }
  }  
  

if(mode == 1){
  Serial.println("ButtonA in mode 2 was pressed");
  Serial.println(command_showing);
  
  if(command_showing == 0){
      msg += " ";
      lcd.print(msg);
    }
  if(command_showing == 1){
      msg.remove(msg.length()-1);
      lcd.print(msg);
    }
   
   if(command_showing == 2){
      Serial.println("Sending");
      msg = " ";
      lcd.print(msg); 
    }
}
  
} //End void
void buttonB(){
  
  
//Mode 1  
if(mode == 0){
   //Change the row.
    ButB_status ++;
    row_changed ++;
  

  if(ButB_status == 1){
    letter_showing = 14; 
   }
  if(ButB_status == 2){
    number_showing = 0;
  }
     
     
  if(ButB_status == 3){
      letter_showing = 0;
      ButB_status = 0;
    }
} 
  
  
//Mode 2    
if(mode == 1){
  ButB_status2++;
  //check if the mode is 2
  Serial.println(" Mode 2 ");
  Serial.print("ButB_status2 = ");  
  Serial.println(ButB_status2);  
    
  if(ButB_status2 == 1){
      lcd.clear();
      command_showing++; 
      Serial.println("command_showing = D");
      Serial.println(command_showing); 
      lcd.setCursor(3,1);
      lcd.print(commands[command_showing]); //show delete function
  }                        
  if(ButB_status2 == 2){ 
      lcd.clear();
      command_showing++;
      Serial.println("command_showing = S");
      Serial.println(command_showing);
      lcd.setCursor(3,1);
      lcd.print(commands[command_showing]); //show send function
    }
  if(ButB_status2 == 3){
      lcd.clear();
      command_showing = 0;
      ButB_status2 = 0;
      reset++;
      Serial.println("reset");
      Serial.println(command_showing);
	}
  }
  
  
}

```
2st development story:....

![](https://github.com/BrightChanges/Unit-2/blob/main/Astro_arrays.png)
Fig.3 Our system model on TinkerCad

## Criteria D: Functionality
#### Real-life program
Link to the desmontration video:....
Picture of our program:

Image...
Fig.4

Image...
Fig.5


## Criteria E: Evaluation

##### Success Criteria
| Criteria:                                                                                                      | Expected outcome                                                                                                   | Met? |
|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|------|
| Criteria 1: The user should be able to input  alphabetic characters and numbers(0-9).                          | You are able to input alphabetic characters  and numbers(0-9) into the system.                                     |      |
| Criteria 2: It should output the user's message  on the LCD and through with light(Using Morse code)           | You are able to see how your message is  outputed on the LCD and the light is blinking  according to a Morse code. |      |
| Criteria 3: It should let the user use the  following commands: send message, delete,  space, repeat, confirm. | You are able to use the following commands:  send message, delete, space, repeat, confirm.                         |      |
| Criteria 4: It should provide an instruction set.                                                              | You are able to see how to use our system with  different button combinations.                                     |      |
| Criteria 5: It should let the user type at least 10 words in 1 minute                                          | You are able to type at least 10 words in 1 minute.                                                                |      |
| Criteria 6: It should contain at most  2 buttons and 1 LED.                                                    | You are able to see that our system contains at most 2 buttons and 1 button.                                       |      |


