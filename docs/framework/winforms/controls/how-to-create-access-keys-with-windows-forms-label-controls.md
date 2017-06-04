---
title: "方法 : Windows フォームの Label コントロールでアクセス キーを作成する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], アクセス キー"
  - "ダイアログ ボックス コントロール, ニーモニック"
  - "ショートカット キー, 作成 (コントロールの)"
  - "Label コントロール [Windows フォーム], 作成 (アクセス キーを)"
  - "ニーモニック"
  - "ニーモニック, 追加 (ダイアログ ボックス コントロールに)"
  - "UseMnemonic プロパティ, Label コントロール"
  - "Windows フォーム コントロール, アクセス キー"
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォームの Label コントロールでアクセス キーを作成する
Windows フォーム <xref:System.Windows.Forms.Label> コントロールを使用すると、他のコントロールのアクセス キーを定義できます。  ラベル コントロールにアクセス キーを定義すると、**Alt** キーを押しながら指定した文字を押して、タブ オーダーで次に設定されているコントロールにフォーカスを移すことができます。  ラベルはフォーカスを受け取ることができないため、タブ オーダー内の次のコントロールに自動的にフォーカスが移ります。  この機能を使用して、テキスト ボックス、コンボ ボックス、リスト ボックス、およびデータ グリッドにアクセス キーを割り当てます。  
  
### ラベルを含むコントロールにアクセス キーを割り当てるには  
  
1.  まずラベルを描画し、次に他のコントロールを描画します。  
  
     または  
  
     任意の順序でコントロールを描画し、ラベルの <xref:System.Windows.Forms.Control.TabIndex%2A> プロパティにもう一方のコントロールより 1 つ小さい値を設定します。  
  
2.  ラベルの <xref:System.Windows.Forms.Label.UseMnemonic%2A> プロパティを `true` に設定します。  
  
3.  ラベルの <xref:System.Windows.Forms.Label.Text%2A> プロパティでアンパサンド \(&\) を使用して、ラベルにアクセス キーを割り当てます。  詳細については、「[Windows フォーム コントロールのアクセス キーの作成](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)」を参照してください。  
  
    > [!NOTE]
    >  アンパサンドでアクセス キーを作成するのではなく、ラベル コントロールにアンパサンドを表示することもできます。  この方法は、データにアンパサンドが含まれるレコードセット内で、フィールドにラベル コントロールを連結する場合に役立ちます。  ラベル コントロールにアンパサンドを表示するには、<xref:System.Windows.Forms.Label.UseMnemonic%2A> プロパティを `false` に設定します。  アンパサンド \(&\) を表示しながら、アクセス キーも設定する場合は、<xref:System.Windows.Forms.Label.UseMnemonic%2A> プロパティを `true` に設定して、アクセス キーは 1 つのアンパサンドで表し、アンパサンドは 2 つのアンパサンドで表します。  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## 参照  
 [方法 : Windows フォーム Label コントロールのサイズを内容に合わせて変更する](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)   
 [Label コントロールの概要](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [Label コントロール](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)