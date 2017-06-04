---
title: "方法 : コードでバインディングを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バインド (データを), 作成"
  - "データ バインディング, 作成"
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 方法 : コードでバインディングを作成する
コードで <xref:System.Windows.Data.Binding> を作成して設定する方法を次の例に示します。  
  
## 使用例  
 <xref:System.Windows.FrameworkElement> クラスと <xref:System.Windows.FrameworkContentElement> クラスはどちらも `SetBinding` メソッドを公開しています。  どちらかのクラスを継承する要素をバインドする場合は、<xref:System.Windows.FrameworkElement.SetBinding%2A> メソッドを直接呼び出すことができます。  
  
 次の例では、`MyDataProperty` という名前のプロパティを含む `MyData` という名前のクラスを作成しています。  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 バインディングのソースを設定するためにバインディング オブジェクトを作成する方法を次の例に示します。  この例では、<xref:System.Windows.FrameworkElement.SetBinding%2A> を使用して、<xref:System.Windows.Controls.TextBlock> コントロールである `myText` の <xref:System.Windows.Controls.TextBlock.Text%2A> プロパティを `MyDataProperty` にバインドします。  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 コード サンプル全体については、「[Code\-only Binding Sample](http://msdn.microsoft.com/ja-jp/764aaf0b-2216-4941-9548-9c98da18d1a6)」を参照してください。  
  
 <xref:System.Windows.FrameworkElement.SetBinding%2A> を呼び出す代わりに、<xref:System.Windows.Data.BindingOperations> クラスの <xref:System.Windows.Data.BindingOperations.SetBinding%2A> 静的メソッドを使用できます。  次の例では、<xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=fullName> の代わりに <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=fullName> を呼び出して、`myText` を `myDataProperty` にバインドします。  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)