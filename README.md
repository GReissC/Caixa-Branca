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

//INSTRUÇÃO SQL
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

Neste repositório, foram adicionadas as especificações de cada parte do código, conhecidas juntas como um JAVADOC. Através de comentários junto às linhas de código, se torna possível entender mais facilmente qual o objetivo de cada linha e suas relações, facilitando o processo de manutenção e possível correção de erros em códigos que estejam compilando de forma incorreta.
