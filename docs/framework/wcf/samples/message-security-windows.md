---
title: "メッセージ セキュリティ Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
caps.latest.revision: "34"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c8bb8d0506dd535a312bd8df8954c8143d9543ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-windows"></a><span data-ttu-id="56544-102">メッセージ セキュリティ Windows</span><span class="sxs-lookup"><span data-stu-id="56544-102">Message Security Windows</span></span>
<span data-ttu-id="56544-103">このサンプルでは、Windows 認証によるメッセージ レベルのセキュリティを使用するよう <xref:System.ServiceModel.WSHttpBinding> バインディングを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="56544-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="56544-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="56544-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="56544-105">このサンプルでは、サービスはインターネット インフォメーション サービス (IIS) によってホストされており、クライアントはコンソール アプリケーション (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="56544-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56544-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56544-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="56544-107">既定のセキュリティ、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)メッセージ セキュリティが Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="56544-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="56544-108">このサンプルでは、構成ファイルが明示的に設定、`mode`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)に`Message`と`clientCredentialType`属性を`Windows`です。</span><span class="sxs-lookup"><span data-stu-id="56544-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="56544-109">これらの値はこのバインディングの既定値ですが、明示的に構成されています。これらの使用例を示すサンプル構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="56544-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="56544-110">クライアント エンドポイント構成は、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="56544-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="56544-111">クライアント バインディングは、適切な `securityMode` と `authenticationMode` で構成されます。</span><span class="sxs-lookup"><span data-stu-id="56544-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"   
            binding="wsHttpBinding"   
            bindingConfiguration="Binding1"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      <!--The default security for the WSHttpBinding is-->  
      <!--Message security using Windows authentication. -->  
      <!--This configuration explicitly defines the security mode -->  
      <!--as Message and the clientCredentialType as Windows  -->  
      <!--for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="56544-112">サービス ソース コードは、<xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> を使用して呼び出し元の ID へのアクセスを可能にする方法を示すように変更されています。</span><span class="sxs-lookup"><span data-stu-id="56544-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```  
  
 <span data-ttu-id="56544-113">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="56544-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="56544-114">最初に呼び出されるメソッド `GetCallerIdentity` は、呼び出し元の ID の名前をクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="56544-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="56544-115">クライアントをシャットダウンするには、コンソール ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="56544-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="56544-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="56544-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="56544-117">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="56544-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="56544-118">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="56544-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="56544-119">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="56544-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56544-120">参照</span><span class="sxs-lookup"><span data-stu-id="56544-120">See Also</span></span>
