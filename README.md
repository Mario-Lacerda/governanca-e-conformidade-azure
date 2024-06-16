# Desafio Dio - Primeiros Passos com Governança e Conformidade na Azure



####     Projeto ainda mais completo e abrangente com mais códigos para: Primeiros Passos com Governança e Conformidade na Azure

**Projeto ainda mais completo e abrangente com mais códigos para: Primeiros Passos com Governança e Conformidade na Azure**

**Introdução**

Este projeto irá guiá-lo pelos fundamentos da governança e conformidade no Microsoft Azure, uma plataforma de computação em nuvem que oferece uma ampla gama de serviços para ajudá-lo a construir, implantar e gerenciar seus aplicativos de forma segura e compatível.



### **Pré-requisitos**

- Uma conta do Microsoft Azure

- O Visual Studio 2019 ou superior

- O .NET Core SDK 3.1 ou superior

  

### **Instruções**

1. **Crie um novo projeto do Visual Studio.**

2. **Selecione o modelo "Aplicativo Web do ASP.NET Core".**

3. **Nomeie o projeto como "AzureGovernanceAndComplianceInAction".**

4. **Clique em "Criar".**

   

5. #### Adicione os seguintes pacotes NuGet ao projeto:

   

   - Microsoft.Azure.Management.Governance

   - Microsoft.Azure.Management.ResourceManager

     

6. #### Adicione as seguintes classes ao projeto:

   

   - **GovernanceService.cs:** Esta classe fornece métodos para interagir com o serviço de governança do Azure.

   - **ResourceManagerService.cs:** Esta classe fornece métodos para interagir com o serviço Resource Manager do Azure.

     

7. #### **Adicione o seguinte código ao arquivo "Startup.cs":**

   

csharp



```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton<IGovernanceService, GovernanceService>();
    services.AddSingleton<IResourceManagerService, ResourceManagerService>();
}
```



1. **Adicione o seguinte código ao arquivo "Controllers/HomeController.cs":**

   

csharp



```csharp
public class HomeController : Controller
{
    private readonly IGovernanceService _governanceService;
    private readonly IResourceManagerService _resourceManagerService;

    public HomeController(IGovernanceService governanceService, IResourceManagerService resourceManagerService)
    {
        _governanceService = governanceService;
        _resourceManagerService = resourceManagerService;
    }

    public IActionResult Index()
    {
        return View();
    }

    [HttpPost]
    public async Task<IActionResult> CreatePolicyAssignment(string scope, string policyDefinitionId)
    {
        await _governanceService.CreatePolicyAssignmentAsync(scope, policyDefinitionId);

        return RedirectToAction("Index");
    }

    [HttpPost]
    public async Task<IActionResult> ListResources(string scope)
    {
        var resources = await _resourceManagerService.ListResourcesAsync(scope);

        return View("Resources", resources);
    }
}
```



1. #### **Execute o projeto.**



## **Conclusão**



Este projeto fornece uma base ainda mais sólida para você começar a implementar governança e conformidade na nuvem no Microsoft Azure. Você pode usar o serviço de governança para criar e gerenciar atribuições de políticas e usar o serviço Resource Manager para listar recursos em seu escopo.

