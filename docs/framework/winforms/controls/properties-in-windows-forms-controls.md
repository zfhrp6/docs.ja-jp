---
title: "Windows フォーム コントロールのプロパティ | Microsoft Docs"
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
  - "コントロール [Windows フォーム], プロパティ"
  - "カスタム コントロール [Windows フォーム], プロパティの概要 (コードを使用)"
  - "プロパティ [Windows フォーム]"
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Windows フォーム コントロールのプロパティ
Windows フォーム コントロールは、基本クラス <xref:System.Windows.Forms.Control?displayProperty=fullName> から数多くのプロパティを継承しています。  こうしたプロパティには、<xref:System.Windows.Forms.Control.Font%2A>、<xref:System.Windows.Forms.Control.ForeColor%2A>、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.Bounds%2A>、<xref:System.Windows.Forms.Control.ClientRectangle%2A>、<xref:System.Windows.Forms.Control.DisplayRectangle%2A>、<xref:System.Windows.Forms.Control.Enabled%2A>、<xref:System.Windows.Forms.Control.Focused%2A>、<xref:System.Windows.Forms.Control.Height%2A>、<xref:System.Windows.Forms.Control.Width%2A>、<xref:System.Windows.Forms.Control.Visible%2A>、<xref:System.Windows.Forms.Control.AutoSize%2A> などがあります。  継承されるプロパティの詳細については、<xref:System.Windows.Forms.Control?displayProperty=fullName> に関するトピックを参照してください。  
  
 コントロールに継承されたプロパティをオーバーライドしたり、新しいプロパティを定義したりできます。  
  
## このセクションの内容  
 [プロパティの定義](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 カスタム コントロールまたはカスタム コンポーネントのプロパティを実装する方法と、そのプロパティをデザイン環境に統合する方法について説明します。  
  
 [ShouldSerialize メソッドと Reset メソッドによる既定値の定義](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 カスタム コントロールまたはカスタム コンポーネントの既定のプロパティ値を定義する方法について説明します。  
  
 [プロパティ変更イベント](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 プロパティ値が変化したときにプロパティ変更通知を有効にする方法について説明します。  
  
 [方法 : 内在コントロールのプロパティを公開する](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 カスタム複合コントロール内の内在コントロールのプロパティを公開する方法について説明します。  
  
 [カスタム コントロールへのメソッドの実装](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 カスタム コントロールおよびカスタム コンポーネントのメソッドを実装する方法について説明します。  
  
## 関連項目  
 <xref:System.Windows.Forms.UserControl>  
 複合コントロールを実装する基本クラスについて説明します。  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 カスタム プロパティの型に使用する <xref:System.ComponentModel.TypeConverter> を指定する属性について説明します。  
  
 <xref:System.ComponentModel.EditorAttribute>  
 カスタム プロパティに使用する <xref:System.Drawing.Design.UITypeEditor> を指定する属性について説明します。  
  
## 関連項目  
 [Windows フォーム コントロールの属性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 カスタム コントロールとカスタム コンポーネントのプロパティやその他のメンバーに適用できる属性について説明します。  
  
 [コンポーネントのデザイン時属性](../Topic/Design-Time%20Attributes%20for%20Components.md)  
 コンポーネントとコントロールに適用されるメタデータ属性の一覧を示します。メタデータ属性が適用されたコンポーネントとコントロールは、デザイン時にビジュアル デザイナーで適切に表示されます。  
  
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)  
 デザイン時サポートを提供するエディターやデザイナーなどのクラスを実装する方法を説明します。