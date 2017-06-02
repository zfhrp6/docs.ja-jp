---
title: "方法 : デザイナーを使って ImageList イメージを追加または削除する | Microsoft Docs"
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
  - "ImageList コンポーネント [Windows フォーム], 追加 (イメージを)"
  - "ImageList コンポーネント [Windows フォーム], 削除 (イメージを)"
  - "イメージ [Windows フォーム], 追加 (ImageList コンポーネントに)"
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : デザイナーを使って ImageList イメージを追加または削除する
イメージを <xref:System.Windows.Forms.ImageList> コンポーネントに追加する方法はいくつかあります。  <xref:System.Windows.Forms.ImageList> に関連付けられているスマート タグを使うと、イメージをすばやく追加できます。また、他のプロパティを <xref:System.Windows.Forms.ImageList> に設定しているときは、\[プロパティ\] ウィンドウでイメージを簡単に追加できます。  コードを使ってイメージを追加することもできます。  コードを使ってイメージを追加する方法の詳細については、「[方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)」を参照してください。  通常は、<xref:System.Windows.Forms.ImageList> コンポーネントをコントロールに関連付ける前に、<xref:System.Windows.Forms.ImageList> コンポーネントにイメージを設定します。ただし、これは強制ではありません。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### \[プロパティ\] ウィンドウを使ってイメージを追加または削除するには  
  
1.  <xref:System.Windows.Forms.ImageList> コンポーネントを選択するか、フォームにコンポーネントを追加します。  
  
2.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.ImageList.Images%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  
  
3.  **Image コレクション エディター**の **\[追加\]** または **\[削除\]** をクリックしてリストからイメージを追加または削除します。  
  
### スマート タグを使ってイメージを追加または削除するには  
  
1.  <xref:System.Windows.Forms.ImageList> コンポーネントを選択するか、フォームにコンポーネントを追加します。  
  
2.  スマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックします。  
  
3.  **\[ImageList タスク\]** ダイアログ ボックスの **\[イメージの選択\]** を選択します。  
  
4.  **Image コレクション エディター**の **\[追加\]** または **\[削除\]** をクリックしてリストからイメージを追加または削除します。  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)   
 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)