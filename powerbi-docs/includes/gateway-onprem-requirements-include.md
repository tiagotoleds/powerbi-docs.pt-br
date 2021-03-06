## <a name="requirements"></a>Requisitos
**Requisitos mínimos:**

* .NET 4.6 Framework
* Versão de 64 bits do Windows 7 / Windows Server 2008 R2 (ou posterior)

**Recomendado:**

* CPU de 8 núcleos
* 8 GB de memória
* Versão de 64 bits do Windows 2012 R2 (ou posterior)

**Considerações relacionadas:**

* O gateway não pode ser instalado em um controlador de domínio
* Se você estiver planejando usar a autenticação do Windows, instale o gateway em um computador que seja membro do mesmo ambiente do Active Directory das fontes de dados.
* Você não deve instalar o gateway em um computador, por exemplo um laptop, que possa ser desativado, colocado em suspensão ou que não possa ser conectado à Internet, porque o gateway não pode ser executado sob nenhuma dessas circunstâncias. Além disso, pode haver perda de desempenho do gateway em caso de uso via rede sem fio.
* O Analysis Services não é necessário para usar o gateway. Você pode usar o gateway para se conectar a uma fonte de dados do Analysis Services.

