---
title: "アクティビティ クラスを使用したワークフロー アクティビティの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# アクティビティ クラスを使用したワークフロー アクティビティの作成
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] で [!INCLUDE[wf](../../../includes/wf-md.md)] を使用してアクティビティを作成する最も基本的な方法は、カスタム アクティビティまたは [ビルトイン アクティビティ ライブラリ](../../../docs/framework/windows-workflow-foundation//net-framework-4-5-built-in-activity-library.md) のアクティビティをアセンブルして、機能を作成する <xref:System.Activities.Activity> から継承するクラスを作成することです。ここでは、2 つのメッセージをコンソールに書き込むアクティビティを作成する方法について説明します。  
  
### アクティビティ デザイナーを使ってカスタム アクティビティを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を開きます。  
  
2.  \[ファイル\]、\[新規作成\]、\[プロジェクト\] の順にクリックします。**\[プロジェクトの種類\]** ウィンドウの **\[Visual C\#\]** の下にある **\[ワークフロー 4.0\]** を選択し、**v2010 ノード**を選択します。**\[テンプレート\]** ウィンドウで **\[アクティビティ ライブラリ\]** をクリックします。新しいプロジェクトに HelloActivity という名前を付けます。  
  
3.  新しいアクティビティを開きます。<xref:System.Activities.Statements.Sequence> アクティビティをツールボックスからデザイナー画面にドラッグします。  
  
4.  <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。**テキスト** フィールドに「`"Hello World"`」\(引用符を含む\) と入力します。  
  
5.  2 つ目の <xref:System.Activities.Statements.WriteLine> アクティビティを、1 つ目の下にある <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。**テキスト** フィールドに「`"Goodbye"`」\(引用符を含む\) と入力します。