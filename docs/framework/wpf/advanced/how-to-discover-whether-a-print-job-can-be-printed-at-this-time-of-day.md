---
title: '方法 : 現在、印刷ジョブが印刷可能であるかどうかを検出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: e5ea5ad3bcb10bfbc091f0b5852ee181a2c3fa8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548036"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>方法 : 現在、印刷ジョブが印刷可能であるかどうかを検出する
印刷キューは常に使用できません、1 日 24 時間です。 1 日の特定の時刻に使用できないように設定できます開始と終了の時刻のプロパティがあります。 たとえば、この機能は、特定の部門午後 5 時以降後に排他的に使用するプリンターを予約するは使用できます。 その部門は、別のキュー サービスの他の部門よりプリンターを使用して必要があります。 午後 5 時以降に他の部署のキューを設定すると、する部門用のキューを設定することが常に使用します。  
  
 さらに、印刷ジョブ自体は、指定した期間内でのみ印刷できるように設定できます。  
  
 <xref:System.Printing.PrintQueue>と<xref:System.Printing.PrintSystemJobInfo>で公開されているクラス、 [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework の特定の印刷ジョブが、現時点で特定のキューに印刷できるかどうかをリモートで確認の手段を提供します。  
  
## <a name="example"></a>例  
 次の例は、印刷ジョブに問題を診断できるサンプルです。  
  
 この種の関数の 2 つの主な手順は次があります。  
  
1.  読み取り、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>のプロパティ、<xref:System.Printing.PrintQueue>をそれらの間は、現在の時刻かどうかを判断します。  
  
2.  読み取り、<xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>と<xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A>のプロパティ、<xref:System.Printing.PrintSystemJobInfo>をそれらの間は、現在の時刻かどうかを判断します。  
  
 これらのプロパティは、ファクトから複雑な問題が発生するが、<xref:System.DateTime>オブジェクト。 それらは<xref:System.Int32>午前 0 時から時間を分単位として日の時刻を表すオブジェクト。 さらに、this、午前 0 時では、現在のタイム ゾーンは UTC (協定世界時) の午前 0 時です。  
  
 最初のコード例は、静的メソッドを表示**ReportQueueAndJobAvailability**、渡された、<xref:System.Printing.PrintSystemJobInfo>ジョブが現在の時刻に印刷するかどうかを判断するヘルパー メソッドを呼び出すと、印刷できない場合、ときにそのことができます。 注意して、<xref:System.Printing.PrintQueue>メソッドに渡されません。 これは、ため、<xref:System.Printing.PrintSystemJobInfo>のキューへの参照が含まれています、<xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>プロパティです。  
  
 下位の方法には、オーバー ロードされた**1 つ**いずれかのメソッド、<xref:System.Printing.PrintQueue>または<xref:System.Printing.PrintSystemJobInfo>をパラメーターとして。 **また**です。 以下は、すべてこれらのメソッドについて説明します。  
  
 **ReportQueueAndJobAvailability**メソッドを確認するかどうか、キューまたは印刷ジョブが使用可能なこの時点ではまずします。 かどうかを確認するのいずれかが使用可能な場合は、使用できないキュー。 使用できませんこのファクトとすると、キュー利用可能になるもう一度時刻、メソッドが報告されます。 ジョブを確認し、[次へ] の時刻を報告使用可能な場合は、ときにまたがるに印刷できるときにします。 最後に、ジョブを印刷できる最も早い時刻を報告します。 これは、次の 2 倍の後です。  
  
-   印刷キューが次に利用可能な時間。  
  
-   印刷ジョブが次に利用可能な時間。  
  
 1 日の時間を報告するときに、<xref:System.DateTime.ToShortTimeString%2A>のため、このメソッドは、年、月、および出力からの日数を表示しません。 メソッドが呼び出されます。 特定の年、月、または日数を印刷キューまたは印刷ジョブのいずれかの可用性を制限することはできません。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 2 つのオーバー ロード、 **1 つ**メソッドはのみそれらに渡される型を除いて同一、<xref:System.Printing.PrintQueue>バージョンを記載します。  
  
> [!NOTE]
>  サンプルはジェネリック メソッドを作成していないため、メソッドが型を除いて同一であることの質問を発生させます**1 つ\<T >** です。 その理由は、このようなメソッドを持つクラスに制限する必要がある、**一度、対象**と**UntilTimeOfDay**メソッドを呼び出すと、プロパティが、ジェネリック メソッドのみに制限できます、1 つのクラスであり、唯一のクラスの両方に共通<xref:System.Printing.PrintQueue>と<xref:System.Printing.PrintSystemJobInfo>ツリーは、継承の<xref:System.Printing.PrintSystemObject>をこのようなプロパティがありません。  
  
 **1 つ**メソッド (次のコード例で表されている) の初期化ではまず、 <xref:System.Boolean> sentinel 変数`true`です。 リセットされます`false`キューが使用できない場合は、します。  
  
 メソッドを次に、かどうかをチェック開始「までの間」時間は同じです。 場合は、キューは常に、使用可能なため、メソッドを返します`true`です。  
  
 メソッドが、静的なを使用して、キューが使用できない場合、すべての時間、<xref:System.DateTime.UtcNow%2A>として現在の時刻を取得するプロパティ、<xref:System.DateTime>オブジェクト。 (ために、ローカル タイムここは必要ありません、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティでは、それ自体を UTC 時刻でします)。  
  
 ただし、これら 2 つのプロパティが<xref:System.DateTime>オブジェクト。 <xref:System.Int32>分後に UTC 深夜の数と時間を表すです。 変換するためは、<xref:System.DateTime>分の後、午前 0 時にオブジェクト。 インストールが完了したら、メソッドだけが確認する"now"かどうかを参照してください、キューの開始の間、および「まで」回、セットを false の場合は"now"sentinel が 2 つの時刻の間ではありませんし、sentinel を返します。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **また**(次のコード例で表されている) メソッドは、ディスカッションは簡単なので、Microsoft .NET Framework で導入されたすべてのメソッドを使用しません。 メソッドには二重の変換: 分の後、午前 0 時を表す整数値を取得および人間が判読できる時間に変換する必要があります、これをローカル時刻に変換する必要があります。 でこれを行う、最初に作成、 <xref:System.DateTime> UTC しを使用して午前 0 時に設定されているオブジェクト、<xref:System.DateTime.AddMinutes%2A>メソッドをメソッドに渡された分を加算します。 返されます。 新しい<xref:System.DateTime>メソッドに渡された元の時刻を表すです。 <xref:System.DateTime.ToLocalTime%2A>メソッドし、この現地時刻に変換します。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.Printing.PrintQueue>  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)
