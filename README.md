# Projeto.Automatizado.Parabank
Projeto Automatizado Site Parabank usando Step By Step



package elementos;

import org.openqa.selenium.By;

public class Elementos {

	public By menuRegister = By.xpath("//a[text()='Register']");

	public By firstName = By.xpath("//input[@id='customer.firstName']");
	public By lastName = By.xpath("//input[@id='customer.lastName']");
	public By address = By.xpath("//input[@id='customer.address.street']");
	public By city = By.xpath("//input[@id='customer.address.city']");
	public By state = By.xpath("//input[@id='customer.address.state']");
	public By zipCode = By.xpath("//input[@id='customer.address.zipCode']");
	public By phone = By.xpath("//input[@id='customer.phoneNumber']");
	public By ssn = By.xpath("//input[@id='customer.ssn']");
	public By userName = By.xpath("//input[@id='customer.username']");
	public By passoWord = By.xpath("//input[@id='customer.password']");
	public By confirm = By.xpath("//*[@id='repeatedPassword']");
	public By btnRegister = By.xpath("//input[@value='Register']");
	
	public By msgRegistroSucesso = By.xpath("//p[text()='Your account was successfully. You are now logged in.']");

}


