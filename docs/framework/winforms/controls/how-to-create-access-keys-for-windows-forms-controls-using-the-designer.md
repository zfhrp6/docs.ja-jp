---
title: "方法 : デザイナーを使用して Windows フォーム コントロールのアクセス キーを作成する | Microsoft Docs"
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
  - "アクセス キー, 作成 (コントロールの)"
  - "アクセス キー, Windows フォーム"
  - "ALT キー"
  - "アンパサンド文字 (ショートカット キーの)"
  - "Button コントロール [Windows フォーム], アクセス キー"
  - "コントロール [Windows フォーム], アクセス キー"
  - "ダイアログ ボックス コントロール, ニーモニック"
  - "例 [Windows フォーム], コントロール"
  - "ショートカット キー, 作成 (コントロールの)"
  - "ニーモニック, 追加 (ダイアログ ボックス コントロールに)"
  - "Text プロパティ, 指定 (コントロールのアクセス キーを)"
  - "Windows フォーム コントロール, アクセス キー"
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : デザイナーを使用して Windows フォーム コントロールのアクセス キーを作成する
*アクセス キー*は、メニュー、メニュー項目、コントロールのラベル \(ボタンなど\) のテキストに含まれている下線付きの文字です。  定義済みのアクセス キーを Alt キーと一緒に押すことにより、ユーザーはボタンを "クリック" できます。  たとえば、フォームを印刷するためのプロシージャを実行するボタンで、`Text` プロパティが "Print" に設定されている場合は、文字 "P" の前にアンパサンド \(&\) を追加すると、実行時にボタンのテキスト内で "P" に下線が引かれます。  ユーザーは、Alt キーを押しながら P キーを押すことにより、ボタンに関連付けられたコマンドを実行できます。  フォーカスを持つことができないコントロールに対しては、アクセス キーを定義できません。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールのアクセス キーを作成するには  
  
1.  **\[プロパティ\]** ウィンドウで、アクセス キーとして使用する文字の前にアンパサンド \(&\) を含む文字列に `Text` プロパティを設定します。  たとえば、文字 "P" をアクセス キーとして設定する場合は、グリッドに「&Print」と入力します。  
  
## 参照  
 <xref:System.Windows.Forms.Button>   
 [方法 : Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [方法 : Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)