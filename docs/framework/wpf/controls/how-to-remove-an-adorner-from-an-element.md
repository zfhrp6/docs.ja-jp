---
title: "方法 : 要素から装飾を削除する | Microsoft Docs"
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
  - "装飾, 削除"
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 要素から装飾を削除する
この例では、指定された <xref:System.Windows.UIElement> からプログラムを使用して特定の装飾を削除する方法を示します。  
  
## 使用例  
 この詳細なコード例では、<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> によって返される装飾の配列にある最初の装飾が削除されます。  この例では、*myTextBox* という名前の <xref:System.Windows.UIElement> の装飾が取得されます。  <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> の呼び出しで指定された要素に装飾がない場合、`null` が返されます。  このコードは NULL 配列を明示的にチェックします。NULL 配列が比較的多いと予想される場合には、このコードがアプリケーションに最も適しています。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## 使用例  
 この縮小されたコード例は、上に示した詳細例と同等の機能を持っています。  このコードは NULL 配列を明示的にチェックしないため、<xref:System.NullReferenceException> 例外が発生する可能性があります。  このコードは、NULL 配列がまれにしかないと予想されるアプリケーションに最も適しています。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## 参照  
 [装飾の概要](../../../../docs/framework/wpf/controls/adorners-overview.md)