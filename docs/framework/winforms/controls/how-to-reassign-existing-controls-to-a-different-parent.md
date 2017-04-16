---
title: "方法 : 既存のコントロールを別の親に再配置する | Microsoft Docs"
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
  - "コンテナー コントロール、Windows フォーム"
  - "レイアウト [Windows フォーム]、サイズ変更"
  - "レイアウト [Windows フォーム]、子コントロール"
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 既存のコントロールを別の親に再配置する
フォームに存在するコントロールを新しいコンテナー コントロールに割り当てることができます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 既存のコントロールを別の親に再配置するには  
  
1.  **\[ツールボックス\]** から 3 つの <xref:System.Windows.Forms.Button> コントロールをフォームにドラッグします。  
  
     これらを互いに近づけて配置しますが、整列はさせません。  
  
2.  **\[ツールボックス\]** で <xref:System.Windows.Forms.FlowLayoutPanel> コントロール アイコンをクリックします。  
  
     アイコンはフォームにドラッグしないでください。  
  
3.  マウス ポインターを 3 つの <xref:System.Windows.Forms.Button> コントロールに近づけます。  
  
     ポインターが <xref:System.Windows.Forms.FlowLayoutPanel> コントロール アイコンが付いた十字カーソルに変わります。  
  
4.  マウス ボタンを押したままにします。  
  
5.  マウス ポインターをドラッグして、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールのアウトラインを描画します。  
  
6.  3 つの <xref:System.Windows.Forms.Button> コントロールを囲むようにアウトラインを描画します。  
  
7.  マウスのボタンを離します。  
  
     これで、3 つの <xref:System.Windows.Forms.Button> コントロールが <xref:System.Windows.Forms.FlowLayoutPanel> コントロールに挿入されました。  
  
## 参照  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)