---
title: "方法 : Windows フォーム コントロールのアクセス キーを作成する | Microsoft Docs"
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
  - "ニーモニック"
  - "ニーモニック, 追加 (ダイアログ ボックス コントロールに)"
  - "Text プロパティ, 指定 (コントロールのアクセス キーを)"
  - "Windows フォーム コントロール, アクセス キー"
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォーム コントロールのアクセス キーを作成する
*アクセス キー*は、メニュー、メニュー項目、コントロールのラベル \(ボタンなど\) のテキストに含まれている下線付きの文字です。  定義済みのアクセス キーを Alt キーと一緒に押すと、ボタンを "クリック" した場合と同じ結果になります。  たとえば、フォームを印刷するためのプロシージャを実行するボタンで、`Text` プロパティが "Print" に設定されている場合は、文字 "P" の前にアンパサンド \(&\) を追加すると、実行時にボタンのテキスト内で "P" に下線が引かれます。  ユーザーは、Alt キーを押しながら P キーを押すことにより、ボタンに関連付けられたコマンドを実行できます。  フォーカスを持つことができないコントロールに対しては、アクセス キーを定義できません。  
  
### コントロールのアクセス キーを作成するには  
  
1.  ショートカットとして使用する文字の前にアンパサンド \(&\) を含む文字列に `Text` プロパティを設定します。  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  アンパサンドをアクセス キーを作成するための記号としてではなく、文字として表示する場合は、アンパサンドを 2 回続けて記述 \(&&\) します。  この場合、画面に表示されるアンパサンドは 1 個だけで、どの文字にも下線は付けられません。  
  
## 参照  
 <xref:System.Windows.Forms.Button>   
 [方法 : Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [方法 : Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)