---
title: "Windows フォーム コントロール開発の基本概念 | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 作成"
  - "カスタム コントロール [Windows フォーム], 派生型"
  - "プログラミングの概念, Windows フォーム コントロール"
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows フォーム コントロール開発の基本概念
Windows フォーム コントロールは、<xref:System.Windows.Forms.Control?displayProperty=fullName> から直接または間接的に派生するクラスです。  一般的な Windows フォーム コントロールの開発方法をまとめた一覧を次に示します。  
  
-   既存の複数のコントロールを組み合わせて、複合コントロールを作成します。  
  
     複合コントロールは、コントロールとして再利用できるユーザー インターフェイスをカプセル化します。  複合コントロールの例としては、テキスト ボックスとリセット ボタンで構成されるコントロールがあります。  ビジュアル デザイナーには、複合コントロールの作成をサポートするさまざまな機能があります。  複合コントロールを作成するには、<xref:System.Windows.Forms.UserControl?displayProperty=fullName> から派生します。  <xref:System.Windows.Forms.UserControl> 基本クラスは子コントロールに対してキーボード ルーティングを提供し、複数の子コントロールを 1 つのグループとして機能させることができます。  詳細については、「[複合 Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)」を参照してください。  
  
-   コントロールを拡張します。コントロールをカスタマイズするか、またはコントロールに機能を追加します。  
  
     拡張コントロールの例としては、色を変更できないボタンや、クリック回数を追跡する追加プロパティが設定されているボタンがあります。  Windows フォーム コントロールをカスタマイズするには、コントロールからクラスを派生させて、プロパティ、メソッド、イベントを追加またはオーバーライドします。  
  
-   既存の複合コントロールや拡張コントロール以外のコントロールを作成します。  
  
     この場合、<xref:System.Windows.Forms.Control> 基本クラスからコントロールを派生させます。  基本クラスのプロパティ、メソッド、イベントをオーバーライドまたは追加できます。  開始するには、「[方法 : シンプルな Windows フォーム コントロールを開発する](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)」を参照してください。  
  
 Windows フォーム コントロールの基本クラスである <xref:System.Windows.Forms.Control> には、クライアント側の Windows ベースのアプリケーションでのビジュアル表示に必要な内部機構が用意されています。  <xref:System.Windows.Forms.Control> には、ウィンドウ ハンドルがあり、メッセージ ルーティングを処理します。また、マウス イベントとキーボード イベントの他、多くのユーザー インターフェイス イベントが含まれています。  このクラスは、高度なレイアウトを提供し、<xref:System.Windows.Forms.Control.ForeColor%2A>、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.Height%2A>、<xref:System.Windows.Forms.Control.Width%2A> など、ビジュアル表示に関連する固有のプロパティを備えています。  さらに、セキュリティ、スレッド処理のサポート、ActiveX コントロールとの相互運用性を提供します。  基本クラスによってインフラストラクチャの大部分が提供されるため、Windows フォーム コントロールは比較的簡単に開発できます。  
  
## 参照  
 [方法 : シンプルな Windows フォーム コントロールを開発する](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)   
 [複合 Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)   
 [方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)   
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)