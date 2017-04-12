---
title: "マルチ スレッド アプリケーション (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5bde7f49a2f2bc8a2e6c1eeab3722428b8a37a95
ms.lasthandoff: 03/13/2017

---
# <a name="multithreaded-applications-visual-basic"></a>マルチ スレッド アプリケーション (Visual Basic)
Visual basic では、同時に複数のタスクを実行するアプリケーションを作成できます。 その他のタスクを停止させる可能性のあるタスク別のスレッドでと呼ばれるプロセスとの実行のできます*マルチ スレッド*または*フリー スレッド*します。  
  
 マルチ スレッドを使用、プロセッサ集中型のタスクを個別のスレッドで実行すると、ユーザー インターフェイスがアクティブに保たれるためのユーザーに応答性を向上するアプリケーション。 マルチ スレッドも役立ちます、スケーラブルなアプリケーションを作成するときにワークロードが増加すると、スレッドを追加できるためです。  
  
## <a name="creating-and-using-threads"></a>作成して、スレッドを使用します。  
 アプリケーションのスレッドの動作をより詳細に制御する場合は、できるスレッドは、自分で管理します。 ただし、正しいマルチ スレッド アプリケーションを作成することは困難を実現します。 アプリケーションの応答を停止または競合状態によって発生する一時的なエラーが発生する可能性があります。 詳細については、次を参照してください。[スレッド セーフなコンポーネント](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)します。  
  
 型の変数を宣言することで、新しいスレッドを作成する<xref:System.Threading.Thread>プロシージャまたは新しいスレッド上で実行するメソッドの名前を指定するコンス トラクターを呼び出すとします</xref:System.Threading.Thread>。 次にコード例を示します。  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a>開始と停止のスレッド  
 新しいスレッドの実行を開始するを使用して、<xref:System.Threading.Thread.Start%2A>メソッドを次のコードに示すようにします</xref:System.Threading.Thread.Start%2A>。  
  
```vb  
newThread.Start()  
```  
  
 スレッドの実行を停止するを使用して、<xref:System.Threading.Thread.Abort%2A>メソッドを次のコードに示すようにします</xref:System.Threading.Thread.Abort%2A>。  
  
```vb  
newThread.Abort()  
```  
  
 開始ほかのスレッドが停止するも一時停止することのスレッドを呼び出して、<xref:System.Threading.Thread.Sleep%2A>または<xref:System.Threading.Thread.Suspend%2A>メソッドを使用して中断されたスレッドを再開、<xref:System.Threading.Thread.Resume%2A>メソッド、および<xref:System.Threading.Thread.Abort%2A>メソッド</xref:System.Threading.Thread.Abort%2A>を使用してスレッドを破棄</xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Sleep%2A>  
  
### <a name="thread-methods"></a>スレッドのメソッド  
 次の表は、個別のスレッドを制御に使用できるメソッドの一部を示します。  
  
|メソッド|操作|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A>|スレッド実行を開始します。|  
|<xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A>|スレッドを指定した時間一時停止します。|  
|<xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Suspend%2A>|セーフ ポイントに達すると、スレッドを一時停止します。|  
|<xref:System.Threading.Thread.Abort%2A></xref:System.Threading.Thread.Abort%2A>|セーフ ポイントに達すると、スレッドを停止します。|  
|<xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Resume%2A>|中断されたスレッドを再開します。|  
|<xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A>|によって現在のスレッドが別のスレッドが完了するまで待機します。 タイムアウト値を持つ場合、このメソッドが戻る`True`割り当てられた時間内に、スレッドが終了した場合。|  
  
### <a name="safe-points"></a>セーフ ポイント  
 これらのメソッドのほとんどは見ればわかるので、その概念の*セーフ ポイント*に新しい可能性があります。 セーフ ポイントとは、安全では、共通言語ランタイムを自動実行するコード内の場所*ガベージ コレクション*、使用されていない変数を解放して、メモリを再利用のプロセスです。 呼び出すと、<xref:System.Threading.Thread.Abort%2A>または<xref:System.Threading.Thread.Suspend%2A>、共通言語ランタイムのスレッドのメソッドは、コードを分析し、スレッドの実行を停止するための適切な場所の場所を決定します</xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Abort%2A>。  
  
### <a name="thread-properties"></a>スレッド プロパティ  
 スレッドには、次の表に示すようにいくつかの便利なプロパティが用意されています。  
  
|プロパティ|値|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A></xref:System.Threading.Thread.IsAlive%2A>|値を含む`True`スレッドがアクティブな場合です。|  
|<xref:System.Threading.Thread.IsBackground%2A></xref:System.Threading.Thread.IsBackground%2A>|取得またはスレッドをバック グラウンド スレッドをする必要がありますかを示すブール値を設定します。 バック グラウンド スレッド フォア グラウンド スレッドと似ていますが、バック グラウンド スレッドが停止するプロセスを妨げられません。 共通言語ランタイムが呼び出すことによって、プロセスを終了するプロセスに属するすべてのフォア グラウンド スレッドが停止されると、<xref:System.Threading.Thread.Abort%2A>生きているバック グラウンド スレッド上のメソッドです</xref:System.Threading.Thread.Abort%2A>。|  
|<xref:System.Threading.Thread.Name%2A></xref:System.Threading.Thread.Name%2A>|取得またはスレッドの名前を設定します。 最も頻繁をデバッグするときに、個別のスレッドを検出するために使用します。|  
|<xref:System.Threading.Thread.Priority%2A></xref:System.Threading.Thread.Priority%2A>|取得またはスレッドのスケジューリング優先順位を付けるオペレーティング システムによって使用される値を設定します。|  
|<xref:System.Threading.Thread.ThreadState%2A></xref:System.Threading.Thread.ThreadState%2A>|スレッドの状態または状態を記述する値が含まれています。|  
  
## <a name="thread-priorities"></a>スレッドの優先順位  
 すべてのスレッドでは、実行する必要があるプロセッサ時間のスライスのサイズを決定する優先度プロパティがあります。 オペレーティング システムでは、優先度の高いスレッドに長いタイム スライスと優先度の低いスレッドに短いタイム スライスを割り当てます。 新しいスレッドが作成され、値の`Normal`、変更することが、<xref:System.Threading.Thread.Priority%2A>プロパティの任意の値を<xref:System.Threading.ThreadPriority>列挙体</xref:System.Threading.ThreadPriority></xref:System.Threading.Thread.Priority%2A>。  
  
 参照してください<xref:System.Threading.ThreadPriority>さまざまなスレッドの優先順位の詳細について</xref:System.Threading.ThreadPriority>。  
  
## <a name="foreground-and-background-threads"></a>フォアグラウンド スレッドとバックグラウンド スレッド  
 A*フォア グラウンド スレッド*一方、無期限に実行される、*スレッドが、*最後のフォア グラウンド スレッドが停止するとすぐに停止します。 使用することができます、<xref:System.Threading.Thread.IsBackground%2A>確認またはスレッドのバック グラウンドの状態を変更するプロパティ</xref:System.Threading.Thread.IsBackground%2A>。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread></xref:System.Threading.Thread>   
 [スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)   
 [パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)   
 [スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)
