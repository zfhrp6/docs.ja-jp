---
title: "WF 内での非同期アクティビティの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# WF 内での非同期アクティビティの作成
<xref:System.Activities.AsyncCodeActivity> は使用する基本クラスをアクティビティ作成者に提供します。その結果、派生アクティビティが非同期実行ロジックを実装できるようになります。これは、ワークフローのスケジューラ スレッドを保持したり、並行して実行される可能性があるすべてのアクティビティをブロックしたりすることなく、非同期作業を実行する必要があるカスタム アクティビティに役立ちます。ここでは、<xref:System.Activities.AsyncCodeActivity> を使用してカスタムの非同期アクティビティを作成する方法の概要を説明します。  
  
## AsyncCodeActivity の使用  
 <xref:System.Activities?displayProperty=fullName> は、カスタム アクティビティ作成者に、アクティビティの作成要件に応じてさまざまな基本クラスを提供します。それぞれが特定のセマンティックを持ち、ワークフロー作成者 \(およびアクティビティ ランタイム\) に対応するコントラクトを提供します。<xref:System.Activities.AsyncCodeActivity> ベースのアクティビティは、スケジューラ スレッド、およびマネージ コードで表される実行ロジックに関連して、非同期に作業を実行するアクティビティです。非同期作業になると、<xref:System.Activities.AsyncCodeActivity> によって実行中にアイドル ポイントが発生する可能性があります。非同期作業には揮発的な性質があるため、<xref:System.Activities.AsyncCodeActivity> はアクティビティの実行期間に対して常に非永続的なブロックを作成します。こうすることで、ワークフロー ランタイムによって、非同期作業中にワークフロー インスタンスが永続化されることを回避できます。また、非同期コードの実行中にワークフロー インスタンスがアンロードされることを回避できます。  
  
### AsyncCodeActivity メソッド  
 <xref:System.Activities.AsyncCodeActivity> から派生するアクティビティでは、<xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> メソッドと <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> メソッドをカスタム コードでオーバーライドすることで、非同期実行ロジックを作成できます。ランタイムから呼び出される場合、これらのメソッドは <xref:System.Activities.AsyncCodeActivityContext> に渡されます。<xref:System.Activities.AsyncCodeActivityContext> はアクティビティの作成者に、コンテキストの <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> プロパティを内の <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>\/ <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 全体で共有状態を提供します。次の例では、`GenerateRandom` アクティビティによって非同期に乱数を生成します。  
  
 [!code-csharp[CFX_ActivityExample#8](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 前の例のアクティビティは、<xref:System.Activities.AsyncCodeActivity%601> から派生し、`Result` という昇格した `OutArgument<int>` を備えています。`GetRandom` メソッドが返す値は、<xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> のオーバーライドによって抽出され、返されます。また、この値は `Result` 値として設定されます。結果を返さない非同期アクティビティは、<xref:System.Activities.AsyncCodeActivity> から派生する必要があります。次の例では、<xref:System.Activities.AsyncCodeActivity> から派生する `DisplayRandom` アクティビティが定義されます。このアクティビティは `GetRandom` アクティビティに似ていますが、結果を返す代わりにコンソールにメッセージを表示します。  
  
 [!code-csharp[CFX_ActivityExample#11](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 戻り値がないため、`DisplayRandom` は <xref:System.Func%602> の代わりに <xref:System.Action> を使用してデリゲートを呼び出し、デリゲートは値を返さないことに注意してください。  
  
 また、<xref:System.Activities.AsyncCodeActivity> は <xref:System.Activities.AsyncCodeActivity.Cancel%2A> のオーバーライドも提供します。<xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> と <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> は必須のオーバーライドですが、<xref:System.Activities.AsyncCodeActivity.Cancel%2A> はオプションで、アクティビティを取り消したり中止したりするときに未処理の非同期状態を消去できるようにオーバーライドすることが可能です。消去が可能で `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` が `true` の場合、アクティビティでは <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> を呼び出します。このメソッドからスローされるすべての例外は、ワークフロー インスタンスにとって致命的なものです。  
  
 [!code-csharp[CFX_ActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### クラスでの非同期メソッドの呼び出し  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の多くのクラスには、非同期機能が用意されています。この非同期機能は、<xref:System.Activities.AsyncCodeActivity> ベースのアクティビティを使用して非同期に呼び出すことができます。「[アクティビティでの AsyncOperationContext の使用](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md)」の次の例では、<xref:System.IO.FileStream> クラスを使用して非同期にファイルを作成するアクティビティが作成されます。  
  
 [!code-csharp[CFX_ActivityExample#12](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### BeginExecute および EndExecute の間の共有状態  
 前の例では、<xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> で作成された <xref:System.IO.FileStream> のオブジェクトは <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 内でアクセスされました。これは、`file` 変数が <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 内の <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=fullName> のプロパティに渡されたために可能です。これは <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> および <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> の間で状態を共有するためのただしい方法です。アクティビティのオブジェクトは複数のアクティビティのインスタンスに参照される可能性があるため、派生クラス内 \(この場合は `FileWriter`\) のメンバー変数を使用して <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> および <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> の間の状態を共有することは正しくありません。状態を共有するためにメンバー変数を使用すると、1 つの <xref:System.Activities.ActivityInstance> からの値をオーバーライドしたり、他の <xref:System.Activities.ActivityInstance> からの値を使用することになる場合があります。  
  
### 引数値へのアクセス  
 <xref:System.Activities.AsyncCodeActivity> の環境は、アクティビティに定義されている引数から構成されます。これらの引数は、<xref:System.Activities.AsyncCodeActivityContext> パラメーターを使用して <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>\/<xref:System.Activities.AsyncCodeActivity.EndExecute%2A> オーバーライドからアクセスできます。デリゲートでは引数にアクセスできませんが、そのパラメーターを使用して引数値または任意の他の必要なデータをデリゲートに渡すことができます。次の例では、`Max` 引数から包含的上限を取得する乱数生成アクティビティを定義します。デリゲートを呼び出すと、引数の値は非同期コードに渡されます。  
  
 [!code-csharp[CFX_ActivityExample#9](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### AsyncCodeActivity を使用した、操作または子アクティビティのスケジュール設定  
 <xref:System.Activities.AsyncCodeActivity> 派生カスタム アクティビティはワークフローのスレッドに関する作業を非同期に実行するメソッドを提供しますが、子アクティビティ、またはアクションをスケジュールする機能は提供しません。ただし、非同期動作は、コンポジションを介して子アクティビティのスケジュールに組み込むことができます。非同期アクティビティを作成し、<xref:System.Activities.Activity> または <xref:System.Activities.NativeActivity> の派生アクティビティと共に構成して、子アクティビティまたはアクションの非同期動作とスケジュール機能を提供できます。たとえば、アクティビティを <xref:System.Activities.Activity> から派生するように作成し、その実装時に <xref:System.Activities.Statements.Sequence> に非同期アクティビティと共にアクティビティのロジックを実装する他のアクティビティを含めることができます。<xref:System.Activities.Activity> および <xref:System.Activities.NativeActivity> を使用したアクティビティの構成例の詳細については、「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md), [アクティビティ作成オプション](../../../docs/framework/windows-workflow-foundation//activity-authoring-options-in-wf.md)」、および「[複合](../../../docs/framework/windows-workflow-foundation/samples/composite.md)」のアクティビティ サンプルを参照してください。  
  
## 参照  
 <xref:System.Action>   
 <xref:System.Func%602>   
 [アクティビティでの AsyncOperationContext の使用](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md)