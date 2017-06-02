---
title: "方法 : リフレクションを使用せずに印刷システム オブジェクトのプロパティを取得する | Microsoft Docs"
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
  - "PrintSystemObject, 取得 (プロパティを)"
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : リフレクションを使用せずに印刷システム オブジェクトのプロパティを取得する
リフレクションを使用してオブジェクトのプロパティ \(およびプロパティの型\) を取得すると、アプリケーションのパフォーマンスが低下する可能性があります。  <xref:System.Printing.IndexedProperties> 名前空間には、リフレクションを使用せずにこの情報を取得するための手段が用意されています。  
  
## 使用例  
 実行手順は次のとおりです。  
  
1.  型のインスタンスを作成します。  次の例では、型は [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] で提供されている <xref:System.Printing.PrintQueue> 型ですが、<xref:System.Printing.PrintSystemObject> から派生した型に対しても、ほぼ同じコードを使用できます。  
  
2.  型の <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> から <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> を作成します。  このディクショナリの各エントリの <xref:System.Collections.DictionaryEntry.Value%2A> プロパティは、<xref:System.Printing.IndexedProperties.PrintProperty> から派生した型の 1 つのオブジェクトです。  
  
3.  ディクショナリのメンバーを列挙します。  各メンバーに対し、以下を行います。  
  
4.  各エントリの値を <xref:System.Printing.IndexedProperties.PrintProperty> にアップキャストし、それを使用して <xref:System.Printing.IndexedProperties.PrintProperty> オブジェクトを作成します。  
  
5.  各 <xref:System.Printing.IndexedProperties.PrintProperty> オブジェクトの <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> の型を取得します。  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## 参照  
 <xref:System.Printing.IndexedProperties.PrintProperty>   
 <xref:System.Printing.PrintSystemObject>   
 <xref:System.Printing.IndexedProperties>   
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Collections.DictionaryEntry>   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)