---
title: "コントロールのカスタム描画およびレンダリング | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], 描画"
  - "カスタム コントロール [Windows フォーム], 描画"
  - "OnPaint メソッド"
  - "ユーザー コントロール [Windows フォーム], 描画"
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# コントロールのカスタム描画およびレンダリング
コントロールのカスタム描画は、.NET Framework によって簡略化された作業の 1 つです。  カスタム コントロールを作成するときには、多くのオプションからコントロールの外観を決定できます。  `Control` から継承するコントロールを作成する場合は、コントロールのグラフィカル表示をレンダリングするためのコードを記述する必要があります。  `UserControl` からの継承、または Windows フォーム コントロールからの継承によってユーザー コントロールを作成する場合は、標準のグラフィカル表示をオーバーライドして、独自のグラフィック コードを指定できます。  作成する `UserControl` の内在コントロールにカスタム レンダリング機能を提供する場合、オプションは制限されますが、コントロールおよびアプリケーションに対して幅広いグラフィカル表現が可能です。  
  
## このセクションの内容  
 [Windows フォーム コントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 コントロールの表示ロジックをプログラミングする方法について説明します。  
  
 [ユーザー描画コントロール](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 コントロールのレンダリング処理コードを記述またはオーバーライドする手順の概要を示します。  
  
 [内在コントロール](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 ユーザー コントロールおよびフォームの内在コントロールに対してカスタム レンダリング処理コードを実装する方法について説明します。  
  
 [方法 : 実行時にコントロールを非表示にする](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 <xref:System.Windows.Forms.Control.Visible%2A> プロパティを使用してコントロールを表示および非表示にする方法を示します。  
  
 [方法 : コントロールに透明な背景を指定する](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 <xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを使用して、背景色を不透明、透明、または半透明にする方法を示します。  
  
 [visual スタイルが使用されているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 コントロールをサポートするオペレーティング システムの visual スタイルを使用してコントロールのレンダリングを行う方法を示します。  
  
## 関連項目  
 <xref:System.Windows.Forms.Control>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.UserControl>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 このメソッドについて説明します。  
  
## 関連項目  
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] グラフィックス機能を Visual Studio の観点から紹介し、詳細情報へのリンクを提供します。  
  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 作成可能なカスタム コントロールの種類について説明します。