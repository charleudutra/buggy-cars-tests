# 2.buggy-cars-tests
Testes automatizados com Selenium para o site Buggy Cars Rating

from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()

driver.get("https://buggy.justtestit.org/register")
driver.maximize_window()

time.sleep(2)

username = "usuario" + str(int(time.time()))
driver.find_element(By.ID, "username").send_keys(username)
driver.find_element(By.ID, "firstName").send_keys("Teste")
driver.find_element(By.ID, "lastName").send_keys("Automatizado")
driver.find_element(By.ID, "password").send_keys("Senha123!")
driver.find_element(By.ID, "confirmPassword").send_keys("Senha123!")

driver.find_element(By.XPATH, "//button[text()='Register']").click()

time.sleep(2)

mensagem = driver.find_element(By.CLASS_NAME, "result").text

if "Registration is successful" in mensagem:
    print("✅ Teste de registro passou!")
else:
    print("❌ Teste de registro falhou!")

driver.quit()
