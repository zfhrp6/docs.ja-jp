---
title: "永続性インスタンス コンテキスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4f1f3f9e840ba422e327792ec2b0554fad45902
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="durable-instance-context"></a><span data-ttu-id="a7bce-102">永続性インスタンス コンテキスト</span><span class="sxs-lookup"><span data-stu-id="a7bce-102">Durable Instance Context</span></span>
<span data-ttu-id="a7bce-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ランタイムをカスタマイズして、永続性インスタンス コンテキストを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-103">This sample demonstrates how to customize the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] runtime to enable durable instance contexts.</span></span> <span data-ttu-id="a7bce-104">バッキング ストアとして、SQL Server 2005 (この場合は SQL Server 2005 Express) を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="a7bce-105">ただし、カスタム ストレージ機構にアクセスする方法も示します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-105">However, it also provides a way to access custom storage mechanisms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7bce-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7bce-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a7bce-107">このサンプルには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のチャネル レイヤとサービス モデル レイヤの両方の拡張が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7bce-107">This sample involves extending both the channel layer and the service model layer of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="a7bce-108">したがって、実装の詳細に進む前に基になる概念を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>  
  
 <span data-ttu-id="a7bce-109">永続性インスタンス コンテキストは、現実のケースでも頻繁に起こりうるものです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="a7bce-110">たとえば、ショッピング カート アプリケーションには、買い物を中断しても別の日に再開できる機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a7bce-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="a7bce-111">そのため、ショッピング カートに翌日アクセスすると、元のコンテキストが復元されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="a7bce-112">接続が切断されている間、ショッピング カート アプリケーション (サーバー上) はショッピング カートのインスタンスを保持しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7bce-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="a7bce-113">その代わり、状態を永続的なストレージ メディアに保持し、復元されたコンテキストの新しいインスタンスを構築するときにこの状態を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="a7bce-114">したがって、同じコンテキストに対してサービスを提供できるサービス インスタンスは、以前のインスタンスと同じではありません (つまり、メモリ アドレスが同じではありません)。</span><span class="sxs-lookup"><span data-stu-id="a7bce-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>  
  
 <span data-ttu-id="a7bce-115">永続性インスタンス コンテキストは、コンテキスト ID をクライアントとサービス間で交換するための簡単なプロトコルによって可能になります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="a7bce-116">このコンテキスト ID はクライアント上で作成され、サービスに転送されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="a7bce-117">サービス インスタンスが作成されると、サービス上のランタイムは、永続ストレージ (既定では SQL Server 2005 のデータベース) 上で永続化されている、このコンテキスト ID に対応する状態を読み込もうとします。</span><span class="sxs-lookup"><span data-stu-id="a7bce-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="a7bce-118">利用できる状態がない場合は、新しいインスタンスに既定の状態が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="a7bce-119">サービス実装は、カスタム属性を使用してサービス実装の状態を変更する操作の詳細を指定し、ランタイムがその操作を呼び出した後にサービス インスタンスを保存できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a7bce-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>  
  
 <span data-ttu-id="a7bce-120">前の説明から、目標を達成するための手順は大きく次の 2 つに分けられます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>  
  
1.  <span data-ttu-id="a7bce-121">ネットワークに出力されるメッセージを、コンテキスト ID が含まれるように変更します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-121">Change the message that goes on the wire to carry the context ID.</span></span>  
  
2.  <span data-ttu-id="a7bce-122">サービス側のローカル動作を変更して、カスタムのインスタンス化ロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-122">Change the service local behavior to implement custom instancing logic.</span></span>  
  
 <span data-ttu-id="a7bce-123">この一覧の前者の手順は、カスタム チャネルとして実装され、チャネル レイヤにフックされる、ネットワーク上のメッセージに影響します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="a7bce-124">後者の手順が影響を及ぼすのは、サービスのローカル動作だけです。したがって、いくつかのサービス拡張ポイントを拡張することによって実装できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="a7bce-125">以降のセクションでは、こうしたそれぞれの拡張について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-125">In the next few sections, each of these extensions are discussed.</span></span>  
  
## <a name="durable-instancecontext-channel"></a><span data-ttu-id="a7bce-126">永続的な InstanceContext チャネル</span><span class="sxs-lookup"><span data-stu-id="a7bce-126">Durable InstanceContext Channel</span></span>  
 <span data-ttu-id="a7bce-127">最初に、チャネル レイヤの拡張について考えます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="a7bce-128">カスタム チャネルを記述する最初の手順として、チャネルの通信構造を決定します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="a7bce-129">新しいワイヤ プロトコルを導入する際には、チャネルはチャネル スタック内の他のほとんどすべてのチャネルに対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="a7bce-130">そのため、すべてのメッセージ交換パターンをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="a7bce-131">ただし、チャネルの中心的な機能は通信構造に関係なく同じです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="a7bce-132">具体的には、コンテキスト ID をクライアント側からメッセージに書き込み、サービス側からこのメッセージのコンテキスト ID を読み取って上位レベルに渡します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="a7bce-133">そのため、すべての永続性インスタンス コンテキスト チャネルの実装に対して抽象基本クラスとして動作する、`DurableInstanceContextChannelBase` クラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="a7bce-134">このクラスには、共通ステート マシンの管理機能と保護された 2 つのメンバが含まれ、これによってコンテキスト情報をメッセージに適用したり、メッセージからコンテキスト情報を読み取ったりします。</span><span class="sxs-lookup"><span data-stu-id="a7bce-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>  
  
```  
class DurableInstanceContextChannelBase  
{  
  //…  
  protected void ApplyContext(Message message)  
  {  
    //…              
  }  
  protected string ReadContextId(Message message)  
  {  
    //…              
  }  
}  
```  
  
 <span data-ttu-id="a7bce-135">これら 2 つのメソッドは、`IContextManager` 実装を使用して、メッセージへのコンテキスト ID の書き込みと、メッセージからのコンテキスト ID の読み取りを行います </span><span class="sxs-lookup"><span data-stu-id="a7bce-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="a7bce-136">(`IContextManager` は、すべてのコンテキスト マネージャのコントラクトの定義に使用されるカスタム インターフェイスです)。チャネルは、このコンテキスト ID を、カスタム SOAP ヘッダーか HTTP クッキー ヘッダーのどちらかに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="a7bce-137">各コンテキスト マネージャの実装は、`ContextManagerBase` クラスを継承します。このクラスには、すべてのコンテキスト マネージャについての共通機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7bce-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="a7bce-138">このクラスの `GetContextId` メソッドは、コンテキスト ID をクライアント側で生成する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="a7bce-139">コンテキスト ID が最初に生成されると、このメソッドはこれをテキスト ファイルに保存します。テキスト ファイルの名前は、リモート エンドポイント アドレスによって作成されます (通常の URI に含まれる、ファイル名として無効な文字は、@ 文字に置き換えられます)。</span><span class="sxs-lookup"><span data-stu-id="a7bce-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>  
  
 <span data-ttu-id="a7bce-140">コンテキスト ID が後で同じリモート エンドポイントで必要になると、このメソッドは適切なファイルが存在するかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="a7bce-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="a7bce-141">ファイルが存在する場合は、コンテキスト ID を読み取って返します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="a7bce-142">存在しない場合は、新しく生成されたコンテキスト ID を返してこれをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="a7bce-143">既定の構成では、これらのファイルは現在のユーザーの一時ディレクトリ内にある ContextStore ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="a7bce-144">ただし、この場所はバインド要素を使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-144">However this location is configurable using the binding element.</span></span>  
  
 <span data-ttu-id="a7bce-145">コンテキスト ID の転送に使用される機構は構成可能です。</span><span class="sxs-lookup"><span data-stu-id="a7bce-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="a7bce-146">HTTP クッキー ヘッダーか、またはカスタム SOAP ヘッダーのどちらかに記述できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="a7bce-147">カスタム SOAP ヘッダーに記述する場合は、このプロトコルを HTTP 以外のプロトコル (TCP や NamedPipes など) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="a7bce-148">これらの 2 つのオプションは、`MessageHeaderContextManager` と `HttpCookieContextManager` という名前の 2 つのクラスに実装されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>  
  
 <span data-ttu-id="a7bce-149">これらのクラスはどちらも、コンテキスト ID をメッセージに適切に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="a7bce-150">たとえば `MessageHeaderContextManager` クラスでは、`WriteContext` メソッドにより SOAP ヘッダーにコンテキスト ID が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>  
  
```  
public override void WriteContext(Message message)  
{  
  string contextId = this.GetContextId();  
  
  MessageHeader contextHeader =  
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,  
      DurableInstanceContextUtility.HeaderNamespace,  
      contextId,   
      true);  
  
  message.Headers.Add(contextHeader);  
}   
```  
  
 <span data-ttu-id="a7bce-151">`ApplyContext` クラス内の `ReadContextId` メソッドと `DurableInstanceContextChannelBase` メソッドは、それぞれ `IContextManager.ReadContext` と `IContextManager.WriteContext` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="a7bce-152">ただし、これらのコンテキスト マネージャは `DurableInstanceContextChannelBase` クラスによって直接作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a7bce-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="a7bce-153">代わりに `ContextManagerFactory` クラスを使用してこの処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 <span data-ttu-id="a7bce-154">`ApplyContext` メソッドは送信チャネルによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="a7bce-155">このメソッドは、コンテキスト ID を送信メッセージに挿入します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="a7bce-156">`ReadContextId` メソッドは受信チャネルによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="a7bce-157">このメソッドは、受信メッセージ内でコンテキスト ID を使用できることを確認し、`Properties` クラスの `Message` コレクションにコンテキスト ID を追加します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="a7bce-158">さらに、コンテキスト ID の読み取りでエラーが発生した場合は `CommunicationException` をスローし、チャネルを中止します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 <span data-ttu-id="a7bce-159">次に進む前に、`Properties` クラスの `Message` コレクションの使用方法について理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a7bce-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="a7bce-160">通常、この `Properties` コレクションは、チャネル レイヤのデータを下位レベルから上位レベルに渡すときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="a7bce-161">この方法により、必要なデータを、プロトコルの詳細に関係なく一貫した方法で上位レベルに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="a7bce-162">つまり、チャネル レイヤはコンテキスト ID を、SOAP ヘッダーとしても HTTP クッキー ヘッダーとしても送受信できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="a7bce-163">しかし、上位レベルではこうした詳細を認識する必要はありません。チャネル レイヤにより、この情報が `Properties` コレクションで使用できるためです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>  
  
 <span data-ttu-id="a7bce-164">`DurableInstanceContextChannelBase` クラスを配備したら、必要な 10 のインターフェイス (IOutputChannel、IInputChannel、IOutputSessionChannel、IInputSessionChannel、IRequestChannel、IReplyChannel、IRequestSessionChannel、IReplySessionChannel、IDuplexChannel、および IDuplexSessionChannel) のすべてを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="a7bce-165">これらは、使用可能なすべてのメッセージ交換パターン (データグラム、一方向、双方向、およびセッションフル バリエーション) と似ています。</span><span class="sxs-lookup"><span data-stu-id="a7bce-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="a7bce-166">これらの各実装は前記の基本クラスを継承し、`ApplyContext` と `ReadContexId` を適切に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContexId` appropriately.</span></span> <span data-ttu-id="a7bce-167">たとえば、IOutputChannel インターフェイスを実装する `DurableInstanceContextOutputChannel` は、メッセージを送信する各メソッドから `ApplyContext` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 <span data-ttu-id="a7bce-168">これに対し、`DurableInstanceContextInputChannel` インターフェイスを実装する `IInputChannel` は、メッセージを受信する各メソッドで `ReadContextId` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 <span data-ttu-id="a7bce-169">これらのチャネル実装は、これ以外には、チャネル スタック内でチャネル実装の下にあるチャネルへのメソッド呼び出しを代行します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="a7bce-170">ただし、セッションフル バリエーションには、セッション作成の基になる最初のメッセージに対してのみコンテキスト ID の送信と読み取りを許可する、基本的なロジックがあります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 <span data-ttu-id="a7bce-171">次にこうしたチャネル実装は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クラスと `DurableInstanceContextBindingElement` クラスによって `DurableInstanceContextBindingElementSection` チャネル ランタイムに適切に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-171">These channel implementations are then added to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="a7bce-172">参照してください、 [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md)チャネルのバインド要素と要素のセクションをバインディングの詳細については、サンプルのドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>  
  
## <a name="service-model-layer-extensions"></a><span data-ttu-id="a7bce-173">サービス モデル レイヤの拡張</span><span class="sxs-lookup"><span data-stu-id="a7bce-173">Service Model Layer Extensions</span></span>  
 <span data-ttu-id="a7bce-174">コンテキスト ID がチャネル レイヤを通過すると、インスタンス化をカスタマイズするようにサービス側の動作を実装できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="a7bce-175">このサンプルでは、記憶域マネージャを使用して永続ストアからの状態の読み込みと、永続ストアへの状態の保存が行われます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="a7bce-176">前述のように、このサンプルにはバッキング ストアとして SQL Server 2005 を使用する記憶域マネージャが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a7bce-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="a7bce-177">ただし、この拡張に対してカスタム ストレージ機構を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="a7bce-178">これを行うには、すべての記憶域マネージャが実装する必要のあるパブリック インターフェイスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 <span data-ttu-id="a7bce-179">`SqlServerStorageManager` クラスには、既定の `IStorageManager` 実装が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="a7bce-180">`SaveInstance` メソッドでは、指定されたオブジェクトは XmlSerializer を使用してシリアル化され、SQL Server データベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>  
  
```  
XmlSerializer serializer = new XmlSerializer(state.GetType());  
string data;  
  
using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))  
{  
    serializer.Serialize(writer, state);  
    data = writer.ToString();  
}  
  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";  
  
    using (SqlCommand command = new SqlCommand(update, connection))  
    {  
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
  
        int rows = command.ExecuteNonQuery();  
  
        if (rows == 0)  
        {  
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";  
            command.CommandText = insert;  
            command.ExecuteNonQuery();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a7bce-181">`GetInstance` メソッドでは、シリアル化されたデータが特定のコンテキスト ID 用に読み取られ、そこから作成されたオブジェクトが呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>  
  
```  
object data;  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";  
    using (SqlCommand command = new SqlCommand(select, connection))  
    {  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
        data = command.ExecuteScalar();  
    }  
}  
  
if (data != null)  
{  
    XmlSerializer serializer = new XmlSerializer(type);  
    using (StringReader reader = new StringReader((string)data))  
    {  
        object instance = serializer.Deserialize(reader);  
        return instance;  
    }  
}  
```  
  
 <span data-ttu-id="a7bce-182">この記憶域マネージャを直接インスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7bce-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="a7bce-183">その代わりに、`StorageManagerFactory` クラスを使用して、記憶域マネージャの作成に関する詳細から抽出します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="a7bce-184">このクラスには、指定された型の記憶域マネージャのインスタンスを作成する、1 つの静的メンバ `GetStorageManager` があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="a7bce-185">型パラメータが `null` の場合、このメソッドは既定の `SqlServerStorageManager` クラスのインスタンスを作成して返します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="a7bce-186">さらに指定された型を検証して、それが `IStorageManager` インターフェイスを実装していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>  
  
```  
public static IStorageManager GetStorageManager(Type storageManagerType)  
{  
IStorageManager storageManager = null;  
  
if (storageManagerType == null)  
{  
    return new SqlServerStorageManager();  
}  
else  
{  
    object obj = Activator.CreateInstance(storageManagerType);  
  
    // Throw if the specified storage manager type does not  
    // implement IStorageManager.  
    if (obj is IStorageManager)  
    {  
        storageManager = (IStorageManager)obj;  
    }  
    else  
    {  
        throw new InvalidOperationException(  
                  ResourceHelper.GetString("ExInvalidStorageManager"));  
    }  
  
    return storageManager;  
}                  
}   
```  
  
 <span data-ttu-id="a7bce-187">永続ストレージのインスタンスの読み取りや書き込みに必要なインフラストラクチャを実装します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="a7bce-188">ここで、サービス側の動作を変更するために必要な手順を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-188">Now the necessary steps to change the service behavior have to be taken.</span></span>  
  
 <span data-ttu-id="a7bce-189">この処理の最初の手順として、チャネル レイヤを通過したコンテキスト ID を現在の InstanceContext に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="a7bce-190">InstanceContext とは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ディスパッチャとサービス インスタンス間のリンクとして動作するランタイム コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-190">InstanceContext is a runtime component that acts as the link between the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatcher and the service instance.</span></span> <span data-ttu-id="a7bce-191">これを使用すると、追加の状態と動作をサービス インスタンスに提供できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="a7bce-192">セッションの多い通信では、コンテキスト ID は最初のメッセージだけに含まれて送信されるので、これが重要になります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7bce-193"> では、拡張可能オブジェクト パターンを使用して、新しい状態および動作を追加することにより、InstanceContext ランタイム コンポーネントを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-193"> allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="a7bce-194">拡張可能オブジェクト パターンは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、既存のランタイム クラスに新しい機能を付け加えて拡張するため、またはオブジェクトに新しい状態の機能を追加するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-194">The extensible object pattern is used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="a7bce-195">拡張可能オブジェクト パターン - IExtensibleObject に 3 つのインターフェイスがある\<T >、IExtension\<T >、および IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="a7bce-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>  
  
-   <span data-ttu-id="a7bce-196">IExtensibleObject\<T > インターフェイスはオブジェクトを拡張して、機能をカスタマイズすることによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>  
  
-   <span data-ttu-id="a7bce-197">基準にして IExtension\<T > インターフェイスは T 型のクラスの拡張であるオブジェクトによって実装</span><span class="sxs-lookup"><span data-stu-id="a7bce-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>  
  
-   <span data-ttu-id="a7bce-198">IExtensionCollection\<T > インターフェイスはで、型ごとに IExtensions を取得できます IExtensions のコレクション。</span><span class="sxs-lookup"><span data-stu-id="a7bce-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>  
  
 <span data-ttu-id="a7bce-199">このため、IExtension インターフェイスを実装して、コンテキスト ID を保存するために必要な状態を定義する、InstanceContextExtension クラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="a7bce-200">このクラスではさらに、使用される記憶域マネージャを保持する状態も提供されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="a7bce-201">新しい状態が保存された後では、その状態を変更できません。</span><span class="sxs-lookup"><span data-stu-id="a7bce-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="a7bce-202">したがって、インスタンスが作成される際、読み取り専用のプロパティを使用してのみアクセス可能になった時点で、状態がインスタンスに提供され、保存されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>  
  
```  
// Constructor  
public DurableInstanceContextExtension(string contextId,   
            IStorageManager storageManager)  
{  
    this.contextId = contextId;  
    this.storageManager = storageManager;              
}  
  
// Read only properties  
public string ContextId  
{  
    get { return this.contextId; }  
}  
  
public IStorageManager StorageManager  
{  
    get { return this.storageManager; }              
}   
```  
  
 <span data-ttu-id="a7bce-203">InstanceContextInitializer クラスは IInstanceContextInitializer インターフェイスを実装し、作成された InstanceContext の Extensions コレクションにインスタンス コンテキスト拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
    string contextId =   
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];  
  
    DurableInstanceContextExtension extension =  
                new DurableInstanceContextExtension(contextId,   
                     storageManager);  
    instanceContext.Extensions.Add(extension);  
}  
```  
  
 <span data-ttu-id="a7bce-204">既に説明したように、コンテキスト ID は `Properties` クラスの `Message` コレクションから読み取られ、拡張クラスのコンストラクタに渡されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="a7bce-205">これによって、レイヤ間で情報を交換する場合の一貫性のある方法が示されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>  
  
 <span data-ttu-id="a7bce-206">次の重要な手順は、サービス インスタンスの作成手順をオーバーライドすることです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-206">The next important step is overriding the service instance creation process.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a7bce-207"> を使用すると、カスタマイズされたインスタンス化動作を実装し、IInstanceProvider インターフェイスを使用してこれをランタイムにフックできます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-207"> allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="a7bce-208">新しい `InstanceProvider` クラスがこの処理を行うために実装されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="a7bce-209">コンストラクタでは、インスタンス プロバイダから予期されるサービス型が受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="a7bce-210">これは、後で新しいインスタンスの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-210">Later this is used to create new instances.</span></span> <span data-ttu-id="a7bce-211">`GetInstance` 実装では、永続するインスタンスを検索する記憶域マネージャのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="a7bce-212">`null` が返された場合、サービス型の新しいインスタンスがインスタンス化され、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>  
  
```  
public object GetInstance(InstanceContext instanceContext, Message message)  
{  
    object instance = null;  
  
    DurableInstanceContextExtension extension =  
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();  
  
    string contextId = extension.ContextId;  
    IStorageManager storageManager = extension.StorageManager;              
  
    instance = storageManager.GetInstance(contextId, serviceType);          
  
    if (instance == null)  
    {  
        instance = Activator.CreateInstance(serviceType);  
    }  
  
    return instance;  
}  
```  
  
 <span data-ttu-id="a7bce-213">次の重要な手順は、`InstanceContextExtension` クラス、`InstanceContextInitializer` クラス、および `InstanceProvider` クラスをサービス モデル ランタイムにインストールすることです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="a7bce-214">カスタム属性を使用すると、サービス実装クラスの詳細を指定して、動作をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="a7bce-215">`DurableInstanceContextAttribute` にはこの属性の実装が含まれ、サービス側のランタイム全体を拡張できるようにするために `IServiceBehavior` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>  
  
 <span data-ttu-id="a7bce-216">このクラスには、使用される記憶域マネージャの型を受け入れるプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="a7bce-217">このようにして実装を行うことにより、ユーザー独自の `IStorageManager` 実装を、この属性のパラメータとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>  
  
 <span data-ttu-id="a7bce-218">`ApplyDispatchBehavior` 実装では、現在の `InstanceContextMode` 属性の `ServiceBehavior` が検証されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="a7bce-219">このプロパティが Singleton に設定されている場合、永続性インスタンスを有効化できず、`InvalidOperationException` がスローされてホストに通知されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>  
  
```  
ServiceBehaviorAttribute serviceBehavior =  
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();  
  
if (serviceBehavior != null &&  
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)  
{  
    throw new InvalidOperationException(  
       ResourceHelper.GetString("ExSingeltonInstancingNotSupported"));  
}  
```  
  
 <span data-ttu-id="a7bce-220">この後、記憶域マネージャのインスタンス、インスタンス コンテキストの初期化子、およびインスタンス プロバイダが作成され、各エンドポイント用に作成された `DispatchRuntime` にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>  
  
```  
IStorageManager storageManager =   
    StorageManagerFactory.GetStorageManager(storageManagerType);  
  
InstanceContextInitializer contextInitializer =  
    new InstanceContextInitializer(storageManager);  
  
InstanceProvider instanceProvider =  
    new InstanceProvider(description.ServiceType);  
  
foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
{  
    ChannelDispatcher cd = cdb as ChannelDispatcher;  
  
    if (cd != null)  
    {  
        foreach (EndpointDispatcher ed in cd.Endpoints)  
        {  
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);  
            ed.DispatchRuntime.InstanceProvider = instanceProvider;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a7bce-221">ここまでを要約すると、このサンプルでは、カスタム コンテキスト ID を交換するためにカスタム ワイヤ プロトコルを有効化するチャネルを作成しました。また、永続ストレージのインスタンスを読み込むように、既定のインスタンス化動作を上書きしました。</span><span class="sxs-lookup"><span data-stu-id="a7bce-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>  
  
 <span data-ttu-id="a7bce-222">残りの手順は、サービス インスタンスを永続ストレージに保存することです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="a7bce-223">既に説明したとおり、`IStorageManager` 実装に状態を保存するには、あらかじめ必要な機能があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="a7bce-224">次に、この機能を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムと統合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-224">We now must integrate this with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime.</span></span> <span data-ttu-id="a7bce-225">これを行うには、サービス実装クラスのメソッドに適用可能な別の属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7bce-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="a7bce-226">つまりこの属性は、サービス インスタンスの状態を変更するメソッドに適用できることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a7bce-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>  
  
 <span data-ttu-id="a7bce-227">この機能は、`SaveStateAttribute` クラスに実装されています。</span><span class="sxs-lookup"><span data-stu-id="a7bce-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="a7bce-228">このクラスには、各操作の `IOperationBehavior` ランタイムを変更する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クラスも実装されています。</span><span class="sxs-lookup"><span data-stu-id="a7bce-228">It also implements `IOperationBehavior` class to modify the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime for each operation.</span></span> <span data-ttu-id="a7bce-229">メソッドの詳細がこの属性で指定されると、適切な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が作成される際に、`ApplyBehavior` ランタイムが `DispatchOperation` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-229">When a method is marked with this attribute, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="a7bce-230">このメソッドの実装のコードは 1 行です。</span><span class="sxs-lookup"><span data-stu-id="a7bce-230">In this method implementation there is single line of code:</span></span>  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 <span data-ttu-id="a7bce-231">この手順により `OperationInvoker` 型のインスタンスが作成され、作成される `Invoker` の `DispatchOperation` プロパティに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="a7bce-232">`OperationInvoker` クラスは、`DispatchOperation` 用に作成された既定の操作呼び出しのラッパーです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="a7bce-233">このクラスは、`IOperationInvoker` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="a7bce-234">`Invoke` メソッドの実装では、実際のメソッド呼び出しは内部の操作呼び出しで代行されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="a7bce-235">ただし、この結果が返される前に `InstanceContext` の記憶域マネージャが使用され、サービス インスタンスが保存されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>  
  
```  
object result = innerOperationInvoker.Invoke(instance,  
    inputs, out outputs);  
  
// Save the instance using the storage manager saved in the   
// current InstanceContext.  
InstanceContextExtension extension =  
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();  
  
extension.StorageManager.SaveInstance(extension.ContextId, instance);  
return result;  
```  
  
## <a name="using-the-extension"></a><span data-ttu-id="a7bce-236">拡張機能の使用</span><span class="sxs-lookup"><span data-stu-id="a7bce-236">Using the Extension</span></span>  
 <span data-ttu-id="a7bce-237">チャネル レイヤとサービス モデル レイヤの拡張を完了すると、どちらも [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-237">Both the channel layer and service model layer extensions are done and they can now be used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span> <span data-ttu-id="a7bce-238">サービスでは、カスタム バインディングを使用してチャネルをチャネル スタックに追加し、サービス実装クラスの詳細を適切な属性で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>  
  
```  
[DurableInstanceContext]  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class ShoppingCart : IShoppingCart  
{  
//…  
     [SaveState]  
     public int AddItem(string item)  
     {  
         //…  
     }  
//…  
 }  
```  
  
 <span data-ttu-id="a7bce-239">クライアント アプリケーションは、カスタム バインディングを使用して DurableInstanceContextChannel をチャネル スタックに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="a7bce-240">構成ファイル内でチャネルを宣言して構成するには、バインド要素セクションをバインド要素拡張のコレクションに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 <span data-ttu-id="a7bce-241">これで、他の基本的なバインド要素と同様、このバインド要素をカスタム バインドで使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a7bce-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>  
  
```xml  
<bindings>  
 <customBinding>  
   <binding name="TextOverHttp">  
     <durableInstanceContext contextType="HttpCookie"/>             
     <reliableSession />  
     <textMessageEncoding />  
     <httpTransport />  
   </binding>  
 </customBinding>  
</bindings>  
```  
  
## <a name="conclusion"></a><span data-ttu-id="a7bce-242">まとめ</span><span class="sxs-lookup"><span data-stu-id="a7bce-242">Conclusion</span></span>  
 <span data-ttu-id="a7bce-243">このサンプルでは、カスタム プロトコル チャネルを作成する方法と、これを有効にするためにサービス動作をカスタマイズする方法を示しました。</span><span class="sxs-lookup"><span data-stu-id="a7bce-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>  
  
 <span data-ttu-id="a7bce-244">構成セクションを使用して `IStorageManager` 実装を指定することで、この拡張機能をさらに強化することができます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="a7bce-245">これにより、サービス コードを再コンパイルせずにバッキング ストアを変更できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>  
  
 <span data-ttu-id="a7bce-246">さらに、インスタンスの状態をカプセル化するクラス (`StateBag` など) を実装できます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="a7bce-247">このクラスにより、変更されるたびに状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="a7bce-248">この方法により、`SaveState` 属性の使用を回避しながら、永続する処理をより正確に実行できます (たとえば、`SaveState` 属性を含むメソッドを呼び出すたびに状態を保存するのではなく、状態が実際に変更されたときに保持できます)。</span><span class="sxs-lookup"><span data-stu-id="a7bce-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>  
  
 <span data-ttu-id="a7bce-249">このサンプルを実行すると、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="a7bce-250">クライアントは、2 つの商品をショッピング カートに追加し、その後ショッピング カートにある商品の一覧をサービスから取得します。</span><span class="sxs-lookup"><span data-stu-id="a7bce-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="a7bce-251">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-251">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  <span data-ttu-id="a7bce-252">サービスを再ビルドすると、データベース ファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="a7bce-253">サンプルを複数回実行する間に状態が保持されていることを確認するには、実行のたびにサンプルを再ビルドしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a7bce-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a7bce-254">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="a7bce-254">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a7bce-255">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7bce-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a7bce-256">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7bce-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a7bce-257">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7bce-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7bce-258">このサンプルを実行するには、SQL Server 2005 または SQL Express 2005 を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="a7bce-259">SQL Server 2005 を実行している場合は、サービスの接続文字列の構成を変更する必要があります </span><span class="sxs-lookup"><span data-stu-id="a7bce-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="a7bce-260">複数コンピューターで実行している場合、SQL Server が必要なのはサーバー コンピューターだけです。</span><span class="sxs-lookup"><span data-stu-id="a7bce-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7bce-261">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7bce-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7bce-262">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a7bce-262">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a7bce-263">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="a7bce-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7bce-264">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a7bce-264">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
## <a name="see-also"></a><span data-ttu-id="a7bce-265">参照</span><span class="sxs-lookup"><span data-stu-id="a7bce-265">See Also</span></span>
