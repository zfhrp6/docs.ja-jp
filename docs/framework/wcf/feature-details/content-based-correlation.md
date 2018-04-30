---
title: コンテンツ ベースの相関関係。
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f46a2b68-8d24-4122-bbee-9573fc3f9fb4
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b4ebd49fbed12f1e8120e67f32496cd782531da
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="content-based-correlation"></a>コンテンツ ベースの相関関係。
ワークフロー サービスがクライアントや他のサービスと通信するときに、交換されるメッセージに、特定のインスタンスに一意に関連付けられたデータが含まれることがよくあります。 コンテンツ ベースの相関関係では、顧客番号や注文 ID などのメッセージ内のデータを使用して、適切なワークフロー インスタンスにメッセージをルーティングします。 このトピックでは、コンテンツ ベースの相関関係をワークフロー内で使用する方法について説明します。  
  
## <a name="using-content-based-correlation"></a>コンテンツ ベースの相関関係の使用  
 コンテンツ ベースの相関関係は、単一のクライアントによってアクセスされる複数のメソッドがワークフロー サービスにあり、交換されるメッセージ内の一部のデータによって目的のインスタンスが識別される場合に使用されます。  
  
> [!NOTE]
>  コンテンツ ベースの相関関係は、コンテキスト交換のバインドがサポート対象のものではないためにコンテキスト相関関係を使用できない場合に便利です。 コンテキスト相関関係の詳細については、次を参照してください。[コンテキスト交換](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)です。  
  
 これらの通信で使用される各メッセージ アクティビティでは、インスタンスを一意に識別するメッセージ内のデータの場所を指定する必要があります。 これを行うには、<xref:System.ServiceModel.MessageQuerySet> または <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> を使用して <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> を指定し、インスタンスを一意に識別するデータを求めるクエリをメッセージに対して実行します。  
  
> [!WARNING]
>  インスタンスの識別に使用されるデータは、相関関係キーにハッシュされます。 相関関係による関連付けで使用するデータは必ず、一意にする必要があります。一意でない場合は、ハッシュされたキーで競合が発生し、誤った場所にメッセージがルーティングされる可能性があります。 たとえば、顧客名だけに基づいた関連付けでは、同じ名前の顧客が複数存在する場合があるため、競合が発生する可能性があります。 メッセージの関連付けに使用するデータの一部として、コロン (`:`) を使用することはできません。コロンは、メッセージ クエリのキーと値の区切り文字として既に使用されており、後でハッシュされる文字列に含まれるためです。  
  
 次の例では、初期<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ワークフロー サービスで返されます、 `OrderId`、次の呼び出しに、クライアントから再び渡される<xref:System.ServiceModel.Activities.Receive>ワークフロー サービス内のアクティビティ。  
  
 [!code-csharp[CFX_ContentCorrelation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#1)]  
  
 前の例は、<xref:System.ServiceModel.Activities.SendReply> によって初期化される、コンテンツ ベースの相関関係を示しています。 <xref:System.ServiceModel.MessageQuerySet> は、このサービスに送信される後続のメッセージを特定するために使用されるデータが `OrderId` であることを指定します。  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 ワークフロー内で <xref:System.ServiceModel.Activities.Receive> に続く <xref:System.ServiceModel.Activities.SendReply> アクティビティは、<xref:System.ServiceModel.Activities.SendReply> によって初期化された関連付けに従います。 どちらのアクティビティも同じ <xref:System.ServiceModel.Activities.CorrelationHandle> を共有しますが、それぞれには、その特定のメッセージ内のどこに対象データがあるかを指定する独自の <xref:System.ServiceModel.MessageQuerySet> および <xref:System.ServiceModel.XPathMessageQuery> があります。 関連付けを初期化するアクティビティでは、この <xref:System.ServiceModel.MessageQuerySet> が <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> プロパティで指定され、後続のすべての <xref:System.ServiceModel.Activities.Receive> アクティビティについては、<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> プロパティを使用して指定されます。  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 コンテンツ ベースの相関関係は、すべてのメッセージ アクティビティ (<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>、<xref:System.ServiceModel.Activities.ReceiveReply>) によって、メッセージの一部としてデータが送信されるときに初期化できます。 特定のデータがメッセージの一部として送信されない場合は、明示的に <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティを使用することで初期化できます。 データの複数の部分で一意にメッセージを識別する必要がある場合は、複数のクエリを <xref:System.ServiceModel.MessageQuerySet> に追加できます。 これらの例では、<xref:System.ServiceModel.Activities.CorrelationHandle> または `CorrelatesWith` プロパティを使用して、`CorrelationHandle` が各アクティビティに明示的に提供されていますが、すべてが `OrderId` で相関するこの例のように、ワークフロー全体で必要な関連付けが 1 つのみである場合は、<xref:System.ServiceModel.Activities.WorkflowServiceHost> で提供される、暗黙の関連付けハンドル管理で十分です。  
  
## <a name="using-the-initializecorrelation-activity"></a>InitializeCorrelation アクティビティの使用  
 前の例では、`OrderId` アクティビティを通じて、<xref:System.ServiceModel.Activities.SendReply> が呼び出し元に送信され、このアクティビティで関連付けが初期化されました。 同じ動作を、<xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティを使用して実現することもできます。 <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティは、<xref:System.ServiceModel.Activities.CorrelationHandle> と、メッセージを適切なインスタンスに割り当てるために使用する項目を表す辞書を受け取ります。 <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティを前のサンプルで使用するには、<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> アクティビティから <xref:System.ServiceModel.Activities.SendReply> を削除し、<xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティを使用して、関連付けを初期化します。  
  
 [!code-csharp[CFX_ContentCorrelation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#4)]  
  
 その後、<xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティは、データを保持する変数が挿入された後、かつ、初期化された <xref:System.ServiceModel.Activities.Receive> との関連付けを行う <xref:System.ServiceModel.Activities.CorrelationHandle> アクティビティの前にワークフローで使用されます。  
  
 [!code-csharp[CFX_ContentCorrelation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#5)]  
  
## <a name="configuring-xpath-queries-using-the-workflow-designer"></a>ワークフロー デザイナーを使用した XPath クエリの構成  
 前の例では、メッセージ クエリで使用されているアクティビティおよび XPath クエリがコードで指定されています。 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] のワークフロー デザイナーでは、XPath の生成を、コンテンツ ベースの相関関係の `DataContract` 型から行うための機能も提供されています。 前の例に示した 1 つ目の XPath 構成は、<xref:System.ServiceModel.Activities.SendReply> 用に構成されていました。  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 XPath をワークフロー デザイナーでメッセージ アクティビティ用に構成するには、ワークフロー デザイナーでアクティビティを選択します。 アクティビティが前の例のように、相関関係を初期化中の場合は、省略記号ボタンをクリックして、 **CorrelationInitializers**プロパティに、**プロパティ**ウィンドウです。 これが表示されます、 **関連付け初期化子**ダイアログ ウィンドウです。 このダイアログ ボックスで、関連付けの種類を指定し、関連付けに使用する内容を選択できます。 <xref:System.ServiceModel.Activities.CorrelationHandle>で変数が指定された、**初期化子の追加**からボックス、および関連付けの種類と、関連付けに使用されるデータが選択されている、 **XPath クエリ** ダイアログ ボックスのセクションでします。  
  
 ![CorrelationInitializer ダイアログ](../../../../docs/framework/wcf/feature-details/media/correlationinitializerdlg.jpg "CorrelationInitializerDlg")  
  
 前の例に示した 2 つ目の XPath クエリは、<xref:System.ServiceModel.Activities.Receive> アクティビティで構成されました。  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 初期化を行わない、関連付けメッセージ アクティビティ用の XPath クエリを構成するのに、ワークフロー デザイナーでアクティビティを選択し、省略記号ボタンをクリックして、 **CorrelatesOn**プロパティに、 **プロパティ**ウィンドウです。 これが表示されます、 **CorrelatesOn の定義**ダイアログ ウィンドウです。  
  
 ![CorrelatesOn の定義](../../../../docs/framework/wcf/feature-details/media/correlatesondialog.jpg "CorrelatesOnDialog")  
  
 指定するこのダイアログ ボックスで、<xref:System.ServiceModel.Activities.CorrelationHandle>内の項目を選択し、 **XPath クエリ**XPath クエリを構築する ボックスの一覧です。
