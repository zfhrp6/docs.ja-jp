---
title: "方法 : プリンターを複製する | Microsoft Docs"
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
  - "複製 (印刷キューを)"
  - "複製 (プリンターを)"
  - "印刷キュー"
  - "印刷キュー, クローンの作成"
  - "プリンター, クローンの作成"
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : プリンターを複製する
ほとんどの企業は、ある時点で、同じモデルのプリンターを複数購入します。  通常、これらのプリンターはすべて、ほぼ同一の構成設定でインストールされます。  プリンターを個別にインストールすると、時間がかかったりエラーが発生したりすることがあります。  [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] で公開されている <xref:System.Printing.IndexedProperties?displayProperty=fullName> 名前空間と <xref:System.Printing.PrintServer.InstallPrintQueue%2A> クラスを使用すると、既存の印刷キューから複製した任意の数の追加印刷キューを直ちにインストールすることができます。  
  
## 使用例  
 次の例の 2 番目の印刷キューは、既存の印刷キューから複製したものです。  2 番目の印刷キューと最初の印刷キューの違いは、名前、場所、ポート、および共有状態だけです。  主な実行手順は次のとおりです。  
  
1.  複製する既存のプリンターの <xref:System.Printing.PrintQueue> オブジェクトを作成します。  
  
2.  <xref:System.Printing.PrintQueue> の <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> から <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> を作成します。  このディクショナリの各エントリの <xref:System.Collections.DictionaryEntry.Value%2A> プロパティは、<xref:System.Printing.IndexedProperties.PrintProperty> から派生した型の 1 つのオブジェクトです。  このディクショナリのエントリの値を設定するには、2 つの方法があります。  
  
    -   ディクショナリの **Remove** メソッドと <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> メソッドを使用してエントリを削除し、目的の値を追加し直します。  
  
    -   ディクショナリの <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> メソッドを使用します。  
  
     両方の方法を次の例に示します。  
  
3.  <xref:System.Printing.IndexedProperties.PrintBooleanProperty> オブジェクトを作成し、その <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> を "IsShared" に、<xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> を `true` にそれぞれ設定します。  
  
4.  <xref:System.Printing.IndexedProperties.PrintBooleanProperty> オブジェクトを <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> の "IsShared" エントリの値として使用します。  
  
5.  <xref:System.Printing.IndexedProperties.PrintStringProperty> オブジェクトを作成し、その <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> を "ShareName" に、<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> を適切な <xref:System.String> にそれぞれ設定します。  
  
6.  <xref:System.Printing.IndexedProperties.PrintStringProperty> オブジェクトを <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> の "ShareName" エントリの値として使用します。  
  
7.  <xref:System.Printing.IndexedProperties.PrintStringProperty> オブジェクトをもう 1 つ作成し、その <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> を "Location" に、<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> を適切な <xref:System.String> にそれぞれ設定します。  
  
8.  2 番目の <xref:System.Printing.IndexedProperties.PrintStringProperty> オブジェクトを <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> の "Location" エントリの値として使用します。  
  
9. <xref:System.String> の配列を作成します。  各項目は、サーバー上のポートの名前です。  
  
10. <xref:System.Printing.PrintServer.InstallPrintQueue%2A> を使用して、新しいプリンターを新しい値でインストールします。  
  
 次に例を示します。  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## 参照  
 <xref:System.Printing.IndexedProperties>   
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Collections.DictionaryEntry>   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)