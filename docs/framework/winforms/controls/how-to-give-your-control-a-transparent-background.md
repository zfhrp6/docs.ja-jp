---
title: "方法 : コントロールに透明な背景を指定する | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], 透明な背景"
  - "透明度, Windows フォーム カスタム コントロール"
  - "透明な背景, カスタム コントロール"
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 方法 : コントロールに透明な背景を指定する
.NET Framework の従来のバージョンでは、あらかじめフォームのコンストラクターに <xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを設定しておかないと、透明な背景色を設定できませんでした。 フレームワークの現在のバージョンでは、ほとんどのコントロールの背景色を、設計時に **\[プロパティ\]** ウィンドウで、またはフォームのコンストラクターのコードで、<xref:System.Drawing.Color.Transparent%2A> に設定できます。  
  
> [!NOTE]
>  Windows フォーム コントロールは、完全な透過性はサポートしていません。 透明な Windows フォーム コントロールの背景は、その親によって描画されます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ButtonBase.BackColor%2A> プロパティが <xref:System.Drawing.Color.Transparent%2A> に設定されている場合でも、<xref:System.Windows.Controls.Button> コントロールは透明な背景をサポートしません。  
  
### コントロールに透明な背景を設定するには  
  
-   \[プロパティ\] ウィンドウで <xref:System.Windows.Forms.ButtonBase.BackColor%2A> プロパティを選択し、<xref:System.Drawing.Color.Transparent%2A> に設定します。  
  
## 参照  
 <xref:System.Drawing.Color.FromArgb%2A>   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [マネージ グラフィックス クラスの使用](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)   
 [方法 : 不透明な直線および半透明な直線を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)