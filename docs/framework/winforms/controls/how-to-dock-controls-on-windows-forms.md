---
title: "方法 : Windows フォーム上のコントロールをドッキングする | Microsoft Docs"
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
  - "コントロール [Windows フォーム], ドッキング"
  - "Dock プロパティ"
  - "エクスプローラー スタイル アプリケーション, 作成"
  - "Windows フォーム コントロール, 設定 (クライアント領域を)"
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォーム上のコントロールをドッキングする
フォームの端にコントロールをドッキングしたり、コントロールのコンテナー \(フォームまたはコンテナー コントロール\) にコントロールを挿入したりできます。  たとえば、Windows エクスプローラーでは、ウィンドウの左側に <xref:System.Windows.Forms.TreeView> コントロールが、ウィンドウの右側に <xref:System.Windows.Forms.ListView> コントロールがドッキングされています。  表示されているすべての Windows フォーム コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティを使用して、ドッキング モードに設定します。  
  
> [!NOTE]
>  コントロールは反転した z オーダーでドッキングされます。  
  
 <xref:System.Windows.Forms.Control.Dock%2A> プロパティは <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティとやり取りします。  詳細については、「[AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)」を参照してください。  
  
### コントロールをドッキングするには  
  
1.  ドッキングするコントロールを選択します。  
  
2.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.Control.Dock%2A> プロパティの右にある矢印をクリックします。  
  
     エディターが開き、フォームの端と中央を表す一連のボックスが表示されます。  
  
3.  コントロールをドッキングするフォームの端を表すボタンをクリックします。  コントロールのフォームまたはコンテナー コントロールの内容を入力するには、中央のボックスをクリックします。  **\[None\]** をクリックすると、ドッキングは無効になります。  
  
     コントロールは、ドッキングされた端の境界線に合わせて、自動的にサイズ変更されます。  
  
    > [!NOTE]
    >  継承したコントロールをドッキングできるようにするには、`Protected` にする必要があります。  コントロールのアクセス レベルを変更するには、\[プロパティ\] ウィンドウで **Modifier** プロパティを設定します。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)   
 [方法 : FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [方法 : Windows フォームにコントロールを固定する](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)