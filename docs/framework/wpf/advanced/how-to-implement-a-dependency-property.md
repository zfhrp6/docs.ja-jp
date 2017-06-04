---
title: "方法 : 依存関係プロパティを実装する | Microsoft Docs"
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
  - "依存関係プロパティ, 補足 (プロパティ)"
  - "プロパティ, 補足 (依存関係プロパティで)"
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : 依存関係プロパティを実装する
この例では、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] のプロパティを <xref:System.Windows.DependencyProperty> フィールドで補足する方法、つまり[依存関係プロパティ](GTMT)を定義する方法を示します。  独自に定義したプロパティが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまな機能、たとえばスタイル、データ バインディング、継承、アニメーション、既定値をサポートできるようにするには、そのプロパティを[依存関係プロパティ](GTMT)として実装します。  
  
## 使用例  
 次に示す例では、最初に <xref:System.Windows.DependencyProperty.Register%2A> メソッドを呼び出して[依存関係プロパティ](GTMT)を登録します。  [依存関係プロパティ](GTMT)の名前と特性を格納するときに使用する識別子フィールドの名前は、<xref:System.Windows.DependencyProperty.Register%2A> の呼び出し時に依存関係プロパティに対して選択した <xref:System.Windows.DependencyProperty.Name%2A> でなければなりません。これに、リテラル文字列 `Property` が付加されます。  たとえば、登録する依存関係プロパティの <xref:System.Windows.DependencyProperty.Name%2A> が `Location` ならば、この依存関係プロパティに対して定義する識別子フィールドの名前は `LocationProperty` とする必要があります。  
  
 この例では、[依存関係プロパティ](GTMT)とその [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] アクセサーの名前は `State`、識別子フィールドは `StateProperty`、プロパティの型は <xref:System.Boolean>、[依存関係プロパティ](GTMT)を登録する型は `MyStateControl` です。  
  
 このパターンに従って名前が付けられていない場合は、定義したプロパティがデザイナーから正しく報告されず、プロパティ システムのスタイル適用の一部が予期したとおりに動作しなくなる可能性があります。  
  
 [依存関係プロパティ](GTMT)の既定のメタデータを指定することもできます。  `State` [依存関係プロパティ](GTMT)の既定値を `false` として登録する例を次に示します。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 単にプライベート フィールドを使用して [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティを補足するのではなく[依存関係プロパティ](GTMT)を実装する理由とその方法の詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
## 参照  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)