---
title: "ステート マシン ワークフロー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# ステート マシン ワークフロー
ステート マシンは、プログラムを開発するための既知のパラダイムです。<xref:System.Activities.Statements.StateMachine> アクティビティは、<xref:System.Activities.Statements.State>、<xref:System.Activities.Statements.Transition> および他のアクティビティと共に、ステート マシン ワークフロー プログラムのビルドに使用できます。このトピックでは、ステート マシン ワークフローの概要について説明します。  
  
## ステート マシン ワークフローの概要  
 ステート マシン ワークフローは、イベント ドリブンの方法でワークフローをモデル化できるモデル化スタイルを提供します。<xref:System.Activities.Statements.StateMachine> アクティビティには、ステート マシンのロジックを構成し、アクティビティが使用される任意の場所で使用できる、状態および遷移が含まれます。ステート マシン ランタイムにはいくつかのクラスがあります:  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 ステート マシン ワークフローを作成するため、状態が <xref:System.Activities.Statements.StateMachine> アクティビティに追加され、遷移は状態間のフローのコントロールに使用されます。次のスクリーンショットには、[チュートリアル入門](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md) の手順 [方法: ステート マシン ワークフローを作成する](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md) から、 3 つの状態と 3 つの遷移を持つステート マシン ワークフローが示されます。**\[ターゲットの初期化\]** が初期状態で、ワークフローの最初の状態を表します。これは **\[開始\]** ノードから伸びる線によって示されます。ワークフローの最終状態は **\[FinalState\]** と呼ばれ、ワークフローが完了する点を表します。  
  
 ![完成したステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation//media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 ステート マシン ワークフローには 1 つのみの初期状態および少なくとも 1 つの最終状態が必要です。最終状態ではない各状態には少なくとも 1 個以上の移行が必要です。次のセクションでは状態および遷移の作成および構成について説明します。  
  
## 状態の作成および構成  
 <xref:System.Activities.Statements.State> はステート マシンの状態を表します。ワークフローに <xref:System.Activities.Statements.State> を追加するには、**\[ツールボックス\]** の **\[ステート マシン\]** セクションから **\[State\]** アクティビティをドラッグし、[!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 画面上の <xref:System.Activities.Statements.StateMachine> アクティビティ上にドロップします。  
  
 ![WF4 ステート マシン アクティビティ](../../../docs/framework/windows-workflow-foundation//media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 に **\[初期状態\]**として状態を構成するには、状態を右クリックして **\[初期状態として設定\]** を選択します。さらに、現在の初期状態がない場合、初期状態はワーク フローの上の **\[開始\]** ノードから目的の状態まで線をドラッグして指定できます。<xref:System.Activities.Statements.StateMachine> のアクティビティがワークフロー デザイナーにドロップされると、**\[State1\]** という名前の初期状態が事前に構成されます。ステート マシン ワークフローには 1 つのみの初期状態が必要です。  
  
 ステート マシンを終了させる状態を表す状態は、最終状態と呼ばれます。最終状態とは、`true` に設定された <xref:System.Activities.Statements.State.IsFinal%2A> のプロパティを持ち、<xref:System.Activities.Statements.State.Exit%2A> のアクティビティは持たず、そこから発生する遷移がない状態です。ワークフローに最終状態を追加するには、**\[FinalState\]** のアクティビティ デザイナーを **\[ツールボックス\]** の **\[ステート マシン\]** セクションからドラッグし、それを [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 画面の <xref:System.Activities.Statements.StateMachine> のアクティビティ上にドロップします。ステート マシン ワークフローには少なくとも 1 つの最終ステートが必要です。  
  
### エントリおよび終了操作の構成  
 状態は、<xref:System.Activities.Statements.State.Entry%2A> アクションおよび <xref:System.Activities.Statements.State.Exit%2A> アクションを持つことができます。\(最終状態として構成されている状態は 1 つのみのエントリ アクションを持つことができます\)。ワークフロー インスタンスが状態に入ると、エントリ アクションのあらゆるアクティビティが実行されます。エントリ アクションが完了すると、状態の遷移のトリガーがスケジュールされます。別のステートへの遷移が確認されると、状態遷移が同じ状態に戻ったとしても、終了アクションのアクティビティが実行されます。終了のアクションが完了すると、遷移のアクションのアクティビティが実行され、その新しい状態が遷移され、エントリ アクションがスケジュールされます。  
  
> [!NOTE]
>  ステート マシン ワークフローをデバッグする場合、ブレークポイントは、ステート マシン ワークフロー内のルート ステート マシンのアクティビティおよび状態の上に配置できます。ブレークポイントは繊維の上に血肉節配置されず、状態及び遷移内の任意のアクティビティ上に配置される場合があります。  
  
## 遷移の作成および構成  
 すべての状態には少なくとも 1 つの遷移が必要です。例外は遷移を持たないかもしれない最終状態です。遷移は、状態マシン ワークフローに状態が追加される後に追加される、または状態がドロップされた時に作成される場合があります。  
  
 1 つの手順で <xref:System.Activities.Statements.State> を追加して遷移を作成するには、**\[ツールボックス\]** の **\[ステート マシン\]** から **\[状態\]** のアクティビティをドラッグしてワークフロー デザイナー内の他の状態の上に置きます。ドラッグされている <xref:System.Activities.Statements.State> が別の <xref:System.Activities.Statements.State> の上にある場合、もう一方の <xref:System.Activities.Statements.State> の周囲に 4 つの三角形が表示されます。<xref:System.Activities.Statements.State> が 4 個の三角形のいずれかの上にドロップされる場合、それはステート マシンに追加され、ソース <xref:System.Activities.Statements.State> からドロップされた目的の <xref:System.Activities.Statements.State> への遷移が作成されます。詳細については、「[Transition アクティビティ デザイナー](../Topic/Transition%20Activity%20Designer.md)」を参照してください。  
  
 状態の追加後に遷移を作成するには、2 つのオプションがあります。最初のオプションは、ワークフロー デザイナー画面から状態をドラッグして既存の状態の上に置き、ドロップ ポイントのいずれかにドロップすることです。これは、前のセクションで説明したメソッドに非常に似ています。また、マウス ポインターを目的のソースの状態の上に置き、線を適切な目的の状態にドラッグすることもできます。  
  
> [!NOTE]
>  ステート マシンの単一の状態はワーク フロー デザイナーを使用して作成された最大 76 の遷移を持つことができます。デザイナーを使用せずに作成されるワーク フローの状態の遷移制限は、システム リソースによってのみ制限されます。  
  
 遷移は <xref:System.Activities.Statements.Transition.Trigger%2A>、<xref:System.Activities.Statements.Transition.Condition%2A>、および <xref:System.Activities.Statements.Transition.Action%2A> を持つ場合があります。移行の <xref:System.Activities.Statements.Transition.Trigger%2A> は遷移のソース状態のアクションの <xref:System.Activities.Statements.State.Entry%2A> アクションが完了する時にスケジュールされます。通常 <xref:System.Activities.Statements.Transition.Trigger%2A> は、ある種のイベント発生を待つアクティビティですが、任意のアクティビティまたはアクティビティがなくてもかまいません。<xref:System.Activities.Statements.Transition.Trigger%2A> のアクティビティが完了したら、<xref:System.Activities.Statements.Transition.Condition%2A> がある場合は評価されます。<xref:System.Activities.Statements.Transition.Trigger%2A> のアクティビティがない場合、<xref:System.Activities.Statements.Transition.Condition%2A> は直ちに評価されます。条件が `false` になる場合、遷移はキャンセルされ、その状態からのすべての遷移の <xref:System.Activities.Statements.Transition.Trigger%2A> アクティビティは再スケジュールされます。現在の遷移と同じソースの状態を共有する他の遷移がある場合、<xref:System.Activities.Statements.Transition.Trigger%2A> のアクションもキャンセルされて、再スケジュールされます。<xref:System.Activities.Statements.Transition.Condition%2A> が `true` である場合、または条件がない場合、ソース状態の <xref:System.Activities.Statements.State.Exit%2A> のアクションが実行され、遷移の <xref:System.Activities.Statements.Transition.Action%2A> が実行されます。<xref:System.Activities.Statements.Transition.Action%2A> が完了すると、コントロールは **\[ターゲット\]** 状態を渡します  
  
 共通トリガーを共有する遷移は、共有トリガー遷移として知られます。共有トリガー遷移グループの各遷移には同じトリガーがありますが、<xref:System.Activities.Statements.Transition.Condition%2A> およびアクションは一意です。遷移に追加のアクションを追加し、共有遷移を作成するには、目的の遷移の開始点を表す円をクリックし、目的の状態にドラッグします。新しい遷移は最初の遷移と同じトリガーを共有しますが、一意の条件とアクションがあります。共有遷移は、Transition デザイナー内から Transition デザイナーの下部にある **\[共有されるトリガーの遷移の追加\]** をクリックし、**\[接続の使用可能な状態\]** ボックスから目的のターゲットの状態を選択することでも作成できます。  
  
> [!NOTE]
>  遷移の <xref:System.Activities.Statements.Transition.Condition%2A> が `False` と評価された場合 \(または共有トリガー遷移のすべての状態が `False` と評価された場合\)、遷移は発生せず、その状態からのすべての遷移のすべてのトリガーは再スケジュールされます。  
  
 ステート マシン ワークフロー作成方法の詳細については、「[方法: ステート マシン ワークフローを作成する](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md)」、「[StateMachine アクティビティ デザイナー](../Topic/StateMachine%20Activity%20Designer.md)」、「[State アクティビティ デザイナー](../Topic/State%20Activity%20Designer.md)」、「[FinalState アクティビティ デザイナー](../Topic/FinalState%20Activity%20Designer.md)」、および「[Transition アクティビティ デザイナー](../Topic/Transition%20Activity%20Designer.md)」を参照してください。  
  
## ステート マシン用語  
 このセクションでは、このトピック全体で使用されるステート マシンの表現形式を定義します。  
  
 State  
 ステート マシンを構成する基本単位。ステート マシンは任意の特定の時刻に 1 つの状態になれます。  
  
 エントリ アクション  
 状態に入るときに実行されるアクティビティ  
  
 終了アクション  
 状態を終了するときに実行されるアクティビティ  
  
 遷移  
 2 つの状態間の直接の関係で、特定の種類のイベントの生成に対するステート マシンの完全な応答を表します。  
  
 共有遷移  
 1 つまたはそれ以上の遷移を持つソースの状態やトリガーを共有するトランザクションですが、一意の条件とアクションを持ちます。  
  
 トリガー  
 遷移を発生させるトリガー アクティビティです。  
  
 条件  
 完了する遷移のためにトリガーを発生した後に `true` となる必要がある制約。  
  
 遷移アクション  
 特定の遷移を実行する時に実行されるアクティビティです。  
  
 条件付き遷移  
 明示的な条件付きの移行です。  
  
 自己遷移  
 状態から自分自身に遷移する遷移です。  
  
 初期状態  
 ステート マシンの開始点を示す状態です。  
  
 最終状態  
 ステート マシンの完了を示す状態です。  
  
## 参照  
 [方法: ステート マシン ワークフローを作成する](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md)   
 [StateMachine アクティビティ デザイナー](../Topic/StateMachine%20Activity%20Designer.md)   
 [State アクティビティ デザイナー](../Topic/State%20Activity%20Designer.md)   
 [FinalState アクティビティ デザイナー](../Topic/FinalState%20Activity%20Designer.md)   
 [Transition アクティビティ デザイナー](../Topic/Transition%20Activity%20Designer.md)