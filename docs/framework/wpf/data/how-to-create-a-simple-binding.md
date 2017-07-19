---
title: "方法 : 簡単なバインディングを作成する | Microsoft Docs"
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
  - "データ バインディング, 作成 (単純バインディングを)"
  - "単純バインディング, 作成"
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 簡単なバインディングを作成する
簡単な <xref:System.Windows.Data.Binding> を作成する方法を次の例に示します。  
  
## 使用例  
 この例では、`PersonName` という名前の文字列プロパティを持つ `Person` オブジェクトがあります。  この `Person` オブジェクトは、`SDKSample` という名前空間で定義されます。  
  
 `Joe` という `PersonName` プロパティ値を使用して `Person` オブジェクトをインスタンス化する例を次に示します。  これは、`Resources` セクションで実行され、`x:Key` が割り当てられます。  
  
 [!code-xml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
[!code-xml[SimpleBinding#EndWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#endwindow)]  
  
 `PersonName` プロパティをバインドするには、次の操作を実行します。  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 結果として、<xref:System.Windows.Controls.TextBlock> には値 "Joe" が表示されます。  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)