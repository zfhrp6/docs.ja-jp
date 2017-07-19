---
title: "InvokeMethod アクティビティの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# InvokeMethod アクティビティの使用
このサンプルでは、<xref:System.Activities.Statements.InvokeMethod%601> アクティビティを使用してパブリック クラス内のパブリック メソッドを呼び出す方法を示します。<xref:System.Activities.Statements.InvokeMethod%601> アクティビティを使用すると、ワークフローでオブジェクトに対してメソッドを呼び出し、パラメーターを渡して、戻り値を取得し、ジェネリック メソッドの型を指定し、メソッドが同期または非同期のどちらであるかを指定できます。  
  
 <xref:System.Activities.Statements.InvokeMethod> アクティビティの非ジェネリック バージョンでは、戻り値が <xref:System.Activities.Statements.InvokeMethod.Result%2A> プロパティに設定され、<xref:System.Activities.Statements.InvokeMethod%601> アクティビティのジェネリック バージョンでは、戻り値が `TResult` 型の <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> プロパティを通じて返されます。  
  
 このサンプルでは、さまざまな型のメソッドの呼び出し方法を示します。次に、このサンプルに示されているメソッドの型の詳細を示します。  
  
-   パラメーターを指定せずにインスタンス メソッドを呼び出します。  
  
-   2 つのパラメーター \(System.String および System.Int32\) を指定してインスタンス メソッドを呼び出します。  
  
-   2 つのパラメーター \(System.String および System.Int32\) と、型 System.String\[\] のパラメーター配列を指定してインスタンス メソッドを呼び出します。  
  
-   2 つのパラメーター \(2 つの System.Int32 数値\) および System.Int32 型の結果を指定してインスタンス メソッドを呼び出します。  
  
     戻り値は変数にバインドされ、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに出力されます。  
  
-   2 つのパラメーター \(System.String および System.Int32\) を指定して静的メソッドを呼び出します。  
  
-   1 つのジェネリック パラメーター \(System.String\) を指定してインスタンス メソッドを呼び出します。  
  
-   2 つのジェネリック パラメーター \(System.String および System.Int32\) を指定して静的メソッドを呼び出します。  
  
-   参照渡しされる 1 つのパラメーター \(System.String\) を持つインスタンス メソッドを呼び出します。  
  
     参照されているパラメーターは変数にバインドされ、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに出力されます。  
  
-   非同期インスタンス メソッドを呼び出します。  
  
## このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、InvokeMethodUsage.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`  
  
## 参照