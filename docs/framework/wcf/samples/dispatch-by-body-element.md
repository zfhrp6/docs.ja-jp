---
title: "本文要素別のディスパッチ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c3624290176d93519ae420a98a7e93534d910fa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="46ba9-102">本文要素別のディスパッチ</span><span class="sxs-lookup"><span data-stu-id="46ba9-102">Dispatch by Body Element</span></span>
<span data-ttu-id="46ba9-103">このサンプルでは、入力メッセージを操作に割り当てるための代替アルゴリズムを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="46ba9-104">既定では、サービス モデル ディスパッチャは、メッセージの WS-Addressing の "Action" ヘッダーまたは HTTP SOAP 要求でのこれと同等の情報に基づいて、入力メッセージの適切な処理メソッドを選択します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="46ba9-105">WS-I Basic Profile 1.1 のガイドラインに従っていない SOAP 1.1 Web サービス スタックの一部では、Action URI に基づくのではなく、SOAP 本文内にある最初の要素の XML 修飾名に基づいてメッセージをディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="46ba9-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="46ba9-106">同様に、クライアント側のこうしたスタックでは、空または任意の HTTP SoapAction ヘッダーが含まれるメッセージを送信する場合があります。これは SOAP 1.1 の仕様で許可されていました。</span><span class="sxs-lookup"><span data-stu-id="46ba9-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="46ba9-107">メッセージをメソッドにディスパッチする方法を変更するために、このサンプルでは <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 拡張インターフェイスを `DispatchByBodyElementOperationSelector` に実装します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="46ba9-108">このクラスは、メッセージ本文の最初の要素に基づいて操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="46ba9-109">クラス コンストラクタには、`XmlQualifiedName` と文字列のペアが記録されたディクショナリが必要です。この修飾名は SOAP 本文の最初の子の名前を示し、文字列は該当する操作名を示します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="46ba9-110">`defaultOperationName` は、このディクショナリで照合できないすべてのメッセージを受信する操作の名前です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <span data-ttu-id="46ba9-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> インターフェイスにはメソッドが 1 つしかないので、<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> を実装すると、ビルドが非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="46ba9-112">このメソッドでの処理は、入力メッセージを検査し、現在のエンドポイントのサービス コントラクトでのメソッド名と同じ文字列を返すことです。</span><span class="sxs-lookup"><span data-stu-id="46ba9-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="46ba9-113">このサンプルでは、操作セレクタは <xref:System.Xml.XmlDictionaryReader> を通じて、入力メッセージの本文の <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> を取得します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="46ba9-114">このメソッドは既にリーダーをメッセージ本文の最初の子に配置しています。そのため、現在の要素の名前と名前空間の URI を取得して、それらを `XmlQualifiedName` に結合することは簡単です。その後、これは操作セレクタによって保持されているディクショナリから対応する操作を検索する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```  
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 <span data-ttu-id="46ba9-115"><xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>、またはメッセージ本文のコンテンツへのアクセスを提供する他のメソッドを使用してメッセージ本文にアクセスすると、そのメッセージは "read" とマークされます。つまり、メッセージは以降の処理に対して無効になります。</span><span class="sxs-lookup"><span data-stu-id="46ba9-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="46ba9-116">したがって、操作セレクタは次のコードに示すメソッドを使用して入力メッセージのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="46ba9-117">リーダーの位置は検査中には変更されていないので、新しく作成されたメッセージはこれを参照できます。入力メッセージのプロパティとヘッダーもこの新しいメッセージにコピーされるので、その結果、元のメッセージの完全な複製ができあがります。</span><span class="sxs-lookup"><span data-stu-id="46ba9-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="46ba9-118">サービスへの操作セレクタの追加</span><span class="sxs-lookup"><span data-stu-id="46ba9-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="46ba9-119">サービス ディスパッチ操作セレクタは [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ディスパッチャに対する拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-119">Service dispatch operation selectors are extensions to the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispatcher.</span></span> <span data-ttu-id="46ba9-120">二重のコントラクトのコールバック チャネルでメソッドを選択する場合、クライアントの操作セレクタも存在します。この操作セレクタはここで説明するディスパッチ操作セレクタと非常によく似ていますが、このサンプルでは明示的には説明しません。</span><span class="sxs-lookup"><span data-stu-id="46ba9-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="46ba9-121">ディスパッチ操作セレクタはほとんどのサービス モデル拡張と同様、動作を使用してディスパッチャに追加されます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="46ba9-122">A*動作*は、構成オブジェクトをディスパッチ ランタイム (またはクライアント ランタイムに)、1 つまたは複数の拡張機能を追加するか、それ以外の場合、設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="46ba9-123">操作セレクタにはコントラクトのスコープがあるので、ここで実装する適切な動作は <xref:System.ServiceModel.Description.IContractBehavior> です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="46ba9-124">このインターフェイスは、次のコードに示すように <xref:System.Attribute> 派生クラスに実装されているため、この動作は任意のサービス コントラクトに宣言として追加できます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="46ba9-125"><xref:System.ServiceModel.ServiceHost> が開いてディスパッチ ランタイムがビルドされるたびに、コントラクト、操作、およびサービス実装の属性の形をとるか、またはサービス構成内の要素の形をとるすべての動作が自動的に追加され、その後拡張機能の支援または既定の構成の変更を求められます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="46ba9-126">次のコードの抜粋では、簡略化のため、メソッド <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> の実装のみを示します。これは、このサンプルのディスパッチャの構成変更に影響します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="46ba9-127">他のメソッドが表示されていないのは、何の処理も行わずに呼び出し元に返されるためです。</span><span class="sxs-lookup"><span data-stu-id="46ba9-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="46ba9-128">最初に、<xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> を実装し、サービス エンドポイントの <xref:System.ServiceModel.Description.OperationDescription> の <xref:System.ServiceModel.Description.ContractDescription> 要素を反復処理することによって、操作セレクタの検索ディクショナリを設定します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="46ba9-129">次に、各操作の記述に `DispatchBodyElementAttribute` 動作が存在するかどうかが検査されます。この動作は、このサンプルでも定義されている <xref:System.ServiceModel.Description.IOperationBehavior> の実装です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="46ba9-130">このクラスも動作の 1 つですが、パッシブな動作です。ディスパッチ ランタイムに対して構成変更をアクティブに支援することはありません。</span><span class="sxs-lookup"><span data-stu-id="46ba9-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="46ba9-131">このすべてのメソッドは、アクションを起こすことなく呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="46ba9-132">この操作の動作は、新しいディスパッチ機構に必要なメタデータ、つまり見つかった場合に操作で選択される本文要素の修飾名を、該当する操作に関連付ける目的でのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="46ba9-133">このような動作が見つかると、XML 修飾名 (`QName` プロパティ) と操作名 (`Name` プロパティ) から作成された値のペアがディクショナリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="46ba9-134">ディクショナリが設定されると、新しい `DispatchByBodyElementOperationSelector` がこの情報で構築され、ディスパッチ ランタイムの操作セレクタとして設定されます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```  
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =   
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in   
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =   
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,   
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =   
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,   
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a><span data-ttu-id="46ba9-135">サービスの実装</span><span class="sxs-lookup"><span data-stu-id="46ba9-135">Implementing the Service</span></span>  
 <span data-ttu-id="46ba9-136">このサンプルに実装されている動作は、通信回線からのメッセージの解釈方法とディスパッチ方法に直接影響します。これはサービス コントラクトの機能です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="46ba9-137">そのため、この動作を使用することを選択したサービス実装では、この動作をサービス コントラクト レベルで宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46ba9-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="46ba9-138">サンプル プロジェクト service が適用されます、`DispatchByBodyElementBehaviorAttribute`コントラクトの動作を`IDispatchedByBody`サービス コントラクトと 2 つの操作のラベル各`OperationForBodyA()`と`OperationForBodyB()`で、`DispatchBodyElementAttribute`操作の動作です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="46ba9-139">このコントラクトを実装しているサービスのサービス ホストが開かれると、このメタデータは前で説明したようにディスパッチャ ビルダによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="46ba9-140">操作セレクタはメッセージ本文の要素のみに基づいてディスパッチし、"Action" を無視するので、返された応答の "Action" ヘッダーをチェックしないようランタイムに通知する必要があります。これを行うには、ワイルドカード "*" を `ReplyAction` の <xref:System.ServiceModel.OperationContractAttribute> プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="46ba9-141">さらに、ワイルドカードに設定した"Action"プロパティを持つ既定の操作を必要とは"\*"です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="46ba9-142">既定の操作は、ディスパッチできず、`DispatchBodyElementAttribute` を持たないすべてのメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="46ba9-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),   
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),   
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 <span data-ttu-id="46ba9-143">このサンプルのサービス実装は簡単です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="46ba9-144">どのメソッドも受信メッセージを応答メッセージにラップし、クライアントに再度エコーします。</span><span class="sxs-lookup"><span data-stu-id="46ba9-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="46ba9-145">サンプルの実行とビルド</span><span class="sxs-lookup"><span data-stu-id="46ba9-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="46ba9-146">このサンプルを実行すると、次に示す (書式設定された) 出力と同様の、操作応答の内容がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="46ba9-147">クライアントは 3 つのメッセージをサービスに送信します。このメッセージ本文のコンテンツ要素の名前は、それぞれ `bodyA`、`bodyB`、および `bodyX` です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="46ba9-148">以上の説明とサービス コントラクトからわかるように、`bodyA` 要素が含まれる受信メッセージは、`OperationForBodyA()` メソッドにディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="46ba9-149">`bodyX` 本文要素が含まれるメッセージについては、明示的なディスパッチ対象がないので、このメッセージは `DefaultOperation()` にディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="46ba9-150">各サービス操作は、受信されたメッセージ本文をメソッド固有の要素にラップして返します。このサンプルでは、入力メッセージと出力メッセージを明確に関連付けるためにこの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="46ba9-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="46ba9-151">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="46ba9-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="46ba9-152">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="46ba9-153">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="46ba9-154">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="46ba9-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46ba9-155">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="46ba9-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="46ba9-156">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="46ba9-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="46ba9-157">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="46ba9-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46ba9-158">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="46ba9-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a><span data-ttu-id="46ba9-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="46ba9-159">See Also</span></span>
