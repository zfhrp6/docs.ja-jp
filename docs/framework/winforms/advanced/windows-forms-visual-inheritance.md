---
title: "Windows フォームのビジュアルの継承 | Microsoft Docs"
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
  - "基本フォーム"
  - "フォームの継承"
  - "継承"
  - "継承, フォーム"
  - "継承フォーム"
  - "継承フォーム, Windows フォーム"
  - "Windows フォーム, 継承"
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows フォームのビジュアルの継承
プロジェクトで、以前のプロジェクトに作成したフォームと同様のフォームが必要になることがあります。  または、プロジェクトで再使用するウォーターマークや特定のコントロール レイアウトなどが設定された基本フォームを作成し、元のフォーム テンプレートを変更しながら繰り返し使用することが必要になる場合があります。  フォームの継承を使用すると、基本フォームを作成し、そのフォームを継承して変更できます。このとき、必要となる元の設定はすべて保持されます。  
  
 派生クラス フォームは、プログラムによって、またはビジュアルな継承ピッカーを使って、作成できます。  
  
## このセクションの内容  
 [方法 : Windows フォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 コードを記述して、継承フォームを作成する方法について説明します。  
  
 [方法 : \[継承ピッカー\] ダイアログ ボックスを使用してフォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 継承ピッカーを使用して、継承フォームを作成する方法について説明します。  
  
 [基本フォームの外観を変更した場合の影響](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 基本フォームのコントロールおよびコントロールのプロパティを変更する方法について説明します。  
  
 [チュートリアル : ビジュアル継承のデモンストレーション](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 基本の Windows フォームを作成し、クラス ライブラリにコンパイルする方法について説明します。  このクラス ライブラリを別のプロジェクトにインポートし、基本のフォームを継承した新規フォームを作成します。  
  
 [方法 : Modifiers プロパティおよび GenerateMember プロパティを使用する](../../../../docs/framework/winforms/advanced/how-to-use-the-modifiers-and-generatemember-properties.md)  
 `GenerateMember` プロパティおよび `Modifiers` プロパティの使用法について説明します。これらのプロパティは、Windows フォーム デザイナーでコンポーネントのメンバー変数を生成するときに使用されます。  
  
## 関連項目  
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/ja-jp/e5e6e240-ed31-4657-820c-079b7c79313c)  
 他のクラスの基本クラスとして、Visual Basic クラスを定義する方法について説明します。  
  
 [クラス](../Topic/class%20\(C%23%20Reference\).md)  
 単一継承ができる C\# のクラスについて説明します。  
  
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)  
 継承コンポーネントのイベント ハンドラーで発生する一般的な問題について説明します。