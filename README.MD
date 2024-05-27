# Testes de Unidade em Aplicações .NET 5
Este repositório contém exemplos de implementação de testes de unidade em aplicações baseadas no .NET 5, utilizando os frameworks xUnit, NUnit e MSTest. Cada seção abaixo detalha a aplicação dos testes e fornece dois cenários de exemplo.

## Testes com xUnit
### Aplicação dos Testes
xUnit é um dos frameworks mais populares para a realização de testes de unidade no .NET. Ele permite a criação de testes parametrizados utilizando os atributos `Theory` e `InlineData`. Esses atributos facilitam a passagem de múltiplos conjuntos de dados para o método de teste, garantindo que diferentes cenários sejam cobertos.

### Exemplos de Cenários
- Conversão de 32°F para 0°C
- Conversão de 90.5°F para 32.5°C

```
using System;
using Xunit;

namespace Temperatura.Testes
{
    public class TestesConversorTemperatura
    {
        [Theory]
        [InlineData(32, 0)]
        [InlineData(90.5, 32.5)]
        public void TestarConversaoTemperatura(double fahrenheit, double celsius)
        {
            double valorCalculado = ConversorTemperatura.FahrenheitParaCelsius(fahrenheit);
            Assert.Equal(celsius, valorCalculado);
        }
    }
}
```
## Testes com NUnit
### Aplicação dos Testes
NUnit é outro framework amplamente utilizado para testes de unidade em .NET. Ele oferece o atributo `TestCase`, que permite especificar diferentes conjuntos de dados diretamente nos métodos de teste. Isso simplifica a validação de múltiplos casos de teste dentro de um único método.

### Exemplos de Cenários
Conversão de 47°F para 8.33°C
Conversão de 212°F para 100°C

```
using NUnit.Framework;

namespace Temperatura.Testes
{
    public class TestesConversorTemperatura
    {
        [TestCase(47, 8.33)]
        [TestCase(212, 100)]
        public void TesteConversaoTemperatura(double tempFahrenheit, double tempCelsius)
        {
            double valorCalculado = ConversorTemperatura.FahrenheitParaCelsius(tempFahrenheit);
            Assert.AreEqual(tempCelsius, valorCalculado);
        }
    }
}
```
## Testes com MSTest
### Aplicação dos Testes
MSTest é o framework de testes padrão oferecido pela Microsoft para aplicações .NET. Utiliza os atributos `DataTestMethod` e `DataRow` para criar testes parametrizados, permitindo a definição de diferentes conjuntos de dados que são aplicados ao método de teste.

### Exemplos de Cenários
- Conversão de 86°F para 30°C
- Conversão de 120.18°F para 48.99°C

```
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace Temperatura.Testes
{
    [TestClass]
    public class TestesConversorTemperatura
    {
        [DataRow(86, 30)]
        [DataRow(120.18, 48.99)]
        [DataTestMethod]
        public void TesteConversaoTemperatura(double tempFahrenheit, double tempCelsius)
        {
            double valorCalculado = ConversorTemperatura.FahrenheitParaCelsius(tempFahrenheit);
            Assert.AreEqual(tempCelsius, valorCalculado);
        }
    }
}
```