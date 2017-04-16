---
title: "方法 : Windows フォーム上のコントロールを位置設定する | Microsoft Docs"
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
  - "Location"
  - "Location.Y"
  - "Location.X"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コントロール [Windows フォーム]"
  - "コントロール [Windows フォーム], 移動"
  - "コントロール [Windows フォーム], 配置"
  - "スナップ線"
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : Windows フォーム上のコントロールを位置設定する
コントロールを位置設定するには、Windows フォーム デザイナーを使用するか、<xref:System.Windows.Forms.Control.Location%2A> プロパティを指定します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### Windows フォーム デザイナーのデザイン サーフェイスに、コントロールを位置設定するには  
  
-   マウスを使用して、適切な位置にコントロールをドラッグします。  
  
    > [!NOTE]
    >  コントロールを選択し、方向キーを使用してさらに正確に位置設定します。  また、*スナップ線*は、コントロールをフォーム内に精密に配置するために役立ちます。  詳細については、「[チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)」を参照してください。  
  
### \[プロパティ\] ウィンドウを使用して、コントロールを位置設定するには  
  
1.  位置設定するコントロールをクリックします。  
  
2.  **\[プロパティ\]** ウィンドウで、コンマで区切った<xref:System.Windows.Forms.Control.Location%2A> プロパティの値を入力して、コンテナー内のコントロール位置を指定します。  
  
     数字 \(X\) は、コンテナーの左の境界線からの距離を表します。数字 \(Y\) は、コンテナー領域の上部の境界線からの距離を表します。このとき、ピクセル単位で数値が示されます。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Control.Location%2A> プロパティを展開して **\[X\]** 値および **\[Y\]** 値を個別に入力できます。  
  
### プログラムによって、コントロールを位置設定するには  
  
1.  コントロールの <xref:System.Windows.Forms.Control.Location%2A> プロパティを <xref:System.Drawing.Point> に設定します。  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <xref:System.Windows.Forms.Control.Left%2A> サブプロパティを使用して、コントロールの位置の X 座標を変更します。  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### プログラムによって、コントロールの位置をインクリメントするには  
  
1.  <xref:System.Windows.Forms.Control.Left%2A> サブプロパティを設定して、コントロールの X 座標をインクリメントします。  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  コントロールの X 座標および Y 座標を同時に設定するには、<xref:System.Windows.Forms.Control.Location%2A> プロパティを使用します。  位置をそれぞれ設定するには、コントロールの <xref:System.Windows.Forms.Control.Left%2A> \(**X**\) サブプロパティまたは <xref:System.Windows.Forms.Control.Top%2A> \(**Y**\) サブプロパティを使用します。  ボタンの位置を表す <xref:System.Drawing.Point> 構造体に含まれているのは、ボタンの座標のコピーであるため、X 座標および Y 座標を暗黙的に設定することはできません。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [チュートリアル : FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)   
 [How to: Set the Screen Location of Windows Forms](http://msdn.microsoft.com/ja-jp/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)