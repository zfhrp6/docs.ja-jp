---
title: "複合 Windows フォーム コントロールの開発 | Microsoft Docs"
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
  - "複合コントロール"
  - "複合コントロール, Windows フォーム"
  - "コントロール [Windows フォーム], 複合"
  - "カスタム コントロール [Windows フォーム], 複合コントロール"
  - "UserControl クラス"
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 複合 Windows フォーム コントロールの開発
異なる複数の Windows フォーム コントロールを組み合わせることによって、複合 Windows フォーム コントロールを開発できます。  [System.Windows.Forms.UserControl](frlrfSystemWebUIUserControlClassTopic) から派生した複合コントロールは、ユーザー コントロールと呼ばれます。  基底クラス <xref:System.Windows.Forms.UserControl> は、子コントロールに対してキーボード ルーティングを提供し、子コントロールがフォーカスを受け取れるようにします。  ユーザー コントロールの例については、「[方法 : Windows フォーム コントロールに属性を適用する](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)」に記載されている <xref:System.Windows.Forms.UserControl> のサンプルを参照してください。  
  
 [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] の Windows フォーム デザイナーには、ユーザー コントロールを作成するための豊富なデザイン時サポートが用意されています。  
  
-   [方法: \[ツールボックス アイテムの選択\] ダイアログ ボックスにコントロールを表示する](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [チュートリアル : DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [チュートリアル: Visual C\# による Windows フォーム コントロールからの継承](http://msdn.microsoft.com/en-us/library/5h0k2e6x%20\(v=vs.110\))  
  
-   [方法 : コントロールにツールボックス ビットマップを指定する](http://msdn.microsoft.com/library/4wk1wc0a%20\(v=vs.110\))  
  
-   [方法 : 既存の Windows フォーム コントロールから継承する](http://msdn.microsoft.com/library/7h62478z%20\(v=vs.110\))  
  
-   [チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [方法 : コントロール クラスを継承する](http://msdn.microsoft.com/library/skcysbt2%20\(v=vs.110\))  
  
-   [方法 : UserControl の実行時の動作をテストする](http://msdn.microsoft.com/library/ms171738%20\(v=vs.110\))  
  
-   [方法 : デザイン時にフォームの端に合わせてコントロールを配置する](http://msdn.microsoft.com/library/1fxyb15b%20\(v=vs.110\))  
  
-   [方法 : UserControl クラスを継承する](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [方法 : Windows フォームのコントロールを作成する](http://msdn.microsoft.com/library/bs3yhkh7%20\(v=vs.110\))  
  
-   [方法 : 複合コントロールを作成する](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [チュートリアル : Visual Basic による複合コントロールの作成](http://msdn.microsoft.com/library/c316f119%20\(v=vs.110\))  
  
-   [チュートリアル : Visual C\# による複合コントロールの作成](http://msdn.microsoft.com/en-us/library/a6h7e207\(v=vs.110\))  
  
-   [チュートリアル: Visual Basic による Windows フォーム コントロールからの継承](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [方法 : デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [方法 : デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## 参照  
 [方法 : Windows フォーム コントロールに属性を適用する](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)