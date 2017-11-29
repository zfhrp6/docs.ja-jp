---
title: "CommentOut アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: df5faa2aacf6b86d708dad4b157b27d2609a0a93
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="commentout-activity"></a>CommentOut アクティビティ
このサンプルでは、実行のパスから他のアクティビティを削除し、それらを有効にコメント化するカスタム アクティビティを記述する方法を示します。  
  
## <a name="the-commentout-activity"></a>CommentOut アクティビティ  
 CommentOut アクティビティでは、目標を達成するために、<xref:System.Activities.CodeActivity> 基本クラスを継承し、空の <xref:System.Activities.CodeActivity.Execute%2A> メソッドを実装します。  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 クラスは次の例のように宣言されます。  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 `Designer` 属性は、デザイン時にアクティビティのビジュアル インターフェイスを実装するクラスを指定します。 `ContentProperty` 属性は、このアクティビティのインスタンスの XAML 表現で `"Body"` プロパティを省略できることを宣言します。  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 デザイナー クラスでは、XAML はアクティビティのカスタム ビジュアル表現を作成するために使用されます。 <xref:System.Activities.Presentation.WorkflowItemPresenter> はビジュアル エディターを提供するクラスです。  
  
 `CommentOut` アクティビティ サーフェイス上には、1 つのアクティビティをドロップできます。 このサーフェイスに複数のアクティビティを追加する場合は、最初にシーケンス アクティビティをここにドラッグします。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で CommentOut.sln を開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをコンパイルします。  
  
3.  Ctrl キーを押しながら F5 キーを押して、サンプルをデバッグなしで開始します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
