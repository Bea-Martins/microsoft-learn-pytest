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
-Não são tão rápidos quanto os testes de unidade e tendem a exigir mais configuração inicial antes de serem executados.
-Funções, métodos ou classes são testados com funcionalidade em outras funções, métodos ou classes.
-Um serviço externo pode ser usado, mas nem todos os serviços do aplicativo.

Como os testes funcionais exigem mais serviços, uma reprodução do ambiente de produção e a configuração mais complexa dos tipos de teste, geralmente consumirão tempo e muitos recursos.

_Integração Contínua_: CI ambiente onde é executado testes automáticos.

# Fazer testes com o Pytest

**Classes de teste e métodos de teste**

Convenções:
- As classes de teste têm o prefixo ```Test```
- Os métodos de teste têm o prefixo ```test_```

**Métodos auxiliares**

setup: é executado uma vez antes de cada teste em uma classe
teardown: é executado uma vez após cada teste em uma classe
setup_class: é executado uma vez antes de todos os testes em uma classe
teardown_class: é executado uma vez após todos os testes em uma classe

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
