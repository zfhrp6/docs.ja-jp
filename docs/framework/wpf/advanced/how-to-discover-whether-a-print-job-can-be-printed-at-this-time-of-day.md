---
title: "方法 : 現在、印刷ジョブが印刷可能であるかどうかを検出する | Microsoft Docs"
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
  - "印刷ジョブ, タイミング"
  - "印刷キュー, タイミング"
  - "プリンター, 可用性"
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 現在、印刷ジョブが印刷可能であるかどうかを検出する
印刷キューは、24 時間常に使用できるわけではありません。  印刷キューには開始時刻と終了時刻のプロパティがあり、特定の時間帯にキューを使用不可能にする場合にこれらを設定します。  この機能は、たとえば、特定の部門が午後 5 時以降にプリンターを独占使用するための予約を行うときに使用できます。  この部門は、プリンターにサービスを提供するキューとして、他の部門が使用するキューとは異なるキューを使用します。  この部門用のキューは常に使用できるように設定し、他の部門のキューは午後 5 時以降は使用できなくなるように設定します。  
  
 さらに、印刷ジョブ自体を、指定した時間の間だけ印刷できるように設定できます。  
  
 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] の [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] で公開される <xref:System.Printing.PrintQueue> クラスおよび <xref:System.Printing.PrintSystemJobInfo> クラスは、特定の印刷ジョブが特定のキューで現在印刷可能かどうかをリモートで確認するときに利用できます。  
  
## 使用例  
 次の例は、印刷ジョブに関する問題を診断できるサンプルです。  
  
 この種の関数の主な手順は次の 2 つです。  
  
1.  <xref:System.Printing.PrintQueue> の <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> プロパティおよび <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> プロパティを読み取って、現在の時刻がこの 2 つの間であるかどうかを判断します。  
  
2.  <xref:System.Printing.PrintSystemJobInfo> の <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> プロパティおよび <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> プロパティを読み取って、現在の時刻がこの 2 つの間であるかどうかを判断します。  
  
 ただし、これらのプロパティは <xref:System.DateTime> オブジェクトではないことに注意してください。  これらのプロパティは、時刻を午前 0 時からの経過時間 \(分\) として表す <xref:System.Int32> オブジェクトです。  さらに、これは、現在のタイム ゾーンでの午前 0 時ではなく、UTC \(世界協定時刻\) の午前 0 時です。  
  
 最初のコード例に示す静的メソッド **ReportQueueAndJobAvailability** では、<xref:System.Printing.PrintSystemJobInfo> を受け取り、ヘルパー メソッドを呼び出して、ジョブが現時点で印刷できるかどうかと、できない場合はいつ印刷できるかを判断します。  <xref:System.Printing.PrintQueue> はメソッドに渡されないことに注意してください。  これは、キューに対する参照が、<xref:System.Printing.PrintSystemJobInfo> の <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> プロパティに格納されているからです。  
  
 下位メソッドの 1 つに、オーバーロードされた **ReportAvailabilityAtThisTime** メソッドがあり、このメソッドはパラメーターとして <xref:System.Printing.PrintQueue> または <xref:System.Printing.PrintSystemJobInfo> を受け取ります。  また、**TimeConverter.ConvertToLocalHumanReadableTime** もあります。  これらのすべてのメソッドについては、後で説明します。  
  
 **ReportQueueAndJobAvailability** メソッドは、最初に、現時点でキューまたは印刷ジョブが使用不可能になっているかどうかを確認します。  どちらかが使用不可能の場合は、次に、キューが使用不可能かどうかを確認します。  使用不可能の場合は、このことと、いつキューが再び使用可能になるかを報告します。  次に、ジョブを確認し、使用不可能の場合は、ジョブが印刷可能になる時間帯を報告します。  最後に、このジョブが最短でいつ印刷可能になるかを報告します。  これは、次の 2 つのうち、遅い方の時刻です。  
  
-   印刷キューが次回使用可能になる時刻。  
  
-   印刷ジョブが次回使用可能になる時刻。  
  
 時刻を報告するときに、<xref:System.DateTime.ToShortTimeString%2A> メソッドも呼び出します。これは、年月日が出力されないようにするためです。  印刷キューと印刷ジョブのどちらも、使用可能な期間として特定の年、月、または日を指定することはできません。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 **ReportAvailabilityAtThisTime** メソッドの 2 つのオーバーロードは、渡される型を除いて同一であるので、<xref:System.Printing.PrintQueue> バージョンだけを後に示します  
  
> [!NOTE]
>  これらのメソッドが型以外は同一であるにもかかわらず、このサンプルでジェネリック メソッド **ReportAvailabilityAtThisTime\<T\>** を作成しない理由について次に説明します。  このようなメソッドでは、メソッドが呼び出す **StartTimeOfDay** プロパティと **UntilTimeOfDay** プロパティを持つクラスを限定する必要がありますが、ジェネリック メソッドでは限定できるクラスは 1 つだけであるにもかかわらず、継承ツリー内の <xref:System.Printing.PrintQueue> と <xref:System.Printing.PrintSystemJobInfo> の両方に共通の唯一のクラス <xref:System.Printing.PrintSystemObject> には、これらのプロパティはありません。  
  
 **ReportAvailabilityAtThisTime** メソッド \(後のコード例に示します\) は、最初に、<xref:System.Boolean> 型のセンティネル変数を `true` に初期化します。  この変数は、キューが使用不可能の場合に `false` に再設定されます。  
  
 次に、開始時刻と終了 \(until\) 時刻が同一であるかどうかを確認します。  同一ならば、キューは常時使用できるので `true` を返します。  
  
 キューが常時使用可能ではない場合は、静的プロパティ <xref:System.DateTime.UtcNow%2A> を使用して、現在の時刻を <xref:System.DateTime> オブジェクトとして取得します   \(<xref:System.Printing.PrintQueue.StartTimeOfDay%2A> および <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> プロパティ自体が UTC 時間なのでローカル時刻は必要ありません\)。  
  
 ただし、この 2 つのプロパティは <xref:System.DateTime> オブジェクトではありません。  これらは、時刻を UTC の午前 0 時からの経過時間 \(分\) として表す <xref:System.Int32> です。  したがって、<xref:System.DateTime> オブジェクトを、午前 0 時からの経過時間 \(分\) に変換する必要があります。  その後で、現在の時刻 \(now\) がキューの開始時刻 \(start\) と終了時刻 \(until\) の間であるかどうかを調べ、現在の時刻が 2 つの時刻の間ではない場合は、センティネル変数を false に設定して返します。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime** メソッド \(後のコード例に示します\) では、[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] で導入されたメソッドを使用していないので、詳しい説明は省略します。  このメソッドは、二重の変換を行います。午前 0 時からの経過時間 \(分\) 表す整数を受け取って、人間可読な時刻に変換し、この時刻をローカル時刻に変換する必要があります。  このことを実現するために、最初に UTC 午前 0 時に設定された <xref:System.DateTime> オブジェクトを作成し、<xref:System.DateTime.AddMinutes%2A> メソッドを使用して、メソッドに渡された午前 0 時からの経過時間 \(分\) を加算します。  このメソッドからは、渡された元の時刻を表す新しい <xref:System.DateTime> が返されます。  次に、<xref:System.DateTime.ToLocalTime%2A> メソッドを使用してこの時刻をローカル時刻に変換します。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## 参照  
 <xref:System.DateTime>   
 <xref:System.Printing.PrintSystemJobInfo>   
 <xref:System.Printing.PrintQueue>   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)