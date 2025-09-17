# INSTAGRAM 
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

# Setup Chrome driver
driver = webdriver.Chrome()
driver.maximize_window()

# Open Instagram login page
driver.get("https://www.instagram.com/accounts/login/")

# Wait until the username field is present (explicit wait)
wait = WebDriverWait(driver, 15)
username_input = wait.until(EC.presence_of_element_located((By.NAME, "username")))
password_input = wait.until(EC.presence_of_element_located((By.NAME, "password")))

# Enter login details
username_input.send_keys("testuser")
password_input.send_keys("password123")

# Click the login button
login_button = driver.find_element(By.XPATH, "//button[@type='submit']")
login_button.click()

# Wait to ensure the page loads after login
time.sleep(10)

# Check if redirected (Optional: Based on what’s loaded post login)
print("Login attempted.")
driver.quit()
