---
title: "モデル アイテム ツリーのプログラミング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# モデル アイテム ツリーのプログラミング
このサンプルでは、[!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] ツリー ビューの宣言型データ バインディングを使用して <xref:System.Activities.Presentation.Model.ModelItem> ツリーを操作する方法を示します。  
  
## サンプルの詳細  
 <xref:System.Activities.Presentation.Model.ModelItem> ツリーは、編集する基のインスタンスに関するデータを公開するために [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] のインフラストラクチャで使用される抽象表現です。次の図は、[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]のインフラストラクチャのさまざまな層を表しています。  
  
 ![ワークフロー デザイナーのアーキテクチャ](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 <xref:System.Activities.Presentation.Model.ModelItem> は、基になる値へのポインターと、<xref:System.Activities.Presentation.Model.ModelProperty> オブジェクトのコレクションで構成されています。<xref:System.Activities.Presentation.Model.ModelProperty> オブジェクトはさらに、プロパティの名前や型などのデータと、また別の <xref:System.Activities.Presentation.Model.ModelItem> である値へのポインターで構成されています。<xref:System.Activities.Presentation.Model.ModelProperty> から返される一部の <xref:System.Activities.Presentation.Model.ModelItem> に対しては、ツリー ビューに正しく表示されるように操作するために値コンバーターが使用されます。このサンプルでは、次の例のような命令構文を使用して <xref:System.Activities.Presentation.Model.ModelItem> ツリーを命令型プログラミングで操作する方法を示します。  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
  
```  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ProgrammingModelItemTree.sln ソリューションを開きます。  
  
2.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックして、ソリューションをビルドします。  
  
3.  F5 キーを押してアプリケーションを実行します。[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] フォームが表示されます。  
  
4.  **\[Load WF\]** ボタンをクリックして <xref:System.Activities.Presentation.Model.ModelItem> を読み込み、ツリー ビューにバインドします。  
  
5.  **\[Change Model Item Tree\]** ボタンをクリックして先ほどのコードを実行して、ツリーにアイテムを追加してプロパティを設定します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## 参照  
 <xref:System.Windows.Data.IValueConverter>