---
title: アクティビティ クラスを使用したワークフロー アクティビティの作成
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 040fe777e332efdfb296e6fb6565935f466ded71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>アクティビティ クラスを使用したワークフロー アクティビティの作成
最も基本的な方法で Windows Workflow Foundation (WF) を使用してアクティビティを作成する[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]から継承するクラスを作成するのには、<xref:System.Activities.Activity>を作成する機能をまとめることでカスタム アクティビティまたはアクティビティから、[組み込みアクティビティ ライブラリ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)です。 ここでは、2 つのメッセージをコンソールに書き込むアクティビティを作成する方法について説明します。  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>アクティビティ デザイナーを使ってカスタム アクティビティを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を開きます。  
  
2.  [ファイル]、[新規作成]、[プロジェクト] の順にクリックします。 選択**Workflow 4.0**  **Visual c#** で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。 選択**アクティビティ ライブラリ**で、**テンプレート**ウィンドウです。 新しいプロジェクトに HelloActivity という名前を付けます。  
  
3.  新しいアクティビティを開きます。  <xref:System.Activities.Statements.Sequence> アクティビティをツールボックスからデザイナー画面にドラッグします。  
  
4.  <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。 入力`"Hello World"`(引用符を含む) に、**テキスト**フィールドです。  
  
5.  2 つ目の <xref:System.Activities.Statements.WriteLine> アクティビティを、1 つ目の下にある <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。 入力`"Goodbye"`(引用符を含む) に、**テキスト**フィールドです。
