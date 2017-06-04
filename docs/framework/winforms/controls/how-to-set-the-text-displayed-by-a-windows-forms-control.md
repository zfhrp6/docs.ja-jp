---
title: "方法 : Windows フォーム コントロールによって表示されるテキストを設定する | Microsoft Docs"
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
  - "Button コントロール [Windows フォーム], ボタンのテキスト"
  - "Button コントロール [Windows フォーム], テキスト表示"
  - "ボタン, テキスト"
  - "キャプション, 設定"
  - "キャプション, Windows フォーム コントロール"
  - "コントロール [Windows フォーム], キャプション"
  - "例 [Windows フォーム], コントロール"
  - "フォーム, キャプション"
  - "ラベル, 追加 (CommandButton コントロールに)"
  - "StdFont オブジェクトと CommandButton キャプション"
  - "テキスト"
  - "Text プロパティ, Windows フォーム コントロール"
  - "テキスト, Windows フォーム コントロール"
  - "Windows フォーム, キャプション"
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : Windows フォーム コントロールによって表示されるテキストを設定する
Windows フォーム コントロールは、通常、コントロールの主な機能に関連するいくつかのテキストを表示します。  たとえば、<xref:System.Windows.Forms.Button> コントロールは、通常、ボタンがクリックされたときにどのようなアクションを実行するかを示すキャプションを表示します。  すべてのコントロールに対して、<xref:System.Windows.Forms.Control.Text%2A> プロパティを使用してテキストを設定または返すことができます。  <xref:System.Windows.Forms.Control.Font%2A> プロパティを使用して、フォントを変更することができます。  また、デザイナーを使用してテキストを設定することもできます。  「[方法 : デザイナーを使用して Windows フォーム コントロールのアクセス キーを作成する](http://msdn.microsoft.com/library/ms233673\(v=vs.110\))」、「[方法 : Windows フォーム コントロールに表示するテキストをデザイナーで設定する](http://msdn.microsoft.com/library/ms233665\(v=vs.110\))」、「[方法 : デザイナーを使用して Windows フォーム コントロールによって表示されるイメージを設定する](http://msdn.microsoft.com/library/ms233656\(v=vs.110\))」も参照してください。  
  
### コントロールによって表示されるテキストをプログラムで設定するには  
  
1.  <xref:System.Windows.Forms.Control.Text%2A> プロパティを文字列に設定します。  
  
     下線付きのアクセス キーを作成するには、アクセス キーにする文字の前にアンパサンド \(&\) を含めます。  
  
2.  <xref:System.Windows.Forms.Control.Font%2A> プロパティを型 <xref:System.Drawing.Font> のオブジェクトに設定します。  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp#  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  エスケープ文字を使用すると、メニュー項目など、通常は別の解釈がなされるユーザー インターフェイス要素の特殊文字を表示できます。  たとえば、次のコード行は、メニュー項目のテキストが "& Now For Something Completely Different" と読めるように設定します。  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp#  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=fullName>   
 [方法 : Windows フォーム コントロールのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)   
 [方法 : Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)