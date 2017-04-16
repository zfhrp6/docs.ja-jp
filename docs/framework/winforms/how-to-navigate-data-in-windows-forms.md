---
title: "方法 : Windows フォームでデータ間を移動する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "CurrencyManager クラス, 移動 (Windows フォームのデータを)"
  - "カーソル, データ ソース"
  - "データ [Windows フォーム], 移動"
  - "データ ソース, Windows フォーム"
  - "Windows フォーム, 移動"
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォームでデータ間を移動する
Windows アプリケーションで、データ ソースのレコード間を最も簡単な方法で移動するには、<xref:System.Windows.Forms.BindingSource> コンポーネントをデータ ソースにバインドし、その <xref:System.Windows.Forms.BindingSource> にコントロールをバインドします。  その後で、<xref:System.Windows.Forms.BindingSource> の組み込みの移動メソッド \(たとえば、<xref:System.Windows.Forms.BindingSource.MoveNext%2A>、<xref:System.Windows.Forms.BindingSource.MoveLast%2A>、<xref:System.Windows.Forms.BindingSource.MovePrevious%2A>、および <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>\) を使用します。  これらのメソッドを使用すると、<xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.Position%2A> プロパティおよび <xref:System.Windows.Forms.BindingSource.Current%2A> プロパティが適切に調整されます。  また、<xref:System.Windows.Forms.BindingSource.Position%2A> プロパティを設定すると、検索した項目を現在の項目として設定できます。  
  
### データ ソース内での位置をインクリメントするには  
  
1.  バインドされているデータの <xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.Position%2A> プロパティを、移動先のレコード位置に設定します。  次に示す例では、`nextButton` がクリックされたときに、<xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.MoveNext%2A> メソッドを使用して <xref:System.Windows.Forms.BindingSource.Position%2A> プロパティをインクリメントします。  <xref:System.Windows.Forms.BindingSource> は、データセット `Northwind` の `Customers` テーブルに関連付けられています。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource.Position%2A> プロパティを最初または最後のレコードを超える値に設定してもエラーにはなりません。これは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では位置をリストの範囲外の値に設定できないためです。  アプリケーションで最初または最後のレコードを超えたかどうかを知る必要がある場合は、データ要素数を超えるかどうかをテストするロジックを追加します。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### 最初または最後を超えたかどうかを確認するには  
  
1.  <xref:System.Windows.Forms.BindingSource.PositionChanged> イベントのイベント ハンドラーを作成します。  このハンドラーで、指定された位置の値が実際のデータ要素数を超えているかどうかをテストできます。  
  
     最後のデータ要素に達したかどうかをテストする方法の例を次に示します。  この例では、最後の要素に達している場合は、フォームの **\[Next\]** ボタンが無効になります。  
  
    > [!NOTE]
    >  コード内を移動するリストを変更する場合は、ユーザーが新しいリスト全体を移動できるように、**\[次へ\]** ボタンをもう一度有効にする必要があるので注意してください。  また、扱う対象となる特定の <xref:System.Windows.Forms.BindingSource> の上記の <xref:System.Windows.Forms.BindingSource.PositionChanged> イベントを、イベント処理メソッドと関連付ける必要がある点にも注意してください。  <xref:System.Windows.Forms.BindingSource.PositionChanged> イベントを処理するメソッドの例を次に示します。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### 項目を検索し、現在の項目として設定するには  
  
1.  現在の項目として設定するレコードを検索します。  <xref:System.ComponentModel.IBindingList> を実装しているデータ ソースの場合には、<xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.Find%2A> メソッドを使用して検索を実行できます。  <xref:System.ComponentModel.IBindingList> を実装しているデータ ソースの例としては、<xref:System.ComponentModel.BindingList%601> および <xref:System.Data.DataView> があります。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## 参照  
 [Windows フォームがサポートするデータ ソース](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)   
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)