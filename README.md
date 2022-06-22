# Ola-mundo-JUnit
Exemplo de teste automatizado livro casa do codigo

Olá mundo, JUnit!

Para facilitar a interpretação do resultado dos testes, o JUnit pinta uma barra
de verde, quando tudo deu certo, ou de vermelho, quando algum teste falhou.
Além disso, ele nos mostra exatamente quais testes falharam e qual foi a saída
incorreta produzida pelo método. O JUnit é tão popular que já vem com o
Eclipse.
Nosso código anterior está muito perto de ser entendido pelo JUnit. Pre-
cisamos fazer apenas algumas mudanças: 1) um método de teste deve sempre
ser público, de instância (isto é, não pode ser static) e não receber nenhum
parâmetro; 2) deve ser anotado com @Test. Vamos fazer estas alterações:
class AvaliadorTest {
@Test
public void main() {
// cenário: 3 lances em ordem crescente
Usuario joao = new Usuario("Joao");
Usuario jose = new Usuario("José");
Usuario maria = new Usuario("Maria");
Leilao leilao = new Leilao("Playstation 3 Novo");

leilao.propoe(new Lance(maria,250.0));
leilao.propoe(new Lance(joao,300.0));
leilao.propoe(new Lance(jose,400.0));
// executando a ação
Avaliador leiloeiro = new Avaliador();
leiloeiro.avalia(leilao);
// comparando a saída com o esperado
double maiorEsperado = 400;
double menorEsperado = 250;
System.out.println(maiorEsperado ==
leiloeiro.getMaiorLance());
System.out.println(menorEsperado ==
leiloeiro.getMenorLance());
}
}


class AvaliadorTest {
@Test
public void deveEntenderLancesEmOrdemCrescente() {
// ...
}
}


import org.junit.Assert;
class AvaliadorTest {
@Test
public void deveEntenderLancesEmOrdemCrescente() {
// cenário: 3 lances em ordem crescente
Usuario joao = new Usuario("Joao");
Usuario jose = new Usuario("José");
Usuario maria = new Usuario("Maria");
Leilao leilao = new Leilao("Playstation 3 Novo");
leilao.propoe(new Lance(maria,250.0));
leilao.propoe(new Lance(joao,300.0));
leilao.propoe(new Lance(jose,400.0));
// executando a ação
Avaliador leiloeiro = new Avaliador();
leiloeiro.avalia(leilao);
// comparando a saída com o esperado
double maiorEsperado = 400;
double menorEsperado = 250;
Assert.assertEquals(maiorEsperado,
leiloeiro.getMaiorLance(), 0.0001);
Assert.assertEquals(menorEsperado,
leiloeiro.getMenorLance(), 0.0001);
}
}

public void avalia(Leilao leilao) {
for(Lance lance : leilao.getLances()) {
if(lance.getValor() > maiorDeTodos) {
maiorDeTodos = lance.getValor();
}
if(lance.getValor() < menorDeTodos) {
menorDeTodos = lance.getValor();
}
}
}
