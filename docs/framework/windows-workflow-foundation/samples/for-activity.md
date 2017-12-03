---
title: "For アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3b97e4bcd8dd60aa2768a8346d120bdebdb55ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="for-activity"></a>For アクティビティ
For サンプルでは、<xref:System.Activities.NativeActivity> から継承するカスタム アクティビティを構築し、そのアクティビティをワークフローで使用して実際の例を実行する方法を示します。 このサンプルに含まれるカスタム アクティビティは、C# の `for` ステートメントと同じように機能します。 T  
  
 `For` カスタム アクティビティには、`InitAction`、`IterationAction`、`Condition`、および `Body` というプロパティがあります。これらのプロパティは、標準的な C# の `For` ステートメントの初期化ステートメント、反復ステートメント、継続条件、および本体ステートメントにそれぞれ対応します。  
  
 次の表で、サンプルの主要なファイルについて説明します。  
  
|ファイル|説明|  
|----------|-----------------|  
|For.cs|`For` カスタム アクティビティのクラス定義。<xref:System.Activities.NativeActivity> クラスを拡張して C# の `For` ステートメントの機能を提供します。|  
|Program.cs|カスタム `For` アクティビティを使用してコレクションに対して基本的な反復処理を実行するクライアント アプリケーション。|  
  
> [!NOTE]
>  `For` カスタム アクティビティを使用する場合は、必ず `Condition` プロパティを設定してください。そうしないと、無限ループが発生する可能性があります。  
  
## <a name="demonstrates"></a>使用例  
 <xref:System.Activities.NativeActivity> から継承するカスタム アクティビティを作成します。  
  
## <a name="discussion"></a>説明  
 次の表で、このサンプルに含まれるアクティビティのプロパティについて説明します。  
  
 InitAction  
 初期化ステートメント  
  
 IterationAction  
 反復ステートメント  
  
 状態  
 条件ステートメント  
  
 Body  
 本体ステートメント  
  
 このアクティビティは、<xref:System.Activities.NativeActivity> から継承して、ランタイム機能 (`ScheduleActivity` のいずれかの <xref:System.Activities.NativeActivityContext> メソッドを使用した追加アクティビティの実行スケジュールの設定など) へのアクセスを取得します。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、For.sln ソリューション ファイルを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  F5 キーを押して、ソリューションを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`