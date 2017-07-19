---
title: "方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する | Microsoft Docs"
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
  - "例 [Windows フォーム], ツールヒント"
  - "ツールヒント [Windows フォーム], コントロールの"
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する
<xref:System.Windows.Forms.ToolTip> 文字列はコード、または Windows フォーム デザイナーで設定できます。  <xref:System.Windows.Forms.ToolTip> コンポーネントの詳細については、「[ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### プログラムによってツールヒントを設定するには  
  
1.  ツールヒントを表示するコントロールを追加します。  
  
2.  <xref:System.Windows.Forms.ToolTip> コンポーネントの <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> メソッドを使用します。  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### デザイナーでツールヒントを設定するには  
  
1.  フォームに <xref:System.Windows.Forms.ToolTip> コンポーネントを追加します。  
  
2.  ツールヒントを表示するコントロールを選択するか、フォームにコントロールを追加します。  
  
3.  **\[プロパティ\]** ウィンドウで、**\[ToolTip1 の ToolTip\]** の値を適切な文字列に設定します。  
  
## 参照  
 [ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)   
 [方法 : Windows フォームの ToolTip コンポーネントの遅延時間を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)   
 [ToolTip コンポーネント](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)