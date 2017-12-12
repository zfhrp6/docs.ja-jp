---
title: "動的引数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 582f8815bd121199e564af7d1806f2e76f4595cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="dynamic-arguments"></a>動的引数
このサンプルでは、アクティビティの作成者ではなくアクティビティのコンシューマーによって引数が定義されるアクティビティの実装方法を示します。 ここではそのために、ランタイムによるアクティビティのメタデータの構築方法をオーバーライドします。  
  
## <a name="sample-details"></a>サンプルの詳細  
 ランタイムは、実行前にアクティビティの記述を構築します。これは、アクティビティ型のパブリック メンバーを調べて、引数、変数、子アクティビティ、およびアクティビティ デリゲートをアクティビティのメタデータの一部として自動的に宣言することによって行われます。 これにより、ワークフローが正しく構築されるようにすると同時に、ランタイム リレーションシップおよび有効期間ルールを管理します。 通常は、アクティビティの作成者が、<xref:System.Activities.Argument> から派生するパブリック メンバーをアクティビティ型で指定することによってアクティビティの引数を定義します。 ランタイムにより、<xref:System.Activities.Argument> から派生する各パブリック メンバーに対して <xref:System.Activities.RuntimeArgument> が作成され、そのメンバーに対してユーザーが指定した引数にバインドされます。 しかし、アクティビティのコンシューマーが指定する構成によって引数のセットが決まる場合もあります。 アクティビティの作成者がアクティビティのメタデータ (アクティビティに関連付けられる引数のセットを含む) の構築方法をカスタマイズするには、<xref:System.Activities.Activity.CacheMetadata%2A> をオーバーライドします。  
  
 このサンプルでは、メソッドを呼び出すアクティビティの引数リストを動的に構築する方法を示します。 アクティビティのコンシューマーが、型および呼び出すメソッドの名前を、そのメソッドに渡す引数のコレクションと共に指定します。  
  
> [!NOTE]
>  このサンプルの目的は、<xref:System.Activities.CodeActivity.CacheMetadata%2A> をオーバーライドする方法と、<xref:System.Activities.RuntimeArgument> を使用する方法を示すことです。 このアクティビティで呼び出すことのできるメソッドの種類に関しては、いくつかの注意事項があります。 たとえば、ジェネリックやパラメーター配列は使用できません。 .NET Framework に含まれている <xref:System.Activities.Statements.InvokeMethod> アクティビティにはこのような制限はありません。  
  
 `MethodInvoke` をオーバーライドする <xref:System.Activities.CodeActivity.CacheMetadata%2A> アクティビティは、まず最初に、メソッド呼び出しの結果を処理するための <xref:System.Activities.RuntimeArgument> を作成し、 <xref:System.Activities.RuntimeArgument> という名前のパブリックに設定可能な <xref:System.Activities.OutArgument> にバインドします `Result`。 `MethodInvoke.Result` が `null` の場合は、その型の既定の式で構成された <xref:System.Activities.OutArgument> が自動的に設定されるため、 引数のプロパティが `null` かどうかをアクティビティの作成者が確認する必要はありません。  
  
 次に、<xref:System.Activities.CodeActivity.CacheMetadata%2A> のオーバーライドにより、ユーザーによって指定された `MethodInfo` および `MethodName` から、呼び出しに使用する `TargetType` が特定されます。 `DetermineMethodInfo` メソッドは、<xref:System.Activities.CodeActivityMetadata> のオーバーライドに渡された <xref:System.Activities.CodeActivity.CacheMetadata%2A> パラメーターを受け取るため、構成エラーがあった場合には検証エラーとして報告できます。 これは、`metadata.AddValidationError` を呼び出すことによって行われます。  
  
 `MethodInfo` が設定されると、`MethodInfo` のパラメーターが反復処理されて、 各パラメーターに対して <xref:System.Activities.RuntimeArgument> が作成され、`Parameters` プロパティのユーザーが指定したコレクションの対応する引数にバインドされます。 最後に、<xref:System.Activities.RuntimeArgument> が呼び出されて、`metadata.SetArgumentsCollection` のコレクションがアクティビティに関連付けられます。  
  
 引数の解決には、<xref:System.Activities.RuntimeArgument> の場合のように `resultArgument` を使用することも、`Parameters` コレクションの場合のようにユーザーが指定した引数を使用することもできます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、DynamicArguments.sln ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`