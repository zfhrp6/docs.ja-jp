---
title: "アクティビティ クラスを使用したワークフロー アクティビティの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f4fc6d0807c07952e9b3abe2861ef04bc225142f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>アクティビティ クラスを使用したワークフロー アクティビティの作成
使用して、アクティビティを作成する最も簡単な方法[!INCLUDE[wf](../../../includes/wf-md.md)]で[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]から継承するクラスを作成するのには、<xref:System.Activities.Activity>を作成する機能をまとめることでカスタム アクティビティまたはアクティビティから、[ビルトイン アクティビティ ライブラリ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). ここでは、2 つのメッセージをコンソールに書き込むアクティビティを作成する方法について説明します。  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>アクティビティ デザイナーを使ってカスタム アクティビティを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を開きます。  
  
2.  [ファイル]、[新規作成]、[プロジェクト] の順にクリックします。 選択**Workflow 4.0**  **Visual c#**で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。 選択**アクティビティ ライブラリ**で、**テンプレート**ウィンドウです。 新しいプロジェクトに HelloActivity という名前を付けます。  
  
3.  新しいアクティビティを開きます。  <xref:System.Activities.Statements.Sequence> アクティビティをツールボックスからデザイナー画面にドラッグします。  
  
4.  <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。 入力`"Hello World"`(引用符を含む) に、**テキスト**フィールドです。  
  
5.  2 つ目の <xref:System.Activities.Statements.WriteLine> アクティビティを、1 つ目の下にある <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。 入力`"Goodbye"`(引用符を含む) に、**テキスト**フィールドです。
