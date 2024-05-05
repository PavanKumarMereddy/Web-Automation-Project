# Automated Testing of a Web Application using Selenium WebDriver

## Table of Contents:
1.	Introduction
2.	Objective
3.	Prerequisites
4.	Technologies Used
5.	Project Setup
6.	Test Scenarios
7.	Test Cases
8.	Implementation Details
9.	Testing Strategy
10.	Conclusion
11.	Future Enhancements
12.	References
    
## 1. Introduction:
This document provides an overview of the automated testing project for [Web Application Name]. The purpose of this project is to automate the testing process to ensure the quality and reliability of the web application.

## 2. Objective:
The main objective of this project is to automate the testing of key functionalities of the web application using Selenium WebDriver. By automating the testing process, we aim to improve efficiency, reduce manual effort, and ensure faster feedback on software quality.

## 3. Prerequisites:
+ Python 3.x
+ Selenium WebDriver
+ Web Browser (Chrome)
+ WebDriver executable (ChromeDriver)
+ IDE or Text Editor (e.g., PyCharm, VS Code)

## 4. Technologies Used:
+ Selenium WebDriver
+ Python
+ ChromeDriver (for Chrome browser automation)

## 5. Project Setup:
+ Install Python from the official website.
+ Install Selenium WebDriver using pip: pip install selenium.
+ Download the WebDriver executable for the desired browser and set its path in the system environment variables.
+ Clone the project repository from [GitHub Link].
+ Open the project in your preferred IDE or text editor.

## 6. Test Scenarios:
+ User Login
+ Product Search
+ Add to Cart
+ Checkout Process
+ Account Management

## 7. Test Cases:
+ TC01: Verify user login with valid credentials.
+ TC02: Verify error message for invalid login credentials.
+ TC03: Verify product search functionality.
+ TC04: Verify adding a product to the cart.
+ TC05: Verify checkout process for a guest user.
+ TC06: Verify account creation process.

## 8. Implementation Details:
+ Utilize Selenium WebDriver to interact with web elements.
+ Use Page Object Model (POM) design pattern for better code organization and maintenance.
+ Handle different types of locators (e.g., ID, Name, XPath) for element identification.
+ Implement explicit waits to handle dynamic elements and ensure synchronization.
+ Log test execution details for debugging and reporting purposes.

## 9. Testing Strategy:
+ Create comprehensive test cases covering all critical functionalities of the web application.
+ Execute tests on different browsers and platforms to ensure cross-browser compatibility.
+ Run tests in parallel to save time and increase test coverage.
+ Integrate with CI/CD pipelines for automated test execution.

## Selenium with Python Integration:
```
# Importing Packages
import time
from selenium import webdriver
from selenium.webdriver import Keys, ActionChains
from selenium.webdriver.common.by import By
from selenium.webdriver.support.select import Select

# Invoking Web Browser
driver = webdriver.Chrome()
driver.get("https://demo.nopcommerce.com/")
driver.maximize_window()

# Dropdown1
dropdown1 = driver.find_element(By.XPATH, "//select[@id='customerCurrency']")
select = Select(dropdown1)
select.select_by_index(1)

# Register
driver.find_element(By.CSS_SELECTOR, ".ico-register").click()
driver.find_element(By.ID, "gender-male").click()
driver.find_element(By.ID, "FirstName").send_keys("Pavan")
driver.find_element(By.ID, "LastName").send_keys("Reddy")
time.sleep(1)

# Register
# Dropdown2
dropdown2 = driver.find_element(By.CSS_SELECTOR, "select[name='DateOfBirthDay']")
dropdown2.click()

select = Select(dropdown2)
select.select_by_index(5)

# Dropdown3
dropdown3 = driver.find_element(By.CSS_SELECTOR, "select[name='DateOfBirthMonth']")
dropdown3.click()
select = Select(dropdown3)
select.select_by_index(2)

# Dropdown4
dropdown4 = driver.find_element(By.CSS_SELECTOR, "select[name='DateOfBirthYear']")
dropdown4.click()
select = Select(dropdown4)
select.select_by_value("2002")

# Email
driver.find_element(By.ID, "Email").send_keys("demo310@gmail.com")
actions = ActionChains(driver)
actions.send_keys(Keys.PAGE_DOWN).perform()

# Password
driver.find_element(By.ID, "Password").send_keys("Demo@123")
driver.find_element(By.ID, "ConfirmPassword").send_keys("Demo@123")

# Submit
Submit = driver.find_element(By.ID, "register-button")
Submit.click()
driver.implicitly_wait(5)

# Logout
Logout = driver.find_element(By.CSS_SELECTOR, ".ico-logout")
Logout.click()

# Login
driver.find_element(By.CSS_SELECTOR, ".ico-login").click()
driver.find_element(By.CSS_SELECTOR, ".email").send_keys("demo310@gmail.com")
driver.find_element(By.ID, "Password").send_keys("Demo@123")
RememberMe = (driver.find_element(By.ID, "RememberMe"))
RememberMe.click()
Login = (driver.find_element(By.XPATH, "//button[@class='button-1 login-button']"))
Login.click()

# Computers
driver.find_element(By.LINK_TEXT, "Computers").click()
driver.find_element(By.LINK_TEXT, "Desktops").click()
driver.find_element(By.XPATH, "//a[text()='Digital Storm VANQUISH 3 Custom Performance PC']").click()
driver.find_element(By.ID, "add-to-cart-button-2").click()
driver.implicitly_wait(1)
Message = driver.find_element(By.CSS_SELECTOR, ".content")
print(Message.text)
actions = ActionChains(driver)
actions.send_keys(Keys.PAGE_UP).perform()
time.sleep(3)
driver.find_element(By.CSS_SELECTOR, ".ico-cart").click()
driver.find_element(By.CSS_SELECTOR, "#termsofservice").click()
driver.find_element(By.ID, "checkout").click()
time.sleep(1)

# Filling Billing Address
driver.find_element(By.ID, "BillingNewAddress_Company").send_keys("Centella AI Therapautics")
dropdown5 = driver.find_element(By.ID, "BillingNewAddress_CountryId")
dropdown5.click()
select = Select(dropdown5)
select.select_by_value("133")
driver.find_element(By.ID, "BillingNewAddress_City").send_keys("Hyderabad")
driver.find_element(By.ID, "BillingNewAddress_Address1").send_keys("Kukatpally")
driver.find_element(By.ID, "BillingNewAddress_ZipPostalCode").send_keys("500085")
driver.find_element(By.ID, "BillingNewAddress_PhoneNumber").send_keys("1234567890")
Continue = driver.find_element(By.XPATH, "//*[@id='billing-buttons-container']/button[2]")
Continue.click()
time.sleep(2)

# Shipping Method
driver.find_element(By.ID, "shippingoption_1").click()
Continue2 = driver.find_element(By.XPATH, "//*[@id='shipping-method-buttons-container']/button")
Continue2.click()
time.sleep(2)

# Payment Mode
driver.find_element(By.ID, "paymentmethod_0").click()
Continue3 = driver.find_element(By.XPATH, "//*[@id='payment-method-buttons-container']/button")
Continue3.click()
time.sleep(2)

# Payment Info
driver.find_element(By.XPATH, "//*[@id='payment-info-buttons-container']/button").click()
time.sleep(2)

# Confirm Order
Confirm = driver.find_element(By.XPATH, "//*[@id='confirm-order-buttons-container']/button")
Confirm.click()
actions = ActionChains(driver)
actions.send_keys(Keys.PAGE_DOWN).perform()

Message2 = driver.find_element(By.XPATH, "//*[@id='main']/div/div/div/div[1]/h1")
print(Message2.text)

Message3 = driver.find_element(By.XPATH, "//*[@id='main']/div/div/div/div[2]/div/div[1]/strong")
print(Message3.text)

Message4 = driver.find_element(By.XPATH, "//*[@id='main']/div/div/div/div[2]/div/div[2]/div[1]/strong")
print(Message4.text)

Continue4 = driver.find_element(By.XPATH, "//*[@id='main']/div/div/div/div[2]/div/div[3]/button")
Continue4.click()

# Log Out
driver.find_element(By.CSS_SELECTOR, ".ico-logout").click()

# Closing the Browser
driver.close()
```
## 10. Conclusion:
The automated testing project using Selenium WebDriver has significantly improved the testing process for the [Nope Commerce Demo]. By automating repetitive tasks and executing tests efficiently, we can ensure faster delivery of high-quality software.

## 11. Future Enhancements:
+ Implement API testing for backend services.
+ Integrate with cloud-based testing platforms for scalability.
+ Enhance test coverage by adding more test scenarios.
+ Implement performance testing to assess application response times.

## 12. References:
+ Selenium Official Documentation: [https://www.selenium.dev/documentation/webdriver/]
+ Python Official Documentation: [https://docs.python.org/3/]
+ WebDriver Downloads: [https://www.selenium.dev/downloads/]
+ Page Object Model (POM) Pattern: [https://www.browserstack.com/guide/page-object-model-in-selenium]

