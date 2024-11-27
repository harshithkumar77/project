from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.keys import Keys
import time

opt = webdriver.ChromeOptions()
opt.add_experimental_option('detach',True)
driver = webdriver.Chrome(options=opt)

driver.get("https://fitpeo.com/")
driver.maximize_window()
time.sleep(2)

revenue_calculator_link = driver.find_element('link text', 'Revenue Calculator') # Adjust the locator as needed
revenue_calculator_link.click()
time.sleep(2)

slider_section = driver.find_element('xpath', "/html/body/div[2]/div[1]/div[1]/div[2]/div/div/span[1]/span[1]")  # Replace with the actual ID or locator
driver.execute_script("arguments[0].scrollIntoView();", slider_section)
time.sleep(2)

slider = driver.find_element('xpath', "/html/body/div[1]/div[1]/div[1]/div[2]/div/div/span[1]")  # Replace with the actual slider ID
action = ActionChains(driver)
action.click_and_hold(slider).move_by_offset(820, 0).release().perform()  # Adjust based on slider configuration
time.sleep(2)

text_field = driver.find_element(By.ID, "text-field-id")  # Replace with the actual text field ID
text_field.click()
text_field.clear()
text_field.send_keys("560")
text_field.send_keys(Keys.RETURN)
time.sleep(2)

slider_value = driver.find_element(By.ID, "slider-value-id")  # Replace with the actual slider value ID
assert slider_value.text == "560", "Slider value did not update correctly"

checkbox_ids = ["cpt-99091", "cpt-99453", "cpt-99454", "cpt-99474"]  # Replace with actual checkbox IDs
for checkbox_id in checkbox_ids:
    checkbox = driver.find_element(By.ID, checkbox_id)
    if not checkbox.is_selected():
        checkbox.click()
time.sleep(2)

total_reimbursement = driver.find_element(By.ID, "total-reimbursement-id")  # Replace with the actual ID
assert total_reimbursement.text == "$110700", "Reimbursement value mismatch"

