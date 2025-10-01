package utility;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import io.github.bonigarcia.wdm.WebDriverManager;
import java.time.Duration;

public class OrangeHRM {
    public static void main(String[] args) throws InterruptedException {
        WebDriverManager.chromedriver().setup();
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get("https://opensource-demo.orangehrmlive.com/web/index.php/auth/login");

        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));

        WebElement emailField = wait.until(
            ExpectedConditions.visibilityOfElementLocated(By.xpath("//input[@placeholder='Username']"))
        );
        emailField.sendKeys("Admin"); 
        Thread.sleep(2000);
        WebElement passwordField = wait.until(
            ExpectedConditions.visibilityOfElementLocated(By.xpath("//input[@placeholder='Password']"))
        );
        passwordField.sendKeys("admin123");
        Thread.sleep(2000);
        WebElement loginButton = wait.until(
            ExpectedConditions.elementToBeClickable(By.xpath("//button[normalize-space()='Login']"))
        );
        loginButton.click();
        Thread.sleep(2000);
        System.out.println("Login Done!");
        Thread.sleep(2000);
        WebElement pimButton = wait.until(
                ExpectedConditions.elementToBeClickable(By.linkText("PIM"))
            );
            pimButton.click();
            Thread.sleep(2000);
            WebElement addEmployeesField = wait.until(
                    ExpectedConditions.visibilityOfElementLocated(By.xpath("//a[normalize-space()='Add Employee']"))
                );
            addEmployeesField.click();
            Thread.sleep(2000);
            WebElement firstNameField = wait.until(
                    ExpectedConditions.visibilityOfElementLocated(By.xpath("//input[@placeholder='First Name']"))
                );
                firstNameField.sendKeys("Admin First Name"); 
                Thread.sleep(2000);
                WebElement lastNameField = wait.until(
                        ExpectedConditions.visibilityOfElementLocated(By.xpath("//input[@placeholder='Last Name']"))
                    );
                    lastNameField.sendKeys("Admin Last Name"); 
                    Thread.sleep(2000);
                   
                    WebElement saveButton = wait.until(
                            ExpectedConditions.elementToBeClickable(By.cssSelector("button[type='submit']"))
                        );
                        saveButton.click();
                        Thread.sleep(3000);
                        WebElement dropDownButton = wait.until(
                                ExpectedConditions.elementToBeClickable(By.cssSelector(".oxd-icon.bi-caret-down-fill.oxd-userdropdown-icon"))
                            );
                            dropDownButton.click();
                            Thread.sleep(2000);
                          
                            WebElement logOutButton = wait.until(
                                    ExpectedConditions.elementToBeClickable(By.xpath("(//a[normalize-space()='Logout'])[1]"))
                                );
                                logOutButton.click();
                                Thread.sleep(2000);
        driver.quit();
    }
}
