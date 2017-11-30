---
title: "カスタム アクティビティ デザイナーでの ExpressionTextBox の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41a5d5645f66f69fd267b75359d0c74952b7b4bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>カスタム アクティビティ デザイナーでの ExpressionTextBox の使用
このサンプルでは、カスタム アクティビティ デザイナーで <xref:System.Activities.Presentation.View.ExpressionTextBox> を使用する方法を示します。 カスタム アクティビティ `MultiAssign` は、2 つの文字列値を 2 つの文字列変数に割り当てます。 <xref:System.Activities.Presentation.View.ExpressionTextBox> コントロールには、<xref:System.Activities.InArgument> にバインドされるものと <xref:System.Activities.OutArgument> にバインドされるものがあります。  
  
## <a name="sample-details"></a>サンプルの詳細  
 `ArgumentToExpressionConverter` は、式を引数にバインドするときに使用される型コンバーターです。 `ConverterParameter` は、必要に応じて、`In` または `Out` に設定する必要があります。 `InOut` がサポートされていません。  
  
 `UseLocationExpression`属性を使用`OutArgument`の式が左辺値 (「左辺値」または「位置値」) 式を指定する必要がありますを指定します。 ほとんど場合、L 値式は、返される `OutArgument` が変数または引数の名前であることを示すために使用される有効な Visual Basic 識別子です。  
  
 この例では、`MaxLines` 属性は 1 に設定され、`MinLines` は設定されていません。 つまり、ユーザーによって入力されるテキストの量に関係なく、<xref:System.Activities.Presentation.View.ExpressionTextBox> のサイズが 1 行に固定されることを示しています。 <xref:System.Activities.Presentation.View.ExpressionTextBox> がユーザーの入力に合わせて拡大されるようにするには、`MaxLines` に `MinLines` より大きい値を設定します。  
  
 ExpressionTextBox は、引数にのみバインドできます。CLR プロパティにはバインドできません。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ExpressionTextBoxSample.sln ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
#### <a name="to-run-this-sample"></a>このサンプルを実行するには  
  
1.  新しいワークフロー コンソール アプリケーションをソリューションに追加します。  
  
2.  参照を追加、 **ExpressionTextBoxSample**新しいワークフロー コンソール アプリケーション プロジェクトからプロジェクト。  
  
3.  ソリューションをビルドします。  
  
4.  ドラッグ、 **MultiAssign**アクティビティをツールボックスし、ワークフローにドロップします。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [ワークフロー デザイナーを使用したアプリケーションの開発](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
