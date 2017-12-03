---
title: "InvokeMethod アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0c2333c14eaebdb6409323bb6b92aa2b29d2ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokemethod-activity"></a>InvokeMethod アクティビティの使用
このサンプルを使用する方法を示します、 <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)パブリック クラス内のパブリック メソッドを呼び出すアクティビティ。 <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)アクティビティにより、ワークフローをオブジェクトに対してメソッドを呼び出して、パラメーターを渡す、戻り値を取得、ジェネリック メソッドの型を指定し、メソッドは同期型かどうかを指定または非同期です。 
  
非ジェネリック バージョンがある、<xref:System.Activities.Statements.InvokeMethod>アクティビティに戻り値が設定されている、<xref:System.Activities.Statements.InvokeMethod.Result%2A>プロパティと、ジェネリック バージョンの<!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)アクティビティの戻り値が返されますを介して、 <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx)型のプロパティ`TResult`です。 
  
 このサンプルでは、さまざまな型のメソッドの呼び出し方法を示します。 次に、このサンプルに示されているメソッドの型の詳細を示します。  
  
-   パラメーターを指定せずにインスタンス メソッドを呼び出します。  
  
-   2 つのパラメーター (System.String および System.Int32) を指定してインスタンス メソッドを呼び出します。  
  
-   2 つのパラメーター (System.String および System.Int32) と、型 System.String[] のパラメーター配列を指定してインスタンス メソッドを呼び出します。  
  
-   2 つのパラメーター (2 つの System.Int32 数値) および System.Int32 型の結果を指定してインスタンス メソッドを呼び出します。  
  
     戻り値は変数にバインドされ、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに出力されます。  
  
-   2 つのパラメーター (System.String および System.Int32) を指定して静的メソッドを呼び出します。  
  
-   1 つのジェネリック パラメーター (System.String) を指定してインスタンス メソッドを呼び出します。  
  
-   2 つのジェネリック パラメーター (System.String および System.Int32) を指定して静的メソッドを呼び出します。  
  
-   参照渡しされる 1 つのパラメーター (System.String) を持つインスタンス メソッドを呼び出します。  
  
     参照されているパラメーターは変数にバインドされ、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに出力されます。  
  
-   非同期インスタンス メソッドを呼び出します。  
  
## <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、InvokeMethodUsage.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`