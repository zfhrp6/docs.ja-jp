---
title: "方法 : Windows フォームにコントロールを固定する | Microsoft Docs"
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
  - "Anchor プロパティ, 有効化 (サイズ変更可能なフォーム)"
  - "コントロール [Windows フォーム], 固定"
  - "コントロール [Windows フォーム], 配置"
  - "フォーム, サイズ変更"
  - "サイズ変更 (フォームを)"
  - "画面の解像度とコントロールの表示"
  - "Windows フォーム コントロール, 画面の解像度"
  - "Windows フォーム コントロール, サイズ"
  - "Windows フォーム, サイズ変更"
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Windows フォームにコントロールを固定する
実行時にユーザーがサイズ変更できるフォームをデザインする場合は、フォームのコントロールが適切にサイズ変更され、再配置されるようにする必要があります。  フォームでコントロールのサイズを動的に変更するには、Windows フォーム コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティを使用します。  <xref:System.Windows.Forms.Control.Anchor%2A> プロパティでは、コントロールの固定位置を定義します。  コントロールをフォームに固定し、フォームをサイズ変更する場合は、コントロールと固定位置の距離が保持されます。  たとえば、フォームの左端、右端、および下端に固定している <xref:System.Windows.Forms.TextBox> コントロールがあるとします。フォームをサイズ変更すると、<xref:System.Windows.Forms.TextBox> コントロールは水平方向にサイズ変更され、フォームの左右の端からの距離が保持されます。  また、フォームの下端からの距離が常に保持されるように、コントロール自体が垂直方向に再配置されます。  コントロールを固定せず、フォームをサイズ変更しない場合は、フォームの端からのコントロールの位置が変更されます。  
  
 <xref:System.Windows.Forms.Control.Anchor%2A> プロパティは <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティとやり取りします。  詳細については、「[AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### フォームにコントロールを固定するには  
  
1.  固定するコントロールを選択します。  
  
    > [!NOTE]
    >  複数のコントロールを同時に固定できます。これを行うには、Ctrl キーを押しながら各コントロールをクリックして選択し、以降の手順を実行します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティの右にある矢印をクリックします。  
  
     エディターにクロスが表示されます。  
  
3.  アンカーを設定するには、クロスの上、下、左、右のいずれかの部分をクリックします。  
  
     既定では、コントロールが上と左に固定されます。  
  
4.  アンカー設定を無効にするには、クロスの該当するアームをクリックします。  
  
5.  <xref:System.Windows.Forms.Control.Anchor%2A> プロパティ エディターを閉じるには、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティ名をもう一度クリックします。  
  
 実行時にフォームが表示されると、フォームの端からの距離を保持するために、コントロールのサイズが変更されます。  固定された端からの距離は、Windows フォーム デザイナーでコントロールを配置したときに定義した距離と常に等しくなります。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ComboBox> コントロールなどの特定のコントロールでは、高さが制限されています。  フォームまたはコンテナーの下端にコントロールを固定する場合、制限された高さよりコントロールを高くすることはできません。  
  
 継承したコントロールを固定できるようにするには、`Protected` にする必要があります。  コントロールのアクセス レベルを変更するには、**\[プロパティ\]** ウィンドウで `Modifiers` プロパティを設定します。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [方法 : Windows フォーム上のコントロールをドッキングする](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [チュートリアル : FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)