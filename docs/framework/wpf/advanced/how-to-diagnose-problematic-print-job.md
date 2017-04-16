---
title: "方法 : 問題のある印刷ジョブを診断する | Microsoft Docs"
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
  - "印刷ジョブ, 診断 (問題を)"
  - "印刷ジョブ, トラブルシューティング"
  - "トラブルシューティング (印刷ジョブに関する問題を)"
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 問題のある印刷ジョブを診断する
ネットワーク管理者は、印刷ジョブで印刷を実行できない、印刷速度が遅いなどのユーザーからの苦情を処理することがよくあります。  [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] の [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] で公開されているさまざまな印刷ジョブのプロパティには、印刷ジョブを迅速にリモート診断する手段が用意されています。  
  
## 使用例  
 このようなユーティリティを作成する主な手順は次のとおりです。  
  
1.  ユーザーから苦情が出ている印刷ジョブを特定します。  多くの場合、ユーザーはそのジョブを正確に特定できません。  プリント サーバーまたはプリンターの名前がわからない場合があります。  プリンターの場所を、<xref:System.Printing.PrintQueue.Location%2A> プロパティの設定に使用した用語とは異なる用語で説明する場合もあります。  したがって、ユーザーが現在送信しているジョブのリストを生成することをお勧めします。  ジョブが複数存在する場合は、ユーザーと印刷システム管理者間の通信を使用して、問題のあるジョブを特定できます。  その手順は次のとおりです。  
  
    1.  すべてのプリント サーバーのリストを取得します。  
  
    2.  印刷キューを照会するためにサーバーをループします。  
  
    3.  サーバー ループの各パス内で、ジョブを照会するためにすべてのサーバーのキューをループします。  
  
    4.  キュー ループの各パス内でジョブをループして、苦情を訴えているユーザーが送信したジョブに関する識別情報を収集します。  
  
2.  問題のある印刷ジョブを特定したら、関連するプロパティを調べて問題を確認します。  たとえば、ジョブがエラー状態になっていないか、キューにサービスを提供しているプリンターがジョブの印刷前にオフラインになっていないかなどを確認します。  
  
 一連のコード例を次のコードに示します。  最初のコード例には、印刷キューのループが示されています   \(前の 手順 1c. を参照\)。変数 `myPrintQueues` は、現在のプリント サーバーの <xref:System.Printing.PrintQueueCollection> オブジェクトです。  
  
 このコード例では、まず <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=fullName> を使用して、現在の印刷キューのオブジェクトを更新します。  これにより、オブジェクトのプロパティが、オブジェクトに示される物理プリンターの状態を正確に表すようになります。  次に、アプリケーションが <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A> を使用して、現在印刷キューに存在する印刷ジョブのコレクションを取得します。  
  
 次に、アプリケーションは <xref:System.Printing.PrintSystemJobInfo> コレクションをループし、各 <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> プロパティと苦情を訴えているユーザーのエイリアスを比較します。  一致した場合、アプリケーションは、ジョブに関する識別情報を表示される文字列に追加します   \(変数 `userName` および `jobList` は、これより前にアプリケーションで初期化されています\)。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 次のコード例では、手順 2. のアプリケーションを取り上げます   \(前の説明を参照\)。問題のあるジョブが特定され、その識別情報の入力を求めるメッセージがアプリケーションから表示されます。  この情報から、<xref:System.Printing.PrintServer>、<xref:System.Printing.PrintQueue>、および <xref:System.Printing.PrintSystemJobInfo> の各オブジェクトが作成されます。  
  
 この時点で、アプリケーションには次の印刷ジョブのステータスを確認する 2 つの方法に対応する分岐構造があります。  
  
-   <xref:System.Printing.PrintJobStatus> 型の <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> プロパティのフラグを読み取ることができる。  
  
-   <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> や <xref:System.Printing.PrintSystemJobInfo.IsInError%2A> などの各関連プロパティを読み取ることができる。  
  
 この例では両方の方法を示すため、ユーザーは使用する方法に関して入力を求められ、<xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> プロパティのフラグを使用する場合は「Y」と応答しています。  2 つの方法の詳細については、以下を参照してください。  最後に、アプリケーションは **ReportQueueAndJobAvailability** というメソッドを使用して、現時点でジョブを印刷できるかどうかを報告します。  このメソッドについては、「[現在、印刷ジョブが印刷可能であるかどうかを検出する](../../../../docs/framework/wpf/advanced/how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md)」で説明しています。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> プロパティのフラグを使用して印刷ジョブのステータスを確認するには、各関連フラグが設定されているかどうかを確認します。  1 ビットがビット フラグ セットで設定されているかどうかを確認するには、通常、フラグ セットを 1 つのオペランドとし、フラグ自体をもう 1 つのオペランドとして、論理 AND 演算を行います。  フラグ自体には 1 ビットのみが設定されているため、論理 AND を実行すると、最大でもその同じビットが設定されます。  該当するかどうかを確認するには、論理 AND の結果とフラグ自体を比較します。  詳細については、<xref:System.Printing.PrintJobStatus>、[& 演算子 \(C\# リファレンス\)](../Topic/&%20Operator%20\(C%23%20Reference\).md)、および <xref:System.FlagsAttribute> を参照してください。  
  
 次のコードでは、ビットが設定されている属性ごとにこの報告をコンソール画面に表示し、場合によっては応答方法を示します   \(ジョブまたはキューが一時停止されている場合に呼び出される **HandlePausedJob** メソッドについては、後で説明します\)。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 個別のプロパティを使用して印刷ジョブのステータスを確認するには、単に各プロパティを読み取り、プロパティが `true` の場合は報告をコンソール画面に表示し、場合によっては応答方法を示します   \(ジョブまたはキューが一時停止されている場合に呼び出される **HandlePausedJob** メソッドについては、後で説明します\)。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** メソッドを使用すると、アプリケーションのユーザーは、一時停止されているジョブをリモートで再開することができます。  印刷キューの一時停止に正当な理由がある可能性もあるため、このメソッドはまず、再開するかどうかの決定をユーザーに求めるプロンプトを表示します。  「Y」と応答すると、<xref:System.Printing.PrintQueue.Resume%2A?displayProperty=fullName> メソッドが呼び出されます。  
  
 次に、ジョブが印刷キューとは関係なく一時停止されている場合のために、ユーザーはジョブ自体を再開するかどうかを決定するように求められます   \(<xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=fullName> と <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=fullName> を比較してください\)。「Y」と応答すると、<xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=fullName> が呼び出されます。それ以外の場合は、<xref:System.Printing.PrintSystemJobInfo.Cancel%2A> が呼び出されます。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## 参照  
 <xref:System.Printing.PrintJobStatus>   
 <xref:System.Printing.PrintSystemJobInfo>   
 <xref:System.FlagsAttribute>   
 <xref:System.Printing.PrintQueue>   
 [& 演算子 \(C\# リファレンス\)](../Topic/&%20Operator%20\(C%23%20Reference\).md)   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)