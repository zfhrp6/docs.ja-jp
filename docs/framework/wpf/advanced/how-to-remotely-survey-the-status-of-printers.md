---
title: '方法 : プリンターのステータスをリモート操作で調査する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: eca1720aea1620683ebc9ed08b47a0f5625da9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545972"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>方法 : プリンターのステータスをリモート操作で調査する
中企業および大企業では、任意の時点において、紙詰まりや用紙切れなどの問題が発生したために動作していないプリンターが複数存在する場合があります。 プリンターのプロパティで公開されている一連の豊富な[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]Microsoft .NET Framework のプリンターの状態の迅速な調査を実行するための手段を提供します。  
  
## <a name="example"></a>例  
 このようなユーティリティを作成する主な手順は次のとおりです。  
  
1.  プリント サーバーの一覧を取得します。  
  
2.  サーバーをループして、印刷キューを照会します。  
  
3.  サーバー ループの各パス内で、すべてのサーバーのキューをループして、キューが現在動作していないことを示している各プロパティを読み取ります。  
  
 以下のコードは、一連のスニペットを示しています。 この例では、説明を簡単にするために、CRLF で区切られたプリント サーバー リストがあることを想定しています。 変数`fileOfPrintServers`は、<xref:System.IO.StreamReader>このファイルのオブジェクト。 すべての呼び出しは各サーバー名は、独自の行では、ため<xref:System.IO.StreamReader.ReadLine%2A>次のサーバーの名前を取得し、移動、<xref:System.IO.StreamReader>の次の行の先頭にカーソル。  
  
 外側のループ内のコードで作成、<xref:System.Printing.PrintServer>最新のプリント サーバーのオブジェクトし、アプリケーションが、サーバーに対する管理者権限があることを指定します。  
  
> [!NOTE]
>  使用してパフォーマンスを向上させることができます、多数のサーバーがある場合、<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29>だけする必要があるプロパティを初期化するコンス トラクターです。  
  
 使用して<xref:System.Printing.PrintServer.GetPrintQueues%2A>サーバーのすべてのコレクションを作成するのキューに配置し、それらをループ処理を開始します。 この内側のループは分岐構造になっており、プリンターの状態を確認する 2 つの方法に対応しています。  
  
-   フラグを読み取ることができます、<xref:System.Printing.PrintQueue.QueueStatus%2A>プロパティの型は<xref:System.Printing.PrintQueueStatus>します。  
  
-   などの関連する各プロパティを読み取ることができる<xref:System.Printing.PrintQueue.IsOutOfPaper%2A>、および<xref:System.Printing.PrintQueue.IsPaperJammed%2A>です。  
  
 この例では、両方の方法、ユーザーが以前に使用する方法の確認メッセージが表示およびのフラグを使用してたい場合は、"y"で応答したため、<xref:System.Printing.PrintQueue.QueueStatus%2A>プロパティです。 2 つの方法の詳細については、以下を参照してください。  
  
 最後に、結果がユーザーに表示されます。  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 フラグを使用してプリンターの状態を確認する、<xref:System.Printing.PrintQueue.QueueStatus%2A>プロパティ、設定されているかどうかに表示する各関連フラグを確認します。 1 ビットがビット フラグ セットで設定されているかどうかを確認するには、通常、フラグ セットを 1 つのオペランドとし、フラグ自体をもう 1 つのオペランドとして、論理 AND 演算を行います。 フラグ自体には 1 ビットのみが設定されているため、論理 AND の結果は、その同じビットが上限となります。 それが該当するかどうかを確認するには、論理 AND の結果とフラグ自体を比較します。 詳細については、次を参照してください。 <xref:System.Printing.PrintQueueStatus>、 [& 演算子 (c# リファレンス)](~/docs/csharp/language-reference/operators/and-operator.md)、および<xref:System.FlagsAttribute>です。  
  
 次のコードでは、ビットが設定されている属性ごとに、ユーザーに表示される最終レポートに警告を追加します  (コードの最後で呼び出している **ReportAvailabilityAtThisTime** メソッドについては以下で説明します)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 各プロパティを使用してプリンターの状態を確認するには、各プロパティを読み取り、プロパティが `true` の場合にユーザーに表示される最終レポートに警告を追加するだけです  (コードの最後で呼び出している **ReportAvailabilityAtThisTime** メソッドについては以下で説明します)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** メソッドは、現在の時刻にキューが使用可能かどうかを確認する必要がある場合に備えて作成されたものです。  
  
 メソッドは何も場合、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>その場合は、プリンターが使用可能なすべての時刻であるために、プロパティが等しい。 異なる場合、メソッドはために、合計深夜に変換する必要があるし、現在の時刻を取得、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティは、<xref:System.Int32>いない深夜後分、を表す<xref:System.DateTime>オブジェクト。 最後に、このメソッドは、現在の時刻が、開始時刻と終了時刻の間にあるかどうかを確認します。  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintQueueStatus>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 [& 演算子 (c# リファレンス)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)
