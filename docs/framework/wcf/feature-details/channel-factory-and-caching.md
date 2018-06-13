---
title: チャネル ファクトリとキャッシュ
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 1bf8e3fe4833b662f16bd6311056fda8609dd9d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490992"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="31352-102">チャネル ファクトリとキャッシュ</span><span class="sxs-lookup"><span data-stu-id="31352-102">Channel Factory and Caching</span></span>
<span data-ttu-id="31352-103">WCF クライアント アプリケーションでは、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して WCF サービスとの通信チャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="31352-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="31352-104"><xref:System.ServiceModel.ChannelFactory%601> インスタンスを作成する場合は、次の操作が必要になるため、オーバーヘッドが生じます。</span><span class="sxs-lookup"><span data-stu-id="31352-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
-   <span data-ttu-id="31352-105"><xref:System.ServiceModel.Description.ContractDescription> ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="31352-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
-   <span data-ttu-id="31352-106">必要なすべての CLR 型の反映</span><span class="sxs-lookup"><span data-stu-id="31352-106">Reflecting all of the required CLR types</span></span>  
  
-   <span data-ttu-id="31352-107">チャネル スタックの構築</span><span class="sxs-lookup"><span data-stu-id="31352-107">Constructing the channel stack</span></span>  
  
-   <span data-ttu-id="31352-108">リソースの破棄</span><span class="sxs-lookup"><span data-stu-id="31352-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="31352-109">このオーバーヘッドを最小限に抑えるために、WCF では、WCF クライアント プロキシの使用時にチャネル ファクトリをキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="31352-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="31352-110"><xref:System.ServiceModel.ChannelFactory%601> クラスを直接使用する場合は、チャネル ファクトリの作成を直接制御できます。</span><span class="sxs-lookup"><span data-stu-id="31352-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="31352-111">WCF クライアント プロキシを使用して生成された[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)から派生した<xref:System.ServiceModel.ClientBase%601>です。</span><span class="sxs-lookup"><span data-stu-id="31352-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="31352-112"><xref:System.ServiceModel.ClientBase%601> では、チャネル ファクトリのキャッシュ動作を定義する静的な <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="31352-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="31352-113">キャッシュ設定は特定の型に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="31352-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="31352-114">たとえば、設定`ClientBase<ITest>.CacheSettings`定義を次に、値のいずれかに影響を与えませんのみプロキシ/clientbase 型の`ITest`します。</span><span class="sxs-lookup"><span data-stu-id="31352-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="31352-115">最初のプロキシ/ClientBase インスタンスが作成された時点で、特定の <xref:System.ServiceModel.ClientBase%601> のキャッシュ設定は不変になります。</span><span class="sxs-lookup"><span data-stu-id="31352-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="31352-116">キャッシュ動作の指定</span><span class="sxs-lookup"><span data-stu-id="31352-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="31352-117">キャッシュ動作は、<xref:System.ServiceModel.ClientBase%601.CacheSetting> プロパティを次のいずれかの値に設定することで指定します。</span><span class="sxs-lookup"><span data-stu-id="31352-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="31352-118">キャッシュの設定値</span><span class="sxs-lookup"><span data-stu-id="31352-118">Cache Setting Value</span></span>|<span data-ttu-id="31352-119">説明</span><span class="sxs-lookup"><span data-stu-id="31352-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="31352-120">アプリケーション ドメイン内の <xref:System.ServiceModel.ClientBase%601> のすべてのインスタンスはキャッシュに参加できます。</span><span class="sxs-lookup"><span data-stu-id="31352-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="31352-121">開発者は、セキュリティがキャッシュに悪影響を与えないことを確認しています。</span><span class="sxs-lookup"><span data-stu-id="31352-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="31352-122">キャッシュが入っていない場合は「セキュリティに影響する」プロパティをオフ<xref:System.ServiceModel.ClientBase%601>にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="31352-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="31352-123">「セキュリティに影響する」プロパティ<xref:System.ServiceModel.ClientBase%601>は<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>、<xref:System.ServiceModel.ClientBase%601.Endpoint%2A>と<xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>です。</span><span class="sxs-lookup"><span data-stu-id="31352-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="31352-124">構成ファイルで定義されているエンドポイントから作成された <xref:System.ServiceModel.ClientBase%601> のインスタンスのみがアプリケーション ドメイン内のキャッシュに参加します。</span><span class="sxs-lookup"><span data-stu-id="31352-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="31352-125">そのアプリケーション ドメイン内にプログラムで作成された <xref:System.ServiceModel.ClientBase%601> のインスタンスはキャッシュに参加しません。</span><span class="sxs-lookup"><span data-stu-id="31352-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="31352-126">また、キャッシュが無効になりますのインスタンスの<xref:System.ServiceModel.ClientBase%601>「セキュリティに影響する」プロパティのいずれかがアクセスされるとします。</span><span class="sxs-lookup"><span data-stu-id="31352-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="31352-127">対象となるアプリケーション ドメイン内にある特定の型の <xref:System.ServiceModel.ClientBase%601> のすべてのインスタンスのキャッシュが無効になります。</span><span class="sxs-lookup"><span data-stu-id="31352-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="31352-128"><xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> プロパティを使用する方法を次のコード スニペットに示します。</span><span class="sxs-lookup"><span data-stu-id="31352-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))   
         {   
            // ...  
            proxy.Test(msg);   
            // ...  
         }   
      }   
   }   
}  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }  
```  
  
 <span data-ttu-id="31352-129">上のコードでは、`TestClient` のすべてのインスタンスで同じチャネル ファクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="31352-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.Default;   
      int i = 1;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            if (i == 4)   
            {   
               ServiceEndpoint endpoint = proxy.Endpoint;   
               ... // use endpoint in some way   
            }   
            proxy.Test(msg);   
         }   
         i++;   
   }   
}   
  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="31352-130">上の例では、`TestClient` のすべてのインスタンスで同じチャネル ファクトリを使用します (インスタンス #4 を除く)。</span><span class="sxs-lookup"><span data-stu-id="31352-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="31352-131">インスタンス #4 では、そのインスタンス専用に作成されたチャネル ファクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="31352-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="31352-132">この設定は、特定のエンドポイントで同じチャネル ファクトリ型 (この場合は `ITest`) の他のエンドポイントと異なるセキュリティ設定が必要なシナリオに有効です。</span><span class="sxs-lookup"><span data-stu-id="31352-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            proxy.Test(msg);   
         }           
      }   
   }  
}  
  
// Generated by SvcUtil.exe   
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="31352-133">上の例では、`TestClient` のすべてのインスタンスで異なるチャネル ファクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="31352-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="31352-134">これは、エンドポイントごとにセキュリティ要件が異なり、キャッシュする意味がない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="31352-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31352-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="31352-135">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601>  
 [<span data-ttu-id="31352-136">クライアントを構築する</span><span class="sxs-lookup"><span data-stu-id="31352-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="31352-137">クライアント</span><span class="sxs-lookup"><span data-stu-id="31352-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 [<span data-ttu-id="31352-138">WCF クライアントを使用したサービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="31352-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [<span data-ttu-id="31352-139">方法 : ChannelFactory を使用する</span><span class="sxs-lookup"><span data-stu-id="31352-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
