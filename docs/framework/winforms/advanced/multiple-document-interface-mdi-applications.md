---
title: "マルチ ドキュメント インターフェイス (MDI) アプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "フォーム, MDI"
  - "MDI"
  - "Windows フォーム, MDI アプリケーション"
  - "ウィンドウ, MDI"
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# マルチ ドキュメント インターフェイス (MDI) アプリケーション
マルチ ドキュメント インターフェイス \(MDI: Multiple Document Interface\) アプリケーションでは、一度に複数のドキュメントを開き、各ドキュメントをそれぞれのウィンドウに表示できます。  通常、MDI アプリケーションには \[ウィンドウ\] メニューがあり、その中にウィンドウまたはドキュメントを切り替えるためのサブメニューがあります。  
  
> [!NOTE]
>  MDI フォームと Windows フォーム内のシングル ドキュメント インターフェイス \(SDI: Single\-Document Interface\) ウィンドウとの間には、動作に関していくつかの違いがあります。  `Opacity` プロパティは、MDI 子フォームの外観には作用しません。  さらに、<xref:System.Windows.Forms.Form.CenterToParent%2A> メソッドも、MDI 子フォームの動作には作用しません。  
  
## このセクションの内容  
 [方法 : MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 MDI アプリケーション内に複数のドキュメントのコンテナーを作成する方法について説明します。  
  
 [方法 : MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 MDI 親フォーム内で動作するウィンドウを 1 つ以上作成する方法について説明します。  
  
 [方法 : アクティブな MDI 子フォームを特定する](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 フォーカスを持つ子ウィンドウを確認する方法、およびそのウィンドウの内容をクリップボードに送る方法について説明します。  
  
 [方法 : アクティブな MDI 子フォームにデータを送信する](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 アクティブな子ウィンドウに情報を転送する方法について説明します。  
  
 [方法 : MDI 子フォームを配置する](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 MDI アプリケーションの子ウィンドウを並べて表示したり、重ねて表示したり、並べ替えたりする方法について説明します。