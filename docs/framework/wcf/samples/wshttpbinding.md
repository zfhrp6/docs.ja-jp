---
title: WSHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 522042606681fe2dfc0ee2bc10b5a5f062a93d55
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wshttpbinding"></a><span data-ttu-id="3405b-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3405b-102">WSHttpBinding</span></span>
<span data-ttu-id="3405b-103">このサンプルでは、一般的なサービスと一般的なクライアントを、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3405b-103">This sample demonstrates how to implement a typical service and a typical client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="3405b-104">このサンプルは、クライアント コンソール プログラム (client.exe) と、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリで構成されています。</span><span class="sxs-lookup"><span data-stu-id="3405b-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="3405b-105">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="3405b-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="3405b-106">このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (加算、減算、乗算、および 除算) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="3405b-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="3405b-107">クライアントは指定された算術演算を同期要求し、サービスは結果と共に応答します。</span><span class="sxs-lookup"><span data-stu-id="3405b-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="3405b-108">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3405b-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3405b-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3405b-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3405b-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3405b-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3405b-111">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="3405b-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3405b-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3405b-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="3405b-113">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3405b-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3405b-114">このサンプルでは公開、`ICalculator`コントラクトを使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="3405b-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="3405b-115">このバインディングの構成は、次のように Web.config ファイルで展開されています。</span><span class="sxs-lookup"><span data-stu-id="3405b-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="3405b-116">ベース `binding` 要素で `maxReceivedMessageSize` 値を使用すると、受信メッセージの最大サイズ (バイト単位) を構成できます。</span><span class="sxs-lookup"><span data-stu-id="3405b-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="3405b-117">`hostNameComparisonMode` 値を使用すると、メッセージの非多重化を行ってサービスに変換する際にホスト名を考慮するかどうかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3405b-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="3405b-118">`messageEncoding` 値を使用すると、メッセージのテキスト エンコーディングまたは MTOM エンコーディングを使用するかどうかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3405b-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="3405b-119">`textEncoding` 値を使用すると、メッセージの文字エンコーディングを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3405b-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="3405b-120">`bypassProxyOnLocal` 値を使用すると、ローカル通信に HTTP プロキシを使用するかどうかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3405b-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="3405b-121">現在のトランザクションをフローするかどうかは、`transactionFlow` 値で構成されます (操作がトランザクション フロー用に構成されている場合)。</span><span class="sxs-lookup"><span data-stu-id="3405b-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="3405b-122">[ \<ReliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)要素、有効なブール値は、信頼できるセッションが有効になっているかどうかを構成します。</span><span class="sxs-lookup"><span data-stu-id="3405b-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="3405b-123">メッセージの順序が保持されるかどうかは、`ordered` 値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="3405b-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="3405b-124">エラーになる前の、セッションのアイドル状態の期間は、`inactivityTimeout` 値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="3405b-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="3405b-125">[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)、`mode`をどのセキュリティ モードを使用する必要があります値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="3405b-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="3405b-126">このサンプルでメッセージ セキュリティが使用されて、その理由は、 [\<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)内側で指定されて、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="3405b-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="3405b-127">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3405b-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3405b-128">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3405b-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3405b-129">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="3405b-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3405b-130">次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="3405b-130">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="3405b-131">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="3405b-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="3405b-132">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3405b-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="3405b-133">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="3405b-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3405b-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3405b-134">See Also</span></span>
