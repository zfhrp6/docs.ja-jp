---
title: "方法 : バインドされているターゲット プロパティからのバインディング オブジェクトの取得 | Microsoft Docs"
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
  - "データ バインディング, 取得 (バインドされているターゲット プロパティからバインディング オブジェクトを)"
  - "プロパティ, 取得 (バインディング オブジェクトを)"
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : バインドされているターゲット プロパティからのバインディング オブジェクトの取得
この例では、データにバインドされているターゲット プロパティからバインディング オブジェクトを取得する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Data.Binding> オブジェクトを取得する方法を次に示します。  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  バインディングの[依存関係プロパティ](GTMT)を指定しなければならないのは、ターゲット オブジェクトに、データ バインディングを使用するプロパティが複数存在する可能性があるためです。  
  
 また、<xref:System.Windows.Data.BindingExpression> を取得してから <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> プロパティの値を取得するという方法もあります。  
  
 コード例全体については、[バインディングの検証のサンプル](http://go.microsoft.com/fwlink/?LinkID=159972)を参照してください。  
  
> [!NOTE]
>  バインディングが <xref:System.Windows.Data.MultiBinding> である場合は、<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A> を使用します。  <xref:System.Windows.Data.PriorityBinding> である場合は、<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A> を使用します。  ターゲット プロパティが、<xref:System.Windows.Data.Binding>、<xref:System.Windows.Data.MultiBinding>、<xref:System.Windows.Data.PriorityBinding> のどれを使用してバインドされているかが不明な場合は、<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A> を使用してください。  
  
## 参照  
 [コードでバインディングを作成する](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)