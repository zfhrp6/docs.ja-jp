---
title: "方法 : バインドされた項目の一覧に基づいて値を生成する | Microsoft Docs"
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
  - "データ バインディング, MultiBinding"
  - "MultiBinding"
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : バインドされた項目の一覧に基づいて値を生成する
<xref:System.Windows.Data.MultiBinding> を使用すると、ソース プロパティの一覧に[バインディング ターゲット](GTMT) プロパティをバインドし、指定した入力で値を生成するロジックを適用することができます。  この例では、<xref:System.Windows.Data.MultiBinding> を使用する方法を示します。  
  
## 使用例  
 次の例では、`NameListData` は、`PersonName` オブジェクトのコレクションを参照します。このオブジェクトは、`firstName` と `lastName` の 2 つのプロパティを含みます。  個人の氏名を姓から表示する <xref:System.Windows.Controls.TextBlock> を生成する例を次に示します。  
  
 [!code-xml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 姓が先の形式を生成する方法を理解するには、次に示す `NameConverter` の実装を参照してください。  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` では、<xref:System.Windows.Data.IMultiValueConverter> インターフェイスを実装します。  `NameConverter` は、個々のバインディングから値を受け取り、それらを値のオブジェクト配列に格納します。  <xref:System.Windows.Data.Binding> 要素が <xref:System.Windows.Data.MultiBinding> 要素の下に出現する順序は、値が配列内に格納されている順序です。  <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> 属性の値は、名前の形式を決定するパラメーターの切り替えを実行する <xref:System.Windows.Data.MultiBinding.Converter%2A> メソッドのパラメーター引数によって参照されます。  
  
## 参照  
 [バインドされたデータを変換する](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)