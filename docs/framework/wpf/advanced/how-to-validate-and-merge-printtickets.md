---
title: "方法 : PrintTickets を検証およびマージする | Microsoft Docs"
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
  - "マージ (PrintTicket を)"
  - "PrintTicket, マージ"
  - "PrintTicket, 検証"
  - "検証 (PrintTicket の)"
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : PrintTickets を検証およびマージする
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [印刷スキーマ](http://go.microsoft.com/fwlink/?LinkId=186397)には、柔軟で拡張性に優れた <xref:System.Printing.PrintCapabilities> 要素と <xref:System.Printing.PrintTicket> 要素が含まれています。  前者は印刷デバイスの機能を明細化し、後者はデバイスが特定のドキュメントのシーケンス、個々のドキュメント、または個々のページに対してこれらの機能を使用する方法を指定します。  
  
 印刷をサポートするアプリケーションの一般的な一連のタスクは次のとおりです。  
  
1.  プリンターの機能を確認します。  
  
2.  その機能を使用するように <xref:System.Printing.PrintTicket> を構成します。  
  
3.  <xref:System.Printing.PrintTicket> を検証します。  
  
 この記事では、この実行方法を示します。  
  
## 使用例  
 次の簡単な例では、プリンターで二面印刷 \(両面印刷\) がサポートされるかどうかにのみ焦点を当てています。  主な手順は次のとおりです。  
  
1.  <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> メソッドを使用して、<xref:System.Printing.PrintCapabilities> オブジェクトを取得します。  
  
2.  必要な機能が存在するかどうかをテストします。  次の例では、<xref:System.Printing.PrintCapabilities> オブジェクトの <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> プロパティをテストして、用紙の長辺に沿って "ページをめくり"、用紙の両面に印刷する機能が存在するかどうかを確認します。  <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> はコレクションであるので、<xref:System.Collections.ObjectModel.ReadOnlyCollection%601> の `Contains` メソッドを使用します。  
  
    > [!NOTE]
    >  この手順は、厳密には必要ありません。  以下で使用される <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> メソッドによって、<xref:System.Printing.PrintTicket> の各要求がプリンターの機能と照合されます。  要求された機能がプリンターでサポートされていない場合、プリンター ドライバーによってメソッドから返される <xref:System.Printing.PrintTicket> の代替要求に置き換えられます。  
  
3.  プリンターで両面印刷がサポートされている場合、サンプル コードによって両面印刷を要求する <xref:System.Printing.PrintTicket> が作成されます。  ただし、アプリケーションでは、<xref:System.Printing.PrintTicket> 要素で使用可能なあらゆるプリンター設定が指定されるわけではありません。  プログラマとプログラムの時間の両方にとって無駄な処理となるためです。  代わりに、コードによって両面印刷要求のみが設定され、この <xref:System.Printing.PrintTicket> と既存の完全に構成および検証された <xref:System.Printing.PrintTicket> \(この場合はユーザーの既定の <xref:System.Printing.PrintTicket>\) がマージされます。  
  
4.  したがって、サンプルによって <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> メソッドが呼び出され、新しい最小限の <xref:System.Printing.PrintTicket> とユーザーの既定の <xref:System.Printing.PrintTicket> がマージされます。  これにより、新しい <xref:System.Printing.PrintTicket> をプロパティの 1 つとして含む <xref:System.Printing.ValidationResult> が返されます。  
  
5.  次に、サンプルによって新しい <xref:System.Printing.PrintTicket> が両面印刷を要求するかどうかがテストされます。  要求する場合、その印刷チケットがユーザーの新しい既定の印刷チケットになります。  前の手順 2. を省略した場合、プリンターで長辺とじ両面印刷がサポートされないと、テストは `false` になります   \(上記のメモを参照してください\)。  
  
6.  最後の重要な手順は、<xref:System.Printing.PrintQueue.Commit%2A> メソッドを使用して、変更を <xref:System.Printing.PrintQueue> の <xref:System.Printing.PrintQueue.UserPrintTicket%2A> プロパティにコミットすることです。  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 この例を迅速にテストできるように、その残りの部分を次に示します。  プロジェクトおよび名前空間を作成し、この記事の両方のコード スニペットを名前空間ブロックに貼り付けます。  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## 参照  
 <xref:System.Printing.PrintCapabilities>   
 <xref:System.Printing.PrintTicket>   
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>   
 <xref:System.Printing.PrintServer>   
 <xref:System.Printing.EnumeratedPrintQueueTypes>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Print Schema \(印刷スキーマ\)](http://go.microsoft.com/fwlink/?LinkId=186397)