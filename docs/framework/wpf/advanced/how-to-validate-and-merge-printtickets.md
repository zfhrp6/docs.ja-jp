---
title: '方法 : PrintTickets を検証およびマージする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: 11160d7ec59914afbe501ba731c0c04a85ffc4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-and-merge-printtickets"></a>方法 : PrintTickets を検証およびマージする
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [印刷スキーマ](http://go.microsoft.com/fwlink/?LinkId=186397)柔軟性と拡張性が含まれています<xref:System.Printing.PrintCapabilities>と<xref:System.Printing.PrintTicket>要素。 前者明細化して、印刷デバイスの機能および後者デバイスが特定のシーケンスのドキュメント、個々 のドキュメント、または個々 のページに対してこれらの機能を使用する方法を指定します。  
  
 印刷をサポートするアプリケーションのタスクの一般的なシーケンスは次のようになります。  
  
1.  プリンターの機能を決定します。  
  
2.  構成、<xref:System.Printing.PrintTicket>それらの機能を使用します。  
  
3.  検証、<xref:System.Printing.PrintTicket>です。  
  
 この記事では、これを行う方法を示します。  
  
## <a name="example"></a>例  
 次の単純な例ではプリンターが両面印刷をサポートするかどうかのみが必要な両面印刷します。 主な手順は次のとおりです。  
  
1.  取得、<xref:System.Printing.PrintCapabilities>オブジェクトを<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>メソッドです。  
  
2.  必要な機能の存在をテストします。 次の例ではテスト、<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>のプロパティ、<xref:System.Printing.PrintCapabilities>用紙の長辺に沿って「ページに」用紙の両面に印刷する機能が存在するオブジェクトします。 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>コレクションでは、使用して、`Contains`メソッドの<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>します。  
  
    > [!NOTE]
    >  この手順は必ずしも必要ではありません。 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>下で使用方法は、各要求を確認するのには、<xref:System.Printing.PrintTicket>プリンターの機能を比較します。 プリンターでは、要求された機能はサポートされていない場合、プリンター ドライバーは、別の要求に置き換え、<xref:System.Printing.PrintTicket>メソッドによって返されます。  
  
3.  プリンターが両面印刷をサポートする場合、サンプル コードでは、<xref:System.Printing.PrintTicket>両面印刷を要求します。 アプリケーションでは設定で使用できるすべての可能なプリンターが指定されていない、<xref:System.Printing.PrintTicket>要素。 場合はプログラマと製品のインストール時の両方の浪費になります。 代わりに、コードが両面印刷要求のみを設定し、その後、これをマージ<xref:System.Printing.PrintTicket>、既存の完全に構成され、検証、 <xref:System.Printing.PrintTicket>、ここでは、ユーザーの既定<xref:System.Printing.PrintTicket>です。  
  
4.  同様に、サンプルを呼び出す、<xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>メソッド、新しい結合を最小限に抑える<xref:System.Printing.PrintTicket>ユーザーの既定値は<xref:System.Printing.PrintTicket>です。 返されます。、<xref:System.Printing.ValidationResult>を含む新しい<xref:System.Printing.PrintTicket>としてそのプロパティのいずれか。  
  
5.  サンプルをテストし、新しい<xref:System.Printing.PrintTicket>両面印刷を要求します。 場合は、このサンプルでは、ユーザーの新しい既定の印刷チケットします。 上記の手順 2 を省略したプリンターが、長辺に沿って両面印刷をサポートしていませんしかどうか、テスト結果となります`false`です。 (前の注を参照してください)。  
  
6.  変更をコミットする最後の重要な手順では、<xref:System.Printing.PrintQueue.UserPrintTicket%2A>のプロパティ、<xref:System.Printing.PrintQueue>で、<xref:System.Printing.PrintQueue.Commit%2A>メソッドです。  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 この例をすばやくテストすることができます、ように残りの部分は次に示します。 プロジェクトと名前空間を作成して、この記事で名前空間ブロックに両方のコード スニペットを貼り付けます。  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [スキーマを印刷します。](http://go.microsoft.com/fwlink/?LinkId=186397)
