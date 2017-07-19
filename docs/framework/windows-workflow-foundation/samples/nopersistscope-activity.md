---
title: "NoPersistScope アクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# NoPersistScope アクティビティ
このサンプルでは、ワークフローでシリアル化不可能で破棄可能な状態を処理する方法を示します。ワークフローでシリアル化不可能な状態を永続化しないようにし、破棄可能なオブジェクトをワークフローで使用した後にクリーンアップすることが重要です。  
  
## 使用例  
 `NoPersistScope` カスタム アクティビティおよびデザイナー。  
  
## NoPersistZone アクティビティの使用  
 サンプル ワークフローの実行時に、`CreateTextWriter` というカスタム アクティビティによって、<xref:System.IO.TextWriter> 型のオブジェクトが作成されてワークフロー変数に保存されます。<xref:System.IO.TextWriter> が <xref:System.IDisposable> オブジェクトです。この <xref:System.IO.TextWriter> は、サンプルが実行されるディレクトリにある out.txt という名前のファイルに書き込むように構成されており、コンソールで入力するテキストをエコーするときに <xref:System.Activities.Statements.WriteLine> アクティビティによって使用されます。  
  
 エコー ロジックは、ワークフローが永続化されないようにする `NoPersistScope` アクティビティ \(このサンプルの一部でもあるコード\) 内で実行されます。コンソールで「`unload`」と入力すると、ホストはワークフロー インスタンスを永続化しようとしますが、ワークフローは `NoPersistScope` 内に留まるので、この操作はタイムアウトします。また、ワークフローは `Dispose` というカスタム アクティビティを使用して、<xref:System.IO.TextWriter> オブジェクトを使い終わったら破棄します。`Dispose` アクティビティは、Try ブロックの実行中に例外が発生した場合でも実行されるように、<xref:System.IO.TextWriter> 変数が宣言される <xref:System.Activities.Statements.TryCatch> アクティビティの <xref:System.Activities.Statements.TryCatch.Finally%2A> ブロック内に配置されます。  
  
 「`exit`」と入力すると、ワークフロー インスタンスを完了してプログラムを終了することができます。  
  
#### サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で NoPersistZone.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、CTRL キーと SHIFT キーを押したまま B キーを押すか、**\[ビルド\]** メニューの **\[ソリューションのビルド\]** を選択します。  
  
3.  ビルドが完了したら、F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。または、Ctrl キーを押しながら F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックして、デバッグ機能なしで実行します。  
  
#### クリーンアップするには \(省略可能\)  
  
1.  SQL インスタンス ストアを削除するには、Cleanup.cmd を実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`  
  
## 参照