# Contact-app
BY using data structures, string, regex & files. Lets use all our newly acquired knowledge to build a contact app, just like the ones in our smartphone.

We will not be building a fancy UI, instead we will focus on understanding the programming logic.

Lets get started!

Think of all the features that your contact app has . . . !

It can show you all the contact names
You can search for contacts (using name)
You can see all the information associated with the contact
You can delete and update contacts
Can you think of anything more ? Our contact app should have at least these features.

The app should show us all the contact names
It should allow us to select a contact and view all the information associated with the contact
It should allow us to update contact info & delete contact
Finally, it should show us all the contact names
For every contact, we will store the name, number & email.

Data Structure
The very first thing that we need to decide is "What data structure to use?"

To store all the contacts, we can use a list of dictionaries; were each dictionary stores the name, number & email of the contact.

# Create a list of dictionaries called contacts with 3 dummy contacts.

```
contacts = [{'name':'mayur','number':9876543210,'email':'mayur@gmail.com'},
            {'name':'harsh','number':9876543210,'email':'harsh@gmail.com'},
            {'name':'raj','number':9876543210,'email':'raj@gmail.com'}]
```

```
contacts[0]['name']
```
List all contact names
Write show_contacts function that takes the contacts list and prints all the contact names. These names will help us to select the contact later.

```
def show_contacts(contacts):
    for i in contacts:
        print(i)
```

```
show_contacts(contacts)
```
{'name': 'mayur', 'number': 9876543210, 'email': 'mayur@gmail.com'}
{'name': 'harsh', 'number': 9876543210, 'email': 'harsh@gmail.com'}
{'name': 'raj', 'number': 9876543210, 'email': 'raj@gmail.com'}

 # Add a new Contact
Write add_contact function that takes user input and adds new contact dictionary to the existing list of contacts.

```
def add_contact(contacts,n):
    name=input("Enter your name")
    mobile=str(input("Enter your number: "))
    email=input("Enter your email")
    contacts.append({'name':name,'number':mobile,'email':email})
```
add_contact(contacts,4)

# Delete Contact
Write delete_contact function to delete an existing contact by providing name of the contact which we want to delete.

```
def delete_contact(contacts, name):
    for i,j in enumerate (contacts):
        if j['name']== name:
            del contacts[i]
```

```
name = ''
delete_contact(contacts, name)
```
NameError                                 Traceback (most recent call last)
Cell In[10], line 1
----> 1 delete_contact(contacts, name)

NameError: name 'delete_contact' is not defined

 # Update Contact details
Let's write update_contact function which will update contact details such as name, email & number. The functions should take contacts and name as arguments. It should also print the newly added contact.
```
def update_contact(contacts, name):
    for i,j in enumerate(contacts):
        if j['name']== name:
            name=input()
            mobile=str(input())
            email=input()
            contacts[i]['name'] = name
            contacts[i]['number'] = mobile
            contacts[i]['email'] = email
```


name = ''
update_contact(contacts, name)


# Open Contact
open_contact function takes the contacts list and a name string as input. It prints the contact details if name matches some contact name in the contacts list, else prints No match found!.

Note: The functions should be case insensitive.

```
def open_contact(contacts, name):
    for i in contacts:
        if i['name']== name:
            print(i)
    if i['name'] != name:
        print("NO match")
```
name = ''
open_contact(contacts, name)

We often see update & delete options after we open a particular contact. It would be great if we can also implement the same.

After opening the contact, the program should wait for user input. The user can press u to update & d delete contact. Any other key press should be ignored

Write the updated open_contact function below

```
def open_contact(contacts, name):
    for i in contacts:
        if i['name']== name:
            update=input()
            if update=='u':
                update_contact(contacts, name)
            elif update=='d':
                delete_contact(contacts, name)
```

name = ''
open_contact(contacts, name)

 # Complete application (using all the above functions in use)
We will use an infinite loop to encapsulate our application logic and break only when q is pressed. We will use clear_output() function from IPython.display to clear the output before printing anything new.

Below is the pseudo-code to help you build the application logic.

```
from IPython.display import clear_output

contacts = [{'name':'mayur','number':9876543210,'email':'mayur@gmail.com'},
            {'name':'harsh','number':9876543210,'email':'harsh@gmail.com'},
            {'name':'raj','number':9876543210,'email':'raj@gmail.com'}]

def show_contacts(contacts):
    for i in contacts:
        print('\n', i)

        
def add_contact(contacts):
    name=input("Enter your name: ")
    mobile=str(input("Enter your number: "))
    email=input("Enter your Email: ")
    contacts.append({'name':name,'number':mobile,'email':email})
    

def open_contact(contacts):
    name=input("Enter your name to open: " )
    for i in contacts:
        if i['name']== name:
            print(i)


def update_contact(contacts):
    name=input("Enter your name for update: " )
    if contacts['name']== name:
        for i,j in enumerate(contacts):
        
           name=input("Enter Your Name: ")
           mobile=str(input("Enter your number: "))
           email=input("Enter your Email: ")
           contacts[i]['name']=name
           contacts[i]['number']=mobile
           contacts[i]['email']=email

def delete_contact(contacts):
    name=input("Enter your name for delet: " )
    for i,j in enumerate (contacts):
        if j['name']==name:
            del contacts[i]       

        
while True: 
    action = input("Press 'a' - add contact, 'o' - open contact, 'u' - update cotact, 'd' - delet contact, 'q' - quit")
    
    if action == 'a':
        add_contact(contacts)
        show_contacts(contacts)
        break
    
    elif action == 'o':
        open_contact(contacts)
        break
        
                    
    elif action == 'u':
        update_contact(contacts)
        show_contacts(contacts)
        break
    
    elif action == 'd':
        delete_contact(contacts)
        show_contacts(contacts)
        break
        
    elif action == 'q':
        break
    
    else:
        print( 'incorrect choice')
```
# Using files
One major problem with the above approach is "persistent storage". Every time you close this notebook, all the new contacts are lost. This happens because contacts is a python variable. Its lives inside python session. As soon as the session is killed/terminated, all the varibles are also deleted.

To address this problem, we will have to use save the contacts in a disk. What better reason to use files? Instead of using list of dictionary, use file to save the contacts.

Save every new contact in a new-line and use " , " to separate the contact fields. This is how the above contacts should look, when saved in a file.

rushikesh, rushikesh@gmail.com, 9876543210
mayur, mayur@gmail.com, 9876543210
vivek, vivek@gmail.com, 9876543210
You task is to make appropriate changes to the above code to use contacts.txt instead of using contacts list.

Using Regex
Yet another problem with our app is "lack of validation". While creating a new contact, user is free to enter anything. But why is that a problem?

Input validation is important to ensure only properly formed data is entering the workflow in an information system, preventing malformed data from persisting in the database and triggering malfunction of various downstream components. Input validation should happen as early as possible in the data flow, preferably as soon as the data is received. source

The above paragraph is the complete gist of Input validation. Read it again & ponder for a minute. Its an important concept when building customer facing applications. We would highly recommend you to Google and read more about it.

Use regular expression to validate user input (before you save it to the file). Implement the following:

Name should be all alphabets. " " should also be allowed.
For email refer regex chapter from course material.
Number should have 10 digits. Not less, not more. Also, not alphabets should be allowed.
Add a new field DOB to each contact. It should follow YYYY-MM-DD format. Then write a regular expression to validate it. Remember, date & month cannot be greater that 31 & 12, respectively.
Can you think of any more validations?

We really hope you had a wonderful time building this applications. This is how applications are developed in really life. You start with a set of basic functionalities and then you keep adding new features (like persistent storage & validation). As the application grows in size, you might encounter new problems to solve.
