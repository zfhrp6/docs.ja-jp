---
title: "方法 : Windows フォーム TabControl の表示形式を変更する | Microsoft Docs"
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
  - "ボタン, 表示 (タブを)"
  - "アイコン, 表示 (タブに)"
  - "TabControl コントロール [Windows フォーム], 変更 (ページの表示形式を)"
  - "タブ, 制御 (外観を)"
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム TabControl の表示形式を変更する
Windows フォーム内のタブの表示形式は、コントロールの各タブを構成する <xref:System.Windows.Forms.TabControl> オブジェクトおよび <xref:System.Windows.Forms.TabPage> オブジェクトのプロパティを使用して変更できます。  これらのプロパティを設定することにより、タブ上にイメージを表示したり、タブを横ではなく縦に並べたり、タブを複数の行に表示したり、プログラムによってタブを有効または無効にしたりできます。  
  
### タブのラベル部分にアイコンを表示するには  
  
1.  フォームに <xref:System.Windows.Forms.ImageList> コントロールを追加します。  
  
2.  イメージ リストにイメージを追加します。  
  
     イメージ リストの詳細については、「[ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)」および「[方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)」を参照してください。  
  
3.  <xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.ImageList%2A> プロパティを <xref:System.Windows.Forms.ImageList> コントロールに設定します。  
  
4.  <xref:System.Windows.Forms.TabPage> の <xref:System.Windows.Forms.TabPage.ImageIndex%2A> プロパティをリスト内の適切なイメージのインデックスに設定します。  
  
### タブを複数の行に表示するには  
  
1.  必要な数のタブ ページを追加します。  
  
2.  <xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.Multiline%2A> プロパティを `true` に設定します。  
  
3.  これでもタブが複数の行に表示されない場合は、<xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.Control.Width%2A> プロパティの値をすべてのタブの合計幅よりも小さい値に設定します。  
  
### タブをコントロールの横側に配置するには  
  
-   <xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.Alignment%2A> プロパティを <xref:System.Windows.Forms.TabAlignment> または <xref:System.Windows.Forms.TabAlignment> に設定します。  
  
### タブのすべてのコントロールをプログラムによって有効または無効にするには  
  
1.  <xref:System.Windows.Forms.TabPage> の <xref:System.Windows.Forms.TabPage.Enabled%2A> プロパティを `true` または `false` に設定します。  
  
    ```vb  
    TabPage1.Enabled = False  
  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### タブをボタンとして表示するには  
  
-   <xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.Appearance%2A> プロパティを <xref:System.Windows.Forms.TabAppearance> または <xref:System.Windows.Forms.TabAppearance> に設定します。  
  
## 参照  
 [TabControl コントロール](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)   
 [TabControl コントロールの概要](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [方法 : タブ ページにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [方法 : タブ ページを無効化する](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [方法 : Windows フォーム TabControl のタブを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)