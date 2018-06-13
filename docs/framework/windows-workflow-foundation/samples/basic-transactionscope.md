---
title: 基本 TransactionScope
ms.date: 03/30/2017
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
ms.openlocfilehash: fe6877c4b2d72dc3d571740395fd4dc92ca8e99c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516803"
---
# <a name="basic-transactionscope"></a>基本 TransactionScope
このサンプルは、<xref:System.Activities.Statements.TransactionScope> インスタンスを入れ子にする方法を示す 4 つのシナリオで構成されています。 1 つ目のシナリオは、作成者には構造がわからないサードパーティのアクティビティを入れ子にする方法を示しています。 2 つ目と 3 つ目のシナリオは、タイムアウトがどのように機能するかを示しています。4 つ目のシナリオは、<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> の設定を示しています。  
  
## <a name="nesting-of-transactionscopeactivity"></a>TransactionScopeActivity の入れ子  
 1 つ目のシナリオのワークフローは、2 つの <xref:System.Activities.Statements.WriteLine> アクティビティと 1 つの <xref:System.Activities.Statements.TransactionScope> のシーケンスで構成されています。 <xref:System.Activities.Statements.TransactionScope> の本体は、2 つの <xref:System.Activities.Statements.WriteLine> アクティビティ、トランザクションのローカル識別子を出力するカスタム アクティビティ、およびサードパーティのアクティビティのシーケンスです。 サードパーティのアクティビティである `TransactionScopeTest` には <xref:System.Activities.Statements.TransactionScope> が含まれていますが、ワークフローの作成者にはわかりません。 このシナリオは、<xref:System.Activities.Statements.TransactionScope> アクティビティを入れ子にできることを示しています。  
  
## <a name="time-outs"></a>タイムアウト  
 2 つ目のシナリオのワークフローは 1 つ目のシナリオとほとんど同じですが、 `TransactionScopeTest` が <xref:System.Activities.Statements.TransactionScope> に置き換えられています。 この <xref:System.Activities.Statements.TransactionScope> の本体は 5 秒の遅延で、トランザクションのタイムアウトは 2 秒に設定されています。 外側の <xref:System.Activities.Statements.TransactionScope> のタイムアウトは 10 秒に設定されています。 スコープで最も小さいタイムアウト値が適用されるため、トランザクションがタイムアウトします。  
  
 3 つ目のシナリオのワークフローは 2 つ目のシナリオとほとんど同じですが、 遅延アクティビティが内側の <xref:System.Activities.Statements.TransactionScope> の本体からその直後 (外側の <xref:System.Activities.Statements.TransactionScope> の本体) に移動されています。 この場合もトランザクションがタイムアウトしますが、内側の <xref:System.Activities.Statements.TransactionScope> の 2 秒のタイムアウトはもう適用されないため、 トランザクションは 10 秒後 (外側の <xref:System.Activities.Statements.TransactionScope> のタイムアウト期間が経過したとき) にタイムアウトします。  
  
## <a name="aborting-on-transaction-failure"></a>トランザクション エラーによる中止  
 このワークフローは 3 つ目のシナリオに似ていますが、タイムアウトが <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> プロパティに置き換えられています。 内側にあるすべての子は、フラグが設定されている場合、フラグが外側の <xref:System.Activities.Statements.TransactionScope> と一致している必要がありますが、 このシナリオでは一致していないため、ワークフローを開くと例外がスローされます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で BasicTransactionScopeSample.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。  
  
3.  F5 キーを押してビルドが成功した後、または選択**デバッグの開始**から、**デバッグ**メニュー。 または ctrl キーを押しながら f5 キーを押してまたは選択**デバッグなしで開始**から、**デバッグ**] メニューの [デバッグなしで実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`