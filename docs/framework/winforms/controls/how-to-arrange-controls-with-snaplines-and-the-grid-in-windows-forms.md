---
title: "方法 : コントロールを Windows フォームのスナップ線とグリッドを使用して配置する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GridSize"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コントロール [Windows フォーム], エイリアスの使用"
  - "合わせる (グリッドに), Windows フォーム デザイナー"
  - "Windows フォーム, グリッド オプション (デザイナーの)"
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : コントロールを Windows フォームのスナップ線とグリッドを使用して配置する
[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] のレイアウト機能を使用すると、フォーム上のコントロールの配置場所を正確に指定できます。  フォームに追加したコントロールやフォーム上で移動したコントロールは、Windows フォーム デザイナーのグリッドの行と列に合わせて自動的に配置されます。また、スナップ線機能を使用してコントロールを配置することもできます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### すべてのコントロールをグリッドにスナップするには  
  
-   Windows フォーム デザイナーの **\[オプション\]** ダイアログ ボックスで、**\[SnapToGrid\]** レイアウト モードを選択します。  
  
     詳細については、「[General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8dd170af-72f0-4212-b04b-034ceee92834)」を参照してください。  グリッドのポイントに沿って、すべてのコントロールが配置されます。  
  
     所定の位置にコントロールをロックして、各コントロールをグリッドにスナップできます。  ただし、コントロールがロックされている間、コントロールを移動したりサイズ変更したりすることはできません。  コントロールのロックの詳細については、「[方法 : Windows フォームにコントロールをロックする](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md)」を参照してください。  
  
### スナップ線を使用してコントロールを配置するには  
  
-   Windows フォーム デザイナーの **\[オプション\]** ダイアログ ボックスで、**\[SnapLines\]** レイアウト モードを選択します。  
  
     詳細については、「[チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)」を参照してください。  これで、スナップ線を使用してフォーム上にコントロールを配置したり、並べ替えたりできます。  
  
## 参照  
 [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8dd170af-72f0-4212-b04b-034ceee92834)   
 [チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)