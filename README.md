# Password-generator-
#It generates any password between 8 and 16 digits inclusive , containing a random amount of numbers ,symbols  and characters . Ensures difficulty in an attempt to brute force break the password. To be executed using python.
import random
symbolsavailable=["*",",","(",")","'","!","$","@","~",".","<",">","?","/","|"]#some may not be compatible with certain password requests
NOOFSYMBOLS=len(symbolsavailable)

def choose_length():
    length=random.randint(8,16)
    return length
def assign_amount_of_types(length):
    left=length
    digits=0#1
    letters=0#2
    symbols=0#3
    valid=False
    while valid==False:
        for i in range(length):
            choice=random.randint(1,3)
            if choice==1:
                digits+=1
            elif choice==2:
                letters+=1
            else:
                symbols+=1
            if symbols>=1 and letters>=1 and digits>=1:
                valid=True
    
    amounts=[digits,letters,symbols]
    return amounts
def create(noofeach,lengthofpass):
    numbers=noofeach[0]#1
    chars=noofeach[1]#2
    symbs=noofeach[2]#3
    capital=False
    password=""
    correct=False
    while correct==False:
        spacesleft=lengthofpass
        while spacesleft>0:
            value=random.randint(1,3)
            if value==1 and numbers!=0:
                numbers-=1
                password+=chr(random.randint(48,57))
                spacesleft-=1
            elif value==2 and chars!=0:
                capitalorlower=random.randint(1,2)
                data=chr(random.randint(65,90))
                if capitalorlower==1:
                    data=data.lower()
                if capitalorlower==2 and capital!=True:
                    capital=True
                spacesleft-=1
                
                password+=data
            elif value==3 and symbs!=0:
                symbolchoosen=symbolsavailable[random.randint(0,NOOFSYMBOLS-1)]
                password+=symbolchoosen
                spacesleft-=1
            else:
                #no more of the specific type left
                pass
        if capital==True:
            correct=True
    return password
lengthofpasswordneeded=choose_length()
noofeachtypeneeded=assign_amount_of_types(lengthofpasswordneeded)
createdpassword=create(noofeachtypeneeded,lengthofpasswordneeded)
print("password has been made")
ready=input("press 1 to reveal")
if ready=="1":
    print("----------------------")
    print("     |CONFIDENTIAL|   ")
    print("     ",createdpassword,"   ")
    print("----------------------")

    
                
                
        
        
        
