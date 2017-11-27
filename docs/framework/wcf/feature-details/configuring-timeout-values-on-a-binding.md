---
title: "バインディングでのタイムアウト値の構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 458f2143021ac40bfcaddbe957113e400bd5f3c5
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2017
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="2a617-102">バインディングでのタイムアウト値の構成</span><span class="sxs-lookup"><span data-stu-id="2a617-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="2a617-103">WCF バインディングには、さまざまなタイムアウト設定が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2a617-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="2a617-104">これらのタイムアウト設定を正しく行うことによって、サービスのパフォーマンスが向上するだけでなく、サービスの操作性とセキュリティにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2a617-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="2a617-105">WCF バインディングで使用できるタイムアウトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2a617-105">The following timeouts are available on WCF bindings:</span></span>  
  
1.  <span data-ttu-id="2a617-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="2a617-106">OpenTimeout</span></span>  
  
2.  <span data-ttu-id="2a617-107">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="2a617-107">CloseTimeout</span></span>  
  
3.  <span data-ttu-id="2a617-108">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="2a617-108">SendTimeout</span></span>  
  
4.  <span data-ttu-id="2a617-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="2a617-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="2a617-110">WCF バインディングのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="2a617-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="2a617-111">このトピックで説明する各設定は、バインディング自体に対して、コードまたは構成を使用して適用されます。</span><span class="sxs-lookup"><span data-stu-id="2a617-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="2a617-112">次のコードは、自己ホスト型サービスのコンテキストで、WCF バインディングのタイムアウトをプログラムで設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2a617-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");
    
    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));
        
        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);
        
        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();
        
        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 <span data-ttu-id="2a617-113">次の例は、構成ファイル内でバインディングのタイムアウトを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2a617-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00" 
                 closeTimeout="00:10:00" 
                 sendTimeout="00:10:00" 
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="2a617-114">これらの設定の詳細については、<xref:System.ServiceModel.Channels.Binding> クラスに関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a617-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="2a617-115">サービス側のタイムアウト</span><span class="sxs-lookup"><span data-stu-id="2a617-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="2a617-116">クライアント側のタイムアウトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2a617-116">On the client side:</span></span>  
  
1.  <span data-ttu-id="2a617-117">SendTimeout: OperationTimeout の初期化に使用します。要求/応答サービス操作の応答メッセージの受信を含め、メッセージの送信プロセス全体を制御します。</span><span class="sxs-lookup"><span data-stu-id="2a617-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="2a617-118">このタイムアウトは、コールバック コントラクト メソッドから応答メッセージを送信するときにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="2a617-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2.  <span data-ttu-id="2a617-119">OpenTimeout: 明示的なタイムアウト値が指定されていない場合、チャネルを開くときに使用します。</span><span class="sxs-lookup"><span data-stu-id="2a617-119">OpenTimeout – used when opening channels when no explicit timeout value is specified</span></span>  
  
3.  <span data-ttu-id="2a617-120">CloseTimeout: 明示的なタイムアウト値が指定されていない場合、チャネルを閉じるときに使用します。</span><span class="sxs-lookup"><span data-stu-id="2a617-120">CloseTimeout – used when closing channels when no explicit timeout value is specified</span></span>  
  
4.  <span data-ttu-id="2a617-121">ReceiveTimeout: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="2a617-121">ReceiveTimeout – is not used</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="2a617-122">サービス側のタイムアウト</span><span class="sxs-lookup"><span data-stu-id="2a617-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="2a617-123">サービス側のタイムアウトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2a617-123">On the service side:</span></span>  
  
1.  <span data-ttu-id="2a617-124">SendTimeout、OpentTimeout、CloseTimeout は、クライアント側と同じです。</span><span class="sxs-lookup"><span data-stu-id="2a617-124">SendTimeout, OpentTimeout, CloseTimeout are the same as on the client</span></span>  
  
2.  <span data-ttu-id="2a617-125">ReceiveTimeout: セッションがタイムアウトするまでのアイドル状態の時間を制御するセッション アイドル タイムアウトを初期化するために Service Framework Layer で使用します。</span><span class="sxs-lookup"><span data-stu-id="2a617-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
