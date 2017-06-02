---
title: "方法 : プリンターのステータスをリモート操作で調査する | Microsoft Docs"
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
  - "プリンターのステータス, 調査 (リモート操作で)"
  - "リモート操作で調査 (プリンターのステータスを)"
  - "ステータス, プリンター, 調査 (リモート操作で)"
  - "調査 (プリンターのステータスをリモート操作で)"
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : プリンターのステータスをリモート操作で調査する
中企業および大企業では、任意の時点において、紙詰まりや用紙切れなどの問題が発生したために動作していないプリンターが複数存在する場合があります。  [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] の [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] で公開されているさまざまなプリンター プロパティには、プリンターの状態を迅速に調査する手段が用意されています。  
  
## 使用例  
 このようなユーティリティを作成する主な手順は次のとおりです。  
  
1.  すべてのプリント サーバーのリストを取得します。  
  
2.  印刷キューを照会するためにサーバーをループします。  
  
3.  サーバー ループの各パス内で、すべてのサーバーのキューをループし、キューが現在動作していないことを示している各プロパティを読み取ります。  
  
 一連のスニペットを次のコードに示します。  この例では、単純化のため、CRLF で区切られたプリント サーバーのリストがあると想定します。  `fileOfPrintServers` 変数は、このファイルの <xref:System.IO.StreamReader> オブジェクトです。  各サーバー名はそれぞれ独自の行に含まれているため、<xref:System.IO.StreamReader.ReadLine%2A> を呼び出すと、次のサーバーの名前が取得され、<xref:System.IO.StreamReader> のカーソルが次の行の先頭に移動します。  
  
 このコードは、外側のループ内で、最新のプリント サーバーの <xref:System.Printing.PrintServer> オブジェクトを作成し、アプリケーションがサーバーに対する管理権限を持つことを指定します。  
  
> [!NOTE]
>  サーバーが多数存在する場合は、必要なプロパティのみを初期化する [PrintServer\(String, String\<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> コンストラクターを使用することで、パフォーマンスを向上させることができます。  
  
 この例では、次に <xref:System.Printing.PrintServer.GetPrintQueues%2A> を使用してサーバーのすべてのキューのコレクションを作成し、これらのキューのループを開始します。  この内側のループには、プリンターのステータスを確認する 2 つの方法に対応する分岐構造が含まれています。  
  
-   <xref:System.Printing.PrintQueueStatus> 型の <xref:System.Printing.PrintQueue.QueueStatus%2A> プロパティのフラグを読み取ることができる。  
  
-   <xref:System.Printing.PrintQueue.IsOutOfPaper%2A> や <xref:System.Printing.PrintQueue.IsPaperJammed%2A> などの各関連プロパティを読み取ることができる。  
  
 この例では両方の方法を示すため、ユーザーは使用する方法に関して入力を求められ、<xref:System.Printing.PrintQueue.QueueStatus%2A> プロパティのフラグを使用する場合は「y」と応答しています。  2 つの方法の詳細については、以下を参照してください。  
  
 最後に、結果をユーザーに表示します。  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <xref:System.Printing.PrintQueue.QueueStatus%2A> プロパティのフラグを使用してプリンターのステータスを確認するには、各関連フラグが設定されているかどうかを確認します。  1 ビットがビット フラグ セットで設定されているかどうかを確認するには、通常、フラグ セットを 1 つのオペランドとし、フラグ自体をもう 1 つのオペランドとして、論理 AND 演算を行います。  フラグ自体には 1 ビットのみが設定されているため、論理 AND を実行すると、最大でもその同じビットが設定されます。  該当するかどうかを確認するには、論理 AND の結果とフラグ自体を比較します。  詳細については、<xref:System.Printing.PrintQueueStatus>、[& 演算子 \(C\# リファレンス\)](../Topic/&%20Operator%20\(C%23%20Reference\).md)、および <xref:System.FlagsAttribute> のトピックを参照してください。  
  
 次のコードでは、ビットが設定されている属性ごとに、ユーザーに表示される最終レポートに警告を追加します   \(コードの最後で呼び出している **ReportAvailabilityAtThisTime** メソッドについては以下で説明します\)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 各プロパティを使用してプリンターのステータスを確認するには、各プロパティを読み取り、プロパティが `true` の場合にユーザーに表示される最終レポートに警告を追加するだけです   \(コードの最後で呼び出している **ReportAvailabilityAtThisTime** メソッドについては以下で説明します\)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** メソッドは、現在の時刻にキューが使用可能かどうかを確認する必要がある場合に備えて作成されたものです。  
  
 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> プロパティと <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> プロパティが等しい場合、このメソッドは何も実行しません。なぜなら、その場合、プリンターは常に使用可能だからです。  それぞれのプロパティが異なる場合、このメソッドは現在の時刻を取得します。次に、この時刻を午前 0 時からの合計分数に変換する必要があります。これは、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A> プロパティと <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> プロパティが <xref:System.DateTime> オブジェクトではなく、午前 0 時以降の分数を表す <xref:System.Int32> であるためです。  最後に、このメソッドは、現在の時刻が開始時刻と "終了" 時刻の間であるかどうかを確認します。  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## 参照  
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
 [& 演算子 \(C\# リファレンス\)](../Topic/&%20Operator%20\(C%23%20Reference\).md)   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)