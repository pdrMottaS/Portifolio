# Pedro Motta Silva



## API 1º Semestre: Smart-Key
<br/>

### Parceiro Acadêmico
Fatec Prof. Jessen Vidal (proposta realizada pelo docente responsável pela disciplina que ordenou o projeto)

<img src="https://user-images.githubusercontent.com/74321890/221617740-afbc3809-af92-43e8-bc11-698eeffb4bf4.png" alt="drawing" width="300" height="200"/>
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

### Hard-Skills
Durante o projeto pude aprender como funciona uma requisição HTTP, já que trabalhei diretamente com a comunicação entre o módulo ESP 8266 e o Realtime database, essa experiência me proporcionou observar como serviços web funcionam.

Também aprendi muito sobre circuitos eletrônicos, principalmente conceitos de elétrica (potência, resistência, etc.) aplicados na prática com o uso da rede elétrica residencial alimentando o circuito de lâmpadas e com a criação da fonte de alimentação com uma fonte de computador.  

 - Circuitos eletrônicos simples: sei fazer com autônomia;
 - Script de comunicação HTTP: sei fazer com autônomia;

### Soft-Skills
Durante minha participação como desenvolvedor nesse projeto, tive a oportunidade de conhecer melhor a metodologia agil e aprimorar diversas soft skills que foram fundamentais para o sucesso do projeto.

<b>Proatividade:</b>

Uma das habilidades que pude desenvolver e aplicar consistentemente foi a proatividade. Em um ambiente dinâmico, percebi a importância de antecipar desafios e agir proativamente para resolvê-los. Isso foi visível nos desafios que tivemos devido a falta de experiências em circuitos eletrônicos.

<b>Entrega de Valor:</b>

Minhas entregas não ficaram limitadas apenas ao que foi designado, sempre busquei entender a real necessidade e requisitos do cliente, podendo garantir que tudo se encaixava também na expectativa.

<b>Entrega de resultado:</b>

Minha dedicação à entrega de resultados foi evidenciada pela minha capacidade de cumprir prazos e metas estabelecidas. Trabalhei em estreita colaboração com a equipe, assegurando que as entregas fossem feitas de maneira oportuna e com a qualidade desejada. 

<br/><br/>

## API 2º Semestre: ERP JornadaDeMotoristas
<br/>

### Parceiro Acadêmico
IACIT

<img src="https://user-images.githubusercontent.com/58821700/228378287-21d8de63-e356-442e-b430-f408a92511ca.png" alt="drawing" width="300" height="200"/>
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
Durante o projeto, atuei na função de SCRUM MASTER e fui responsável pelo backend da aplicação, criando uma API Rest com spring boot, além disso trabalhei com algumas funcionalidades do frontend, principalmente no consumo do serviço de backend.

<details><summary>Organização de tasks e burndown</summary>

 > Devido a minha atuação como master, tive a responsabilidade de organizar as tarefas em sprints e para cada desenvolvedor de acordo com a prioridade, além disso, mensurar a entrega de resultados dos desenvolvedores através de um gráfico burndown.

</details>

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

### Hard-Skills
Durante esse projeto, tive meu primeiro contato com o framework Spring Boot, tive participação em todo o backend, ou seja, entendi passo a passo como criar uma API Restful robusta. Um dos maiores desafios foi a biblioteca Spring security, devido a falta de experiência, não sabia como funcionava uma requisição com um token de autenticação jwt, todo o conhecimento foi adiquirido durante esse projeto, além disso, a criptografia de senha dos usuários era uma novidade para toda a equipe.

 - Web Service com Spring Boot: sei fazer com autônomia;
 - Configuração das regras de segurança com Spring Boot security: sei fazer com consulta;

### Soft-Skills

Nesse projeto, tive a oportunidade de contribuir como scrum master pela primeira vez, dessa forma desenvolvi soft skills importantes para a função:

<b>Comunicação:</b>

Assumir o papel de Scrum Master pela primeira vez me desafiou a aprimorar minhas habilidades de comunicação. Foi essencial estabelecer canais claros de comunicação para alinhar a equipe, garantindo que todos entendessem suas responsabilidades e metas. Utilizando o método do burndown, acompanhei o progresso das tarefas e mantive um diálogo constante para garantir que as informações fluíssem livremente. 

<b>Organização:</b>

A experiência como Scrum Master me ofereceu a oportunidade de aprimorar minha habilidade de organização. Ao priorizar as tarefas com base no valor agregado, aprendi a gerenciar as demandas de maneira mais eficiente, garantindo que as funcionalidades essenciais fossem desenvolvidas primeiro.

<b>Proatividade:</b>

Ao longo do projeto, percebi a importância de antecipar as necessidades futuras da equipe. Investi tempo em pesquisas e estudos sobre tecnologias emergentes, visando preparar terreno para sprints subsequentes. 

<br/><br/>

## API 3º Semestre: DescontOn
<br/>

### Parceiro Acadêmico
MidAll

<img src="https://user-images.githubusercontent.com/58821700/228382217-c1300fbf-09db-4bd2-a380-feb260988b03.png" alt="drawing" width="300" height="200"/>
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

### Hard-Skills
Nesse projeto aprendi sobre design UI e UX, o desafio de criar uma ferramenta server side fez com que todo o "frontend" fosse criado com HTML, CSS, Javascript e JQuery. Como os inputs do usuário final precisavam ser dinâmicos, aprendi muito sobre eventos em js e sobre como a árvore de elementos DOM funciona e suas propriedades.

Em relação ao backend, o grande desafio foi o banco de dados Oracle em um container Docker, ja que era meu primeiro contato coma ferramenta. Além disso foi o primeiro projeto que aprendi todo o conceito e caso de uso de DTO e sobre Script Engine para execução de scripts dentro do Java.

 - Criação de telas com Javascript e JQuery: sei fazer com autonômia;
 - Uso de DTO em uma aplicação: sei fazer com autonômia;
 - Script Engine: sei fazer com autonômia;

### Soft-Skills
Durante o projeto, muitos desenvolvedores acabaram desistindo, dessa forma desenvolvi novas habilidades para minimizar o gap deixado pela saída de outros integrantes, tais como:

<b>Autonomia e entrega de resultado:</b>

Diante da saída de vários membros da equipe durante o projeto, adquiri a habilidade de operar de forma mais autônoma. Isso envolveu a capacidade de assumir responsabilidades adicionais, tomar decisões pertinentes e conduzir tarefas de maneira independente.

<b>Flexibilidade:</b>

Com o desafio de uma equipe reduzida, desenvolvi uma nova habilidade de ser flexível em relação às tecnologias utilizadas. Esta flexibilidade foi fundamental para garantir que as funcionalidades do projeto continuassem a ser desenvolvidas, mesmo com menos recursos.

<b>Proatividade:</b>

Para minimizar os impactos da saída de membros da equipe, tornei-me proativo na antecipação de tarefas e na realização de pesquisas relevantes para o cumprimento de todos os requisitos do projeto.

<br/><br/>

## API 4º Semestre: MCS
<br/>

### Parceiro Acadêmico
Subiter

<img src="https://github.com/pdrMottaS/Portifolio/assets/58821700/ea6a22bf-e487-4c7b-be9a-a62ba65377ef" alt="drawing" width="300" height="200"/>

##### *Figura 04. Subiter*

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

<details><summary>Fazer o levantamento de requisitos do cliente</summary>

 > Como PO, tive a função de conversar com o cliente e levantar as necessidades e requisitos para a solução, nesse projeto em específico houve algumas mudanças de escopo, forçando o contato recorrente e entendimento de todas as regras de negócio, além disso, organizar tudo de forma priorizada para que o SCRUM MASTER pudesse organizar as tarefas.
  
</details>

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

### Hard-Skills
Com o desenvolvimento da solução, um dos principais desafios foi o uso do Oracle Cloud, já que foi minha primeira vez usando um serviço de computação em nuvem e a documentação é escassa e com vocabulário mais complicado, meu conhecimento prévio de linux foi essencial para conseguir configurar o banco de dados e o servidor linux para a aplicação JAVA.

 - Configurar banco de dados Oracle na Oracle cloud: sei fazer com autonomia;
 - Conversa com cliente: sei fazer com autonomia;
 - Criação de servidor linux na Oracle cloud: sei fazer com autonomia;

### Soft-Skills
Durante esse projeto exerci pela primeira vez a função de PO (product Owner), um dos grandes desafios foi entender a dor do cliente e transformar em story cards que realmente entregavam valor. Com esse desafio, desenvolvi algumas habilidades:
 
<b>Comunicação e negociação:</b>

A minha função central era compreender profundamente as regras de negócio e os requisitos do cliente. Focando nesse entendimento, aprimorei minhas habilidades de comunicação para traduzir essas necessidades de forma clara e precisa para a equipe de desenvolvimento. Além disso, desempenhei um papel essencial na negociação das entregas com o cliente. Esta habilidade de comunicação e negociação foi crucial para garantir que as expectativas do cliente fossem alinhadas com as entregas realizadas, proporcionando um produto final que atendesse às suas necessidades.

<b>Pensamento Crítico:</b>

Um aspecto fundamental do meu trabalho como PO foi desenvolver um pensamento crítico, baseado na compreensão das dores e necessidades do cliente. Ao tomar decisões importantes em cada entrega, foi necessário analisar criticamente o impacto das soluções propostas, levando em consideração diretamente as necessidades do cliente.

<b>Foco:</b>

Com a equipe reduzida, aprendi a priorizar e concentrar minha energia nas tarefas mais cruciais para o projeto. A falta de recursos exigiu um foco intenso nas prioridades do projeto, otimizando o tempo e os esforços dedicados a cada tarefa. Essa habilidade de manter o foco permitiu que mesmo com um grupo menor de integrantes, pudéssemos avançar de maneira eficiente, maximizando o impacto das nossas ações e entregas.

<br/><br/>

## API 5º Semestre: Cloud-In
<br/>

### Parceiro Acadêmico
Mid-All


<img src="https://user-images.githubusercontent.com/58821700/228382217-c1300fbf-09db-4bd2-a380-feb260988b03.png" alt="drawing" width="300" height="200"/>

##### *Figura 03. MidAll*

### Visão do Projeto
O software Cloud-In é um aplicativo orquestrador para transferência automática de arquivos entre sistemas de armazenamento online. Através de sua interface minimalista e interativa, o usuário pode cadastrar suas credenciais e configurar as transferências conforme sua necessidade, iniciando a jornada de download e upload entre os storages.
<br/>

### Tecnologias adotadas na solução
<details><summary>Flask</summary>

 > Flask é um micro framework que utiliza a linguagem Python para criar aplicativos Web.<br/>No contexto da aplicação, foi usada para a criação do microsserviço backend que faz as transferências entre os drives.

</details>
<details><summary>Github Actions</summary>

 > GitHub Actions é um orquestrador de workflows para repositórios do Github.<br/>Na aplicação, foi usada para crias fluxos de CI e testes.

</details>
<details><summary>AWS</summary>

 > A AWS (Amazon Web Services) é um serviço de computação em nuvem desenvolvido pela Amazon.<br/>Foi usado para criação de ambientes para deploy da aplicação backend, fontend e banco de dados com os serviços EC2, IAM e S3

</details>
<br/>

### Contribuições Pessoais
Nesse projeto atuei como Scrum Master, organizando as Sprints e tasks de cada integrante, além disso, trabalhei diretamente no desenvolvimento do backend da aplicação e integrações com S3 e Google Drive.

<details><summary>Organizações de projeto no Jira</summary>
	
 > Para a organização do projeto, configurei o Jira para organizações das Sprints, lançamento de horas trabalhadas, relatório burndown para acompanhamento do projeto e tracking das issues no github.

</details>

<details><summary>Job para operações de arquivos</summary>

 > O usuário poderia definir a frequência que o programa procura os arquivos no drive de origem e a quantidade de banda utilizada, as configurações ficam em um arquivo JSON.
 ```python
@scheduler.scheduled_job("interval", seconds=int(load_json_file()["JOB_TIME"]))
@limit_bandwidth(int(getBandwidth() * (int(load_json_file()["BAND"]) / 100)))
def myFunction():
with app.app_context():
    schema = TransactionSchema()
    query = Config().query.all()
    for i in query:
	if i.origin == "google":
	    originService = GoogleService(i.originToken)
	elif i.origin == "s3":
	    originService = s3Service(i.originToken)
	if i.destiny == "google":
	    destinyService = GoogleService(i.destinyToken)
	elif i.destiny == "s3":
	    destinyService = s3Service(i.destinyToken)
	new_files = originService.files_by_folder(i.originFolder)
	if new_files > 0:
	    transaction = new_transaction(i)
	    msg = format_sse(
		data={"config": i.id, "transaction": schema.dump(transaction)},
		event="newTransaction",
	    )
	    announcer.announce(msg=msg)
	    try:
		files = make_transaction(i, originService, destinyService)
		if len(files) <= 0:
		    transaction = update_transaction(transaction, "Erro", [])
		else:
		    transaction = update_transaction(
			transaction, "Concluido", files
		    )
	    except Exception as e:
		transaction = update_transaction(transaction, "Erro", [])

	    msg = format_sse(
		data={"config": i.id, "transaction": schema.dump(transaction)},
		event="updateTransaction",
	    )
	    announcer.announce(msg=msg)
 ```
</details>

<details><summary>Integração com Google Drive</summary>

 > Para as operações de arquivo (download, upload, listagem, etc) foi criado um service para cada drive.
 ```python
class GoogleService:
    token = ""

    def __init__(self, refreshToken: str):
        data = {
            "refresh_token": refreshToken,
            "client_id": "532089225272-1im33klerc0hmvspgo6mh08aobithavt.apps.googleusercontent.com",
            "client_secret": "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",
            "grant_type": "refresh_token",
        }

        req = requests.post("https://oauth2.googleapis.com/token", json=data).json()

        self.token = req["access_token"]

    def files_by_folder(self, folder):
        headers = {"Authorization": f"Bearer {self.token}"}
        params = {"q": f"'{folder}' in parents and trashed = false", "fields": "*"}
        req = requests.get(
            "https://www.googleapis.com/drive/v3/files", headers=headers, params=params
        )

        num_of_files = len(req.json()["files"])

        return num_of_files
 ```
> Cada vez que a classe era instanciada, ou seja, uma nova transferência inicia, o token passa pelo processo de refresh.

</details>

</br>

### Hard-Skills
Um ponto focal no projeto era desenvolver uma solução destribuída e escalável, afirmando conhecimentos de design pattern e arquitetura de código. Além disso, foi o primeiro projeto com o uso de uma cloud (AWS), que permitiu novos aprendizados sobre billing e recursos em nuvem.

 - Serviços básicos AWS: sei fazer com autonomia;
 - Autenticação em APIs com OAuth2.0: sei fazer com autonomia;
 - Programação paralela em python: sei fazer com autonomia;

### Soft-Skills
Durante esse projeto exerci a função de SM, reforçando atividades de organização e acompanhamento da equipe com o auxílio do Jira software, algumas skills desenvolvidas foram:

<b>Tomada de decisão crítica:</b>

Assumir a função de Scrum Master (SM) durante o projeto me expôs à necessidade de tomar decisões críticas. Em uma situação específica, um membro da equipe foi desligado devido à falta de entregas. Esse contexto demandou ação imediata e a tomada de decisão crítica para resolver a situação. O processo envolveu análise cuidadosa das circunstâncias e impactos, reforçando a importância de decisões assertivas para manter o ritmo e a eficácia do projeto.

<b>Organização e comunicação:</b>

O uso do software Jira para o acompanhamento da equipe fortaleceu minhas habilidades de organização. Através dessa ferramenta, aprendi a organizar de maneira mais eficaz as tarefas e a acompanhar o progresso de cada membro da equipe. Além disso, aprimorei a comunicação ao questionar a equipe sobre o andamento das tarefas e prazos. 

<b>Liderança e motivação:</b>

A oportunidade de atuar como Scrum Master me permitiu explorar e desenvolver minhas habilidades de liderança e motivação. Trabalhando em estreita colaboração com a equipe, busquei liderar pelo exemplo, inspirando e motivando os demais desenvolvedores.

<br/><br/>

## API 6º Semestre: POP
<br/>

### Parceiro Acadêmico
Visiona


<img src="https://github.com/pdrMottaS/Portifolio/assets/58821700/762c378d-3f43-4cc6-9979-795ab1b90d23" alt="drawing" width="300" height="200"/>

##### *Figura 05. Visiona*

### Visão do Projeto
O POP é uma plataforma de monitoramento das atividades agropecuárias cadastradas no Proagro, o projeto conta com ferramentas de machine learning para previsão de indices NDVI e integração com ferramentas meteorológicas.
<br/>

### Tecnologias adotadas na solução
<details><summary>FastAPI</summary>

 > astAPI é uma estrutura web moderna para construção de APIs RESTful em Python.<br/>No contexto da aplicação, foi usada para a criação do microsserviço backend que serve informações geográficas, administrativas e predição das glebas

</details>
<details><summary>Postgis</summary>

 > O PostGIS é uma extensão espacial gratuita e de código fonte livre. Sua construção é feita sobre o sistema de gerenciamento de banco de dados objeto relacional PostgreSQL.<br/>A ferramenta é o banco de dados relacional do projeto, armazenando os dados tratados que foram extraídos da base do Proagro.

</details>
<details><summary>QGis</summary>

 > QGIS é um software livre com código-fonte aberto, multiplataforma de sistema de informação geográfica que permite a visualização, edição e análise de dados georreferenciados.<br/>No projeto foi utilizado como frontend para análise visual das layers geográficas, relatórios e informações. 

</details>
<br/>

### Contribuições Pessoais
Minha atuação nesse projeto foi no papel de DEV, com foco nas funcionalidades de extração e tratamento de dados, desenvolvimento da interface QGis e desenvolvimento do modelo de predição.

<details><summary>Modelo de Série Temporal</summary>

 > Após a extração dos dados da própria Visiona, foi desenvolvido um modelo de série temporal com o modelo SARIMAX usando os dados de timestamp e índice NDVI.
 ```python
import json
import pandas as pd
import os

# extração dos arquivos
df = pd.DataFrame()
for dirname, _, filenames in os.walk('../data/1633/'):
    for filename in filenames:
        data = {}
        with open(os.path.join(dirname, filename),'r') as file:
            d = json.loads(file.read())
        data['date'] = d['Indices']['NDVI']['Serie Processada']['Data']
        data['indices'] = d['Indices']['NDVI']['Serie Processada']['Indice']
        part = pd.DataFrame(data)
        part['date'] = pd.to_datetime(part['date'], format='%Y-%m-%d')
        print(os.path.join(dirname, filename))
        df = pd.concat([df, part])
df['date'] = pd.to_datetime(df['date'], format='%Y-%m-%d')
df = df.set_index('date')
df = df.groupby(df.index).mean()
df = df.asfreq("W",method='backfill')
df = df.sort_index()

# separação dos dados de teste e treino 
steps=10
X_train = df.loc[:datetime.strptime('2019-02-28', "%Y-%m-%d")]
X_test = df.loc[datetime.strptime('2019-02-28', "%Y-%m-%d"):datetime.strptime('2019-05-30', "%Y-%m-%d")]

# busca dos melhores parâmetros (p,d,q) e treinamento do modelo
from pmdarima.arima import auto_arima
from statsmodels.tsa.statespace.sarimax import SARIMAX
auto = auto_arima(
    X_train['indices'],
    seasonal=True,
    stationary=True,
    trace=True, 
    error_action='ignore', 
    suppress_warnings=True
)
sarima = SARIMAX(X_train['indices'],order=auto.order,seasonal_order=(1,2,1,8),freq='W',enforce_stationarity=True)
model = sarima.fit()
 ```
> Mesmo com o uso da função auto_arima para busca automática dos parâmetros, ainda foi necessário trabalhar com os parâmetros sazonais (P,D,Q,s) para melhores resultados.
</details>

<details><summary>Layer Qgis com glebas</summary>

 > Para a renderização dos polígonos com informações armazenados no banco de Dados, para isso foi feito uma query buscando polígonos e dados para filtros.
 ```python
uri = QgsDataSourceUri()
uri.setConnection("localhost", "5432", "postgres", "postgres", "root")
query = '''select opr.opr_inicio_plantio as inicio_plantio, 
    opr.opr_fim_plantio as fim_plantio, 
    opr.opr_inicio_colheita as inicio_colheita, 
    opr.opr_fim_colheita as fim_colheita, 
    mun.mun_descricao as municipio, 
    std.std_descricao as estado, 
    glb.glb_poligono as gleba, 
    opr.opr_id as id_operacao, 
    glb.glb_id as id_gleba 
    from opr_operacao as opr 
    inner join mun_municipio as mun 
    on mun.mun_id = opr.mun_id
    inner join std_estado as std 
    on std.std_id = opr.std_id 
    inner join glb_gleba as glb 
    on glb.opr_id = opr.opr_id'''
uri.setDataSource('', f'({query})', 'gleba','','id_gleba')
layer = QgsVectorLayer(uri.uri(), "Glebas", "postgres")
QgsProject.instance().addMapLayer(layer)
symbol = QgsSymbol.defaultSymbol(layer.geometryType())
symbol.symbolLayer(0).setFillColor(QColor(255, 255, 255, 100))
symbol.symbolLayer(0).setStrokeColor(QColor(255, 255, 255, 100))
symbol.symbolLayer(0).setStrokeWidth(2.0)
renderer = QgsSingleSymbolRenderer(symbol)
layer.setRenderer(renderer)
layer.triggerRepaint()
 ```
> A layer criada no Qgis pode ser manipulada por todas as ferramentas do QGis e com ferramentas personalizadas, na aplicação foi desenvolvida uma ferramenta customizada para renderização das informações e gráficos.
```python
class identifyGleba(mapTool):

    def __init__(self, canvas: QgsMapCanvas,layer:QgsMapLayer,label: str):
        super().__init__(canvas, label)
        self.layer = layer
        self.map_tool = identifyDecorator(self)

    def canvasPressEvent(self, event):
        x, y = event.pos().x(), event.pos().y()
        results = self.map_tool.identify(x,y,[self.layer],True)
        for item in results:
            feature = item.mFeature
            dlg = detailDialog(opr=feature[6],gleba=feature[7],inicio=feature[1],fim=feature[3])
            dlg.show()
            result = dlg.exec_()
```

</details>

</br>

### Aprendizado efetivo HS

#### Hard-Skills
Nesse projeto tive bastante contato com ferramentas de tratamento de dados com pandas e modelos de série temporal como SARIMAX. Além disso, um grande desafio foi o uso de dados geográficos, já que fiquei responsável pela modelagem e manipulação usando Postgis e Geopandas.

- Desenvolvimento de plugins no Qgis: Sei fazer com autônomia;
- Modelagem e manipulação de dados geográficos: Sei fazer com ajuda;
- Tratamento de dados com Pandas: Sei fazer com autônomia 

#### Soft-Skills
Nesse projeto, devido ao desconhecimento da equipe sobre dados e ferramentas geográficas, desenvolvi algumas habilidades como:

<b>Trabalho em equipe e comunicação:</b>

Reconhecendo a necessidade de apoio na equipe, ofereci ajuda e orientação a colegas que enfrentavam desafios semelhantes. Essa colaboração foi fundamental para promover um ambiente de trabalho colaborativo. Além disso, aprimorei minhas habilidades de comunicação ao compartilhar conhecimentos e auxiliar outros membros da equipe no desenvolvimento de suas soluções. Esse processo fortaleceu o trabalho em equipe e contribuiu para o crescimento coletivo do grupo.

<b>Autonomia:</b>

O desconhecimento da equipe sobre dados e ferramentas geográficas me colocou em uma posição em que precisei tomar decisões de forma independente, fundamentadas em meu conhecimento prévio. A autonomia foi essencial para superar os desafios, permitindo-me agir com segurança e eficácia na resolução de problemas.

<b>Proatividade:</b>

Para preencher a lacuna de conhecimento na equipe, adiantei várias pesquisas e tarefas relacionadas ao uso de dados e ferramentas geográficas. Essa iniciativa proativa foi crucial para agilizar o processo de encontrar soluções e garantir que a equipe estivesse melhor preparada para lidar com esses aspectos, contribuindo assim para o progresso mais rápido do projeto.


