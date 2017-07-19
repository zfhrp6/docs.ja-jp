---
title: "方法 : 印刷キューのサブセットを列挙する | Microsoft Docs"
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
  - "列挙, 印刷キューのサブセット"
  - "印刷キュー, 列挙 (サブセットを)"
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 印刷キューのサブセットを列挙する
企業全体のプリンターを管理する情報テクノロジ \(IT\) 専門家は、特定の特性を持つプリンターのリストを生成しなければならない状況に直面することがしばしばあります。  この機能は、<xref:System.Printing.PrintServer> オブジェクトの <xref:System.Printing.PrintServer.GetPrintQueues%2A> メソッドと、<xref:System.Printing.EnumeratedPrintQueueTypes> 列挙体によって提供されます。  
  
## 使用例  
 次の例のコードでは、まず最初に、リストする印刷キューの特性を指定するフラグの配列を作成しています。  この例では、プリント サーバーにローカルにインストールされ、共有されている印刷キューを検索しています。  <xref:System.Printing.EnumeratedPrintQueueTypes> 列挙体には、他にもさまざまな使用方法があります。  
  
 次にこのコードでは、<xref:System.Printing.PrintServer> の派生クラスである <xref:System.Printing.LocalPrintServer> オブジェクトを作成しています。  ローカル プリント サーバーは、このアプリケーションを実行中のコンピューターです。  
  
 最後の重要な手順は、配列を <xref:System.Printing.PrintServer.GetPrintQueues%2A> メソッドに渡すことです。  
  
 最後に、結果をユーザーに表示します。  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 この例は、各印刷キューをステップ スルーしてさらに絞り込む `foreach` ループを追加することにより拡張できます。  たとえば、このループで各印刷キューの <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> メソッドを呼び出し、戻り値を検査して両面印刷のサポートの有無を調べることで、両面印刷をサポートしないプリンターを除外することができます。  
  
## 参照  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>   
 <xref:System.Printing.PrintServer>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.EnumeratedPrintQueueTypes>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Microsoft XPS Document Writer \(Microsoft XPS ドキュメント ライター\)](http://go.microsoft.com/fwlink/?LinkId=147319)