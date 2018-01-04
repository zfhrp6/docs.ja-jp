---
title: "方法 : 印刷キューのサブセットを列挙する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 397ec40e2d8a0694e208296593687e9268546fc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>方法 : 印刷キューのサブセットを列挙する
プリンターの全社的なセットを管理する情報技術 (IT) プロフェッショナルが直面している一般的な状況では、特定の特性を持つプリンターの一覧を生成します。 この機能が用意されて、<xref:System.Printing.PrintServer.GetPrintQueues%2A>のメソッド、<xref:System.Printing.PrintServer>オブジェクトおよび<xref:System.Printing.EnumeratedPrintQueueTypes>列挙します。  
  
## <a name="example"></a>例  
 次の例では、一覧を表示すると印刷キューの特性を指定するフラグの配列を作成することで、コードを開始します。 この例では、プリント サーバーでローカルにインストールされていて、共有されている印刷キューを探しています。 <xref:System.Printing.EnumeratedPrintQueueTypes>列挙体は、さまざまな操作を提供します。  
  
 このコードを作成し、<xref:System.Printing.LocalPrintServer>オブジェクトから派生したクラス<xref:System.Printing.PrintServer>です。 ローカルのプリント サーバーは、アプリケーションが実行されているコンピューターです。  
  
 最後の重要な手順は、先の配列を渡すには、<xref:System.Printing.PrintServer.GetPrintQueues%2A>メソッドです。  
  
 最後に、結果がユーザーに表示されます。  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 用意することによって、この例を拡張する可能性があります、`foreach`各印刷キューをステップ実行をさらにはループ スクリーン処理します。 たとえば、する可能性があります画面ループ呼び出し用意することによって、両面印刷をサポートしていないプリンタを各印刷キューの<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>メソッドと二重化の有無のテスト、返される値。  
  
## <a name="see-also"></a>参照  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)
