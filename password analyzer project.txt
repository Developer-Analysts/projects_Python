import sys,math,re

def check_password_length(password):

    length = str(len(password))
    global password_length_good

    if len (password) < 8:
        print('[!] password should be at least 8 characters long')
        print(('[!] password is only' ,length, 'character(s) long'))
        password_length_good = False;
    else:
        print(('[*]your password is' ,length, 'characters'))
        password_length_good = True;

def check_password_uppercase(password):
    global UpperLength
    UpperLength = len(re.findall(r'[A-Z]',password))
    print('[*] your password contain' ,UpperLength, 'upper case character(s)')
    if UpperLength == 0:
        print('[!} no Uppercase characters in password')

def check_password_numbers(password):

    global digits
    digits = len(re.findall(r'[0-9]',password))

    print('{*] your password contains' ,digits, 'numeric digit(s)')

    if digits == 0:
        print('[!] no digits in password')

def check_common_passwords(password):

    global matchedPass
    matchedPass = False

    commonPasswords = ['password','rahul','raju','user123','ram','lemon','hacker']

    for commonPass in commonPasswords:

        if commonPass == password:
            matchedPass = True

        if matchedPass == True:
            print('[!] the password given is matched a commonly used password')

def password_eval(password,password_length_good,UpperLength,digits,matchedPass):

    print('\n[*] password evaluation:')

    if password_length_good == True:
        print('[*] password length is good')
    else:
        print('[!] password length is bad')

    if UpperLength >=3:
        print('[*] your password contains a good amount of uppercase letters')
    else:
        print('[!] your password doesn\t enough letters')

    if digits >=3:
        print('[*] your password contains a good amount of numeric digits')
    else:
        print('[!] your password contains a good amount of numeric digits')

    if matchedPass == True:
        print('[!!!] your password cmatches a commonly used password')

    if password_length_good == True and UpperLength >=3 and digits >=3 and matchedPass >= False:
        print('[*] you have a good password')
    else:
        print('[*] your password may be vulnerable - please review the "[!]" warnings and consider a strong password')
        
            
            

def main():
    password = input ('enter your password:')
    check_password_length(password)
    check_password_uppercase(password)
    check_password_numbers(password)
    check_common_passwords(password)
    password_eval(password,password_length_good,UpperLength,digits,matchedPass)
    

if __name__ == '__main__':
    main()
    
