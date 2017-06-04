---
title: "WorkflowInvoker クラスの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# WorkflowInvoker クラスの使用
このサンプルでは、<xref:System.Activities.WorkflowInvoker> クラスを使用して、メソッドのようにアクティビティを呼び出す方法を示します。  
  
## サンプルの詳細  
 アクティビティを実行するための最も簡単な方法は、<xref:System.Activities.WorkflowInvoker> クラスを使用する方法です。このクラスは、メソッドを呼び出すようにアクティビティを直接実行することを目的として設計されています。このクラスは、軽量で高性能な、使いやすい API で、アクティビティを実行する際に他のホスティングのバリエーションが提供する制御インフラストラクチャを必要としないシナリオで使用できます。  
  
 このサンプルは、2 つの <xref:System.Activities.InArgument%601> \(`X` および `Y`\) を追加する `Add` という名前の <xref:System.Activities.CodeActivity%601>\<Int32\> から派生したカスタム アクティビティを使用し、`Result`<xref:System.Activities.OutArgument%601> を返します \(`Result` という名前の <xref:System.Activities.OutArgument%601>\<T\> を持つ <xref:System.Activities.Activity%601>\<T\> から派生した <xref:System.Activities.CodeActivity%601>\<T\>\)。`Dictionary`\<文字列、オブジェクト\> は、<xref:System.Activities.WorkflowInvoker> を介して呼び出されるアクティビティに引数を渡すために使用されます。ディクショナリのキーは、呼び出し先のアクティビティにおける引数名に対応します。特定のキーに関連付けられた値は、キーによって識別される引数にバインドされます。  
  
 このサンプルは、<xref:System.Activities.WorkflowInvoker.Invoke%2A> を呼び出して、`X` および `Y` の値を含むディクショナリを渡します。<xref:System.Activities.WorkflowInvoker> クラスは、これらの値を `Add` アクティビティの引数にバインドし、アクティビティを実行して、結果を返します。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、Invoker.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`  
  
## 参照