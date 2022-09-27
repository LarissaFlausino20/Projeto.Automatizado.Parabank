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



package metodos;

import static org.junit.Assert.assertEquals;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class Metodos {

	WebDriver driver;

	public void abrirNavegador() {

		System.setProperty("webdriver.chrome.driver", "./Drivers/chromedriver.exe");
		driver = new ChromeDriver();
		driver.get("https://parabank.parasoft.com/parabank/index.htm");
		driver.manage().window().maximize();
	}

	public void escrever(By elemento, String texto) {

		driver.findElement(elemento).sendKeys(texto);

	}

	public void clicar(By elemento) {
		driver.findElement(elemento).click();
	}

	public void validarMensagem(By elemento, String mensagemEsperada) {
		String mensagemCapturada = driver.findElement(elemento).getText();
		assertEquals(mensagemEsperada, mensagemCapturada);
	}

	public void validarPorTexto(String atributo, String texto, String mensagemEsperada) {
		String mensagemCapturada = driver.findElement(By.xpath("//*[text()='" + texto + "']")).getText();
		assertEquals(mensagemEsperada, mensagemCapturada);
	}
}




package testes;

import org.junit.Before;
import org.junit.Test;

import elementos.Elementos;
import metodos.Metodos;

public class RegistrarTest {

	Metodos metodos = new Metodos(); // ponteiro
	Elementos el = new Elementos();

	@Before
	public void acessarFormulario() {
		metodos.abrirNavegador();
		metodos.clicar(el.menuRegister);

	}

	@Test
	public void registrar() {
		metodos.escrever(el.firstName, "LarissaTeste");
		metodos.escrever(el.lastName, "automatizador");
		metodos.escrever(el.address, "rua teste");
		metodos.escrever(el.city, "São Paulo");
		metodos.escrever(el.state, "SP");
		metodos.escrever(el.zipCode, "0545487");
		metodos.escrever(el.phone, "(11)999999875");
		metodos.escrever(el.ssn, "100");
		metodos.escrever(el.userName, "LarissaTeste");
		metodos.escrever(el.passoWord, "123456");
		metodos.escrever(el.confirm, "123456");
		metodos.clicar(el.btnRegister);
		metodos.validarMensagem(el.msgRegistroSucesso, "Your account was successfully. You are now logged in");

	}

	@Test
	public void camposBranco() {
		metodos.clicar(el.btnRegister);
		metodos.validarPorTexto("span", "First name is required", "First name is required");
		metodos.validarPorTexto("span", "Last name is required", "Last name is required");
		metodos.validarPorTexto("span", "Address is required", "Address is required");
		metodos.validarPorTexto("span", "City is required", "City is required");
		metodos.validarPorTexto("span", "State is required", "State is required");
		metodos.validarPorTexto("span", "Zip Code is required", "Zip Code is required");
		metodos.validarPorTexto("span", "Social Security Number is required", "Social Security Number is required");
		metodos.validarPorTexto("span", "Username is required", "Username is required");
		metodos.validarPorTexto("span", "Password is required", "Password is required");
		metodos.validarPorTexto("span", "Password confirmation is required", "Password confirmation is required");

	}

	public void camposInvalidos() {
		metodos.escrever(el.firstName, "!@#");
		metodos.escrever(el.lastName, "@");
		metodos.escrever(el.address, "@");
		metodos.escrever(el.city, "@");
		metodos.escrever(el.state, "@");
		metodos.escrever(el.zipCode, "@");
		metodos.escrever(el.phone, "(11)@");
		metodos.escrever(el.ssn, "100");
		metodos.escrever(el.userName, "@");
		metodos.escrever(el.passoWord, "@");
		metodos.escrever(el.confirm, "@");
		metodos.clicar(el.btnRegister);

	}

	public void senhasDiferentes() {
		metodos.escrever(el.firstName, "LarissaTeste");
		metodos.escrever(el.lastName, "automatizador");
		metodos.escrever(el.address, "rua teste");
		metodos.escrever(el.city, "São Paulo");
		metodos.escrever(el.state, "SP");
		metodos.escrever(el.zipCode, "0545487");
		metodos.escrever(el.phone, "(11)999999875");
		metodos.escrever(el.ssn, "100");
		metodos.escrever(el.userName, "LarissaTeste");
		metodos.escrever(el.passoWord, "123456");
		metodos.escrever(el.confirm, "654321");
		metodos.clicar(el.btnRegister);

	}

	public void usuarioCadastrado() {
		metodos.escrever(el.firstName, "LarissaTeste");
		metodos.escrever(el.lastName, "automatizador");
		metodos.escrever(el.address, "rua teste");
		metodos.escrever(el.city, "São Paulo");
		metodos.escrever(el.state, "SP");
		metodos.escrever(el.zipCode, "0545487");
		metodos.escrever(el.phone, "(11)999999875");
		metodos.escrever(el.ssn, "100");
		metodos.escrever(el.userName, "LarissaTeste");
		metodos.escrever(el.passoWord, "123456");
		metodos.escrever(el.confirm, "123456");
		metodos.clicar(el.btnRegister);
	}

}




