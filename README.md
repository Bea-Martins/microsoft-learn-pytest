# Introdução a testes no Python 

**Exercício - gravar um teste de unidade com o módulo unittest**

- função str_to_bool()
- bloco try/except na função str_to_bool() que captura AttributeError.
- classe de teste TestStrToBool() que herda de unittest.TestCase.
- três métodos de teste que testam entradas para a função str_to_bool().

**Tipos de testes**

_Teste de Unidade_
- Eles testam a menor parte da lógica possível.
- Funções, métodos ou classes são testados o mais isolado possível, evitando a necessidade de configurar outras funções, métodos ou classes como um requisito.
- Nenhum serviço externo, como bancos de dados ou serviços de rede, é necessário para sua execução.

_Teste de Integração_
- Não são tão rápidos quanto os testes de unidade e tendem a exigir mais configuração inicial antes de serem executados.
- Funções, métodos ou classes são testados com funcionalidade em outras funções, métodos ou classes.
- Um serviço externo pode ser usado, mas nem todos os serviços do aplicativo.

_Testes Funcionais_
- Não são tão rápidos quanto os testes de unidade e tendem a exigir mais configuração inicial antes de serem executados.
- Funções, métodos ou classes são testados com funcionalidade em outras funções, métodos ou classes.
- Um serviço externo pode ser usado, mas nem todos os serviços do aplicativo.

Como os testes funcionais exigem mais serviços, uma reprodução do ambiente de produção e a configuração mais complexa dos tipos de teste, geralmente consumirão tempo e muitos recursos.

_Integração Contínua_: CI ambiente onde é executado testes automáticos.

# Fazer testes com o Pytest

**Classes de teste e métodos de teste**

Convenções:
- As classes de teste têm o prefixo ```Test```
- Os métodos de teste têm o prefixo ```test_```

**Métodos auxiliares**

```setup:``` é executado uma vez antes de cada teste em uma classe <br>
```teardown:``` é executado uma vez após cada teste em uma classe <br>
```setup_class:``` é executado uma vez antes de todos os testes em uma classe <br>
```teardown_class:``` é executado uma vez após todos os testes em uma classe <br>

Perguntas gerais a serem feitas que podem lhe ajudar a determinar quando usar uma classe:

- Seus testes precisam de um código auxiliar de limpeza ou configuração semelhante?
- Faz sentido lógico agrupar seus testes?
- Há pelo menos alguns testes em seu conjunto de testes?
- Seus testes podem se beneficiar de um conjunto comum de funções auxiliares?
Uma função admin_command() que aceita um argumento e um argumento de palavra-chave.
Uma exceção TypeError com uma mensagem de erro útil na função admin_command().

Temos no arquivo test_exercise2.py:
- Uma função admin_command() que aceita um argumento e um argumento de palavra-chave.
- Uma exceção TypeError com uma mensagem de erro útil na função admin_command().
- Uma classe de teste TestAdminCommand() que tem um método auxiliar command() e três métodos de teste que verificam a função admin_command().

# Teste avançado com Pytest

A parametrização no pytest é uma técnica que permite executar um mesmo teste com diferentes conjuntos de dados de entrada, economizando tempo e tornando o código mais limpo e modular. É feita utilizando o decorador `@pytest.mark.parametrize()`, onde você pode especificar os argumentos e os valores associados a eles para vários casos de teste em uma única função de teste.

Dois cenários comuns para o uso de parametrização: For-loops e testes que declaram o mesmo comportamento.

**Acessórios de Pytest**<br>
Funcionalidades adicionais que podem ser utilizadas para modificar o comportamento dos testes ou fornecer informações adicionais durante a execução dos testes. Alguns dos acessórios mais comuns incluem:

1. **Fixtures**: São funções que fornecem um objeto de teste para ser utilizado em um ou mais testes. Podem ser utilizadas para configurar o ambiente de teste, como criar instâncias de objetos ou abrir conexões de banco de dados.
2. **Markers**: São marcadores que podem ser adicionados a testes ou funções para especificar comportamentos ou categorias específicas. Por exemplo, você pode marcar um teste como "lento" ou "experimental", para controlar quando ele deve ser executado.
3. **Hooks**: São pontos de extensão que permitem que você execute código personalizado em diferentes estágios do ciclo de vida de execução do pytest. Por exemplo, você pode usar hooks para executar ações antes ou depois de cada teste, ou para personalizar a forma como os resultados dos testes são relatados.
4. **Parametrize**: Como mencionado anteriormente, o parametrize é uma funcionalidade que permite executar um mesmo teste com diferentes conjuntos de dados de entrada.

Exemplo de acessório ficture (tmp_file()):
```
  import pytest
  import tempfile

  @pytest.fixture
  def tmp_file():
      def create():
          temp = tempfile.NamedTemporaryFile(delete=False)
          return temp.name
      return create
```

Exemplo de teste para o acessório criado:
```
  import os

  def test_file(tmp_file):
      path = tmp_file()
      assert os.path.exists(path)
```

**Escopos**<br>
São usados para controlar a vida útil das fixtures. Existem 4 escopos diferentes em Pytest:

1. ```Function```: é executada uma vez por teste.
2. ```Class```: é executada uma vez por classe.
3. ```Module```: é executada uma vez para um módulo.
4. ```Session```: é executada uma vez para uma sessão.

Os escopos permitem que você controle o momento em que as fixtures são criadas e destruídas, garantindo que os objetos de teste estejam disponíveis quando necessário e que recursos sejam liberados de forma eficiente quando não forem mais necessários. 

O arquivo `conftest.py` em projetos Pytest é utilizado para definir configurações, fixtures e hooks que são compartilhados por todos os testes dentro de um diretório ou pacote. Ele organiza e centraliza esses aspectos importantes do teste, promovendo a modularização e a reutilização de código.

**Acessórios internos**<br>
Além da possibilidade de criar seus acessórios, há muitos acessórios internos em Pytest. A maioria desses acessórios tem as próprias funções de limpeza para que você possa se concentrar em seu uso e não se preocupar com a limpeza.

Estes são alguns acessórios interessantes de Pytest:
- ```cache```: permite criar e gerenciar um sistema de cache para testes
- ```capsys```: auxiliar para captura e gravação de ```stderr``` e ```stdout```
- ```tmpdir```: criar e gerenciar diretórios temporários
- ```monkeypatch```: aplicar patch em módulos, classes ou funções com comportamento específico