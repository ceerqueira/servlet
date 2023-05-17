# Índice 

* [Índice](#índice)


# Java Web: crie aplicações com Servlets e MVC
  
  Seguindo o cronograma de estudo do <a href="https://techguide.sh/pt-BR/path/java/">Tech Guide em Java<a>

  
  
  
  <img width="1132" alt="Captura de Tela 2023-05-17 às 19 08 12" src="https://github.com/ceerqueira/servlet/assets/50030996/c22a95bd-77cc-4865-af32-a390369f99d2">

  crio um arquivo Servlet, com o metodo service; 
  
  ```
  protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    //COm esse codigo consigo recolher a string que foi escrita no html
    var nomeEmpresa = request.getParameter("nome");
  
    //Seria para fazer um response
    PrintWriter resp = response.getWriter();
	  resp.println("<html><body>Empresa "+nomeEmpresa+" cadastrada com sucesso!</body></html>");
  
  
  	// chamar o JSP (Java Server Pages)
		var rd = request.getRequestDispatcher("/imprimirlista.jsp");
  
		//colocar na requistição, o que deseja enviar, nesse caso o nome da empresa e como o JSP vai receber
		request.setAttribute("empresa", empresa.getNome() );
		
		//Envia a requi
		rd.forward(request, response);
  }
  
 ```
  
  A requisição chega no Servlet, através da requisição http
  fica tbm o codigo java
  usamos o dispacher da requisição para chamar o JSP
