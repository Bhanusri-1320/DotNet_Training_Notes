```c#
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Interactions;
using OpenQA.Selenium.Support.UI;
using SeleniumExtras.WaitHelpers;

namespace Assignment_1
{
     class AmazonAddToCart
    {
        [Test]
        public void amazonAddToCartTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://www.amazon.in/");
            driver.Manage().Window.Maximize();

            Actions action = new Actions(driver);
            IWebElement search = driver.FindElement(By.XPath("//input[@placeholder='Search Amazon.in']"));
            action.SendKeys(search, "Noise Twist Go Round dial Smartwatch");
            IWebElement searchButton = driver.FindElement(By.Id("nav-search-submit-button"));
            action.MoveToElement(searchButton).Click().Perform();

            // find the element
            IWebElement product = driver.FindElement(By.XPath("//span[text()='Noise Twist Go Round dial Smartwatch with BT Calling, 1.39\" Display, Metal Build, 100+ Watch Faces, IP68, Sleep Tracking, 100+ Sports Modes, 24/7 Heart Rate Monitoring (Gold Link)']"));
            // scroll unit the element is visible
            //((IJavaScriptExecutor)driver).ExecuteScript("arguments[0].scrollIntoView(true);", product);
            action.MoveToElement(product).Perform();



            // Define FluentWait
            DefaultWait<IWebDriver> fluentWait = new DefaultWait<IWebDriver>(driver)
            {
                Timeout = TimeSpan.FromSeconds(20),
                PollingInterval = TimeSpan.FromMilliseconds(500)
            };

            IWebElement addToCart = fluentWait.Until(ExpectedConditions.ElementToBeClickable(By.XPath("//span[text()='Noise Twist Go Round dial Smartwatch with BT Calling, 1.39\" Display, Metal Build, 100+ Watch Faces, IP68, Sleep Tracking, 100+ Sports Modes, 24/7 Heart Rate Monitoring (Gold Link)']//ancestor::div[@class='puisg-col puisg-col-4-of-4 puisg-col-4-of-8 puisg-col-8-of-12 puisg-col-8-of-16 puisg-col-12-of-20 puisg-col-12-of-24 puis-list-col-right']//button")));
            // find the add to cart button
            // click on it 
            //((IJavaScriptExecutor)driver).ExecuteScript("arguments[0].click();", addtoCart);
            action.MoveToElement(addToCart).Click().Perform();

            // view Cart
            IWebElement viewCart = driver.FindElement(By.CssSelector("#nav-cart"));
            action.MoveToElement(viewCart).Click().Perform();
        }
    }
}


////////////////////////////////////////////////////////////////////////////////////////////////
/// 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;

namespace Assignment_1
{
     class ContactUsForm
    {
        [Test]
        public void ContactUsFormTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            //defining IJavaScriptExecutor
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;

            // using implict wait
            driver.Manage().Timeouts().ImplicitWait = TimeSpan.FromSeconds(10);

            // click on contactUs 
            IWebElement contactUs = driver.FindElement(By.XPath("//a[contains(text(),' Contact us')]"));
            js.ExecuteScript("arguments[0].click();", contactUs);

            // enter name
            IWebElement name = driver.FindElement(By.XPath("//input[@placeholder='Name']"));
            js.ExecuteScript("arguments[0].value='user';", name);

            //enter emial
            IWebElement email = driver.FindElement(By.XPath("//input[@placeholder='Email']"));
            js.ExecuteScript("arguments[0].value='user1218@gmail.com';", email);


            // enter subject
            IWebElement subject = driver.FindElement(By.XPath("//input[@placeholder='Subject']"));
            js.ExecuteScript("arguments[0].value='testing the contact us form!';", subject);

            // enter message
            IWebElement message = driver.FindElement(By.XPath("//textarea[@placeholder='Your Message Here']"));
            js.ExecuteScript("arguments[0].value='message for testing the contact us form';", message);

            // click on submit
            IWebElement submit = driver.FindElement(By.XPath("//input[@value='Submit']"));
            ((IJavaScriptExecutor)driver).ExecuteScript("arguments[0].click();", submit);

            // handling alert
            IAlert alert = driver.SwitchTo().Alert();
            alert.Accept();
        }
    }
}

///////////////////////////////////////////////////////////////////

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;

namespace Assignment_1
{
     class Login
    {
        // login with valid details
        [Test]
        public void LoginTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();
            // finding the signup button and clicking
            IWebElement signUp = driver.FindElement(By.XPath("//a[text()=' Signup / Login']\r\n"));
            signUp.Click();

            // entering user name
            IWebElement name = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::input[@name='email']"));
            name.SendKeys("user1218@gmail.com");

            //email
            IWebElement email = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::input[@name='password']"));
            email.SendKeys("User@12345");

            // click signup button
            IWebElement loginButton = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::button[text()='Login']"));
            loginButton.Click();
        }

        // login with invalid details
        [Test]
        public void LogInTest_Invalid()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();
            // finding the signup button and clicking
            IWebElement signUp = driver.FindElement(By.XPath("//a[text()=' Signup / Login']\r\n"));
            signUp.Click();

            // entering user name
            IWebElement name = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::input[@name='email']"));
            name.SendKeys("user1211@gmail.com");

            //email
            IWebElement email = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::input[@name='password']"));
            email.SendKeys("User@12345");

            // click signup button
            IWebElement loginButton = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::button[text()='Login']"));
            loginButton.Click();
        }

        // logout 
        [Test]
        public void LogOut()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();
            IWebElement signUp = driver.FindElement(By.XPath("//a[text()=' Signup / Login']\r\n"));
            signUp.Click();

            // entering user name
            IWebElement name = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::input[@name='email']"));
            name.SendKeys("user1218@gmail.com");

            //email
            IWebElement email = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::input[@name='password']"));
            email.SendKeys("User@12345");

            // click signup button
            IWebElement loginButton = driver.FindElement(By.XPath("//h2[text()='Login to your account']//following-sibling::form//descendant::button[text()='Login']"));
            loginButton.Click();
            IWebElement lognOut = driver.FindElement(By.XPath("//a[text()=' Logout']"));
            lognOut.Click();
        }
    }
}


////////////////////////////////////////////////////////////////////////////////
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using NUnit.Framework.Internal;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Support.UI;

namespace Assignment_1
{
     class RegisterUser
    {
        [Test]
        public void RegisterUserTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();
            // finding the signup button and clicking
            IWebElement signUp = driver.FindElement(By.XPath("//a[text()=' Signup / Login']\r\n"));
            signUp.Click();
            // entering user name
            IWebElement name = driver.FindElement(By.XPath("//h2[text()='New User Signup!']//following-sibling::form//descendant::input[@name='name']"));
            name.SendKeys("user");
            //email
            IWebElement email = driver.FindElement(By.XPath("//h2[text()='New User Signup!']//following-sibling::form//descendant::input[@name='email']"));
            email.SendKeys("user1210@gmail.com");

            // click signup button
            IWebElement dignUpButton = driver.FindElement(By.XPath("//h2[text()='New User Signup!']//following-sibling::form//descendant::button[text()='Signup']"));
            dignUpButton.Click();

            // selecting title
            IWebElement title = driver.FindElement(By.XPath("//label[text()='Title']//ancestor::div[@class='clearfix']//descendant::input[@value='Mrs']"));
            title.Click();

            // entering password
            IWebElement password = driver.FindElement(By.XPath("//label[text()='Password ']//following-sibling::input"));
            password.SendKeys("User@12345");

            // Date of Birth
            // days
            IWebElement days = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='days']"));
            SelectElement dropdown_Days = new SelectElement(days);
            dropdown_Days.SelectByIndex(12);

            // month
            IWebElement month = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='months']"));
            SelectElement month_Days = new SelectElement(month);
            month_Days.SelectByIndex(3);

            // year
            IWebElement year = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='years']"));
            SelectElement year_Days = new SelectElement(year);
            year_Days.SelectByValue("2003");

            // select the check box
            IWebElement newsLetter_Checkbox = driver.FindElement(By.XPath("//label[text()='Sign up for our newsletter!']//ancestor::div[@class='checkbox']//descendant::input"));
            newsLetter_Checkbox.Click();

            // first name
            IWebElement firstName = driver.FindElement(By.XPath("//label[text()='First name ']//following-sibling::input[@id='first_name']"));
            firstName.SendKeys("user");

            // last name
            IWebElement lastName = driver.FindElement(By.XPath("//label[text()='Last name ']//following-sibling::input[@id='last_name']"));
            lastName.SendKeys("1218");

            // company name
            IWebElement company = driver.FindElement(By.XPath("//label[text()='Company']//following-sibling::input[@id='company']"));
            company.SendKeys("xyz");

            // address1
            IWebElement address = driver.FindElement(By.XPath("//label[text()='Address ']//following-sibling::input[@id='address1']"));
            address.SendKeys("address");

            // country
            IWebElement country = driver.FindElement(By.XPath("//label[text()='Country ']//following-sibling::select[@id='country']"));
            SelectElement country_dropdown=new SelectElement(country);
            country_dropdown.SelectByValue("India");

            // State
            IWebElement state = driver.FindElement(By.XPath("//label[text()='State ']//following-sibling::input[@id='state']"));
            state.SendKeys("Telangana");

            // city
            IWebElement city = driver.FindElement(By.XPath("//label[text()='City ']//following-sibling::input[@id='city']"));
            city.SendKeys("Hyd");

            //zipcode
            IWebElement zipcode = driver.FindElement(By.XPath("//label[text()='Zipcode ']//following-sibling::input[@id='zipcode']"));
            zipcode.SendKeys("12345");

            // Mobile number
            IWebElement mobileNumber = driver.FindElement(By.XPath("//label[text()='Mobile Number ']//following-sibling::input[@id='mobile_number']"));
            mobileNumber.SendKeys("1234567890");

            // create accout button
            IWebElement createAccount = driver.FindElement(By.XPath("//button[text()='Create Account']"));
            createAccount.Click();
        }

    }
}

///////////////////////////////////////////////////////////////////////////////////////////

 using NUnit.Framework;
using OpenQA.Selenium;
using OpenQA.Selenium.DevTools.V136.Audits;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Support.UI;

namespace Assignment_1
{
    public class Tests
    {

        [Test]
        public void SignUpTest()
        {
             IWebDriver driver = new EdgeDriver();
             driver.Navigate().GoToUrl("https://automationexercise.com/");
            // finding the signup button and clicking
            IWebElement signUp = driver.FindElement(By.XPath("//a[text()=' Signup / Login']\r\n"));
            signUp.Click();
            // entering user name
            IWebElement name = driver.FindElement(By.XPath("//input[@data-qa=\"signup-name\"]"));
            name.SendKeys("user");
            //email
            IWebElement email = driver.FindElement(By.XPath("//input[@data-qa=\"signup-email\"]"));
            email.SendKeys("user1218@gmail.com");

            // click signup button
            IWebElement dignUpButton = driver.FindElement(By.XPath("//button[@data-qa=\"signup-button\"]"));
            dignUpButton.Click();

        }

        // signup with existing user details
        [Test]
        public void SignUpWithExistingUser()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            // finding the signup button and clicking
            IWebElement signUp = driver.FindElement(By.XPath("//a[text()=' Signup / Login']\r\n"));
            signUp.Click();
            // entering user name
            IWebElement name = driver.FindElement(By.XPath("//input[@data-qa=\"signup-name\"]"));
            name.SendKeys("user");
            //email
            IWebElement email = driver.FindElement(By.XPath("//input[@data-qa=\"signup-email\"]"));
            email.SendKeys("user1218@gmail.com");

            // click signup button
            IWebElement dignUpButton = driver.FindElement(By.XPath("//button[@data-qa=\"signup-button\"]"));
            dignUpButton.Click();
        }

       
    }
}
///////////////////////////////////////////////////////////////////////////////

 using System;
using System.Collections.Generic;
using System.Linq;
using System.Security.Cryptography.X509Certificates;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using SeleniumExtras.WaitHelpers;
using OpenQA.Selenium.Support.UI;

namespace Assignment_1
{
     class VerifyProducts
    {
        [Test]
        public void VerifyProductsTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;

            // navigate to products page
            IWebElement products = driver.FindElement(By.XPath("//a[contains(normalize-space(text()),'Products')]"));
            js.ExecuteScript("arguments[0].click();", products);


            // using an explaict wait
            WebDriverWait wait=new WebDriverWait(driver,TimeSpan.FromSeconds(10));
            // view product on first element
            IWebElement viewProduct = wait.Until(ExpectedConditions.ElementIsVisible(By.XPath("//p[text()='Blue Top']//ancestor::div[@class='product-image-wrapper']//a[text()='View Product']")));
            js.ExecuteScript("arguments[0].click();", viewProduct);
        }
    }
}






///////////////////////////////////////////////////////////////////////

using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Interactions;

namespace Assignment_1
{
     class VerifyTestCasesPage
    {
        [Test]
        public void VerifyTestCasesPageTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            Actions action = new Actions(driver);
            IWebElement testCasesPage = driver.FindElement(By.XPath("//a[contains(text(),' Test Cases')]"));
            action.MoveToElement(testCasesPage).Click().Perform();
        }
    }
}

/////////////////////////////////////////////////////

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.DevTools.V136.Audits;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Interactions;
using OpenQA.Selenium.Support.UI;
using SeleniumExtras.WaitHelpers;

namespace Assignment_2
{
     class AddToCart
    {
        [Test]
        public void AddToCartTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            WebDriverWait wait = new WebDriverWait(driver,TimeSpan.FromSeconds(10));
            // verify we are on home page
            IWebElement home = driver.FindElement(By.XPath("//h2[text()='Features Items']"));
            Assert.IsTrue(home.Displayed, "Not in home page");

            // go to the products page
            IWebElement products = driver.FindElement(By.XPath("//a[normalize-space(text())='Products']"));
            products.Click();

            // checks if landed in all products page
            IWebElement allProd = driver.FindElement(By.XPath("//h2[@class='title text-center']"));
            Assert.IsTrue(allProd.Displayed, "Not in All products page");


            // add the prod to cart
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;
            IWebElement blueTop = wait.Until(ExpectedConditions.ElementIsVisible(By.XPath("//p[text()='Blue Top']//ancestor::div[@class='productinfo text-center']//a[text()='Add to cart']")));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", blueTop);












            js.ExecuteScript("arguments[0].click();", blueTop);

            // click on continue shopping
            // wait for modal to appear

            // THEN click continue shopping
            IWebElement continueShoping = wait.Until(ExpectedConditions.ElementToBeClickable(By.XPath("//button[text()='Continue Shopping']")));
            js.ExecuteScript("arguments[0].click();", continueShoping);



            // add men tshirt to cart
            IWebElement menTShirt = driver.FindElement(By.XPath("//p[text()='Men Tshirt']//ancestor::div[@class='productinfo text-center']//a[text()='Add to cart']"));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", menTShirt);

            js.ExecuteScript("arguments[0].click();", menTShirt);

            // go to cart
            // wait for modal after adding Men Tshirt

            // THEN click on view cart
            IWebElement viewCart = wait.Until(ExpectedConditions.ElementToBeClickable(By.XPath("//u[text()='View Cart']")));
            js.ExecuteScript("arguments[0].click();", viewCart);


            // assertions
            IWebElement cartTop = driver.FindElement(By.XPath("//a[text()='Blue Top']"));
            Assert.IsTrue(cartTop.Displayed, "blue top not in  cart");
            IWebElement cartTShirt = driver.FindElement(By.XPath("//a[text()='Men Tshirt']"));
            Assert.IsTrue(cartTShirt.Displayed, "men i short is not in  cart");
        }
    }
}

////////////////////////////////////////////////////////////////////////

using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Support.UI;
using SeleniumExtras.WaitHelpers;

namespace Assignment_2
{
    public class Myntra
    {

        [Test]
        public void MyntraAddToCart()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://www.myntra.com/");
            driver.Manage().Window.Maximize();

            // searching the item
            IWebElement search = driver.FindElement(By.CssSelector("input[placeholder='Search for products, brands and more']"));
            search.SendKeys("Embroidered Thread Work Kurti");
            search.SendKeys(Keys.Enter);


            WebDriverWait wait=new WebDriverWait(driver,TimeSpan.FromSeconds(10));
            IWebElement product = wait.Until(ExpectedConditions.ElementIsVisible(By.XPath("//ul[@class='results-base']//li")));
            product.Click();


            // have to switch the window
            // Store the original window handle
            var parentWindow = driver.CurrentWindowHandle;

            // Get all window handles
            var allWindows = driver.WindowHandles;

            foreach (var window in allWindows)
            {
                if(window!=parentWindow)
                {
                    driver.SwitchTo().Window(window);
                }
            }

            IWebElement size = driver.FindElement(By.XPath("//div[@class='size-buttons-size-buttons']//p[text()='S']"));
            size.Click();


            IWebElement addToBag = driver.FindElement(By.XPath("//div[text()='ADD TO BAG']"));
            addToBag.Click();


            IWebElement goToBag = wait.Until(ExpectedConditions.ElementIsVisible(By.XPath("//span[text()='GO TO BAG']")));
            goToBag.Click();

            driver.SwitchTo().Window(parentWindow);
        }
    }
}

/////////////////////////////////////////////////////////////////////////
/// 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Support.UI;
using SeleniumExtras.WaitHelpers;

namespace Assignment_2
{
     class PlaceOrder_RegBeforeCheckout
    {
        [Test]
        public void PlaceOrder_RegBeforeCheckoutTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            driver.Manage().Timeouts().ImplicitWait = TimeSpan.FromSeconds(10);

            WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(10));
            // verify we are on home page
            IWebElement home = driver.FindElement(By.XPath("//h2[text()='Features Items']"));
            Assert.IsTrue(home.Displayed, "Not in home page");

            // signup
            // finding the signup button and clicking
            IWebElement signUp = driver.FindElement(By.XPath("//a[text()=' Signup / Login']\r\n"));
            signUp.Click();
            // entering user name
            IWebElement name = driver.FindElement(By.XPath("//input[@data-qa=\"signup-name\"]"));
            name.SendKeys("user");
            //email
            IWebElement email = driver.FindElement(By.XPath("//input[@data-qa=\"signup-email\"]"));
            email.SendKeys("user121s@gmail.com");

            // click signup button
            IWebElement dignUpButton = driver.FindElement(By.XPath("//button[@data-qa=\"signup-button\"]"));
            dignUpButton.Click();

            // selecting title
            IWebElement title = driver.FindElement(By.XPath("//label[text()='Title']//ancestor::div[@class='clearfix']//descendant::input[@value='Mrs']"));
            title.Click();

            // entering password
            IWebElement password = driver.FindElement(By.XPath("//label[text()='Password ']//following-sibling::input"));
            password.SendKeys("User@12345");

            // Date of Birth
            // days
            IWebElement days = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='days']"));
            SelectElement dropdown_Days = new SelectElement(days);
            dropdown_Days.SelectByIndex(12);

            // month
            IWebElement month = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='months']"));
            SelectElement month_Days = new SelectElement(month);
            month_Days.SelectByIndex(3);

            // year
            IWebElement year = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='years']"));
            SelectElement year_Days = new SelectElement(year);
            year_Days.SelectByValue("2003");

            // select the check box
            IWebElement newsLetter_Checkbox = driver.FindElement(By.XPath("//label[text()='Sign up for our newsletter!']//ancestor::div[@class='checkbox']//descendant::input"));
            newsLetter_Checkbox.Click();

            // first name
            IWebElement firstName = driver.FindElement(By.XPath("//label[text()='First name ']//following-sibling::input[@id='first_name']"));
            firstName.SendKeys("user");

            // last name
            IWebElement lastName = driver.FindElement(By.XPath("//label[text()='Last name ']//following-sibling::input[@id='last_name']"));
            lastName.SendKeys("1218");

            // company name
            IWebElement company = driver.FindElement(By.XPath("//label[text()='Company']//following-sibling::input[@id='company']"));
            company.SendKeys("xyz");

            // address1
            IWebElement address = driver.FindElement(By.XPath("//label[text()='Address ']//following-sibling::input[@id='address1']"));
            address.SendKeys("address");

            // country
            IWebElement country = driver.FindElement(By.XPath("//label[text()='Country ']//following-sibling::select[@id='country']"));
            SelectElement country_dropdown = new SelectElement(country);
            country_dropdown.SelectByValue("India");

            // State
            IWebElement state = driver.FindElement(By.XPath("//label[text()='State ']//following-sibling::input[@id='state']"));
            state.SendKeys("Telangana");

            // city
            IWebElement city = driver.FindElement(By.XPath("//label[text()='City ']//following-sibling::input[@id='city']"));
            city.SendKeys("Hyd");

            //zipcode
            IWebElement zipcode = driver.FindElement(By.XPath("//label[text()='Zipcode ']//following-sibling::input[@id='zipcode']"));
            zipcode.SendKeys("12345");

            // Mobile number
            IWebElement mobileNumber = driver.FindElement(By.XPath("//label[text()='Mobile Number ']//following-sibling::input[@id='mobile_number']"));
            mobileNumber.SendKeys("1234567890");

            // create accout button
            IWebElement createAccount = driver.FindElement(By.XPath("//button[text()='Create Account']"));
            createAccount.Click();

            // click on continue
            IWebElement countinue = driver.FindElement(By.XPath("//a[text()='Continue']"));
            countinue.Click();


            // checking loggned as use or not
            IWebElement user = driver.FindElement(By.XPath("//b[text()='user']"));
            Assert.IsTrue(user.Displayed, "not loggned as user");


            // go to the products page
            IWebElement products = driver.FindElement(By.XPath("//a[normalize-space(text())='Products']"));
            products.Click();

            // checks if landed in all products page
            IWebElement allProd = driver.FindElement(By.XPath("//h2[@class='title text-center']"));
            Assert.IsTrue(allProd.Displayed, "Not in All products page");


            // add the prod to cart
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;
            IWebElement blueTop = wait.Until(ExpectedConditions.ElementIsVisible(By.XPath("//p[text()='Blue Top']//ancestor::div[@class='productinfo text-center']//a[text()='Add to cart']")));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", blueTop);

            js.ExecuteScript("arguments[0].click();", blueTop);

            // THEN click on view cart
            IWebElement viewCart = wait.Until(ExpectedConditions.ElementToBeClickable(By.XPath("//u[text()='View Cart']")));
            js.ExecuteScript("arguments[0].click();", viewCart);

            // assertions
            IWebElement cartTop = driver.FindElement(By.XPath("//a[text()='Blue Top']"));
            Assert.IsTrue(cartTop.Displayed, "blue top not in  cart");

            // proceed to checkout 
            IWebElement proceedToCheckOut = driver.FindElement(By.XPath("//a[text()='Proceed To Checkout']"));
            proceedToCheckOut.Click();

            IWebElement Deladdress = driver.FindElement(By.XPath("//h3[text()='Your delivery address']"));
            Assert.AreEqual(Deladdress.Text, "YOUR DELIVERY ADDRESS");

            IWebElement placeOrder = driver.FindElement(By.XPath("//a[text()='Place Order']"));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", placeOrder);
            placeOrder.Click();


            // entering payment details
            IWebElement name_Card = driver.FindElement(By.XPath("//input[@name='name_on_card']"));
            name_Card.SendKeys("user");

            IWebElement card_Num = driver.FindElement(By.XPath("//input[@name='card_number']"));
            card_Num.SendKeys("1231456789");

            IWebElement cvc = driver.FindElement(By.XPath("//input[@name='cvc']"));
            cvc.SendKeys("123");

            IWebElement expiry_month = driver.FindElement(By.XPath("//input[@name='expiry_month']"));
            expiry_month.SendKeys("03");

            IWebElement expiry_year = driver.FindElement(By.XPath("//input[@name='expiry_year']"));
            expiry_year.SendKeys("20256");

            IWebElement payButton = driver.FindElement(By.XPath("//button[text()='Pay and Confirm Order']"));
            payButton.Click();

            // order plced
            IWebElement order_Places = driver.FindElement(By.XPath("//b[text()='Order Placed!']"));
            Assert.IsTrue(order_Places.Displayed, "Not placed");


            // click on delete button
            IWebElement delete_Acc = driver.FindElement(By.XPath("//a[text()=' Delete Account']"));
            delete_Acc.Click();

            // click on continue
            IWebElement continueee = driver.FindElement(By.XPath("//a[text()='Continue']"));
            continueee.Click();

        }
    }
}

//////////////////////////////////////////////////////////////////////////////

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Support.UI;
using SeleniumExtras.WaitHelpers;

namespace Assignment_2
{
     class PlaceOrderRegWhileCheckout
    {
        [Test]
        public void PlaceOrderRegWhileCheckoutTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(10));
            // verify we are on home page
            IWebElement home = driver.FindElement(By.XPath("//h2[text()='Features Items']"));
            Assert.IsTrue(home.Displayed, "Not in home page");


            // go to the products page
            IWebElement products = driver.FindElement(By.XPath("//a[normalize-space(text())='Products']"));
            products.Click();

            // checks if landed in all products page
            IWebElement allProd = driver.FindElement(By.XPath("//h2[@class='title text-center']"));
            Assert.IsTrue(allProd.Displayed, "Not in All products page");


            // add the prod to cart
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;
            IWebElement blueTop = wait.Until(ExpectedConditions.ElementIsVisible(By.XPath("//p[text()='Blue Top']//ancestor::div[@class='productinfo text-center']//a[text()='Add to cart']")));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", blueTop);

            js.ExecuteScript("arguments[0].click();", blueTop);

            // THEN click on view cart
            IWebElement viewCart = wait.Until(ExpectedConditions.ElementToBeClickable(By.XPath("//u[text()='View Cart']")));
            js.ExecuteScript("arguments[0].click();", viewCart);

            // proceed to checkout 
            IWebElement proceedRoCheckOut = driver.FindElement(By.XPath("//a[text()='Proceed To Checkout']"));
            proceedRoCheckOut.Click();

            // register/login
            IWebElement register = wait.Until(ExpectedConditions.ElementIsVisible(By.XPath("//u[text()='Register / Login']")));
            js.ExecuteScript("arguments[0].click();", register);


            // signup
            // finding the signup button and clicking
            IWebElement signUp = driver.FindElement(By.XPath("//a[text()=' Signup / Login']\r\n"));
            signUp.Click();
            // entering user name
            IWebElement name = driver.FindElement(By.XPath("//input[@data-qa=\"signup-name\"]"));
            name.SendKeys("user");
            //email
            IWebElement email = driver.FindElement(By.XPath("//input[@data-qa=\"signup-email\"]"));
            email.SendKeys("user121x@gmail.com");

            // click signup button
            IWebElement dignUpButton = driver.FindElement(By.XPath("//button[@data-qa=\"signup-button\"]"));
            dignUpButton.Click();

            // selecting title
            IWebElement title = driver.FindElement(By.XPath("//label[text()='Title']//ancestor::div[@class='clearfix']//descendant::input[@value='Mrs']"));
            title.Click();

            // entering password
            IWebElement password = driver.FindElement(By.XPath("//label[text()='Password ']//following-sibling::input"));
            password.SendKeys("User@12345");

            // Date of Birth
            // days
            IWebElement days = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='days']"));
            SelectElement dropdown_Days = new SelectElement(days);
            dropdown_Days.SelectByIndex(12);

            // month
            IWebElement month = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='months']"));
            SelectElement month_Days = new SelectElement(month);
            month_Days.SelectByIndex(3);

            // year
            IWebElement year = driver.FindElement(By.XPath("//label[text()='Date of Birth']//ancestor::div[@class='form-group']//descendant::select[@id='years']"));
            SelectElement year_Days = new SelectElement(year);
            year_Days.SelectByValue("2003");

            // select the check box
            IWebElement newsLetter_Checkbox = driver.FindElement(By.XPath("//label[text()='Sign up for our newsletter!']//ancestor::div[@class='checkbox']//descendant::input"));
            newsLetter_Checkbox.Click();

            // first name
            IWebElement firstName = driver.FindElement(By.XPath("//label[text()='First name ']//following-sibling::input[@id='first_name']"));
            firstName.SendKeys("user");

            // last name
            IWebElement lastName = driver.FindElement(By.XPath("//label[text()='Last name ']//following-sibling::input[@id='last_name']"));
            lastName.SendKeys("1218");

            // company name
            IWebElement company = driver.FindElement(By.XPath("//label[text()='Company']//following-sibling::input[@id='company']"));
            company.SendKeys("xyz");

            // address1
            IWebElement address = driver.FindElement(By.XPath("//label[text()='Address ']//following-sibling::input[@id='address1']"));
            address.SendKeys("address");

            // country
            IWebElement country = driver.FindElement(By.XPath("//label[text()='Country ']//following-sibling::select[@id='country']"));
            SelectElement country_dropdown = new SelectElement(country);
            country_dropdown.SelectByValue("India");

            // State
            IWebElement state = driver.FindElement(By.XPath("//label[text()='State ']//following-sibling::input[@id='state']"));
            state.SendKeys("Telangana");

            // city
            IWebElement city = driver.FindElement(By.XPath("//label[text()='City ']//following-sibling::input[@id='city']"));
            city.SendKeys("Hyd");

            //zipcode
            IWebElement zipcode = driver.FindElement(By.XPath("//label[text()='Zipcode ']//following-sibling::input[@id='zipcode']"));
            zipcode.SendKeys("12345");

            // Mobile number
            IWebElement mobileNumber = driver.FindElement(By.XPath("//label[text()='Mobile Number ']//following-sibling::input[@id='mobile_number']"));
            mobileNumber.SendKeys("1234567890");

            // create accout button
            IWebElement createAccount = driver.FindElement(By.XPath("//button[text()='Create Account']"));
            createAccount.Click();

            // verify that account is created
            IWebElement accCreated = driver.FindElement(By.XPath("//b[text()='Account Created!']"));
            Assert.IsTrue(accCreated.Displayed, "Account is not created");

            // click on continue
            IWebElement countinue = driver.FindElement(By.XPath("//a[text()='Continue']"));
            countinue.Click();

            // checking loggned as use or not
            IWebElement user = driver.FindElement(By.XPath("//b[text()='user']"));
            Assert.IsTrue(user.Displayed, "not loggned as user");


            // click on cart
            IWebElement cart = driver.FindElement(By.XPath("//a[text()=' Cart']"));
            cart.Click();

            // proceed to checkout 
            IWebElement proceedToCheckOut = driver.FindElement(By.XPath("//a[text()='Proceed To Checkout']"));
            proceedToCheckOut.Click();

            IWebElement Deladdress = driver.FindElement(By.XPath("//h3[text()='Your delivery address']"));
            Assert.AreEqual(Deladdress.Text, "YOUR DELIVERY ADDRESS");

            IWebElement placeOrder =driver.FindElement(By.XPath("//a[text()='Place Order']"));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", placeOrder);
            placeOrder.Click();


            // entering payment details
            IWebElement name_Card = driver.FindElement(By.XPath("//form[@id='payment-form']//input[@name='name_on_card']"));
            name_Card.SendKeys("user");

            IWebElement card_Num = driver.FindElement(By.XPath("//form[@id='payment-form']//input[@name='card_number']"));
            card_Num.SendKeys("1231456789");

            IWebElement cvc = driver.FindElement(By.XPath("//form[@id='payment-form']//input[@name='cvc']"));
            cvc.SendKeys("123");

            IWebElement expiry_month = driver.FindElement(By.XPath("//form[@id='payment-form']//input[@name='expiry_month']"));
            expiry_month.SendKeys("03");

            IWebElement expiry_year = driver.FindElement(By.XPath("//form[@id='payment-form']//input[@name='expiry_year']"));
            expiry_year.SendKeys("20256");

            IWebElement payButton = driver.FindElement(By.XPath("//form[@id='payment-form']//button[text()='Pay and Confirm Order']"));
            payButton.Click();

            // order plced
            IWebElement order_Places = driver.FindElement(By.XPath("//b[text()='Order Placed!']"));
            Assert.IsTrue(order_Places.Displayed, "Not placed");


            // click on delete button
            IWebElement delete_Acc = driver.FindElement(By.XPath("//a[text()=' Delete Account']"));
            delete_Acc.Click();

            // click on continue
            IWebElement continueee = driver.FindElement(By.XPath("//a[text()='Continue']"));
            continueee.Click();

        }
    }
}

///////////////////////////////////////////////////////////////////////////////////////////////////////////
/// 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Interactions;

namespace Assignment_2
{
     class ProdDetails
    {
        [Test]
        public void ProductDetaislTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            // go to the products page
            IWebElement products = driver.FindElement(By.XPath("//a[normalize-space(text())='Products']"));
            products.Click();

            // checks if landed in all products page
            IWebElement allProd = driver.FindElement(By.XPath("//h2[@class='title text-center']"));
            Assert.IsTrue(allProd.Displayed, "Not in All products page");


            // click on the view product
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;
            IWebElement viewProd = driver.FindElement(By.XPath("//div[@class='features_items']//ul[@class='nav nav-pills nav-justified']"));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", viewProd);
            viewProd.Click();

            // verify that it is redirected to product detials page
            IWebElement prodDetails = driver.FindElement(By.XPath("//p[text()='Category: Women > Tops']"));
            string prodDetailsText = prodDetails.Text;
            string actualText = "Category: Women > Tops";
            //Assert.IsTrue(prodDetails.Displayed, "Not redirected to the products detail page");
            Assert.AreEqual(actualText, prodDetailsText);
        }
    }
}

///////////////////////////////////////////////////////////////////////////////////////
/// 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Support.UI;
using SeleniumExtras.WaitHelpers;

namespace Assignment_2
{
     class ProdQunatity
    {
        [Test]
        public void ProductQuantityTest()
        {

            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            // go to the products page
            IWebElement products = driver.FindElement(By.XPath("//a[normalize-space(text())='Products']"));
            products.Click();

            // checks if landed in all products page
            IWebElement allProd = driver.FindElement(By.XPath("//h2[@class='title text-center']"));
            Assert.IsTrue(allProd.Displayed, "Not in All products page");


            // click on the view product
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;
            IWebElement viewProd = driver.FindElement(By.XPath("//div[@class='features_items']//ul[@class='nav nav-pills nav-justified']"));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", viewProd);
            viewProd.Click();

            // verify that it is redirected to product detials page
            IWebElement prodDetails = driver.FindElement(By.XPath("//p[text()='Category: Women > Tops']"));
            string prodDetailsText = prodDetails.Text;
            string actualText = "Category: Women > Tops";
            //Assert.IsTrue(prodDetails.Displayed, "Not redirected to the products detail page");
            Assert.AreEqual(actualText, prodDetailsText);

            // increase the quantity
            IWebElement quantity = driver.FindElement(By.Id("quantity"));
            quantity.Clear();
            quantity.SendKeys("4");

            // add to cart
            IWebElement addToCart = driver.FindElement(By.XPath("//button[@class='btn btn-default cart']"));
            addToCart.Click();

            // view cart
            WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(10));
            IWebElement viewCart = wait.Until(ExpectedConditions.ElementToBeClickable(By.XPath("//u[text()='View Cart']")));
            js.ExecuteScript("arguments[0].click();", viewCart);

            // assertions
            IWebElement cartTop = driver.FindElement(By.XPath("//a[text()='Blue Top']"));
            Assert.IsTrue(cartTop.Displayed, "blue top not in  cart");
        }
    }
}

//////////////////////////////////////////////////////////////////////////////////////
/// 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;

namespace Assignment_2
{
     class searchProd
    {
        [Test]
        public void searchProducts()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            // go to the products page
            IWebElement products = driver.FindElement(By.XPath("//a[normalize-space(text())='Products']"));
            products.Click();

            // checks if landed in all products page
            IWebElement allProd = driver.FindElement(By.XPath("//h2[@class='title text-center']"));
            Assert.IsTrue(allProd.Displayed, "Not in All products page");

            // search prod
            IWebElement search = driver.FindElement(By.Id("search_product"));
            search.SendKeys("Winter Top");
            IWebElement searchSubmit = driver.FindElement(By.Id("submit_search"));
            searchSubmit.Click();


            //verify
            IWebElement searchedProd = driver.FindElement(By.XPath("//p[text()='Winter Top']"));
            Assert.IsTrue(searchedProd.Displayed, "Element not displyed");
        }
    }
}

///////////////////////////////////////////////////////////////////////////////////////////
/// 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;

namespace Assignment_2
{
     class SubCart
    {
        [Test]
        public void SubCartTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            // verify we are on home page
            IWebElement home = driver.FindElement(By.XPath("//h2[text()='Features Items']"));
            Assert.IsTrue(home.Displayed, "Not in home page");

            //goto cart
            IWebElement cart = driver.FindElement(By.XPath("//a[text()=' Cart']"));
            cart.Click();

            // scroll to subscription
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;
            IWebElement sub = driver.FindElement(By.XPath("//h2[text()='Subscription']"));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", sub);

            // enter emil
            IWebElement email = driver.FindElement(By.XPath("//input[@id=\"susbscribe_email\"]"));
            email.SendKeys("user1218@gmail.com");
            IWebElement send = driver.FindElement(By.XPath("//button[@id=\"subscribe\"]"));
            send.Click();


            // verify that it is successful
            IWebElement verificationText = driver.FindElement(By.XPath("//div[text()='You have been successfully subscribed!']"));
            string verification = verificationText.Text;
            string actualText = "You have been successfully subscribed!";
            Assert.AreEqual(actualText, verification);
        }
    }
}

/////////////////////////////////////////////////////////////////////////////////////////////
/// 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;

namespace Assignment_2
{
     class SubHome
    {
        [Test]
        public void SubHomePageTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            // verify we are on home page
            IWebElement home = driver.FindElement(By.XPath("//h2[text()='Features Items']"));
            Assert.IsTrue(home.Displayed, "Not in home page");

            // scroll to subscription
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;
            IWebElement sub = driver.FindElement(By.XPath("//h2[text()='Subscription']"));
            js.ExecuteScript("arguments[0].scrollIntoView(true);", sub);

            // enter emil
            IWebElement email = driver.FindElement(By.XPath("//input[@id=\"susbscribe_email\"]"));
            email.SendKeys("user1218@gmail.com");
            IWebElement send = driver.FindElement(By.XPath("//button[@id=\"subscribe\"]"));
            send.Click();


            // verify that it is successful
            IWebElement verificationText = driver.FindElement(By.XPath("//div[text()='You have been successfully subscribed!']"));
            string verification = verificationText.Text;
            string actualText = "You have been successfully subscribed!";
            Assert.AreEqual(actualText, verification);

        }
    }
}

///////////////////////////////////////////////////////////////////////////////////////////////////
/// 
using OpenQA.Selenium;
using OpenQA.Selenium.Edge;
using OpenQA.Selenium.Support.UI;

namespace Assignment_3
{
    public class LoginBeforecheckout
    {

        [Test]
        public void LoginBeforecheckoutTest()
        {
            IWebDriver driver = new EdgeDriver();
            driver.Navigate().GoToUrl("https://automationexercise.com/");
            driver.Manage().Window.Maximize();

            driver.Manage().Timeouts().ImplicitWait = TimeSpan.FromSeconds(10);

            WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(10));
            // verify we are on home page
            IWebElement home = driver.FindElement(By.XPath("//h2[text()='Features Items']"));
            Assert.IsTrue(home.Displayed, "Not in home page");


            // finding the signup button and clicking
            IWebElement logIn = driver.FindElement(By.XPath("//a[text()=' Signup / Login']"));
            logIn.Click();




        }
    }
}

```
