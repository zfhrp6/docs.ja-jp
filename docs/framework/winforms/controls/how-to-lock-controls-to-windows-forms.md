---
title: "方法 : Windows フォームにコントロールをロックする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コントロール [Windows フォーム], locking"
  - "Windows フォーム コントロール, locking"
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォームにコントロールをロックする
Windows アプリケーションのユーザー インターフェイス \(UI\) をデザインする場合、コントロールを正しく配置した後、他のプロパティを設定するときに誤って移動やサイズ変更をしないようにコントロールをロックできます。  
  
 また、フォームのすべてのコントロールを一度にロック、またはロック解除することもできます。フォームに数多くのコントロールがある場合は、一度にロックすると便利です。コントロールのロックを個々に解除することもできます。  フォームの任意の位置にコントロールを配置した後、誤って移動しないようにすべてのコントロールを適切な位置にロックします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールをロックするには  
  
1.  **\[プロパティ\]** ウィンドウの **\[更新しない\]** プロパティをクリックし、`true` を選択します。  名前をダブルクリックすると、プロパティの設定値が切り替わります。  
  
     または、コントロールを右クリックし、**\[コントロールのロック\]** をクリックします。  
  
    > [!NOTE]
    >  コントロールをロックすると、デザイン サーフェイス上でコントロールをドラッグしてサイズや位置を変更できなくなります。  ただし、**\[プロパティ\]** ウィンドウで設定したりコードを書き換えたりすることで、コントロールのサイズや位置を変更できます。  
  
### フォームのすべてのコントロールをロックするには  
  
1.  **\[書式\]** メニューの **\[コントロールのロック\]** をクリックします。  
  
    > [!NOTE]
    >  フォームはコントロールであるため、\[コントロールのロック\] によってフォームのサイズもロックされます。  
  
### フォームのすべてのコントロールのロックを解除するには  
  
1.  **\[書式\]** メニューの **\[コントロールのロック\]** をクリックします。  
  
     フォーム上でロックされているコントロールはすべてロックが解除されます。  
  
### コントロールのロックを個別に解除するには  
  
1.  **\[プロパティ\]** ウィンドウの **\[更新しない\]** プロパティをクリックし、`false` を選択します。  名前をダブルクリックすると、プロパティの設定値が切り替わります。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)