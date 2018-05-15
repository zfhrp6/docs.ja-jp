---
title: .NET Framework 4 で実行されている IIS 内の .NET Framework 3.5 で作成された WCF サービスをホストする方法
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: 83343cef119f6c8b97fd8f1be50c229c64b10227
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="d594d-102">.NET Framework 4 で実行されている IIS 内の .NET Framework 3.5 で作成された WCF サービスをホストする方法</span><span class="sxs-lookup"><span data-stu-id="d594d-102">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>
<span data-ttu-id="d594d-103">記述された Windows Communication Foundation (WCF) サービスをホストする場合に[!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]実行しているコンピューターで[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]、受け取ることがあります、<xref:System.ServiceModel.ProtocolException>を次のテキスト。</span><span class="sxs-lookup"><span data-stu-id="d594d-103">When hosting a Windows Communication Foundation (WCF) service written with [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] on a machine running [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>  
  
```Output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="d594d-104">または、サービスの .svc ファイルを参照する際に、次のテキストのエラー ページが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d594d-104">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```Output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="d594d-105">これらのエラーは、IIS が実行されているアプリケーション ドメインが [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] を実行していて、WCF サービスが [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] で実行されるように構成されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="d594d-105">These errors occur because the application domain IIS is running within is running [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] and the WCF service is expecting to run under [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="d594d-106">このトピックでは、このサービスを実行するために必要な変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="d594d-106">This topic explains the modifications required to get the service to run.</span></span>  
  
 <span data-ttu-id="d594d-107">次の検索、<`compilers`> 要素と 4.0 の値を持つ CompilerVersion プロバイダー オプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="d594d-107">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="d594d-108">既定では、2 つ <`compiler`> の下の要素、<`compilers`> 要素。</span><span class="sxs-lookup"><span data-stu-id="d594d-108">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="d594d-109">次の例に示すように、両方の CompilerVersion プロバイダー オプションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d594d-109">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="d594d-110">必要な targetFramework 属性の追加</span><span class="sxs-lookup"><span data-stu-id="d594d-110">Add the required targetFramework attribute</span></span>  
  
1.  <span data-ttu-id="d594d-111">サービスの Web.config ファイルを開き、検索、<`compilation`> 要素。</span><span class="sxs-lookup"><span data-stu-id="d594d-111">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2.  <span data-ttu-id="d594d-112">追加、`targetFramework`属性を <`compilation`> 要素の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="d594d-112">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3.  <span data-ttu-id="d594d-113">検索、<`compilers`> 要素と 4.0 の値を持つ CompilerVersion プロバイダー オプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="d594d-113">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="d594d-114">既定では、2 つ <`compiler`> の下の要素、<`compilers`> 要素。</span><span class="sxs-lookup"><span data-stu-id="d594d-114">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="d594d-115">次の例に示すように、両方の CompilerVersion プロバイダー オプションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d594d-115">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
