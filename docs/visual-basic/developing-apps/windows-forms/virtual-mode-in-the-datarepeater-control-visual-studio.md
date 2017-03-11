---
title: "Virtual Mode in the DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "virtual data binding"
  - "DataRepeater"
  - "DataRepeater, virtual mode"
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Virtual Mode in the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

大きな表形式のデータを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールに表示するときは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> プロパティを `True` に設定してコントロールとデータ ソースのやり取りを明示的に管理することによって、パフォーマンスを向上させることができます。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールには、必要に応じてデータ ソースの操作とデータの表示を行うために実行時に処理できる複数のイベントがあります。  
  
## 仮想モードの動作  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを使用するうえで最も一般的なシナリオは、デザイン時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> の子コントロールをデータ ソースにバインドし、必要に応じて <xref:System.Windows.Forms.BindingSource> でデータの受け渡しができるようにすることです。  仮想モードを使用すると、コントロールはデータ ソースにバインドされず、データは実行時に基になるデータ ソースとの間で受け渡されます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> プロパティを `True` に設定する場合、**\[データ ソース\]** ウィンドウからバインド コントロールを追加する代わりに、**ツールボックス**からコントロールを追加してユーザー インターフェイスを作成します。  
  
 イベントはコントロール単位で発生するので、データの表示を処理するコードを追加する必要があります。  新しい <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> をスクロールして表示すると、コントロールごとに <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> イベントが 1 回発生するので、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> イベント ハンドラー内でコントロールごとの値を指定する必要があります。  
  
 1 つのコントロールのデータがユーザーによって変更されると、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> イベントが発生するので、そのデータを検証し、データ ソースに保存する必要があります。  
  
 ユーザーが新しい項目を追加すると、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> イベントが発生します。  このイベントのハンドラーを使用して、データ ソースに新しいレコードを作成します。  意図しない変更を防ぐために、コントロールごとに <xref:System.Windows.Forms.Control.KeyDown> イベントを監視して、ユーザーが Esc キーを押した場合には <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> を呼び出すことも必要です。  
  
 データ ソースが変更された場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetTemplateItem%2A> メソッドおよび <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetTemplateItem%2A> メソッドを呼び出すことで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを更新できます。  これらのメソッドは順番に呼び出す必要があります。  
  
 最後に、項目が削除されると発生する <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> イベントのイベント ハンドラーを実装する必要があり、また、オプションで、ユーザーが Del キーを押して項目を削除するたびに発生する <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> イベントおよび <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> イベントのイベント ハンドラーも実装します。  
  
## 仮想モードの実装  
 仮想モードの実装に必要な手順を次に示します。  
  
#### 仮想モードを実装するには  
  
1.  **ツールボックス**の **\[Visual Basic PowerPacks\]** タブから <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをフォームまたはコンテナー コントロールにドラッグします。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> プロパティを `True` に設定します。  
  
2.  **ツールボックス**からコントロールを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域 \(上部の領域\) にドラッグします。  データ ソースから表示するフィールドごとに 1 つのコントロールが必要です。  
  
3.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> イベントのハンドラーを実装して、各コントロールに値を指定します。  このイベントは、新しい <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> をスクロールして表示すると発生します。  コードは、次のコード例のようになります。この例は `Employees` という名前のデータ ソースを使用します。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#1)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#1)]  
  
4.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> イベントのハンドラーを実装して、データを保存します。  このイベントは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> の子コントロールへの変更をユーザーがコミットすると発生します。  コードは、次のコード例のようになります。この例は `Employees` という名前のデータ ソースを使用します。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#2)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#2)]  
  
5.  各コントロールの <xref:System.Windows.Forms.Control.KeyDown> イベントのハンドラーを実装して、Esc キーを監視します。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> イベントが発生しないようにするには、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> メソッドを呼び出します。  コードは、次のコード例のようになります。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#3)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#3)]  
  
6.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> イベントのハンドラーを実装します。  このイベントは、ユーザーが <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールに新しい項目を追加すると発生します。  コードは、次のコード例のようになります。この例は `Employees` という名前のデータ ソースを使用します。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#4)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#4)]  
  
7.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> イベントのハンドラーを実装します。  このイベントは、ユーザーが既存の項目を削除すると発生します。  コードは、次のコード例のようになります。この例は `Employees` という名前のデータ ソースを使用します。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#5)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#5)]  
  
8.  コントロール レベルの検証を行う場合、オプションで、子コントロールの <xref:System.Windows.Forms.Control.Validating> イベントのハンドラーを実装します。  コードは、次のコード例のようになります。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#6)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#6)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)