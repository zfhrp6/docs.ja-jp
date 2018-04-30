---
title: フィルターの選択
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 653013de37278f051f37fdda52e68fc3d84c2cbb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="choosing-a-filter"></a><span data-ttu-id="ab8e1-102">フィルターの選択</span><span class="sxs-lookup"><span data-stu-id="ab8e1-102">Choosing a Filter</span></span>
<span data-ttu-id="ab8e1-103">ルーティング サービスを構成する際には、適切なメッセージ フィルターを選択し、受信するメッセージと正確に一致できるように、それらのフィルターを構成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="ab8e1-104">選択したフィルターの適合基準が幅広すぎる場合や、適切に構成されていない場合は、メッセージが正しくルーティングされません。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="ab8e1-105">フィルターの適合基準が厳格すぎると、一部のメッセージの有効なルーティング先が見つからないことがあります。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>  
  
## <a name="filter-types"></a><span data-ttu-id="ab8e1-106">フィルターの種類</span><span class="sxs-lookup"><span data-stu-id="ab8e1-106">Filter Types</span></span>  
 <span data-ttu-id="ab8e1-107">ルーティング サービスで使用するフィルターを選択する際には、各フィルターのしくみと、受信メッセージの一部として使用できる情報について理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="ab8e1-108">たとえば、すべてのメッセージが同じエンドポイントを介して受信される場合は、すべてのメッセージが Address フィルターと EndpointName フィルターに一致するため、これらのフィルターは役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>  
  
### <a name="action"></a><span data-ttu-id="ab8e1-109">アクション</span><span class="sxs-lookup"><span data-stu-id="ab8e1-109">Action</span></span>  
 <span data-ttu-id="ab8e1-110">Action フィルターは <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="ab8e1-111">メッセージの Action ヘッダーの内容が、フィルター構成で指定されているフィルター データ値と一致する場合、このフィルターは `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="ab8e1-112">次の例では定義、`FilterElement`アクション フィルターを使用して、値を含むアクション ヘッダーを持つメッセージに一致する"http://namespace/contract/operation/"です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of "http://namespace/contract/operation/".</span></span>  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 <span data-ttu-id="ab8e1-113">一意のアクション ヘッダーを含むメッセージをルーティングするときは、このフィルターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-113">This filter should be used when routing messages that contain a unique Action header.</span></span>  
  
### <a name="endpointaddress"></a><span data-ttu-id="ab8e1-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="ab8e1-114">EndpointAddress</span></span>  
 <span data-ttu-id="ab8e1-115">EndpointAddress フィルターは、メッセージを受信した EndpointAddress を確認します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="ab8e1-116">メッセージが着信したアドレスが、フィルター構成で指定されたフィルター アドレスと正確に一致した場合、このフィルターは `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="ab8e1-117">次の例では定義、`FilterElement`宛てのメッセージに一致するアドレス フィルターを使用する"http://\<ホスト名 >/vdir/s.svc/b"です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="ab8e1-118">アドレスのホスト名部分は、クライアントで完全修飾ドメイン名、NetBIOS 名、IP アドレス、それ以外の名前のどれが使用されるかによって異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="ab8e1-119">異なる値が同じホストを参照している場合があるため、この比較の既定の動作では、照合の際にアドレスのホスト名部分は使用されません。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
>   
>  <span data-ttu-id="ab8e1-120">ルーティング サービスをプログラムで構成する際に、比較の際にホスト名を評価できるように、この動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>  
  
 <span data-ttu-id="ab8e1-121">受信メッセージが一意のアドレス宛てである場合は、このフィルターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>  
  
### <a name="endpointaddressprefix"></a><span data-ttu-id="ab8e1-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="ab8e1-122">EndpointAddressPrefix</span></span>  
 <span data-ttu-id="ab8e1-123">EndpointAddressPrefix フィルターは、EndpointAddress フィルターに似ています。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="ab8e1-124">EndpointAddressPrefix フィルターは、メッセージを受信した EndpointAddress を確認します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="ab8e1-125">ただし、EndpointAddressPrefix フィルターは、フィルター構成で指定された値で始まるアドレスを一致させることによって、ワイルドカードとして機能します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="ab8e1-126">次の例では定義、 `FilterElement` EndpointAddressPrefix フィルターを使用して、宛てのメッセージに一致する"http://\<ホスト名 >/vdir \*"です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to "http://\<hostname>/vdir\*".</span></span>  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="ab8e1-127">アドレスのホスト名部分は、クライアントで完全修飾ドメイン名、NetBIOS 名、IP アドレス、それ以外の名前のどれが使用されるかによって異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="ab8e1-128">異なる値が同じホストを参照している場合があるため、この比較の既定の動作では、照合の際にアドレスのホスト名部分は使用されません。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
  
 <span data-ttu-id="ab8e1-129">共通のアドレス プレフィックスを共有する受信メッセージをルーティングするときは、このフィルターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>  
  
### <a name="and"></a><span data-ttu-id="ab8e1-130">AND</span><span class="sxs-lookup"><span data-stu-id="ab8e1-130">AND</span></span>  
 <span data-ttu-id="ab8e1-131">AND フィルターが、メッセージ内の値を直接フィルターすることはありません。しかし、AND フィルターを使用すると、他の 2 つのフィルターを組み合わせて `AND` 条件を作成し、それらのフィルターの両方がメッセージと一致した場合に、AND フィルターが `true` に評価されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="ab8e1-132">これにより、すべてのサブフィルターが一致した場合にだけ一致する、複雑なフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="ab8e1-133">次の例では、Address フィルターと Action フィルターを定義した後で、それらのフィルターの両方に照合してメッセージを評価する AND フィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="ab8e1-134">Address フィルターと Action フィルターの両方と一致した場合、AND フィルターは `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>  
  
```xml  
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>  
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);  
```  
  
 <span data-ttu-id="ab8e1-135">複数のフィルターのロジックを組み合わせて一致を判断する必要がある場合は、このフィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="ab8e1-136">たとえば、アクションとメッセージの特定の組み合わせだけを特定のアドレスに受け取る必要がある複数の送信先がある場合は、AND フィルターを使用して、必要な Action フィルターと Address フィルターを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>  
  
### <a name="custom"></a><span data-ttu-id="ab8e1-137">カスタム</span><span class="sxs-lookup"><span data-stu-id="ab8e1-137">Custom</span></span>  
 <span data-ttu-id="ab8e1-138">カスタム フィルターの種類を選択する場合を含むアセンブリの型を含む customType 値を指定する必要があります、 **MessageFilter**このフィルターに使用する実装。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="ab8e1-139">また、filterData には、Custom フィルターがメッセージの評価に必要とするすべての値が格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="ab8e1-140">次の例では、`FilterElement` MessageFilter 実装を使用する `CustomAssembly.MyCustomMsgFilter` を定義します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 <span data-ttu-id="ab8e1-141">提供されるフィルターで保証されていないメッセージに対してカスタムの一致するロジックを実行する必要があるかどうかは[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]の実装であるカスタム フィルターを作成する必要があります、 **MessageFilter**クラスです。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="ab8e1-142">たとえば、受信メッセージ内の 1 つのフィールドを、構成としてフィルターに指定された既知の値のリストと比較するカスタム フィルターや、特定のメッセージ要素をハッシュしてから、その値を調査してフィルターが `true` と `false` のどちらを返すかを判断するカスタム フィルターを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>  
  
### <a name="endpointname"></a><span data-ttu-id="ab8e1-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="ab8e1-143">EndpointName</span></span>  
 <span data-ttu-id="ab8e1-144">EndpointName フィルターは、メッセージを受信したエンドポイントの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="ab8e1-145">次の例では定義、 `FilterElement` SvcEndpoint で受信したメッセージをルーティングする EndpointName フィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 <span data-ttu-id="ab8e1-146">このフィルターは、ルーティング サービスが複数の名前付きサービス エンドポイントを公開する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="ab8e1-147">たとえば、ルーティング サービスがメッセージの受信に使用する 2 つのエンドポイントを公開し、その 1 つを、メッセージのリアルタイム処理を必要とする優先顧客が使用し、残りの 1 つを使用して、受信のタイミングが重要でないメッセージを受信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>  
  
 <span data-ttu-id="ab8e1-148">メッセージを受信したエンドポイントを特定する際に完全なアドレスの一致を使用することはよくありますが、定義されたエンドポイント名を使用すると、エラーの可能性が少なく、すばやく処理できるので便利です。特に、エンドポイント名が必須の属性となる、構成ファイルを使用したルーティング サービスの構成では、この方法が便利です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>  
  
### <a name="matchall"></a><span data-ttu-id="ab8e1-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="ab8e1-149">MatchAll</span></span>  
 <span data-ttu-id="ab8e1-150">MatchAll フィルターは、受信したすべてのメッセージと一致します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="ab8e1-151">受信したすべてのメッセージのコピーを格納するログ サービスの場合など、受信したすべてのメッセージを常に特定のエンドポイントにルーティングする必要がある場合は、このフィルターが便利です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="ab8e1-152">次の例で定義する `FilterElement` では、MatchAll フィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a><span data-ttu-id="ab8e1-153">XPath</span><span class="sxs-lookup"><span data-stu-id="ab8e1-153">XPath</span></span>  
 <span data-ttu-id="ab8e1-154">XPath フィルターを使用すると、XPath クエリを指定して、メッセージ内の特定の要素を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="ab8e1-155">XPath フィルターは、メッセージ内の XML アドレス指定可能なエントリを直接確認できる、強力なフィルター オプションです。ただし、このフィルターを使用するには、受信するメッセージの構造に関する特定の知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="ab8e1-156">次の例では定義、 `FilterElement` XPath フィルターを使用して、メッセージ"名前空間プレフィックス ns で参照されている名前空間内"の element"をという名前の要素を確認します。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 <span data-ttu-id="ab8e1-157">受信するメッセージに特定の値が含まれていることがわかっている場合は、このフィルターが便利です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="ab8e1-158">たとえば、同じサービスの 2 つのバージョンをホストしており、そのサービスの新しい方のバージョン宛てのメッセージのカスタム ヘッダーに一意の値が含まれていることがわかっている場合は、XPath を使用するフィルターを作成してそのヘッダーに移動し、そのヘッダー内にある値を、フィルター構成で指定されている別の値と比較して、そのフィルターが一致するかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>  
  
 <span data-ttu-id="ab8e1-159">XPath クエリには、長い文字列値または複雑な文字列値である一意の名前空間が含まれていることが多いため、XPath フィルターでは、名前空間用の一意のプレフィックスを定義する名前空間テーブルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="ab8e1-160">名前空間のテーブルの詳細については、次を参照してください。[メッセージ フィルター](../../../../docs/framework/wcf/feature-details/message-filters.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="ab8e1-161">XPath クエリのデザインの詳細については、次を参照してください。 [XPath 構文](http://go.microsoft.com/fwlink/?LinkId=164592)です。</span><span class="sxs-lookup"><span data-stu-id="ab8e1-161">For more information about designing XPath queries, see [XPath Syntax](http://go.microsoft.com/fwlink/?LinkId=164592).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8e1-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab8e1-162">See Also</span></span>  
 [<span data-ttu-id="ab8e1-163">メッセージ フィルター</span><span class="sxs-lookup"><span data-stu-id="ab8e1-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [<span data-ttu-id="ab8e1-164">フィルターを使用する方法</span><span class="sxs-lookup"><span data-stu-id="ab8e1-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
