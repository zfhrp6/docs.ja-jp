---
title: "基本 TransactionScope | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# 基本 TransactionScope
このサンプルは、<xref:System.Activities.Statements.TransactionScope> インスタンスを入れ子にする方法を示す 4 つのシナリオで構成されています。1 つ目のシナリオは、作成者には構造がわからないサードパーティのアクティビティを入れ子にする方法を示しています。2 つ目と 3 つ目のシナリオは、タイムアウトがどのように機能するかを示しています。4 つ目のシナリオは、<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> の設定を示しています。  
  
## TransactionScopeActivity の入れ子  
 1 つ目のシナリオのワークフローは、2 つの <xref:System.Activities.Statements.WriteLine> アクティビティと 1 つの <xref:System.Activities.Statements.TransactionScope> のシーケンスで構成されています。<xref:System.Activities.Statements.TransactionScope> の本体は、2 つの <xref:System.Activities.Statements.WriteLine> アクティビティ、トランザクションのローカル識別子を出力するカスタム アクティビティ、およびサードパーティのアクティビティのシーケンスです。サードパーティのアクティビティである `TransactionScopeTest` には <xref:System.Activities.Statements.TransactionScope> が含まれていますが、ワークフローの作成者にはわかりません。このシナリオは、<xref:System.Activities.Statements.TransactionScope> アクティビティを入れ子にできることを示しています。  
  
## タイムアウト  
 2 つ目のシナリオのワークフローは 1 つ目のシナリオとほとんど同じですが、`TransactionScopeTest` が <xref:System.Activities.Statements.TransactionScope> に置き換えられています。この <xref:System.Activities.Statements.TransactionScope> の本体は 5 秒の遅延で、トランザクションのタイムアウトは 2 秒に設定されています。外側の <xref:System.Activities.Statements.TransactionScope> のタイムアウトは 10 秒に設定されています。スコープで最も小さいタイムアウト値が適用されるため、トランザクションがタイムアウトします。  
  
 3 つ目のシナリオのワークフローは 2 つ目のシナリオとほとんど同じですが、遅延アクティビティが内側の <xref:System.Activities.Statements.TransactionScope> の本体からその直後 \(外側の <xref:System.Activities.Statements.TransactionScope> の本体\) に移動されています。この場合もトランザクションがタイムアウトしますが、内側の <xref:System.Activities.Statements.TransactionScope> の 2 秒のタイムアウトはもう適用されないため、トランザクションは 10 秒後 \(外側の <xref:System.Activities.Statements.TransactionScope> のタイムアウト期間が経過したとき\) にタイムアウトします。  
  
## トランザクション エラーによる中止  
 このワークフローは 3 つ目のシナリオに似ていますが、タイムアウトが <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> プロパティに置き換えられています。内側にあるすべての子は、フラグが設定されている場合、フラグが外側の <xref:System.Activities.Statements.TransactionScope> と一致している必要がありますが、このシナリオでは一致していないため、ワークフローを開くと例外がスローされます。  
  
#### サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で BasicTransactionScopeSample.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、CTRL キーと SHIFT キーを押したまま B キーを押すか、**\[ビルド\]** メニューの **\[ソリューションのビルド\]** を選択します。  
  
3.  ビルドが完了したら、F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。または、Ctrl キーを押しながら F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックして、デバッグ機能なしで実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`  
  
## 参照