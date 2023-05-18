# Índice 

* [Índice](#índice)


# Java Web: crie aplicações com Servlets e MVC
  
  Seguindo o cronograma de estudo do <a href="https://techguide.sh/pt-BR/path/java/">Tech Guide em Java<a>

  
  
  
  <img width="1132" alt="Captura de Tela 2023-05-17 às 19 08 12" src="https://github.com/ceerqueira/servlet/assets/50030996/c22a95bd-77cc-4865-af32-a390369f99d2">

  crio um arquivo Servlet, com o metodo service; 
	
 - JSP significa Java Server Pages
 - JSP é uma página automaticamente processada pelo Tomcat
 - Para gerar HTML dinamicamente no JSP usamos Scriptlets
 - Um scriptlet <% %> é um código Java dentro do HTML
 - Um scriptlet só funciona em uma página JSP
 - Usamos o RequestDispatcher para chamar um JSP a partir da servlet
 - Obtemos o RequestDispatcher a partir do HttpServletRequest
 - Usamos a requisição para colocar ou pegar um atributo (setAttribute(.., ..) ou getAttribute(..))
  
  ```ruby
	
	protected void service (HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		Criar um objeto do tipo banco;
		Banco banco = new Banco();
		Recolher a lista de empresas pelo metodo;
		List<Empresa> listaEmpresas = banco.getListaEmpresas();
		
		//Para utilizar no futuro out.println("HelloWolrd!")
		var out = response.getWriter();
		

		colocar na requistição, o que deseja enviar, nesse caso o nome da empresa e como o JSP vai receber
		request.setAttribute("empresa", listaEmpresas);
	
		chamar o JSP (Java Server Pages) e dizer para onde vai esse "Pacote"
		var rd = request.getRequestDispatcher("/imprimirLista.jsp"); 

		Enviar a requisição 
		rd.forward(request, response);
		
		
		
	}
  
 ```
  
  A requisição chega no Servlet, através da requisição http
  fica tbm o codigo java
  usamos o dispacher da requisição para chamar o JSP

Utilização da biblioteca JSTL (JavaServer Pages Standard Tag Library) no JSP(Java Server Pages) deixa o html mais limpo
	
	
JSTL (Java Standard Tag Library):
 - core - controle de fluxo
 - fmt - formatação / i18n (internacionalização) 
 - sql - executar SQL
 - xml - gerar XML
	
	
core - controle de fluxo
```ruby<%@ taglib uri = "http://java.sun.com/jsp/jstl/core" prefix = "c"%>```
	
fmt - formatação / i18n (internacionalização)
```ruby<%@ taglib uri = "http://java.sun.com/jsp/jstl/fmt" prefix = "fmt"%>```
	
Exemplo no jsp:
```ruby
<%@ page language="java" contentType="text/html; charset=UTF-8"
pageEncoding="UTF-8"%>
<%@ taglib uri = "http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Imprmir Lista de Empresa</title>
</head>
<body>
	<h5>Lista de Empresas:</h5>
	<ul>
		<c:forEach items ="${empresas}" var ="empresa">
			<li>${empresa.nome}</li>
		</c:forEach>
	</ul>
</body>
</html>```
