---
title: "WCF トラブルシューティング クイックスタート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d464042411b2d06368bb596e6d8d1dc0976808e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="af909-102">WCF トラブルシューティング クイックスタート</span><span class="sxs-lookup"><span data-stu-id="af909-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="af909-103">このトピックでは、WCF クライアントと WCF サービスの開発時に生じるさまざまな既知の問題の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="af909-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="af909-104">発生している問題がこの一覧にない場合は、サービスに対してトレースを構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="af909-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="af909-105">これにより、トレース ファイル ビューアーで表示し、サービス内で発生することがある例外に関する詳細情報を取得できるトレース ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="af909-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="af909-106">トレースの構成の詳細については、「 [Configuring Tracing](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af909-106">For more information on configuring tracing, see: [Configuring Tracing](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="af909-107">トレース ファイル ビューアーの詳細については、「 [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af909-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1.  [<span data-ttu-id="af909-108">Windows 7 と IIS のインストール後に WCF サービスを参照しようとすると、"HTTP エラー 404.3 - Not Found" というエラー メッセージが表示されます</span><span class="sxs-lookup"><span data-stu-id="af909-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     <span data-ttu-id="af909-109">HTTP エラー 404.3 - Not Found 拡張構成により、要求しているページは使用できません。</span><span class="sxs-lookup"><span data-stu-id="af909-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="af909-110">ページがスクリプトの場合は、ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="af909-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="af909-111">ファイルをダウンロードする場合は、MIME マップを追加します。</span><span class="sxs-lookup"><span data-stu-id="af909-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="af909-112">エラーの詳細: InformationModule StaticFileModule。</span><span class="sxs-lookup"><span data-stu-id="af909-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2.  [<span data-ttu-id="af909-113">最初の要求の後でクライアントがしばらくアイドル状態になった場合、2 番目の要求で MessageSecurityException を受け取ることがあります。どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [<span data-ttu-id="af909-114">サービスと対話しているクライアントの数が約 10 個になると、サービスが新しいクライアントを拒否し始めます。どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [<span data-ttu-id="af909-115">WCF アプリケーションの構成ファイル以外の場所からサービス構成を読み込むことはできますか。</span><span class="sxs-lookup"><span data-stu-id="af909-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [<span data-ttu-id="af909-116">サービスとクライアントの動作に問題はないのですが、クライアントが別のコンピューター上にあるときにサービスとクライアントがうまく動作しません。どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [<span data-ttu-id="af909-117">FaultException をスローするときに\<例外 > 型では、例外は、必ずクライアントで一般的な FaultException 型とジェネリック型ではなく受け取ります。どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [<span data-ttu-id="af909-118">応答にデータがない場合、一方向操作と要求/応答操作が戻る速度がほぼ同じになるようです。どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [<span data-ttu-id="af909-119">サービスで X.509 証明書を使用していますが、System.Security.Cryptography.CryptographicException を受け取ります。どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [<span data-ttu-id="af909-120">操作の最初のパラメーターを大文字から小文字に変更したら、クライアントが例外をスローするようになりました。どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [<span data-ttu-id="af909-121">トレース ツールの 1 つを使用していますが、EndpointNotFoundException を受け取りました。どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [<span data-ttu-id="af909-122">WCF SOAP アプリケーションから WCF Web HTTP アプリケーションを呼び出すと、サービスから "405 メソッドは許可されていません" というエラーが返されます</span><span class="sxs-lookup"><span data-stu-id="af909-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [<span data-ttu-id="af909-123">ベース アドレスについて教えてください。エンドポイント アドレスとどのように関連していますか。</span><span class="sxs-lookup"><span data-stu-id="af909-123">What is the base address? How does it relate to an endpoint address?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="af909-124">Windows 7 と IIS のインストール後に WCF サービスを参照しようとすると、"HTTP エラー 404.3 - Not Found" というエラー メッセージが表示されます</span><span class="sxs-lookup"><span data-stu-id="af909-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="af909-125">エラー メッセージの全文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="af909-125">The full error message is:</span></span>  
  
 <span data-ttu-id="af909-126">HTTP エラー 404.3 - Not Found 拡張構成により、要求しているページは使用できません。</span><span class="sxs-lookup"><span data-stu-id="af909-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="af909-127">ページがスクリプトの場合は、ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="af909-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="af909-128">ファイルをダウンロードする場合は、MIME マップを追加します。</span><span class="sxs-lookup"><span data-stu-id="af909-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="af909-129">エラーの詳細: InformationModule StaticFileModule。</span><span class="sxs-lookup"><span data-stu-id="af909-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="af909-130">このエラー メッセージは、コントロール パネルで"Windows Communication Foundation HTTP Activation が明示的に設定されていない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="af909-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="af909-131">これを設定するには、コントロール パネルに移動し、ウィンドウの左下にある [プログラム] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af909-131">To set this go to the Control Panel, click Programs in the lower left hand corner of the window.</span></span> <span data-ttu-id="af909-132">[Windows の機能の有効化または無効化] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af909-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="af909-133">[Microsoft .NET Framework 3.5.1] を展開し、[Windows Communication Foundation HTTP Activation] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="af909-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="af909-134">最初の要求の後でクライアントがしばらくアイドル状態になった場合、2 番目の要求で MessageSecurityException を受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="af909-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="af909-135">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-135">What is happening?</span></span>  
 <span data-ttu-id="af909-136">2 番目の要求は、主に次の 2 つの理由から失敗する可能性があります。(1) セッションがタイムアウトした。(2) サービスをホストしている Web サーバーがリサイクルされている。</span><span class="sxs-lookup"><span data-stu-id="af909-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="af909-137">最初の理由の場合、セッションはサービスがタイムアウトするまで有効です。サービスは、サービスのバインディング (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>) で指定された期間内にクライアントから要求を受信しなかった場合、セキュリティ セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="af909-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="af909-138">それ以降のクライアント メッセージでは、 <xref:System.ServiceModel.Security.MessageSecurityException>が発生します。</span><span class="sxs-lookup"><span data-stu-id="af909-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="af909-139">クライアントは、セキュリティで保護されたセッションをサービスとの間に再度確立して、後続のメッセージを送信するか、ステートフルなセキュリティ コンテキスト トークンを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="af909-140">また、ステートフルなセキュリティ コンテキスト トークンによって、セキュリティで保護されたセッションは、再利用される Web サーバーで存続することができます。</span><span class="sxs-lookup"><span data-stu-id="af909-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="af909-141">セキュリティで保護されたセッションでステートフルなセキュリティ コンテキスト トークンを使用して、参照してください[する方法: セキュリティで保護されたセッションのセキュリティ コンテキスト トークンを作成](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="af909-141"> using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="af909-142">また、セキュリティで保護されたセッションは無効にできます。</span><span class="sxs-lookup"><span data-stu-id="af909-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="af909-143">使用すると、 [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 、バインドを設定できます、`establishSecurityContext`プロパティを`false`をセキュリティで保護されたセッションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="af909-143">When you use the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="af909-144">その他のバインディングでセキュリティで保護されたセッションを無効にするには、カスタム バインディングを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="af909-145">カスタム バインディングの作成の詳細については、「 [How to: Create a Custom Binding Using the SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af909-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="af909-146">このオプションを適用する前に、アプリケーションのセキュリティ要件を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="af909-147">サービスと対話しているクライアントの数が約 10 個になると、サービスが新しいクライアントを拒否し始めます。</span><span class="sxs-lookup"><span data-stu-id="af909-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="af909-148">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-148">What is happening?</span></span>  
 <span data-ttu-id="af909-149">既定では、サービスは、10 個の同時セッションだけをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="af909-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="af909-150">したがって、サービス バインディングでセッションを使用する場合、サービスは 10 個に到達するまで新しいクライアント接続を受け入れますが、その数に到達した後は、現在実行中のセッションの 1 つが終了するまで新しいクライアント接続を拒否します。</span><span class="sxs-lookup"><span data-stu-id="af909-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="af909-151">いくつかの方法で、より多くのクライアントをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="af909-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="af909-152">サービスにセッションが必要ない場合、セッションの多いバインディングを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="af909-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="af909-153">([!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [セッションを使用して](../../../docs/framework/wcf/using-sessions.md))。他には、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> プロパティの値をユーザーの環境に適した数値に変更することによって、セッションの制限値を増やす方法があります。</span><span class="sxs-lookup"><span data-stu-id="af909-153">([!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Using Sessions](../../../docs/framework/wcf/using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="af909-154">WCF アプリケーションの構成ファイル以外の場所からサービス構成を読み込むことはできますか。</span><span class="sxs-lookup"><span data-stu-id="af909-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="af909-155">できます。ただし、 <xref:System.ServiceModel.ServiceHost> メソッドをオーバーライドするカスタムの <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> クラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="af909-156">そのメソッドでは、ベースを呼び出して最初に構成を読み込むことができますが (標準の構成情報も読み込む場合)、構成読み込みシステム全体を置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="af909-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="af909-157">アプリケーションの構成ファイルとは異なる構成ファイルから構成を読み込む場合は、構成ファイルを自分で解析して構成を読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-157">Note that if you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="af909-158"><xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> メソッドをオーバーライドし、エンドポイントを直接構成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="af909-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>   
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="af909-159">サービスとクライアントの動作に問題はないのですが、クライアントが別のコンピューター上にあるときにサービスとクライアントがうまく動作しません。</span><span class="sxs-lookup"><span data-stu-id="af909-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="af909-160">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-160">What’s happening?</span></span>  
 <span data-ttu-id="af909-161">例外によっては、次のようないくつかの問題が存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af909-161">Depending upon the exception, there may be several issues:</span></span>  
  
-   <span data-ttu-id="af909-162">場合によっては、クライアントのエンドポイント アドレスを "localhost" ではなくホスト名に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
-   <span data-ttu-id="af909-163">場合によっては、アプリケーションに対してポートを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-163">You might need to open the port to the application.</span></span> <span data-ttu-id="af909-164">詳細については、SDK サンプルから「 [Firewall Instructions](../../../docs/framework/wcf/samples/firewall-instructions.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af909-164">For details, see [Firewall Instructions](../../../docs/framework/wcf/samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
-   <span data-ttu-id="af909-165">考えられる他の問題については、サンプル トピックの「 [Running the Samples in a Workgroup and Across Machines](http://msdn.microsoft.com/en-us/a451a525-e7ce-452d-9da9-620221260113)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af909-165">For other possible issues, see the samples topic [Running the Samples in a Workgroup and Across Machines](http://msdn.microsoft.com/en-us/a451a525-e7ce-452d-9da9-620221260113).</span></span>  
  
-   <span data-ttu-id="af909-166">クライアントが Windows 資格情報を使用し、例外が <xref:System.ServiceModel.Security.SecurityNegotiationException>の場合、次のように Kerberos を設定します。</span><span class="sxs-lookup"><span data-stu-id="af909-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1.  <span data-ttu-id="af909-167">クライアントの App.config ファイルのエンドポイント要素に ID 資格情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="af909-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
        ```xml
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2.  <span data-ttu-id="af909-168">System または NetworkService アカウントで自己ホスト型サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="af909-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="af909-169">次のコマンドを実行すると、System アカウントでコマンド ウィンドウを作成できます。</span><span class="sxs-lookup"><span data-stu-id="af909-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  <span data-ttu-id="af909-170">既定でサービス プリンシパル名 (SPN) アカウントを使用するインターネット インフォメーション サービス (IIS) でのサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="af909-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4.  <span data-ttu-id="af909-171">SetSPN を使用してドメインに新しい SPN を登録します。</span><span class="sxs-lookup"><span data-stu-id="af909-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="af909-172">この操作を行えるのは、ドメイン管理者のみです。</span><span class="sxs-lookup"><span data-stu-id="af909-172">Note that you will need to be a domain administrator in order to do this.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="af909-173"> については、「 [Security Concepts Used in WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) 」および以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af909-173"> the Kerberos protocol, see [Security Concepts Used in WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
-   [<span data-ttu-id="af909-174">Windows 認証エラーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="af909-174">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [<span data-ttu-id="af909-175">Http.sys を使用した Kerberos サービス プリンシパル名の登録</span><span class="sxs-lookup"><span data-stu-id="af909-175">Registering Kerberos Service Principal Names by Using Http.sys</span></span>](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [<span data-ttu-id="af909-176">Kerberos の説明</span><span class="sxs-lookup"><span data-stu-id="af909-176">Kerberos Explained</span></span>](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="af909-177">FaultException をスローするときに\<例外 > 型では、例外は、必ずクライアントで一般的な FaultException 型とジェネリック型ではなく受け取ります。</span><span class="sxs-lookup"><span data-stu-id="af909-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="af909-178">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-178">What’s happening?</span></span>  
 <span data-ttu-id="af909-179">独自のカスタム エラー データ型を作成し、エラー コントラクトで詳細な型としてその型を宣言することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="af909-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="af909-180">その理由は、システム指定の例外型を使用すると、次のような状況が起こるためです。</span><span class="sxs-lookup"><span data-stu-id="af909-180">The reason is that using system-provided exception types:</span></span>  
  
-   <span data-ttu-id="af909-181">サービス指向アプリケーションの長所の 1 つを排除する型依存関係が作成されます。</span><span class="sxs-lookup"><span data-stu-id="af909-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
-   <span data-ttu-id="af909-182">標準的な方法でシリアル化している例外に依存できません。</span><span class="sxs-lookup"><span data-stu-id="af909-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="af909-183"><xref:System.Security.SecurityException>のような例外はまったくシリアル化できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af909-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
-   <span data-ttu-id="af909-184">クライアントに内部実装の詳細が公開されます。</span><span class="sxs-lookup"><span data-stu-id="af909-184">Exposes internal implementation details to clients.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="af909-185">[コントラクトおよびサービスでエラー指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="af909-185"> [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="af909-186">ただし、アプリケーションをデバッグしている場合、 <xref:System.ServiceModel.Description.ServiceDebugBehavior> クラスを使用することによって例外情報をシリアル化して、その情報をクライアントに返すことができます。</span><span class="sxs-lookup"><span data-stu-id="af909-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="af909-187">応答にデータがない場合、一方向操作と要求/応答操作が戻る速度がほぼ同じになるようです。</span><span class="sxs-lookup"><span data-stu-id="af909-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="af909-188">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-188">What's happening?</span></span>  
 <span data-ttu-id="af909-189">操作を一方向に指定すると、操作コントラクトは入力メッセージを受け入れるだけで、出力メッセージを返しません。</span><span class="sxs-lookup"><span data-stu-id="af909-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="af909-190">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]では、送信データがネットワークに書き込まれるか、例外がスローされたとき、すべてのクライアント呼び出しが戻ります。</span><span class="sxs-lookup"><span data-stu-id="af909-190">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="af909-191">一方向操作は同様に動作し、この操作では、サービスが見つからない場合は例外をスローし、サービスがネットワークからのデータの受け入れ準備を完了していない場合はブロックできます。</span><span class="sxs-lookup"><span data-stu-id="af909-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="af909-192">このため、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]では通常、一方向呼び出しは要求/応答よりも速くクライアントに戻りますが、ネットワーク上でデータの送信速度が遅くなると、一方向操作の速度も要求/応答操作の速度と同様に遅くなります。</span><span class="sxs-lookup"><span data-stu-id="af909-192">Typically in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="af909-193">[一方向サービス](../../../docs/framework/wcf/feature-details/one-way-services.md)と[WCF クライアントを使用してサービスにアクセスする](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="af909-193"> [One-Way Services](../../../docs/framework/wcf/feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="af909-194">サービスで X.509 証明書を使用していますが、System.Security.Cryptography.CryptographicException を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="af909-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="af909-195">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-195">What’s happening?</span></span>  
 <span data-ttu-id="af909-196">この例外は通常、IIS ワーカー プロセスの実行に使用しているユーザー アカウントを変更すると発生します。</span><span class="sxs-lookup"><span data-stu-id="af909-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="af909-197">たとえば、 [!INCLUDE[wxp](../../../includes/wxp-md.md)]で、既定のユーザー アカウントを使用して Aspnet_wp.exe を実行しているときにそのアカウントを ASPNET からカスタムのユーザー アカウントに変更した場合、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="af909-197">For example, in [!INCLUDE[wxp](../../../includes/wxp-md.md)], if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="af909-198">秘密キーを使用している場合、そのキーを使用するプロセスには、そのキーを格納しているファイルにアクセスするためのアクセス許可が必要になります。</span><span class="sxs-lookup"><span data-stu-id="af909-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="af909-199">この場合、秘密キーを格納しているファイルについて、プロセスのアカウントに読み取りアクセス権を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="af909-200">たとえば、IIS ワーカー プロセスを Bob というアカウントで実行している場合、秘密キーを格納しているファイルへの読み取りアクセス権を Bob に与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="af909-201"> については、「 [How to: Make X.509 Certificates Accessible to WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af909-201"> how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="af909-202">操作の最初のパラメーターを大文字から小文字に変更したら、クライアントが例外をスローするようになりました。</span><span class="sxs-lookup"><span data-stu-id="af909-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="af909-203">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-203">What's happening?</span></span>  
 <span data-ttu-id="af909-204">操作シグネチャのパラメーター名の値はコントラクトに含まれ、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="af909-204">The value of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="af909-205">ローカル パラメーター名と、クライアント アプリケーションの操作を記述するメタデータを区別する必要がある場合は、<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="af909-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="af909-206">トレース ツールの 1 つを使用していますが、EndpointNotFoundException を受け取りました。</span><span class="sxs-lookup"><span data-stu-id="af909-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="af909-207">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="af909-207">What’s happening?</span></span>  
 <span data-ttu-id="af909-208">使用しているトレース ツールが、システム指定の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] トレース機構でなく、アドレス フィルターの不一致があることを示す <xref:System.ServiceModel.EndpointNotFoundException> を受け取った場合は、 <xref:System.ServiceModel.Description.ClientViaBehavior> クラスを使用してメッセージをトレース ユーティリティに送信し、そのユーティリティがそのメッセージをサービス アドレスにリダイレクトするようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="af909-208">If you are using a tracing tool that is not the system-provided [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="af909-209"><xref:System.ServiceModel.Description.ClientViaBehavior> クラスは、 `Via` アドレス指定ヘッダーを変更して、 `To` アドレス指定ヘッダーで示されている最終受信者とは別に、次のネットワーク アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="af909-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="af909-210">ただし、このとき、エンドポイント アドレスは `To` 値の設定に使用されるので変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="af909-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="af909-211">次のコード例は、クライアント構成ファイルの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="af909-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint   
  address=http://localhost:8000/MyServer/  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="af909-212">ベース アドレスについて教えてください。</span><span class="sxs-lookup"><span data-stu-id="af909-212">What is the base address?</span></span> <span data-ttu-id="af909-213">エンドポイント アドレスとどのように関連していますか。</span><span class="sxs-lookup"><span data-stu-id="af909-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="af909-214">ベース アドレスとは、 <xref:System.ServiceModel.ServiceHost> クラスのルート アドレスです。</span><span class="sxs-lookup"><span data-stu-id="af909-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="af909-215">既定では、 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスをサービス構成に追加する場合、ホストが発行するすべてのエンドポイントの Web サービス記述言語 (WSDL) は、HTTP ベース アドレスから取得され、それにメタデータ動作に提供される相対アドレスと "?wsdl" が追加されます。</span><span class="sxs-lookup"><span data-stu-id="af909-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="af909-216">[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] と IIS では、ベース アドレスは仮想ディレクトリに相当します。</span><span class="sxs-lookup"><span data-stu-id="af909-216">If you are familiar with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="af909-217">NetTcpBinding を使用したサービス エンドポイントと MEX エンドポイント間でのポートの共有</span><span class="sxs-lookup"><span data-stu-id="af909-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="af909-218">サービスのベース アドレスとして net.tcp://MyServer:8080/MyService を指定して次のエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="af909-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="af909-219">次の構成スニペットに示すように、NetTcpBinding 設定の 1 つを変更するとします。</span><span class="sxs-lookup"><span data-stu-id="af909-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="af909-220">次のようなエラーが表示されます: ハンドルされない例外: System.servicemodel.addressalreadyinuseexception:: このエラーを回避するには、別のポートの完全修飾 URL を指定することで IP エンドポイント 0.0.0.0:9000 には既にリスナーがあります次の構成スニペットに示すようには、MEX エンドポイント:</span><span class="sxs-lookup"><span data-stu-id="af909-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="af909-221">WCF SOAP アプリケーションから WCF Web HTTP アプリケーションを呼び出すと、サービスから "405 メソッドは許可されていません" というエラーが返されます</span><span class="sxs-lookup"><span data-stu-id="af909-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="af909-222">WCF Web HTTP アプリケーションを呼び出す (を使用するサービス、<xref:System.ServiceModel.WebHttpBinding>と<xref:System.ServiceModel.Description.WebHttpBehavior>) WCF からサービスは、次の例外を生成可能性があります: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: リモート サーバーが、予期しない応答を返しました: (405) メソッドいない許可済みです。 '、発信 WCF が上書きされるため、この例外が発生した<xref:System.ServiceModel.OperationContext>を受信<xref:System.ServiceModel.OperationContext>です。</span><span class="sxs-lookup"><span data-stu-id="af909-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.\` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="af909-223">この問題を解決するには、WCF Web HTTP サービス操作内で <xref:System.ServiceModel.OperationContextScope> を作成します。</span><span class="sxs-lookup"><span data-stu-id="af909-223">To solve this problem create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="af909-224">例:</span><span class="sxs-lookup"><span data-stu-id="af909-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="af909-225">関連項目</span><span class="sxs-lookup"><span data-stu-id="af909-225">See Also</span></span>  
 [<span data-ttu-id="af909-226">Windows 認証エラーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="af909-226">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
