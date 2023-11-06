# Pedro Motta Silva


## API 1º Semestre: Smart-Key
<br/>

### Parceiro Acadêmico
Fatec Prof. Jessen Vidal (proposta realizada pelo docente responsável pela disciplina que ordenou o projeto)

![image](https://user-images.githubusercontent.com/74321890/221617740-afbc3809-af92-43e8-bc11-698eeffb4bf4.png)
##### *Figura 01. FATEC*

### Visão do Projeto
Desenvolver uma aplicação mobile com App Inventor que controle de forma remota Um sistema de automação residencial usando Arduino. O objetivo é trazer conforto para o usuário com tecnologias de baixo custo.
<br/>
### Tecnologias adotadas na solução
<details><summary>App Inventor</summary>

 > O App Inventor é um software web criado pela universidade americana Massachusetts Institute of Technology (MIT) que permite desenvolver aplicativos Android usando um navegador da Web e um telefone ou emulador conectados.<br/>Foi utilizado no projeto como frontend para controlar as automações.

</details>
<details><summary>Arduino</summary>

 > O arduino é uma plataforma eletrônica de prototipagem open-source e hardware livre, de fácil utilização, projetado através de um microcontrolador de programação específico, com pinos de entrada e saída.<br/>Nesse projeto foi usado o modelo ESP-8266, reponsável por controlar todo o circuito eletrônico e integração HTTP com o realtime database.

</details>
<details><summary>Firebase</summary>

 > Firebase é um conjunto de serviços de computação em nuvem de back-end e plataformas de desenvolvimento de aplicativos fornecidos pelo Google.<br/> No contexto do projeto, foi usado o produto 'realtime database' como banco de dados não relacional, armazenando na nuvem o estado dos componentes automatizados

</details>
<br/>

### Contribuições Pessoais
Trabalhei em todos os processos de desenvolvimento, entre elas se destacam:

<details><summary>Comunicação do módulo ESP8266 com o Realtime Database</summary>

 > A comunicação feita entre o módulo e o banco de dados não relacional feita através de rotas http contava com:

 > Setup da rede:
 ```c++
    /*conexão wifi*/
    connectWifi(<WIFI>,<Password>);
    /*setup das variávies do bd*/
    Firebase.begin("https://projeto-smartkey.firebaseio.com/", "O66MUynB7ndUBrpQqiqqDUYmTQCDTbj45rG5ZHZF");
    Firebase.setString(firebaseData, "casa%2001/sala", "true");
    Firebase.setString(firebaseData, "casa%2001/cozinha", "true");
 ```
 > O código acima está usando a biblioteca "Firebase" e "Wifi" adicionada ao projeto, a função "connectWifi", conecta o módulo ESP8266 a rede "Cembranelli" com a senha "eunaosei", todas as funções que começam com "Firebase" estão fazendo a conexão com o Realtime Database com as Strings de conexão previamente configuradas
 <br/>

 > Estrutura de decisão baseado no retorno da query:
 ```c++
    /*get Cooler string*/
    if (Firebase.getString(firebaseData, "casa%2001/Liga%20cooler")) {
      String state_cooler_DB=firebaseData.stringData();
      if(state_cooler != state_cooler_DB){
        state_cooler=state_cooler_DB;
        Serial.print(state_cooler);
        if(state_cooler_DB=="true"){
            /*turn Cooler on*/
          digitalWrite(14, HIGH);
        }
        else{
            /*turn Cooler off*/
          digitalWrite(14, LOW);
        }
      }
    }
 ```
 > O código acima consulta a rota "casa%2001/Liga%20cooler" no banco de dados configurado no código anterior, com o retorno da query, o arduino está definindo o estado da porta 14, caso o resultado seja verdadeiro, a porta 14 entrará em estado HIGH(ligado), caso seja falso, a porta 14 entrará em estado LOW(desligado)
</details>
<details><summary>Construção do circuito eletrônico</summary>

 > O circuito eletrônico era baseado em um módulo ESP8266 com mais 3 relês controlados, nesses relês estavam ligados 3 lâmpadas ligadas a rede elétrica da casa, além disso o módulo controla um cooler que simula um ventilador.<br/><img src="https://blog.arduinoomega.com/wp-content/uploads/2018/10/Untitled-Sketch_bb.png" width="400" height="200"/>

 >O arduino era alimentado por uma fonte caseira contruída com uma fonte ATX<br/><img src="https://adcomputum.files.wordpress.com/2019/12/projeto-003-2019-fonte-de-bancada-tipo-atx-montado-2_thumb.jpg?w=244&h=139&zoom=2" width="400" height="200"/>
</details>
<br/>

### Aprendizado efetivo HS
Durante o projeto pude aprender como funciona uma requisição HTTP, já que trabalhei diretamente com a comunicação entre o módulo ESP 8266 e o Realtime database, essa experiência me proporcionou observar como serviços web funcionam.

Também aprendi muito sobre circuitos eletrônicos, principalmente conceitos de elétrica (potência, resistência, etc.) aplicados na prática com o uso da rede elétrica residencial alimentando o circuito de lâmpadas e com a criação da fonte de alimentação com uma fonte de computador.  

Além disso foi meu primeiro contato com a metodologia SCRUM, com esse desafio consegui tive meus primeiros passos para entender sobre os papéis de DEV, MASTER e PO. Estar no papel de DEV me ensinou sobre a metodologia de história e entrega de valores, além de como funciona um gráfico burndown.

 - Circuitos eletrônicos simples: sei fazer com autônomia;
 - Script de comunicação HTTP: sei fazer com autônomia;

<br/><br/>

## API 2º Semestre: ERP JornadaDeMotoristas
<br/>

### Parceiro Acadêmico
IACIT

![image](https://user-images.githubusercontent.com/58821700/228378287-21d8de63-e356-442e-b430-f408a92511ca.png)
##### *Figura 02. IACIT*

### Visão do Projeto
Desenvolver um ERP para administrar motoristas, veículos e suas respectivas jornadas, além disso, crias funcionalidades para controle de atividades financeiras relacionadas as viagens feitas.
<br/>
### Tecnologias adotadas na solução
<details><summary>React</summary>

 > O React é uma biblioteca modular, o que significa que os componentes podem ser facilmente reutilizados e compartilhados entre diferentes partes da aplicação. Isso torna mais fácil manter e expandir uma aplicação à medida que ela cresce, e permite que equipes de desenvolvimento trabalhem de forma mais eficiente juntas.<br/>Nesse projeto foi usado para criar o frontend, oferecendo ao usuário uma forma amigável de visualizar suas informações.

</details>
<details><summary>Spring Boot</summary>

 > Spring Boot é uma estrutura da Web Java baseada em microsserviços de código aberto oferecida pela Spring, especialmente útil para engenheiros de software que desenvolvem aplicativos da Web e microsserviços.<br/>Foi usado para desenvolver a API RESTFUL e estrutura do banco de dados com o ORM.

</details>
<details><summary>Postgres</summary>

 > O PostgreSQL é um banco de dados objeto-relacional (sem relação com linguagens de programação orientadas a objetos), em que cada coisa criada é tratada como um objeto, tais como bancos de dados, tabelas, views, triggers, etc.<br/>No projeto foi usado o banco de dados relacional, sendo que suas tabelas eram criadas automaticamente pelo Spring Boot.

</details>
<br/>

### Contribuições Pessoais
Fui responsável pelo backend da aplicação, criando uma API Rest com spring boot, além disso trabalhei com algumas funcionalidades do frontend, principalmente no consumo do serviço de backend.
<details><summary>Configurações de segurança com Spring security</summary>

 > Um dos principais tópicos foi a segurança da aplicação e suas rotas, para isso foi escolhido a autenticação com jwt (Jswn Web Token), o arquivo abaixo define uma série de configurações de segurança para a aplicação. 
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter{

    @Autowired
    private CustomUserDetailsService customUserDetailsService;

    @Autowired
    private JWTFilter jwtFilter;
 
    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception{
        auth.userDetailsService(customUserDetailsService);
    }

    @Bean
    public PasswordEncoder passwordEncoder(){
        return NoOpPasswordEncoder.getInstance();
    }

    @Bean(name=BeanIds.AUTHENTICATION_MANAGER)
    @Override
    public AuthenticationManager authenticationManagerBean() throws Exception{
        return super.authenticationManagerBean();
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception{
        http.cors().and().csrf().disable().authorizeRequests()
        .antMatchers("/session").permitAll()
        .anyRequest().authenticated()
        .and().exceptionHandling().and().sessionManagement()
        .sessionCreationPolicy(SessionCreationPolicy.STATELESS);
        http.addFilterBefore(jwtFilter, UsernamePasswordAuthenticationFilter.class);
    }

}
```
 > A classe acima define a criptografia de senhas na função "passwordEncoder", o gerenciamento de autenticação para criar o token JWT e a configuração de rotas públicas e privadas no método "configure", sendo que a única rota pública é a rota de autenticação que pode ser encontrado no endpoint "/session", outra configuração importante é o comando "addFilterBefore" que define que toda rota deve passar pelo jwtFilter antes de realmente executar uma função.

</details>
<details><summary>Middleware para verificação de JWT</summary>

 > Como explicado na demonstração anterior, toda requisição deveria passar pelo jwtFilter (middleware) antes de realmente executar alguma função. Além disso, caso houvessem erros, o middleware deveria interromper a requisição.
 ```java
public class JWTFilter extends OncePerRequestFilter{

    @Autowired
    private JWTUtil jwtUtil;

    @Autowired
    private CustomUserDetailsService service;

    @Override
    protected void doFilterInternal(HttpServletRequest httpServletRequest,HttpServletResponse httpServletResponse,FilterChain filterChain) throws ServletException, IOException {
        String authHeader = httpServletRequest.getHeader("Authorization");
        String token = null;
        String username = null;
        if(authHeader!=null && authHeader.startsWith("Bearer ")){
            token = authHeader.substring(7);
            username = jwtUtil.extractUsername(token);
        }
        if(username!=null && SecurityContextHolder.getContext().getAuthentication()==null){
            UserDetails userDetails = service.loadUserByUsername(username);
            if(jwtUtil.validateToken(token, userDetails)){
                UsernamePasswordAuthenticationToken usernamePasswordAuthenticationToken = new UsernamePasswordAuthenticationToken(userDetails, null, userDetails.getAuthorities());
                usernamePasswordAuthenticationToken.setDetails(new WebAuthenticationDetailsSource().buildDetails(httpServletRequest));
                SecurityContextHolder.getContext().setAuthentication(usernamePasswordAuthenticationToken);
            }
        }
        filterChain.doFilter(httpServletRequest, httpServletResponse);
    }
}
 ```
 > O código acima faz algumas verificação sobre o token, a primeira é caso o cabeçalho "header" exista e inicie com "Bearer", além disso as informações são descriptografadas e autenticadas. O comando "doFilter" da continuidade a requisição, caso algum erro aconteça uma exception será lançada.

</details>
<br/>

### Aprendizado efetivo HS
Durante esse projeto, tive meu primeiro contato com o framework Spring Boot, tive participação em todo o backend, ou seja, entendi passo a passo como criar uma API Restful robusta. Um dos maiores desafios foi a biblioteca Spring security, devido a falta de experiência, não sabia como funcionava uma requisição com um token de autenticação jwt, todo o conhecimento foi adiquirido durante esse projeto, além disso, a criptografia de senha dos usuários era uma novidade para toda a equipe.

Além disso, foi minha primeira vez na função de SCRUM MASTER, tive a responsabilidade de organizar as tarefas entre os membros da equipe e confeccionei o gráfico burndown para acompanhar o andamento das tarefas e provionar possíveis atrasos e obstáculos com o time.

 - Web Service com Spring Boot: sei fazer com autônomia;
 - Configuração das regras de segurança com Spring Boot security: sei fazer com consulta;
 - Organização de tarefas: sei fazer com autônomia;
 - Acompanhamento de andamento da equipe através de gráficos: sei fazer com autônomia;

<br/><br/>

## API 3º Semestre: DescontOn
<br/>

### Parceiro Acadêmico
MidAll

![image](https://user-images.githubusercontent.com/58821700/228382217-c1300fbf-09db-4bd2-a380-feb260988b03.png)
##### *Figura 03. MidAll*

### Visão do Projeto
Ferramenta para criar promoções de E-commerce, onde as mecânicas de promoções são feitas de forma flexível e de rápida atualização no sistema. As regras de promoções são cadastradas e posteriormente aplicadas no momento em que os itens são adicionados ao carrinho. Atualmente implementamos e apresentaremos o cadastro dos produtos em várias promoções no servidor/ banco de dados, utilizando operadores lógicos para criar diferentes mecânicas de promoções, o desconto é aplicado na sacola de compra e possui uma visualização dedicada para conferência e escolha de possíveis promoções. Além disso, há a autonomia fornecida ao usuário para editar, remover, arquivar ou desarquivar seus produtos e para editar, deletar, interromper ou ativar promoções e da visualização prática e intuitiva dos produtos e promoções cadastradas através da listagem que possui um filtro para que seja possível diferenciar quais os status de produtos e promoções.
<br/>

### Tecnologias adotadas na solução
<details><summary>Thymeleaf</summary>

 > o Thymeleaf permite que desenvolvedores incorporem código Java em páginas HTML e também utilizem as principais características da linguagem em seus templates.<br/>Nesse projeto foi usado para criar os templates do frontend com HTML, CSS e Javascript

</details>
<details><summary>Spring Boot</summary>

 > Spring Boot é uma estrutura da Web Java baseada em microsserviços de código aberto oferecida pela Spring, especialmente útil para engenheiros de software que desenvolvem aplicativos da Web e microsserviços.<br/>Foi usado para desenvolver uma API e implementar regras de negócio da aplicação

</details>
<details><summary>OracleBD</summary>

 > É o SGBD da Oracle, o mais utilizado em aplicações corporativas, lançado em meados dos anos 70, é multiplataforma e possui licença comercial.<br/>Foi usado para estruturar o modelo de dados relacional da aplicação.

</details>
<br/>

### Contribuições Pessoais
Em um primeiro momento trabalhei nos templates da aplicação usando Javascript e JQuery. Minha outra grande contribuição foi na hora de aplicar as promoções de forma efetiva nas compras
<details><summary>Páginas dinâmicas com JS e JQuery</summary>

 > Para uma boa experiência do usuário, as telas foram pensadas de forma que atendenssem suas necessidades, exibindo somente o que é necessário e com poucos clicks
 ```javascript
 async function popularTabela(){
    $("#disp").empty();
    $("#arqui").empty();
    const res = await axios.get("/produto");
    console.log(res.data)
    res.data.forEach(produto => {
        if(produto.status==0){
            var elemento = "<tr><td>"+produto.id+"</td><td>"+produto.nome+"</td><td>"+produto.categoria+"</td><td>"+produto.valor.toLocaleString('pt-br',{style: 'currency', currency: 'BRL',minimumFractionDigits: 2})+"</td>";
            elemento += "<td colspan='2'><a class='btn btn-info btn-sm' role='button' onclick='adicionarSacola("+JSON.stringify(produto)+")'><span class='bx bxs-shopping-bag' title='Adicionar na Sacola' aria-hidden='true'></span><td>";
            elemento += "<a href='/administrativo/produto?id="+produto.id+"' class='btn btn-info btn-sm editar' role='button'><span class='bx bx-edit' title='Editar' aria-hidden='true'></span></a>";
            elemento +="&nbsp;"
            elemento += "<a class='btn btn-sm btn-danger' data-toggle='modal' data-target='#modal-warning' onclick='abreModal("+produto.id+")'><span class='bx bxs-x-circle' title='Remover' aria-hidden='true'></span></a></td></tr>";
            $("#disp").append(elemento);
        }else{
            var elemento="<tr><td>"+produto.id+"</td><td>"+produto.nome+"</td><td>"+produto.categoria+"</td><td>"+produto.valor.toLocaleString('pt-br',{style: 'currency', currency: 'BRL',minimumFractionDigits: 2})+"</td>"
            elemento += "<td colspan='3'><a class='btn btn-info btn-sm editar' data-toggle='modal' data-target='#modal-warning'>";
            elemento += "<span class='bx bx-upload' title='Desarquivar' onclick='desarquivar("+JSON.stringify(produto)+")' aria-hidden='true'></span></a></td></tr>";
            $("#arqui").append(elemento);
        }
    });
}
 ```
 > A função acima popula duas tabelas com os produtos do ecommerce dependendo do status dele, dessa forma o usuário pode ver uma tabela filtrada, já que a tabela completa é muito grande e seria necessário rolar pela tela.

</details>
<details><summary>Script Engine</summary>

 > Dentro do Java é possível executar scripts de diversas linguaguens, no caso do projeto, quando o usuário escolhia a regra de sua promoção, um script era gerado de forma dinâmica e executado em cima da condição que o usuário escolhia para aplicar o desconto
 ```java
 if(condicao.contains(categoria)){
	int index = 0;
	for(SacolaDTO item:lista){
		engine.eval(categoria+index+"='"+item.getCategoria()+"'");
		index++;
	}
}
if(condicao.contains("ProdutoQuantidade")){
  int index = 0;
  for(SacolaDTO item:lista){
    engine.eval("ProdutoQuantidade"+index+"="+item.getQuantidade());
    index++;
  }
}
if(condicao.contains("ProdutoValor")){
  int index = 0;
  for(SacolaDTO item:lista){
    engine.eval("ProdutoValor"+index+"="+(item.getQuantidade()*item.getValor()));
    index++;
  }
}
if(condicao.contains("CompraTotal")){
  engine.eval("CompraTotal="+total);
}
if(condicao.contains("QuantidadeTotal")){
  engine.eval("QuantidadeTotal="+quantidade);
}
 ```
 > O código acima cria variáveis de forma dinâmica dentro do script em JS que será executado no Engine, nesse caso as váriáveis que contém a quantidade de produtos comprados, o valor dos produtos comprados, o total da compra e a quantidade total estão sendo setadas. 

</details>

<br/>

### Aprendizado efetivo HS
Nesse projeto aprendi sobre design UI e UX, o desafio de criar uma ferramenta server side fez com que todo o "frontend" fosse criado com HTML, CSS, Javascript e JQuery. Como os inputs do usuário final precisavam ser dinâmicos, aprendi muito sobre eventos em js e sobre como a árvore de elementos DOM funciona e suas propriedades.

Em relação ao "backend", o grande desafio foi o banco de dados Oracle em um container Docker, ja que era meu primeiro contato coma ferramenta. Além disso foi o primeiro projeto que aprendi todo o conceito e caso de uso de DTO e sobre Script Engine para execução de scripts dentro do Java.

 - Criação de telas com Javascript e JQuery: sei fazer com autonômia;
 - Uso de DTO em uma aplicação: sei fazer com autonômia;
 - Script Engine: sei fazer com autonômia;

<br/><br/>

## API 4º Semestre: MCS
<br/>

### Parceiro Acadêmico
Subiter

![image](https://user-images.githubusercontent.com/58821700/228385162-80ac6bda-4e3b-433a-819b-ea91db32a205.png)
##### *Figura 03. Subiter*

### Visão do Projeto
Sistema ERP que visa gerenciar e controlar dados, afim de reduzir custos, facilitar tomadas de decisão, otimizar o tempo de atendimento de chamados e aprimorar o solucionamento destes. É composta por níveis de usuários, onde o administrador terá controle sobre todas as funcionalidades existentes, dentre elas o cadastro, edição e exclusão de outros usuários; o suporte ficará responsável pelo CRUD de falhas e soluções genéricas e CRUD de equipamentos; o cliente trará o problema para o suporte e, este ficará responsável por gerenciar o chamado e resolvê-los.

A MCS (Management and Control System) trouxe de uma forma fácil e rápida o mais importante: o mapeamento gráfico de anomalias nas silhuetas.

O Mapemamento de anomalias consiste em durante ou após uma inspeção, o suporte conseguirá fazer o upload da silhueta e adicionar as falhas (específicas do chamado) encontradas em formas e tamanhos diferentes para uma melhor identificação da posição e tamanho, facilitando na identificação de quantidade e quais materiais serão utilizados para a solução dessas falhas e também no cálculo do orçamento.

Sua interface web facilita a gestão de dados e dá autonomia aos usuários dessa aplicação para que possam atuar com desenvoltura dentro das permissões concedidas.
<br/>

### Tecnologias adotadas na solução
<details><summary>Vue</summary>

 > Vue.js é um framework JavaScript de código-aberto, focado no desenvolvimento de interfaces de usuário e aplicativos de página única.<br/>No contexto do projeto foi usado para criar o frontend, com o padrão de gerenciamento de estado do vuex e manipulação de imagens com a biblioteca konva.

</details>
<details><summary>Spring Boot</summary>

 > Spring Boot é uma estrutura da Web Java baseada em microsserviços de código aberto oferecida pela Spring, especialmente útil para engenheiros de software que desenvolvem aplicativos da Web e microsserviços.<br/>Foi usado para desenvolver uma API RESTFUL com a implementação do Spring Security, fornecendo accesso seguro aos dados sensíveis.

</details>
<details><summary>OracleBD</summary>

 > É o SGBD da Oracle, o mais utilizado em aplicações corporativas, lançado em meados dos anos 70, é multiplataforma e possui licença comercial.<br/>Foi usado para estruturar o modelo de dados relacional da aplicação, além disso foram criadas procedures e triggers no SGBD.

</details>
<br/>

### Contribuições Pessoais
Nesse projeto atuei como PO, porém devido ao tamanho reduzido da equipe, acabei desenvolvendo features no backend e frontend, o maior problema foi desenvolver as telas dinâmicas e o uso da biblioteca konva para desenhos em canvas, além disso, o uso de vuex para persistencia de dados.

<details><summary>Desenho dentro do canvas</summary>

 > A cada vez que o usuário clicava dentro da tag canvas uma função era disparada para adicionar as coordenadas do formato desenhado para uma array local e em seguida ser armazenada no banco de dados
 ```javascript
 draw(evt){
  const stage = evt.target.getStage();
  const pos = stage.getPointerPosition();
  const nl = {
    x:pos.x,
    y:pos.y,
    height: this.tamanho,
    width: (this.forma=="alongado")?(this.tamanho*3):this.tamanho,
    fill:this.color,
    type:this.forma,
    info:{
        w:null,
        h:null,
        d:null
    }
  }
  if(this.forma=="isolado"){
      nl['radius']=this.tamanho/2
  }
  this.layers[this.forma].push(nl)
}
 ```
 > Na função acima a função captura a posição cartesiana do click do mouse em relação a área da tag canvas, dessa forma é possível manter as layers salvas.Após o button com a ação de submit era disparado, através do comando dispatch do vuex e armazenado na state para futura requisição no backend e armazenamento no banco de dados

</details>

<details><summary>Profile no Spring Boot</summary>

 > Dentro do Spring boot é possível definir profiles (configurações pré definidas), com o intuito de não precisar fazer alterações recorrentes na configuração, nesse projeto foi usado para a definição do DB de produção (Oracle Cloud) e DB dev (docker local)
 ```
 spring.h2.console.enabled=false

spring.datasource.url=jdbc:oracle:thin:@<database_hostname> ?TNS_ADMIN=<path_to_wallet>
spring.datasource.username=<username>
spring.datasource.password=<password>
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.Oracle12cDialect
 ```
 > A configuração é a de produção com o nome "application-prod.properties", a conexão com o banco é feita via tns e com driver thin (Driver OCI: conexão nativa com a database, Driver thin: Usa Java sockets para conexão com a database)
```
spring.datasource.url=jdbc:oracle:thin:@<host>:1521/<database>
spring.datasource.username=<username>
spring.datasource.password=<password>
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
spring.jpa.hibernate.ddl-auto=update
```
 > A configuração é a de produção com o nome "application-dev.properties", a conexão com o banco em um container docker na máquina local.
 > Dentro do arquivo "application.properties", é definido qual profile será executado quando a aplicação iniciar
 ```
 spring.profiles.active = prod
 ```
</details>

</br>

### Aprendizado efetivo HS
Durante esse projeto exerci pela primeira vez a função de PO (product Owner), um dos grandes desafios foi entender a dor do cliente e transformar em story cards que realmente entregavam valor. Com esse desafio aprendi a fazer perguntas mais pontuais para conseguir requisitos.

Outro desafio foi o uso do Oracle Cloud, já que foi minha primeira vez usando um serviço de computação em nuvem e a documentação é escassa e com vocabulário mais complicado, meu conhecimento prévio de linux foi essencial para conseguir configurar o banco de dados e o servidor linux para a aplicação JAVA.

 - Configurar banco de dados Oracle na Oracle cloud: sei fazer com autonomia;
 - Conversa com cliente: sei fazer com autonomia;
 - Criação de servidor linux na Oracle cloud: sei fazer com autonomia;

<br/><br/>

## API 5º Semestre: Cloud-In
<br/>

### Parceiro Acadêmico
Mid-All

![image](https://user-images.githubusercontent.com/58821700/228382217-c1300fbf-09db-4bd2-a380-feb260988b03.png)
##### *Figura 03. MidAll*

### Visão do Projeto

<br/>

### Tecnologias adotadas na solução
<details><summary>Flask</summary>

 > Flask

</details>
<details><summary>Github Actions</summary>

 > GitHub Actions

</details>
<details><summary>AWS</summary>

 > AWS

</details>
<br/>

### Contribuições Pessoais
Nesse projeto atuei como PO, porém devido ao tamanho reduzido da equipe, acabei desenvolvendo features no backend e frontend, o maior problema foi desenvolver as telas dinâmicas e o uso da biblioteca konva para desenhos em canvas, além disso, o uso de vuex para persistencia de dados.

<details><summary>Desenho dentro do canvas</summary>

 > A cada vez que o usuário clicava dentro da tag canvas uma função era disparada para adicionar as coordenadas do formato desenhado para uma array local e em seguida ser armazenada no banco de dados
 ```javascript
 draw(evt){
  const stage = evt.target.getStage();
  const pos = stage.getPointerPosition();
  const nl = {
    x:pos.x,
    y:pos.y,
    height: this.tamanho,
    width: (this.forma=="alongado")?(this.tamanho*3):this.tamanho,
    fill:this.color,
    type:this.forma,
    info:{
        w:null,
        h:null,
        d:null
    }
  }
  if(this.forma=="isolado"){
      nl['radius']=this.tamanho/2
  }
  this.layers[this.forma].push(nl)
}
 ```
 > Na função acima a função captura a posição cartesiana do click do mouse em relação a área da tag canvas, dessa forma é possível manter as layers salvas.Após o button com a ação de submit era disparado, através do comando dispatch do vuex e armazenado na state para futura requisição no backend e armazenamento no banco de dados

</details>

<details><summary>Profile no Spring Boot</summary>

 > Dentro do Spring boot é possível definir profiles (configurações pré definidas), com o intuito de não precisar fazer alterações recorrentes na configuração, nesse projeto foi usado para a definição do DB de produção (Oracle Cloud) e DB dev (docker local)
 ```
 spring.h2.console.enabled=false

spring.datasource.url=jdbc:oracle:thin:@<database_hostname> ?TNS_ADMIN=<path_to_wallet>
spring.datasource.username=<username>
spring.datasource.password=<password>
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.Oracle12cDialect
 ```
 > A configuração é a de produção com o nome "application-prod.properties", a conexão com o banco é feita via tns e com driver thin (Driver OCI: conexão nativa com a database, Driver thin: Usa Java sockets para conexão com a database)
```
spring.datasource.url=jdbc:oracle:thin:@<host>:1521/<database>
spring.datasource.username=<username>
spring.datasource.password=<password>
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
spring.jpa.hibernate.ddl-auto=update
```
 > A configuração é a de produção com o nome "application-dev.properties", a conexão com o banco em um container docker na máquina local.
 > Dentro do arquivo "application.properties", é definido qual profile será executado quando a aplicação iniciar
 ```
 spring.profiles.active = prod
 ```
</details>

</br>

### Aprendizado efetivo HS
Durante esse projeto exerci pela primeira vez a função de PO (product Owner), um dos grandes desafios foi entender a dor do cliente e transformar em story cards que realmente entregavam valor. Com esse desafio aprendi a fazer perguntas mais pontuais para conseguir requisitos.

Outro desafio foi o uso do Oracle Cloud, já que foi minha primeira vez usando um serviço de computação em nuvem e a documentação é escassa e com vocabulário mais complicado, meu conhecimento prévio de linux foi essencial para conseguir configurar o banco de dados e o servidor linux para a aplicação JAVA.

 - Configurar banco de dados Oracle na Oracle cloud: sei fazer com autonomia;
 - Conversa com cliente: sei fazer com autonomia;
 - Criação de servidor linux na Oracle cloud: sei fazer com autonomia;

<br/><br/>

