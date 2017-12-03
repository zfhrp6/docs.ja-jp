---
title: "Windows Workflow の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b74ecc3363e84d006d82ecb14accbf40de7e2738
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="windows-workflow-overview"></a>Windows Workflow の概要
ワークフローは、一連の要素の単位と呼ばれる*アクティビティ*実際のプロセスを記述するモデルとして保存されています。 ワークフローでは、短期間だけ行われる業務や長期間にわたって行われる業務の各部分の実行順序と、それらの間の依存関係を表すことができます。 このような業務はモデルの最初から最後まで通して行われます。アクティビティには、人間によって実行されるものと、システム機能によって実行されるものがあります。  
  
## <a name="workflow-run-time-engine"></a>ワークフロー ランタイム エンジン  
 実行されるそれぞれのワークフロー インスタンスは、ホスト プロセスが次のいずれかを通して対話するプロセス内ランタイム エンジンによって作成および保持されます。  
  
-   <xref:System.Activities.WorkflowInvoker>。メソッドのようにワークフローを呼び出します。  
  
-   <xref:System.Activities.WorkflowApplication>。1 つのワークフロー インスタンスの実行に対して明示的な制御を行います。  
  
-   <xref:System.ServiceModel.WorkflowServiceHost>。複数のインスタンスを使用する場合にメッセージ ベースの対話を行います。  
  
 これらの各クラスは、アクティビティの実行に関与する <xref:System.Activities.ActivityInstance> として表されるコアのアクティビティ ランタイムをラップします。 実行するアプリケーション ドメイン内では、同時に複数の <xref:System.Activities.ActivityInstance> オブジェクトを使用できます。  
  
 前述のホストと対話する 3 つのオブジェクトは、それぞれワークフロー プログラムと呼ばれるアクティビティのツリーから作成されます。 ワークフローは、これらの型を使用するか、<xref:System.Activities.ActivityInstance> をラップするカスタムのホストを使用して、コンソール アプリケーション、フォームに基づくアプリケーション、Windows サービス、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web サイト、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスなどの任意の Windows プロセス内で実行できます。  
  
 ![ホスト プロセス内のワークフロー コンポーネント](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
ホスト プロセス内のワークフローのコンポーネント  
  
## <a name="interaction-between-workflow-components"></a>ワークフロー コンポーネント間の対話  
 次の図は、ワークフロー コンポーネントが互いにどのように対話するかを示しています。  
  
 ![ワークフローの相互作用](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")  
  
 前の図では、複数のワークフロー インスタンスを呼び出すために、<xref:System.Activities.WorkflowInvoker.Invoke%2A> クラスの <xref:System.Activities.WorkflowInvoker> メソッドが使用されています。 <xref:System.Activities.WorkflowInvoker> は、ホストからの管理が不要の簡易なワークフローに使用されます。ホストからの管理が必要なワークフロー (<xref:System.Activities.Bookmark> の再開など) は、代わりに <xref:System.Activities.WorkflowApplication.Run%2A> を使用して実行する必要があります。 他のワークフロー インスタンスを呼び出す前に、現在のワークフロー インスタンスが完了するのを待機する必要はありません。ランタイム エンジンでは、複数のワークフロー インスタンスの同時実行をサポートしています。  呼び出されるワークフローは次のとおりです。  
  
-   <xref:System.Activities.Statements.Sequence> 子アクティビティを含む <xref:System.Activities.Statements.WriteLine> アクティビティ。 親アクティビティの <xref:System.Activities.Variable> は、子アクティビティの <xref:System.Activities.InArgument> にバインドされます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]変数、引数、およびバインディングの場合は、次を参照してください。[変数と引数](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md)です。  
  
-   `ReadLine` という名前のカスタム アクティビティ。 <xref:System.Activities.OutArgument> メソッドの呼び出しに対して `ReadLine` アクティビティの <xref:System.Activities.WorkflowInvoker.Invoke%2A> が返されます。  
  
-   <xref:System.Activities.CodeActivity> 抽象クラスから派生するカスタム アクティビティ。 <xref:System.Activities.CodeActivity> は、<xref:System.Activities.CodeActivityContext> メソッドのパラメーターとして使用可能な <xref:System.Activities.CodeActivity.Execute%2A> を使用して、ランタイム機能 (追跡やプロパティなど) にアクセスできます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]これらのランタイムの機能を参照してください[ワークフロー追跡とトレース](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)と[ワークフロー実行プロパティ](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)です。  
  
## <a name="see-also"></a>関連項目  
 [BizTalk Server 2006 または WF?プロジェクトの適切なワークフロー ツールの選択](http://go.microsoft.com/fwlink/?LinkId=154901)
