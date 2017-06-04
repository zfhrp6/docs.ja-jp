---
title: "方法 : バインドされたデータを変換する | Microsoft Docs"
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
  - "バインド (データを), 変換 (バインドされたデータを)"
  - "変換, バインドされたデータ"
  - "データ バインディング, 変換 (バインドされたデータを)"
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : バインドされたデータを変換する
この例では、バインディングで使用するデータに変換を適用する方法を示します。  
  
 バインディング中にデータを変換するには、<xref:System.Windows.Data.IValueConverter> インターフェイスを実装するクラスを作成する必要があります。このインターフェイスには、<xref:System.Windows.Data.IValueConverter.Convert%2A> メソッドや <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> メソッドなどが用意されています。  
  
## 使用例  
 渡された日付の値を変換し、年、月、日だけを表示する日付コンバーターの実装を次の例に示します。  <xref:System.Windows.Data.IValueConverter> インターフェイスを実装する際、次の例のように、実装を <xref:System.Windows.Data.ValueConversionAttribute> 属性で修飾し、変換に関連するデータ型を開発ツールに示すことをお勧めします。  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 コンバーターを作成したら、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイル内でリソースとしてそのコンバーターを追加できます。  次の例では、*DateConverter* が定義される名前空間に *src* を割り当てます。  
  
 [!code-xml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 最後に、次の構文を使用して、このコンバーターをバインディングで使用できます。  次の例では、<xref:System.Windows.Controls.TextBlock> のテキスト コンテンツは、外部データ ソースのプロパティである *StartDate* にバインドされています。  
  
 [!code-xml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 上の例で参照したスタイル リソースは、ここでは示していないリソース セクションで定義されます。  
  
## 参照  
 [バインディングの検証の実装](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)