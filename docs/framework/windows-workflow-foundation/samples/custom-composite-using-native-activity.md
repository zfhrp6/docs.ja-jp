---
title: "ネイティブ アクティビティを使用したカスタム複合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# ネイティブ アクティビティを使用したカスタム複合
このサンプルでは、他の <xref:System.Activities.Activity> オブジェクトをスケジュールしてワークフローの実行のフローを制御する <xref:System.Activities.NativeActivity> を作成する方法を示します。この方法を示すために、このサンプルでは一般的な制御フローである Sequence と While の 2 つを使用します。  
  
## サンプルの詳細  
 `MySequence` から始めるとき、最初に気づくことは、それが <xref:System.Activities.NativeActivity> から派生しているということです。<xref:System.Activities.NativeActivity> は、`Execute` メソッドに渡される <xref:System.Activities.NativeActivityContext> を介して、ワークフロー ランタイム一式を公開する <xref:System.Activities.Activity> オブジェクトです。  
  
 `MySequence` は、ワークフローの作成者によって設定された <xref:System.Activities.Activity> オブジェクトのパブリック コレクションを公開します。ワークフローの実行前に、ワークフロー ランタイムがワークフローの各アクティビティに対して <xref:System.Activities.Activity.CacheMetadata%2A> メソッドを呼び出します。このプロセスの実行中に、ランタイムによって、データのスコープや有効期間を管理するための親子のリレーションシップが確立されます。<xref:System.Activities.Activity.CacheMetadata%2A> メソッドの既定の実装では、`MySequence` アクティビティの <xref:System.ComponentModel.TypeDescriptor> インスタンス クラスを使用して、<xref:System.Activities.Activity> 型または <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Activity>\> 型のパブリック プロパティを `MySequence` アクティビティの子として追加します。  
  
 アクティビティで子アクティビティのパブリック コレクションを公開するときは、それらの子アクティビティ間で状態を共有すると考えられます。そのため、親アクティビティ \(この場合は `MySequence`\) で、子アクティビティがそれを実現するための変数のコレクションも公開することをお勧めします。子アクティビティと同様に、<xref:System.Activities.Activity.CacheMetadata%2A> メソッドで、<xref:System.Activities.Variable> 型または <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Variable>\> 型のパブリック プロパティを `MySequence` アクティビティに関連付けられた変数として追加します。  
  
 `MySequence` の子によって操作されるパブリック変数に加えて、`MySequence` では、子の実行の進行状況を追跡する必要もあります。これを実現するために、プライベート変数 `currentIndex` を使用します。この変数は、`MySequence` アクティビティの <xref:System.Activities.Activity.CacheMetadata%2A> メソッド内に <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> メソッドの呼び出しを追加することで、`MySequence` 環境の一部として登録されています。`MySequence` `Activities` コレクションに追加された <xref:System.Activities.Activity> オブジェクトは、この方法で追加された変数にアクセスできません。  
  
 `MySequence` をランタイムで実行すると、ランタイムがその <xref:System.Activities.NativeActivity.Execute%2A> メソッドを呼び出し、<xref:System.Activities.NativeActivityContext> を渡します。<xref:System.Activities.NativeActivityContext> は、引数と変数の逆参照と、他の <xref:System.Activities.Activity> オブジェクトや `ActivityDelegates` のスケジュールを行うランタイムに返すアクティビティのプロキシです。`MySequence` は、`InternalExecute` メソッドを使用して、最初の子と後続のすべての子を単一のメソッドでスケジュールするロジックをカプセル化します。このメソッドは、まず `currentIndex` を逆参照します。`Activities` コレクションに含まれる数と等しい場合、シーケンスは終了し、アクティビティが処理をスケジュールせずに戻り、ランタイムによって状態が <xref:System.Activities.ActivityInstanceState> に変更されます。`currentIndex` がアクティビティ数より小さい場合、次の子は `Activities` コレクションから取得され、`MySequence` が <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> を呼び出して、スケジュールされている子と、`InternalExecute` メソッドを指す <xref:System.Activities.CompletionCallback> を渡します。最後に、`currentIndex` がインクリメントされ、制御がランタイムに戻されます。`MySequence` のインスタンスで子 <xref:System.Activities.Activity> オブジェクトがスケジュールされていれば、ランタイムはそのインスタンスの状態が Executing であると見なします。  
  
 子アクティビティが完了すると、<xref:System.Activities.CompletionCallback> が実行され、ループが先頭から継続されます。`Execute` と同様、<xref:System.Activities.CompletionCallback> は <xref:System.Activities.NativeActivityContext> を受け取り、実装側へのアクセスをランタイムに提供します。  
  
 `MyWhile` が `MySequence` と異なるのは、1 つの <xref:System.Activities.Activity> オブジェクトを繰り返しスケジュールし、`Condition` という名前の <xref:System.Activities.Activity%601>\<bool\> を使用して、そのスケジュールを実行するかどうかを判断することです。`MySequence` と同様に、`MyWhile` でも、`InternalExecute` メソッドを使用してスケジュール ロジックを集中化しています。`OnEvaluationCompleted` という名前の <xref:System.Activities.CompletionCallback%601>\<bool\> を使用して `Condition`<xref:System.Activities.Activity>\<bool\> をスケジュールします。`Condition` の実行が完了すると、その結果を、この <xref:System.Activities.CompletionCallback> を通じて、`result` という名前の厳密に型指定されたパラメーターで使用できるようになります。`true` の場合、`MyWhile` は <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> を呼び出し、<xref:System.Activities.CompletionCallback> として `Body`<xref:System.Activities.Activity> オブジェクトと `InternalExecute` を渡します。`Body` の実行が完了すると、`InternalExecute` でもう一度 `Condition` がスケジュールされ、再度ループが開始されます。`Condition` が `false` を返すと、`MyWhile` のインスタンスが `Body` をスケジュールせずに制御をランタイムに戻し、ランタイムによって状態が <xref:System.Activities.ActivityInstanceState> に変更されます。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で Composite.sln サンプル ソリューションを開きます。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`  
  
## 参照