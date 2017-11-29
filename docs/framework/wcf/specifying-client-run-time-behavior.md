---
title: "クライアントのランタイム動作の指定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3aebab3799af562d958eb8e3e83380e734fe9268
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-client-run-time-behavior"></a><span data-ttu-id="5327f-102">クライアントのランタイム動作の指定</span><span class="sxs-lookup"><span data-stu-id="5327f-102">Specifying Client Run-Time Behavior</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="5327f-103"> クライアントは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスと同様に、クライアント アプリケーションに合わせてランタイム動作を変更するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="5327f-103"> clients, like [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services, can be configured to modify the run-time behavior to suit the client application.</span></span> <span data-ttu-id="5327f-104">クライアントのランタイム動作を指定する際には、3 つの属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5327f-104">Three attributes are available for specifying client run-time behavior.</span></span> <span data-ttu-id="5327f-105">双方向クライアント コールバック オブジェクトは、<xref:System.ServiceModel.CallbackBehaviorAttribute> 属性と <xref:System.ServiceModel.Description.CallbackDebugBehavior> 属性を使用して、そのランタイム動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="5327f-105">Duplex client callback objects can use the <xref:System.ServiceModel.CallbackBehaviorAttribute> and <xref:System.ServiceModel.Description.CallbackDebugBehavior> attributes to modify their run-time behavior.</span></span> <span data-ttu-id="5327f-106">もう 1 つの属性 <xref:System.ServiceModel.Description.ClientViaBehavior> は、論理送信先を直接のネットワーク送信先と区別するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5327f-106">The other attribute, <xref:System.ServiceModel.Description.ClientViaBehavior>, can be used to separate the logical destination from the immediate network destination.</span></span> <span data-ttu-id="5327f-107">さらに、双方向クライアントのコールバック型では、サービス側の動作の一部を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5327f-107">In addition, duplex client callback types can use some of the service-side behaviors.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="5327f-108">[サービス ランタイムの動作を指定する](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)です。</span><span class="sxs-lookup"><span data-stu-id="5327f-108"> [Specifying Service Run-Time Behavior](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).</span></span>  
  
## <a name="using-the-callbackbehaviorattribute"></a><span data-ttu-id="5327f-109">CallbackBehaviorAttribute の使用</span><span class="sxs-lookup"><span data-stu-id="5327f-109">Using the CallbackBehaviorAttribute</span></span>  
 <span data-ttu-id="5327f-110"><xref:System.ServiceModel.CallbackBehaviorAttribute> クラスを使用して、クライアント アプリケーションのコールバック コントラクト実装の実行動作を構成または拡張できます。</span><span class="sxs-lookup"><span data-stu-id="5327f-110">You can configure or extend the execution behavior of a callback contract implementation in a client application by using the <xref:System.ServiceModel.CallbackBehaviorAttribute> class.</span></span> <span data-ttu-id="5327f-111">この属性は、インスタンス化動作とトランザクションの設定を除き、<xref:System.ServiceModel.ServiceBehaviorAttribute> クラスと同様の機能をコールバック クラスに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="5327f-111">This attribute performs a similar function for the callback class as the <xref:System.ServiceModel.ServiceBehaviorAttribute> class, with the exception of instancing behavior and transaction settings.</span></span>  
  
 <span data-ttu-id="5327f-112"><xref:System.ServiceModel.CallbackBehaviorAttribute> クラスは、コールバック コントラクトを実装するクラスに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5327f-112">The <xref:System.ServiceModel.CallbackBehaviorAttribute> class must be applied to the class that implements the callback contract.</span></span> <span data-ttu-id="5327f-113">双方向以外のコントラクト実装に適用した場合は、実行時に <xref:System.InvalidOperationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5327f-113">If applied to a nonduplex contract implementation, an <xref:System.InvalidOperationException> exception is thrown at run time.</span></span> <span data-ttu-id="5327f-114"><xref:System.ServiceModel.CallbackBehaviorAttribute> オブジェクトを使用してマーシャリングするスレッドを決定するコールバック オブジェクトの <xref:System.Threading.SynchronizationContext> クラス、メッセージ検証を実施する <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> プロパティ、およびデバッグのために例外を <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> オブジェクトとしてサービスに返す <xref:System.ServiceModel.FaultException> プロパティのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5327f-114">The following code example shows a <xref:System.ServiceModel.CallbackBehaviorAttribute> class on a callback object that uses the <xref:System.Threading.SynchronizationContext> object to determine the thread to marshal to, the <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> property to enforce message validation, and the <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> property to return exceptions as <xref:System.ServiceModel.FaultException> objects to the service for debugging purposes.</span></span>  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a><span data-ttu-id="5327f-115">CallbackDebugBehavior を使用したマネージ例外情報のフローの有効化</span><span class="sxs-lookup"><span data-stu-id="5327f-115">Using CallbackDebugBehavior to Enable the Flow of Managed Exception Information</span></span>  
 <span data-ttu-id="5327f-116">アプリケーション構成ファイルまたはプログラムで、<xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> プロパティを `true` に設定すると、デバッグのためにクライアント コールバック オブジェクト内のマネージ例外情報をサービスに戻すフローを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="5327f-116">You can enable the flow of managed exception information in a client callback object back to the service for debugging purposes by setting the <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> property to `true` either programmatically or from an application configuration file.</span></span>  
  
 <span data-ttu-id="5327f-117">マネージ例外情報をサービスに戻すのは、セキュリティ リスクになる可能性があります。これは、例外の詳細により、非承認のサービスで使用可能な内部クライアントの実装についての情報が公開されるからです。</span><span class="sxs-lookup"><span data-stu-id="5327f-117">Returning managed exception information to services can be a security risk because exception details expose information about the internal client implementation that  unauthorized services could use.</span></span> <span data-ttu-id="5327f-118">さらに、<xref:System.ServiceModel.Description.CallbackDebugBehavior> プロパティをプログラムで設定することはできますが、配置するときに <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> を無効にすることを忘れがちになります。</span><span class="sxs-lookup"><span data-stu-id="5327f-118">In addition, although the <xref:System.ServiceModel.Description.CallbackDebugBehavior> properties can also be set programmatically, it can be easy to forget to disable <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> when deploying.</span></span>  
  
 <span data-ttu-id="5327f-119">セキュリティの問題にかかわるので、以下を強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5327f-119">Because of the security issues involved, it is strongly recommended that:</span></span>  
  
-   <span data-ttu-id="5327f-120"><xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> プロパティの値を `true` に設定するには、アプリケーション構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="5327f-120">You use an application configuration file to set the value of the <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="5327f-121">これは、制御されたデバッグ シナリオの場合に限って行います。</span><span class="sxs-lookup"><span data-stu-id="5327f-121">You do so only in controlled debugging scenarios.</span></span>  
  
 <span data-ttu-id="5327f-122">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に、SOAP メッセージのクライアント コールバック オブジェクトからマネージ例外情報を返すように指示するクライアント構成ファイルを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="5327f-122">The following code example shows a client configuration file that instructs [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to return managed exception information from a client callback object in SOAP messages.</span></span>  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a><span data-ttu-id="5327f-123">ClientViaBehavior 動作の使用</span><span class="sxs-lookup"><span data-stu-id="5327f-123">Using the ClientViaBehavior Behavior</span></span>  
 <span data-ttu-id="5327f-124"><xref:System.ServiceModel.Description.ClientViaBehavior> 動作を使用して、トランスポート チャネルを作成する対象の URI (Uniform Resource Identifier) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5327f-124">You can use the <xref:System.ServiceModel.Description.ClientViaBehavior> behavior to specify the Uniform Resource Identifier for which the transport channel should be created.</span></span> <span data-ttu-id="5327f-125">この動作は、直接のネットワーク送信先が、メッセージの処理先と異なる場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="5327f-125">Use this behavior when the immediate network destination is not the intended processor of the message.</span></span> <span data-ttu-id="5327f-126">これにより、呼び出し側のアプリケーションが最終的な送信先を知っているとは限らないとき、または送信先の `Via` ヘッダーがアドレスでないときに、複数のホップを経由するメッセージ交換が可能になります。</span><span class="sxs-lookup"><span data-stu-id="5327f-126">This enables multiple-hop conversations when the calling application does not necessarily know the ultimate destination or when the destination `Via` header is not an address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5327f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="5327f-127">See Also</span></span>  
 [<span data-ttu-id="5327f-128">サービスのランタイム動作の指定</span><span class="sxs-lookup"><span data-stu-id="5327f-128">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
