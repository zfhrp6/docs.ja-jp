---
title: "Walkthrough: Declaring and Raising Events (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarations, events"
  - "events [Visual Basic], walkthroughs"
  - "declaring events, walkthroughs"
  - "events [Visual Basic], declaring"
  - "events [Visual Basic], raising"
  - "raising events, walkthroughs"
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Declaring and Raising Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このチュートリアルでは、`Widget` というクラスのイベントを宣言および発生させる方法を説明します。  ここでの手順が完了したら、関連トピックの「[Walkthrough: Handling Events](../Topic/Walkthrough:%20Handling%20Events%20\(Visual%20Basic\).md)」を参照してください。このトピックでは、`Widget` オブジェクトのイベントを使用して、アプリケーションのステータス情報を提供する方法を説明しています。  
  
## ウィジェット クラス  
 ここでは `Widget` クラスが既にあると仮定します。  `Widget` クラスには、実行に時間がかかるメソッドが 1 つあるので、アプリケーションに完了のインジケーターを用意することにします。  
  
 `Widget` オブジェクトに、完了した割合を示すダイアログ ボックスを表示させることもできますが、ここでは、`Widget` クラスを使用するすべてのプロジェクトでダイアログ ボックスを表示する処理を行います。  オブジェクトの目的がフォームやダイアログ ボックスを制御することでない場合、オブジェクト設計の原則は、オブジェクトを使用するアプリケーションにユーザー インターフェイスを処理させることです。  
  
 `Widget` の目的は他のタスクを実行することです。したがって、`PercentDone` イベントを追加して、`Widget` のメソッドを呼び出すプロシージャにイベントの処理と更新状態の表示を実行させる方が適切です。  `PercentDone` イベントは、タスクをキャンセルするしくみも提供できます。  
  
#### このトピックのコード例を作成するには  
  
1.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の新しい Windows アプリケーション プロジェクトを開き、`Form1` という名前のフォームを作成します。  
  
2.  `Form1` に、2 つのボタンと 1 つのラベルを追加します。  
  
3.  次の表のとおりにオブジェクトに名前を付けます。  
  
    |Object|プロパティ|設定|  
    |------------|-----------|--------|  
    |`Button1`|`Text`|Start Task|  
    |`Button2`|`Text`|\[キャンセル\]|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  **\[プロジェクト\]** メニューの **\[クラスの追加\]** を選択し、プロジェクトに `Widget.vb` というクラスを追加します。  
  
#### ウィジェット クラスのイベントを宣言するには  
  
-   `Event` キーワードを使って `Widget` クラス内にイベントを宣言します。  イベントは `ByVal` および `ByRef` 引数を受け取ることができます。`Widget` の `PercentDone` イベントの例を示します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 呼び出し元のオブジェクトが `PercentDone` イベントを受け取るとき、`Percent` 引数には完了したタスクの割合が含まれています。  `Cancel` 引数を `True` に設定すると、イベントを発生させるメソッドをキャンセルできます。  
  
> [!NOTE]
>  イベントの引数は、プロシージャの引数と同様に宣言できます。ただし、イベントに対して `Optional` 引数や `ParamArray` 引数は指定できず、イベントには戻り値がありません。  
  
 `Widget` クラスの `LongTask` メソッドによって、`PercentDone` イベントが発生します。  `LongTask` は 2 つの引数を受け取ります。1 つはメソッドが動作し続ける時間を表し、もう 1 つは `LongTask` が一時停止して `PercentDone` イベントを発生させるまでの最小の時間間隔を表します。  
  
#### PercentDone イベントを発生させるには  
  
1.  このクラスによって使用される `Timer` プロパティへのアクセスを簡単にするために、クラス モジュールの宣言セクションの先頭で、`Class Widget` ステートメントの上に `Imports` ステートメントを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  `Widget` クラスに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 アプリケーションで `LongTask` メソッドを呼び出すと、`Widget` クラスは `PercentDone` イベントを `MinimumInterval` 秒間隔で発生させます。  イベントが返されると、`LongTask` は `Cancel` 引数が `True` に設定されたかどうかを確認します。  
  
 ここで、次の点に注意してください。  簡略化のために、`LongTask` プロシージャでは、タスクにかかる時間があらかじめわかっているとします。  実際には、このような場合はほとんどありません。  タスクを均等なサイズのチャンクに分割することは難しい場合があり、ユーザーにとって最も重要なことは、処理が進行中であることを知らされるまでの時間である場合も多くあります。  
  
 このサンプルに別の欠点があります。  `Timer` プロパティは、深夜 0 時からの経過時間を秒単位で返します。したがって、アプリケーションが 0 時直前に開始された場合、アプリケーションは正しく動作しなくなります。  時間を慎重に測定するには、このような境界条件を考慮に入れるか、`Now` などのプロパティを使用して問題が発生するのを避けます。  
  
 これで `Widget` クラスからイベントを発生できるようになったので、次のチュートリアルに進むことができます。  「[Walkthrough: Handling Events](../Topic/Walkthrough:%20Handling%20Events%20\(Visual%20Basic\).md)」では、`WithEvents` を使用して `PercentDone` イベントにイベント ハンドラーを関連付ける方法を示します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>   
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>   
 [Walkthrough: Handling Events](../Topic/Walkthrough:%20Handling%20Events%20\(Visual%20Basic\).md)   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)