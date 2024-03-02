# Introdução a testes no Python 

**Exercício - gravar um teste de unidade com o módulo unittest**

- função str_to_bool()
- bloco try/except na função str_to_bool() que captura AttributeError.
- classe de teste TestStrToBool() que herda de unittest.TestCase.
- três métodos de teste que testam entradas para a função str_to_bool().

**Tipos de testes**

*Teste de Unidade*
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

_Integração Contínua_
CI ambiente onde é executado testes automáticos.