---
title: "ユーザ補助ガイドラインをサポートする Windows フォーム コントロールのプロパティ | Microsoft Docs"
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
  - "アクセシビリティ, Windows フォーム コントロール プロパティ"
  - "Windows フォーム, アクセシビリティ プロパティ (コントロールの)"
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# ユーザ補助ガイドラインをサポートする Windows フォーム コントロールのプロパティ
Windows フォームの標準ツールボックス上のコントロールは、キーボード フォーカスの公開や画面要素の公開など、ユーザー補助ガイドラインの多くをサポートしています。  
  
## ユーザー補助の事前計画  
 これらのコントロールのプロパティを使うと、次の表に示すように、他のユーザー補助ガイドラインをサポートできます。  また、プログラムの各機能にアクセスするメニューも使う必要があります。  
  
|コントロール プロパティ|ユーザー補助に関する考慮点|  
|------------------|-------------------|  
|AccessibleDescription|スクリーン リーダーなどのユーザー補助機能に対する説明が報告されます。  ユーザー補助機能とは、障碍を持つユーザーがコンピューターをより効果的に使用できるように特別に設計されたプログラムや装置です。|  
|AccessibleName|ユーザー補助機能に対して報告される名前です。|  
|AccessibleRole|ユーザー インターフェイスの要素の使用方法を記述します。|  
|TabIndex|フォームでのフォーカスの移動順序を指定します。  固有のラベルを持たないコントロール \(テキスト ボックスなど\) では、関連するラベルがタブ オーダーで直前になるように配置する必要があります。|  
|テキスト|"&" 文字を使用してアクセス キーを作成します。  アクセス キーの使い方は、機能へのキーボード アクセスの一部として公開されています。|  
|Font Size|フォント サイズが調整できない場合は、10 ポイント以上に設定する必要があります。  フォームのフォント サイズが設定されると、それ以降、フォームに追加されるコントロールにはすべて同じフォント サイズが使用されます。|  
|Forecolor|このプロパティが既定値に設定されると、フォーム上でユーザーの色設定が使用されます。|  
|Backcolor|このプロパティが既定値に設定されると、フォーム上でユーザーの色設定が使用されます。|  
|BackgroundImage|テキストが読みやすくなるように、このプロパティは空白のままにします。|  
  
## 参照  
 [チュートリアル : ユーザー補助対応の Windows ベースのアプリケーションの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)