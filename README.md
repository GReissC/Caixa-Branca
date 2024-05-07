# Caixa-Branca
Exercício de Caixa Branca feita com base no código fornecido pelo Canva, pelo professor Daniel Ohata.

Código original:

package login;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet:
import java.sql.Statement;


public class User {

public Connection conectarBD() {

Connection conn = null;

try{

Class.forName("com.mysql.Driver.Manager").newInstance();
String url = "jdbc:mysql://127.0.0.1/test?user=lopes&password=123";
conn = DriverManager.getConnection(url);

} catch (Exception e) { }

return conn;}

public String nome="";
public boolean result = false;
public boolean verificarUsuario (String login, String senha) {

String sql = "";
Connection conn = conectarBD();

//INSTRUÇÃO SOL
sql += "select nome from usuarios";
sql +="where login = " + " ' " + login + " ' ";
sql += " and senha = " + " ' " + senha + " '; ";

try {
Statement st = conn.createStatement();
ResultSet rs = st.executeQuery(sql);

if (rs.next()) {
result = true;
nome = rs.getString("nome");}

}catch (Exception e) { }
return result; }

}//fim da class

ERROS:

O uso do Driver JDBC está errado, devido ao fato de que deve-se ser usado "jdbc.Driver", ao invés de "Driver.Manager". Este erro está presente na linha 22 do ReadMe.

Quebra de boa prática ao não usar as exceções presentes no "Catch", devendo pelo menos printá-las em um registro de exceções detectadas. Os Catchs estão presentes nas linhas 26 e 50 do ReadMe.

Visitantes são bem-vindos para fazerem alterações e correções no código, apenas mantendo a versão original no ReadMe, como está acima.

Detalhamento do Grafo de Fluxo: O grafo se inicia com a conexão com o DataBase, seguindo para um teste de conexão. Dali, o grafo pode seguir dois caminho: Em caso de falha, ele cai em um Catch que detecta essa falha e a processa, em caso de sucesso, é registrado que houve sucesso, e se segue para a consulta no DataBase, criando-a e executando a consulta. Para executar essa consulta, é necessário verificar o usuário, verificação essa que cria três cenários diferentes, cenários 6.5, 7 e 8: Cenário 6,5 é caso haja alguma falha de verificação, caindo novamente em um Catch que a registra. Através de uma Boolean, no cenário 7, o usuário é confirmado que existe, enquanto no cenário 8, é confirmado que o usuário não existe, ambos levando ao resultado do cenário 9, onde se devolve o resultado da Boolean, e a aplicação agirá de acordo com o mesmo.
