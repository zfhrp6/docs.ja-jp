---
title: "方法 : 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ | Microsoft Docs"
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
  - "コントロール [Windows フォーム], バインド (複数を)"
  - "コントロール [Windows フォーム], 同期 (データ ソースとの)"
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ
Windows フォームでデータ バインディングを操作するときには、複数のコントロールを 1 つのデータ ソースにバインドすることがよくあります。  場合によっては、コントロールのバインド プロパティを他のコントロールやデータ ソースと同期した状態を保つために、追加の手順が必要になります。  追加の手順が必要となるケースとして、次の 2 つが挙げられます。  
  
-   データ ソースが <xref:System.ComponentModel.IBindingList> を実装していないため、<xref:System.ComponentModel.ListChangedType> 型の <xref:System.ComponentModel.IBindingList.ListChanged> イベントを生成する場合。  
  
-   データ ソースが <xref:System.ComponentModel.IEditableObject> を実装している場合。  
  
 前者の場合、<xref:System.Windows.Forms.BindingSource> を使用してコントロールにデータ ソースをバインドできます。  後者の場合、<xref:System.Windows.Forms.BindingSource> を使用して <xref:System.Windows.Forms.BindingSource.BindingComplete> イベントを処理し、バインドされた <xref:System.Windows.Forms.BindingManagerBase> で <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> を呼び出します。  
  
## 使用例  
 次のコード例は、3 つのコントロール \(2 つのテキスト ボックスと 1 つの <xref:System.Windows.Forms.DataGridView> コントロール\) について、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用して <xref:System.Data.DataSet> の同じ列にバインドする方法を示します。  この例は、<xref:System.Windows.Forms.BindingSource.BindingComplete> イベントを処理して、1 つのテキスト ボックスのテキスト値が変更されると、その他のテキスト ボックスと <xref:System.Windows.Forms.DataGridView> コントロールを適切な値で更新する方法を示しています。  
  
 この例では、<xref:System.Windows.Forms.BindingSource> を使用してデータ ソースとコントロールをバインドします。  または、コントロールをデータ ソースに直接バインドし、フォームの <xref:System.Windows.Forms.Control.BindingContext%2A> からバインディングの <xref:System.Windows.Forms.BindingManagerBase> を取得した後、<xref:System.Windows.Forms.BindingManagerBase> の <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> イベントを処理することもできます。  この処理方法の例については、<xref:System.Windows.Forms.BindingManagerBase> の <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> イベントに関するヘルプ ページを参照してください。  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## コードのコンパイル  
  
-   このコード例で必要な要件は次のとおりです。  
  
-   <xref:System> アセンブリ、<xref:System.Windows.Forms> アセンブリ、および <xref:System.Drawing> アセンブリへの参照。  
  
-   <xref:System.Windows.Forms.Form.Load> イベントを処理するフォーム。このフォームの <xref:System.Windows.Forms.Form.Load> イベント ハンドラーから、コード例の `InitializeControlsAndDataSource` メソッドを呼び出す必要があります。  
  
## 参照  
 [方法 : BindingSource コンポーネントを使用してフォーム間でバインド データを共有する](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)   
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [データ連結に関連するインターフェイス](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)