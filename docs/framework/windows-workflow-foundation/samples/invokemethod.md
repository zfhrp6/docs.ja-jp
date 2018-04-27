---
title: InvokeMethod
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f988f206fbd84b7b7d47fb3bd540420601ba30c9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="invokemethod"></a>InvokeMethod
このサンプルでは、<xref:System.Activities.Statements.InvokeMethod> アクティビティを使用してクラスのメソッドを呼び出すさまざまな方法を示します。  
  
 メソッドはクラスに属し、含まれる操作のセットを表します。 <xref:System.Activities.Statements.InvokeMethod> アクティビティを使用すると、オブジェクトまたは型に対してメソッドを呼び出し、パラメーターを渡して、戻り値を取得できます。 メソッドは、同期または非同期に呼び出すことができます。  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルでは、<xref:System.Activities.Statements.InvokeMethod> アクティビティを使用して次のシナリオを実行します。  
  
1.  パラメーターを指定せずにインスタンス メソッドを呼び出します。  
  
2.  2 つのパラメーター (<xref:System.String> と <xref:System.Int32>) を指定してインスタンス メソッドを呼び出します。  
  
3.  2 つのパラメーター (<xref:System.String> と <xref:System.Int32>) および <xref:System.String>[] 型のパラメーター配列を指定してインスタンス メソッドを呼び出します。  
  
4.  <xref:System.Int32> 型の 2 つのパラメーターおよび <xref:System.Int32> 型の結果を指定してインスタンス メソッドを呼び出します。 このシナリオでは、結果値は変数にバインドされ、別のアクティビティで使用されます。 この値は、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに表示されます。  
  
5.  <xref:System.String> 型と <xref:System.Int32> 型の 2 つのパラメーターを指定して静的メソッドを呼び出します。  
  
6.  <xref:System.String> 型の 1 つのジェネリック パラメーターを指定してインスタンス メソッドを呼び出します。  
  
7.  <xref:System.String> 型と <xref:System.Int32> 型の 2 つのジェネリック パラメーターを指定して静的メソッドを呼び出します。  
  
8.  <xref:System.String> 型の参照渡しされる 1 つのパラメーターを持つインスタンス メソッドを呼び出します。 このシナリオでは、参照パラメーターは変数 (`outParam`) にバインドされ、別のアクティビティで使用されます。 この値は、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに表示されます。  
  
9. 非同期インスタンス メソッドを呼び出します。  
  
10. 2 つの <xref:System.Activities.Statements.InvokeMethod> アクティビティを使用して、1 つのオブジェクトの同じインスタンスで 2 つの異なるメソッドを呼び出します。  
  
11. オブジェクトのインスタンスに値を格納します。  
  
12. オブジェクトのインスタンスから値を取得します。  
  
## <a name="to-use-this-sample"></a>このサンプルを使用するには  
 このサンプルには、2 つのバージョンが用意されています。 このサンプルの最初のバージョンは、の使用法を示しています<xref:System.Activities.Statements.InvokeMethod>c# コードから Windows Workflow Foundation (WF) のプログラミング モデルを使用して、Codedworkflow \cs フォルダーにあります。 第 2 のバージョンでは、XAML で <xref:System.Activities.Statements.InvokeMethod> を使用する方法を示します。これは、DesignerWorkflow\CS フォルダーにあります。  
  
#### <a name="to-run-the-coded-workflow-sample"></a>コード化されたワークフロー サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CodedWorkflow\CS フォルダーにある InvokeMethodUsage.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
#### <a name="to-run-the-designer-workflow-sample"></a>デザイナー ワークフロー サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、DesignerWorkflow\CS フォルダーにある InvokeMethodUsage.sln ソリューション ファイルを開きます。  
  
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