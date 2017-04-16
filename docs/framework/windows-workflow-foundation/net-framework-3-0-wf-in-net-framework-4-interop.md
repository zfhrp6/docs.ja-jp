---
title: "Interop アクティビティと .NET Framework 4 内の .NET Framework 3.0 WF アクティビティの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Interop アクティビティと .NET Framework 4 内の .NET Framework 3.0 WF アクティビティの使用
 <xref:System.Activities.Statements.Interop> アクティビティは、 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (WF 4.5) アクティビティをラップする、 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] (WF 3.5) アクティビティ内で、 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ワークフローです。 WF 3 アクティビティは、単一のリーフ アクティビティまたはツリー全体のアクティビティです。 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] アクティビティの実行 (取り消しおよび例外処理を含む) および保持は、実行中の [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ワークフロー インスタンスのコンテキスト内で発生します。  
  
> [!NOTE]
>   <xref:System.Activities.Statements.Interop> ワークフローのプロジェクトで、アクティビティがワークフロー デザイナー ツールボックスに表示されない、 **ターゲット フレームワーク** ] に設定 **.NET Framework 4.5**します。  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>WF 3 アクティビティと Interop アクティビティを使用するための基準  
 WF 3 アクティビティ内で正常に実行する、 <xref:System.Activities.Statements.Interop> アクティビティ、次の条件を満たす必要があります。  
  
-   WF 3 アクティビティから派生する必要があります <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName>します。  
  
-   WF 3 アクティビティが `public` として宣言されています。また、`abstract` ではありません。  
  
-   WF 3 アクティビティにパブリックの既定コンストラクターがあります。  
  
-   型がインターフェイスでの制限のため、 <xref:System.Activities.Statements.Interop> アクティビティがサポートできる、 <xref:System.Workflow.Activities.HandleExternalEventActivity> と <xref:System.Workflow.Activities.CallExternalMethodActivity> ことはできませんが、直接使用、派生アクティビティをワークフロー通信アクティビティ ツール (WCA.exe) を使用して作成を使用できます。 参照してください [Windows Workflow Foundation ツール](http://go.microsoft.com/fwlink/?LinkId=178889) 詳細です。  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Interop アクティビティ内の WF 3 アクティビティの構成  
 構成し、相互運用の境界を越えて、WF 3 アクティビティに出入りするデータを渡す、WF 3 アクティビティのプロパティとメタデータのプロパティがによって公開されて、 <xref:System.Activities.Statements.Interop> アクティビティ。 WF 3 アクティビティのメタデータのプロパティ (よう <xref:System.Workflow.ComponentModel.Activity.Name%2A>) を介して公開される、 <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> コレクションです。 これは、WF 3 アクティビティのメタデータのプロパティに関する値を定義するために使用される名前と値ペアのコレクションです。 メタデータのプロパティは、プロパティを依存関係プロパティに基づく、 <xref:System.Workflow.ComponentModel.DependencyPropertyOptions> フラグを設定します。  
  
 WF 3 アクティビティのプロパティがを介して公開される、 <xref:System.Activities.Statements.Interop.ActivityProperties%2A> コレクションです。 これは名前と値のペアのセットの各値が、 <xref:System.Activities.Argument> オブジェクト、WF 3 アクティビティのプロパティの引数を定義するために使用します。 としてすべてのプロパティを表示、WF 3 アクティビティのプロパティの方向は推論できないため、 <xref:System.Activities.InArgument>/<xref:System.Activities.OutArgument> のペアです。 やすい表示するアクティビティの使用方法、プロパティ、によって、 <xref:System.Activities.InArgument> エントリ、 <xref:System.Activities.OutArgument> エントリ、またはその両方です。 想定される名前、 <xref:System.Activities.InArgument> コレクション内のエントリがプロパティの名前を WF 3 アクティビティに定義されています。 想定される名前、 <xref:System.Activities.OutArgument> コレクション内のエントリは、プロパティの名前、および文字列"out を"連結したものです。  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Interop アクティビティ内で WF 3 アクティビティを使用する際の制限  
 WF 3 システム標準アクティビティを直接ラップすることはできません、 <xref:System.Activities.Statements.Interop> アクティビティ。 一部の WF 3 アクティビティなど、 <xref:System.Workflow.Activities.DelayActivity>, 、これは、類似する WF 4.5 アクティビティがあるためです。 その他のアクティビティの場合、これはそのアクティビティの機能がサポートされないことが原因です。 多くの WF 3 システム標準アクティビティによってラップしたワークフロー内で使用できます、 <xref:System.Activities.Statements.Interop> アクティビティは、次の制限を受けます。  
  
1.  <xref:System.ServiceModel.Activities.Send> と <xref:System.ServiceModel.Activities.Receive> では使用できません、 <xref:System.Activities.Statements.Interop> アクティビティ。  
  
2.  <xref:System.Workflow.Activities.WebServiceInputActivity>, 、<xref:System.Workflow.Activities.WebServiceOutputActivity>, 、および <xref:System.Workflow.Activities.WebServiceFaultActivity> 内で使用されることはできません、 <xref:System.Activities.Statements.Interop> アクティビティ。  
  
3.  <xref:System.Workflow.Activities.InvokeWorkflowActivity> 内で使用されることはできません、 <xref:System.Activities.Statements.Interop> アクティビティ。  
  
4.  <xref:System.Workflow.ComponentModel.SuspendActivity> 内で使用されることはできません、 <xref:System.Activities.Statements.Interop> アクティビティ。  
  
5.  補正に関連するアクティビティを使用できない、 <xref:System.Activities.Statements.Interop> アクティビティ。  
  
 内の WF 3 アクティビティの使用に関して理解できるいくつかの動作仕様もあります、 <xref:System.Activities.Statements.Interop> アクティビティ。  
  
1.  WF 3 アクティビティに含まれている、 <xref:System.Activities.Statements.Interop> アクティビティがするときに初期化、 <xref:System.Activities.Statements.Interop> アクティビティが実行されます。 WF 4.5 には、実行前にワークフロー インスタンスの初期化フェーズはありません。  
  
2.  そのトランザクションの開始位置に関係なく、トランザクションの開始時に、WF 4.5 ランタイムはワークフロー インスタンス状態を確認できません (内部または外部で、 <xref:System.Activities.Statements.Interop> アクティビティ)。  
  
3.  内のアクティビティに関する WF 3 追跡レコード、 <xref:System.Activities.Statements.Interop> として WF 4.5 の追跡参加要素に提供されます <xref:System.Activities.Tracking.InteropTrackingRecord> オブジェクトです。 <xref:System.Activities.Tracking.InteropTrackingRecord> の派生クラスは、 <xref:System.Activities.Tracking.CustomTrackingRecord>します。  
  
4.  WF 3 カスタム アクティビティからは、WF 3 ワークフロー ランタイム内とまったく同じ方法で、相互運用環境内でワークフロー キューを使用してデータにアクセスできます。 カスタム アクティビティ コードの変更は必要ありません。 ホストで、データが追加、WF 3 ワークフロー キューを再開することで、 <xref:System.Activities.Bookmark>します。 ブックマークの名前の文字列の形式は、 <xref:System.IComparable> ワークフロー キューの名前。  
  
## <a name="see-also"></a>「  
 [.NET Framework 4.5 ワークフローでの .NET Framework 3.0 または .NET Framework 3.5 アクティビティの使用](../../../docs/framework/windows-workflow-foundation/samples/using-a-net-3-0-or-net-3-5-activity-in-a-net-4-5-workflow.md)