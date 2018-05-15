---
title: 操作フォーマッタと操作セレクター
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: db548e99c99ba6f29cc1c6e998d0e7485cd41046
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="9ef1a-102">操作フォーマッタと操作セレクター</span><span class="sxs-lookup"><span data-stu-id="9ef1a-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="9ef1a-103">このサンプルでは、Windows Communication Foundation (WCF) の機能拡張ポイントを使用して、WCF で期待から別の形式でメッセージ データを許可する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="9ef1a-104">WCF のフォーマッタを既定では、含まれるメソッドのパラメーターを想定して、`soap:body`要素。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="9ef1a-105">このサンプルでは、代わりに HTTP GET クエリ文字列のパラメータ データを解析するカスタム操作フォーマッタを実装し、そのデータを使用してメソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="9ef1a-106">サンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)を実装する、`ICalculator`サービス コントラクト。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="9ef1a-107">加算、減算、乗算、および除算のメッセージを変更して、クライアントからサーバーへの要求を行うための HTTP GET と、サーバーからクライアントへの要求を行うための POX メッセージ付きの HTTP POST を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="9ef1a-108">これを行うために、サンプルには次の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-108">To do so, the sample provides the following:</span></span>  
  
-   <span data-ttu-id="9ef1a-109">`QueryStringFormatter`。クライアントとサーバー用に、それぞれ <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> と <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> を実装し、クエリ文字列内のデータを処理します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
-   <span data-ttu-id="9ef1a-110">`UriOperationSelector`。サーバー上に、GET 要求内の操作名に基づいて操作ディスパッチを実行する <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> を実装します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
-   <span data-ttu-id="9ef1a-111">`EnableHttpGetRequestsBehavior` エンドポイント動作 (および対応する構成)。必要な操作セレクタをランタイムに追加します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
-   <span data-ttu-id="9ef1a-112">新しい操作フォーマッタをランタイムに挿入する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
-   <span data-ttu-id="9ef1a-113">このサンプルでは、クライアントとサービスは両方ともコンソール アプリケーション (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ef1a-114">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="9ef1a-115">主要な概念</span><span class="sxs-lookup"><span data-stu-id="9ef1a-115">Key Concepts</span></span>  
 <span data-ttu-id="9ef1a-116">`QueryStringFormatter` -この操作フォーマッタは、wcf メッセージをメッセージにパラメーター オブジェクトの配列とパラメーター オブジェクトの配列に変換を担当するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="9ef1a-117">この操作は、クライアント上では <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> インターフェイスを使用して、サーバー上では <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> インターフェイスを使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="9ef1a-118">これらのインターフェイスを使用すると、ユーザーは `Serialize` メソッドと `Deserialize` メソッドから要求メッセージと応答メッセージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="9ef1a-119">このサンプルでは、`QueryStringFormatter` にこれら両方のインターフェイスが実装され、クライアントとサーバーで実装されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="9ef1a-120">要求 :</span><span class="sxs-lookup"><span data-stu-id="9ef1a-120">Request:</span></span>  
  
-   <span data-ttu-id="9ef1a-121">このサンプルでは、<xref:System.ComponentModel.TypeConverter> クラスを使用して要求メッセージ内のパラメータ データを文字列に変換したり、その逆の処理を行ったりします。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="9ef1a-122"><xref:System.ComponentModel.TypeConverter> が特定の型で使用できない場合は、サンプルのフォーマッタから例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
-   <span data-ttu-id="9ef1a-123">クライアントの `IClientMessageFormatter.SerializeRequest` メソッドでは、フォーマッタは適切な宛先アドレスを使用して URI を作成し、操作名をサフィックスとして追加します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="9ef1a-124">この操作名は、サーバー上の適切な操作へのディスパッチに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="9ef1a-125">次にパラメータ名と <xref:System.ComponentModel.TypeConverter> によって変換された値を使用して、パラメータ オブジェクトの配列を取得し、そのパラメータ データを URI クエリ文字列にシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="9ef1a-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A> プロパティおよび <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> プロパティは、この URI に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="9ef1a-127"><xref:System.ServiceModel.Channels.MessageProperties> にアクセスするには、<xref:System.ServiceModel.Channels.Message.Properties%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
-   <span data-ttu-id="9ef1a-128">サーバーの `IDispatchMessageFormatter.DeserializeRequest` メソッドでは、フォーマッタは受信要求メッセージ プロパティ内で`Via` URI を検索します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="9ef1a-129">次に URI クエリ文字列内にある名前と値の組み合わせを解析してパラメータ名と値に分け、そのパラメータ名と値を使用してこのメソッドに渡されるパラメータの配列を設定します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="9ef1a-130">操作ディスパッチは既に発生しているので、このメソッドでは操作名のサフィックスは無視されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="9ef1a-131">応答 :</span><span class="sxs-lookup"><span data-stu-id="9ef1a-131">Response:</span></span>  
  
-   <span data-ttu-id="9ef1a-132">このサンプルでは、HTTP GET は要求のみに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="9ef1a-133">応答を送信するには、フォーマッタを XML メッセージの生成時に使用できたはずの最初のフォーマッタに代行させます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="9ef1a-134">このサンプルの目的の 1 つは、このような代行フォーマッタの実装方法を示すことです。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="9ef1a-135">UriPathSuffixOperationSelector クラス</span><span class="sxs-lookup"><span data-stu-id="9ef1a-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="9ef1a-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> インターフェイスを使用すると、特定のメッセージをディスパッチする必要がある操作で、ユーザー独自のロジックを実装できます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="9ef1a-137">このサンプルでは、操作名がメッセージのアクション ヘッダーではなく、HTTP GET URI に含まれているため、適切な操作を選択するには、`UriPathSuffixOperationSelector` がサーバーに実装されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="9ef1a-138">サンプルは、大文字小文字が区別されない操作名のみを許可するようにセットアップされています。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="9ef1a-139">`SelectOperation` メソッドは、受信メッセージを取得し、メッセージ プロパティ内の `Via` URI を検索します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="9ef1a-140">次に、この URI から操作名のサフィックスを抽出し、内部テーブルを検索してメッセージをディスパッチする必要がある操作名を取得して、その操作名を返します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="9ef1a-141">EnableHttpGetRequestsBehavior クラス</span><span class="sxs-lookup"><span data-stu-id="9ef1a-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="9ef1a-142">`UriPathSuffixOperationSelector` コンポーネントは、プログラムまたはエンドポイント動作を使用してセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="9ef1a-143">サンプルでは、サービスのアプリケーション構成ファイルで指定された `EnableHttpGetRequestsBehavior` の動作を実装します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="9ef1a-144">サーバー側 :</span><span class="sxs-lookup"><span data-stu-id="9ef1a-144">On the server:</span></span>  
  
 <span data-ttu-id="9ef1a-145"><xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> は <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 実装に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="9ef1a-146">既定では、WCF は、完全一致のアドレス フィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="9ef1a-147">受信メッセージ上の URI には、操作名のサフィックスと、その後にパラメータ データを格納するクエリ文字列が含まれています。したがって、アドレス フィルタは、エンドポイントの動作によっても、プレフィックスが一致するフィルタに変更されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="9ef1a-148">WCF を使用して<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>この目的のためです。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="9ef1a-149">操作フォーマッタのインストール</span><span class="sxs-lookup"><span data-stu-id="9ef1a-149">Installing operation formatters</span></span>  
 <span data-ttu-id="9ef1a-150">フォーマッタを指定する操作の動作は一意です。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="9ef1a-151">このような動作は、常に既定で操作ごとに実装され、必要な操作フォーマッタを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="9ef1a-152">ただし、これらの動作は他の操作動作と同様に見えるため、他の属性では識別できません。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="9ef1a-153">置換動作をインストールするには、実装が既定とするか、WCF 型ローダーによってインストールされている特定のフォーマッタの動作を置き換えることを探しますか、ビヘイビアーを追加する互換性のある既定の動作後に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="9ef1a-154">これらの操作フォーマッタの動作は、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> を呼び出す前にプログラムでセットアップするか、または既定のフォーマッタ動作後に実行される操作動作を指定することによってセットアップすることができます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="9ef1a-155">ただし、エンドポイント動作を介したセットアップ (および構成を介したセットアップ) は容易ではありません。この動作モデルでは、動作によって別の動作を置き換えることはできず、他の方法で説明ツリーを変更することもできないためです。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="9ef1a-156">クライアント側 :</span><span class="sxs-lookup"><span data-stu-id="9ef1a-156">On the client:</span></span>  
  
 <span data-ttu-id="9ef1a-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> の実装を行って、要求を HTTP GET 要求に変換し、応答を元のフォーマッタに代行させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="9ef1a-158">これを行うには、`EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` ヘルパー メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="9ef1a-159">この手順は、`CreateChannel` を呼び出す前に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-159">This must be done before calling `CreateChannel`.</span></span>  
  
```  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 <span data-ttu-id="9ef1a-160">サーバー側 :</span><span class="sxs-lookup"><span data-stu-id="9ef1a-160">On the server:</span></span>  
  
-   <span data-ttu-id="9ef1a-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> インターフェイスを実装して、HTTP GET 要求を読み込み、応答の書き出しを元のフォーマッタに代行させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="9ef1a-162">これを行うには、クライアントと同じ`EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` ヘルパー メソッドを呼び出します (前述のコード サンプルを参照)。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
-   <span data-ttu-id="9ef1a-163">この手順は、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> を呼び出す前に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="9ef1a-164">このサンプルでは、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> を呼び出す前にこのフォーマッタを手動で変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="9ef1a-165">同じ結果を得るための別の方法としては、オープン操作の前に <xref:System.ServiceModel.ServiceHost> を呼び出す `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` からクラスを派生します (ホスティングのドキュメントおよびサンプル例を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="9ef1a-166">ユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="9ef1a-166">User experience</span></span>  
 <span data-ttu-id="9ef1a-167">サーバー側 :</span><span class="sxs-lookup"><span data-stu-id="9ef1a-167">On the server:</span></span>  
  
-   <span data-ttu-id="9ef1a-168">サーバーの `ICalculator` 実装は、変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="9ef1a-169">サービス用の App.config では、`messageVersion` 要素の `textMessageEncoding` 属性を `None` に設定するカスタムの POX バインディングを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   <span data-ttu-id="9ef1a-170">サービス用の App.config ではさらに、カスタムの `EnableHttpGetRequestsBehavior` を動作の拡張セクションに追加して使用することによって、これを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
-   <span data-ttu-id="9ef1a-171"><xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> を呼び出す前に操作フォーマッタを追加します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="9ef1a-172">クライアント側 :</span><span class="sxs-lookup"><span data-stu-id="9ef1a-172">On the client:</span></span>  
  
-   <span data-ttu-id="9ef1a-173">クライアントの実装は、変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-173">The client implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="9ef1a-174">クライアント用の App.config では、`messageVersion` 要素の `textMessageEncoding` 属性を `None` に設定するカスタムの POX バインディングを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="9ef1a-175">サービスとの違いは、クライアントでは送信先アドレスを変更できるように手動アドレス指定を有効にする必要があるという点です。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   <span data-ttu-id="9ef1a-176">クライアント用の App.config では、サーバーと同じカスタムの `EnableHttpGetRequestsBehavior` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
-   <span data-ttu-id="9ef1a-177"><xref:System.ServiceModel.ChannelFactory%601.CreateChannel> を呼び出す前に操作フォーマッタを追加します。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="9ef1a-178">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9ef1a-179">4 つすべての操作 (加算、減算、乗算、および除算) が正常に行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ef1a-180">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ef1a-181">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ef1a-182">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ef1a-183">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9ef1a-184">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="9ef1a-184">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9ef1a-185">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9ef1a-186">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9ef1a-187">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef1a-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef1a-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ef1a-188">See Also</span></span>
