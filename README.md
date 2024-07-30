# Selenium-Mini--Project
In this selenium mini project you will be able to 
1) Launch Browser And Website
2) Find Web Elements And Provide Actions
3) Take Screenshots
4) Close the browser

   CODE
   -----------------------------------------------------------
   package home;

import java.io.File;
import java.io.IOException;
import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.io.FileHandler;

public class Login {

	public static void main(String[] args) throws InterruptedException, IOException {
		// TODO Auto-generated method stub
		
		// Step 1: Launch Browser And Website
		System.setProperty("webdriver.chrome.driver", "Browser/chromedriver.exe");
		WebDriver driver = new ChromeDriver();
		driver.get("https://opensource-demo.orangehrmlive.com/web/index.php/auth/login");
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
		
		//Step 2: Find Web Elements And Provide Actions
		Thread.sleep(4000);
		WebElement username = driver.findElement(By.name("username"));
		username.sendKeys("Admin");
		
		WebElement password = driver.findElement (By.name("password"));
		password.sendKeys("admin123");
		
		WebElement loginBtn = driver.findElement(By.xpath("//button[@class = 'oxd-button oxd-button--medium oxd-button--main orangehrm-login-button']"));
		loginBtn.click();
		
		//Step 3: Take Screenshot
		Thread.sleep(5000);
		
		File source = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
		File dest = new File("ScreenShot\\test_1.png");
		
		FileHandler.copy(source, dest);
		
		//Step 4: Close The Browser
		System.out.println("Test Scenario is successfully tested");
		driver.close();
		driver.quit();
		
		
	}
	
}

