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
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="d26e4-102">方法 : 印刷キューのサブセットを列挙する</span><span class="sxs-lookup"><span data-stu-id="d26e4-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="d26e4-103">プリンターの全社的なセットを管理する情報技術 (IT) プロフェッショナルが直面している一般的な状況では、特定の特性を持つプリンターの一覧を生成します。</span><span class="sxs-lookup"><span data-stu-id="d26e4-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="d26e4-104">この機能が用意されて、<xref:System.Printing.PrintServer.GetPrintQueues%2A>のメソッド、<xref:System.Printing.PrintServer>オブジェクトおよび<xref:System.Printing.EnumeratedPrintQueueTypes>列挙します。</span><span class="sxs-lookup"><span data-stu-id="d26e4-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d26e4-105">例</span><span class="sxs-lookup"><span data-stu-id="d26e4-105">Example</span></span>  
 <span data-ttu-id="d26e4-106">次の例では、一覧を表示すると印刷キューの特性を指定するフラグの配列を作成することで、コードを開始します。</span><span class="sxs-lookup"><span data-stu-id="d26e4-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="d26e4-107">この例では、プリント サーバーでローカルにインストールされていて、共有されている印刷キューを探しています。</span><span class="sxs-lookup"><span data-stu-id="d26e4-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="d26e4-108"><xref:System.Printing.EnumeratedPrintQueueTypes>列挙体は、さまざまな操作を提供します。</span><span class="sxs-lookup"><span data-stu-id="d26e4-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="d26e4-109">このコードを作成し、<xref:System.Printing.LocalPrintServer>オブジェクトから派生したクラス<xref:System.Printing.PrintServer>です。</span><span class="sxs-lookup"><span data-stu-id="d26e4-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="d26e4-110">ローカルのプリント サーバーは、アプリケーションが実行されているコンピューターです。</span><span class="sxs-lookup"><span data-stu-id="d26e4-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="d26e4-111">最後の重要な手順は、先の配列を渡すには、<xref:System.Printing.PrintServer.GetPrintQueues%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d26e4-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="d26e4-112">最後に、結果がユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d26e4-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="d26e4-113">用意することによって、この例を拡張する可能性があります、`foreach`各印刷キューをステップ実行をさらにはループ スクリーン処理します。</span><span class="sxs-lookup"><span data-stu-id="d26e4-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="d26e4-114">たとえば、する可能性があります画面ループ呼び出し用意することによって、両面印刷をサポートしていないプリンタを各印刷キューの<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>メソッドと二重化の有無のテスト、返される値。</span><span class="sxs-lookup"><span data-stu-id="d26e4-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26e4-115">参照</span><span class="sxs-lookup"><span data-stu-id="d26e4-115">See Also</span></span>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="d26e4-116">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="d26e4-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="d26e4-117">印刷の概要</span><span class="sxs-lookup"><span data-stu-id="d26e4-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="d26e4-118">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="d26e4-118">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
