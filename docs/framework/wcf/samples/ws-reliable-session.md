---
title: WS 信頼できるセッション
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d7b28968a77f03a622c67acdb58e239593199a2
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="ws-reliable-session"></a><span data-ttu-id="efbf6-102">WS 信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="efbf6-102">WS Reliable Session</span></span>
<span data-ttu-id="efbf6-103">このサンプルでは、信頼できるセッションの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="efbf6-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="efbf6-104">信頼できるセッションは、信頼できるメッセージとセッションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="efbf6-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="efbf6-105">信頼できるメッセージは、エラー時に通信を再試行するほか、メッセージの順次到着などの配信の保証を指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="efbf6-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="efbf6-106">セッションでは、呼び出し間でクライアントの状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="efbf6-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="efbf6-107">サンプルでは、クライアントの状態を保持するセッションを実装し、配信順序を保証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="efbf6-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="efbf6-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="efbf6-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="efbf6-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="efbf6-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="efbf6-110">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="efbf6-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="efbf6-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="efbf6-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="efbf6-112">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="efbf6-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="efbf6-113">信頼できるセッション機能は、クライアントとサービスのアプリケーション構成ファイルで有効化され、構成されています。</span><span class="sxs-lookup"><span data-stu-id="efbf6-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="efbf6-114">このサンプルでは、サービスはインターネット インフォメーション サービス (IIS) によってホストされており、クライアントはコンソール アプリケーション (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="efbf6-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efbf6-115">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efbf6-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="efbf6-116">このサンプルでは、`wsHttpBinding` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="efbf6-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="efbf6-117">バインディングは、クライアントとサービスの両方の構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="efbf6-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="efbf6-118">バインディングの種類はエンドポイント要素の `binding` 属性に指定します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efbf6-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="efbf6-119">エンドポイントには、"Binding1" という名前のバインディング構成を参照する `bindingConfiguration` 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="efbf6-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="efbf6-120">バインド構成により、信頼できるセッションの設定、`enabled`の属性、 [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)に`true`です。</span><span class="sxs-lookup"><span data-stu-id="efbf6-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="efbf6-121">順序付きセッションの配信の保証は、ordered 属性を `true` または `false` に設定することによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="efbf6-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="efbf6-122">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="efbf6-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="efbf6-123">サービス実装クラスは、クライアントごとに個別のクラスのインスタンスをインスタンス化して保持する <xref:System.ServiceModel.InstanceContextMode.PerSession> を実装します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="efbf6-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="efbf6-124">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="efbf6-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="efbf6-125">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="efbf6-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="efbf6-126">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="efbf6-126">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="efbf6-127">次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="efbf6-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="efbf6-128">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="efbf6-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="efbf6-129">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="efbf6-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="efbf6-130">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="efbf6-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efbf6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="efbf6-131">See Also</span></span>
