import random
import string
import time
import names
from threading import Thread
from selenium import webdriver
import colorama
from colorama import Fore, Back, Style
colorama.init()

print('''
 __          __   _                      _                                               
 \ \        / /  | |                    | |                                              
  \ \  /\  / /_ _| |_ __ ___   __ _ _ __| |_                                             
   \ \/  \/ / _` | | '_ ` _ \ / _` | '__| __|                                            
    \  /\  / (_| | | | | | | | (_| | |  | |_                                             
     \/  \/ \__,_|_|_| |_| |_|\__,_|_|   \__|___                           _             
     /\                            | |    / ____|                         | |            
    /  \   ___ ___ ___  _   _ _ __ | |_  | |  __  ___ _ __   ___ _ __ __ _| |_ ___  _ __ 
   / /\ \ / __/ __/ _ \| | | | '_ \| __| | | |_ |/ _ \ '_ \ / _ \ '__/ _` | __/ _ \| '__|
  / ____ \ (_| (_| (_) | |_| | | | | |_  | |__| |  __/ | | |  __/ | | (_| | || (_) | |   
 /_/    \_\___\___\___/ \__,_|_| |_|\__|  \_____|\___|_| |_|\___|_|  \__,_|\__\___/|_|   
                                                                                                                                                                                
''')

print("Please Wait...")
filler= input("Press Enter")
accounts_number =int(input("How many accounts would like to create: "))
catchall= input("Please input your catchall domain: ")
password= input("Please input the password you would like to use: ")


def main(accounts_number):
    print("Let's Go!!")
    
    chromedriver = [chromedriver_win32.zip](https://github.com/coolkid1234Q/vvvv/files/11537829/chromedriver_win32.zip)

    driver = webdriver.Chrome(chromedriver)
    driver.get("https://www.walmart.com/account/signup?ref=domain")
    
    first_name = '//*[@id="first-name-su"]'
    last_name = '//*[@id="last-name-su"]'
    email = '//*[@id="email-su"]'
    password_location = '//*[@id="password-su"]'
    create_account = '//*[@id="sign-up-form"]/button[1]'
    randomname = ''.join([random.choice(string.ascii_letters + string.digits) for n in range(10)])
    emails = randomname + "@" + catchall

    time.sleep(2)
    print(Fore.YELLOW + 'Filling in Info')
    driver.find_element_by_xpath(first_name).send_keys("John")
    driver.find_element_by_xpath(last_name).send_keys("Jay")
    driver.find_element_by_xpath(email).send_keys(emails)
    driver.find_element_by_xpath(password_location).send_keys(password)
    driver.find_element_by_xpath(create_account).click()
    time.sleep(2.5)
    print(Fore.GREEN + 'Account Created!!')
    time.sleep(4)
    driver.quit()
for i in range(accounts_number):
    t = Thread(target=main, args=(i,))
    t.start()
    
