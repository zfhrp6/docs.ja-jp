---
title: 絶対遅延
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 3a104f6b879e9cdc899bad2201ad1ed320a38a2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518386"
---
# <a name="absolute-delay"></a>絶対遅延
このサンプルの主要なシナリオは、ワークフロー アプリケーションで永続的なタイマーを使用して、指定した <xref:System.DateTime> まで遅延することです。 これは、特定の <xref:System.Activities.Statements.Delay> (または分数/秒数) の遅延のみ行うことができるため、組み込みの <xref:System.TimeSpan> アクティビティの使用とは異なります。  
  
 この区別を行う現実のシナリオとして、次のようなものがあります。  
  
1.  メールの送信を 30 秒遅延させて、誤りがないことを確認します。  
  
2.  時間外に作業し、通常の営業時間 (午前 8 時など) まですべてのメールを遅延させます。  
  
## <a name="demonstrates"></a>使用例  
  
1.  絶対遅延を実装するための <xref:System.Activities.Statements.DurableTimerExtension>  
  
2.  永続的なタイマーに <xref:System.Activities.WorkflowApplication> を使用した永続性の設定  
  
3.  拡張ポイントを使用するための <xref:System.Activities.NativeActivity%601> の使用  
  
4.  SendEmail アクティビティでの <xref:System.Activities.CodeActivity%601> の使用  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  XAML のみのワークフロー  
  
 このサンプルでは、<xref:System.DateTime> を取得するカスタム アクティビティの作成方法と、永続的なタイマーを使用して遅延期間を登録する方法を示します。 永続的なタイマーを使用している場合は、<xref:System.Activities.NativeActivity> を使用してブックマークを作成する必要があります。このブックマークをタイマー拡張に登録する必要があります。 このサンプルでは、永続的なタイマーが時間切れになると、`OnTimerExpired` メソッドが呼び出されます。 タイマー拡張を <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> イベントに追加して、この情報がランタイムに確実に提供されるようにします。 永続的なタイマーは <xref:System.DateTime> のみを取得するため、その他の実装詳細として挙げられるものは、<xref:System.TimeSpan> から <xref:System.DateTime> に変換するためのロジックを実装する必要があることのみです。 次の操作を行うことで、精度に小さな逸脱があることに注意します。  
  
> [!NOTE]
>  <xref:System.DateTime> から <xref:System.TimeSpan> への変換により、精度が若干低下します。  
  
 このサンプルは、<xref:System.Activities.WorkflowApplication> の永続性をオンにする方法も示しています。 このサンプルでは、タイマーの時間切れを待機している間のアイドル時間中にワークフロー データが永続性データベースにアンロードされる永続的なタイマーを使用します。 この実装は、他の永続性アクションにも使用できます。 このサンプルは、SQL Server で永続性接続文字列を設定する方法、およびワークフロー インスタンスのデータを永続化するためにインスタンス ストアを作成する方法を示しています。 ワークフロー インスタンスを実行可能にするイベントが発生した後でワークフローを再開する方法に関するロジックも提供されています。  
  
 このサンプルをステップ実行するを組み込みの待機時間を開始および完了に時間がかかると送信される電子メール メッセージが表示されます。 ここから、AbsoluteDelay アクティビティは指定した <xref:System.DateTime> まで (または <xref:System.DateTime> を経過している場合は 0 秒間) 停止します。時間切れになると、電子メールが送信されます。 これは、組み込みの <xref:System.Activities.Statements.Delay> 機能と AbsoluteDelay アクティビティの使用の 2 つの異なるユース ケースを示します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  SQL Server Express (またはそれ以降) がコンピューターにインストールされていることを確認します。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトで setup.cmd (WF/Basic/Services/AbsoluteDelay/CS にあります) を実行して AbsoluteDelaySampleDB データベースを作成し、永続性スキーマと永続性ロジックを作成します。  
  
3.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。  
  
4.  Delay アクティビティに Duration を指定します。  
  
5.  AbsoluteDelay アクティビティに ExpirationTime を指定します。  
  
6.  SendMail アクティビティの SendMailTo、SendMailFrom、SendMailSubject、SendMailBody、SmtpHost の各フィールドを更新します。  
  
    > [!NOTE]
    >  有効な SMTP ホストを入力しない場合は、アプリケーションで SMTP 例外がスローされます。  
  
7.  選択して、ソリューションをビルド**ビルド**、**ソリューションのビルド**です。  
  
8.  キーを押して、ソリューションを実行**f5 キーを押して**です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
