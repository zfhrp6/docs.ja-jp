---
title: "方法 : 定型入力を設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "net.ComponentModel.MaskPropertyEditor"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "MaskedTextBox コントロール [Windows フォーム]"
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : 定型入力を設定する
マスク付きテキスト ボックス コントロールは、ユーザー入力を受け入れまたは拒否するための宣言構文をサポートする、拡張されたテキスト ボックス コントロールです。  \[マスク\] プロパティを設定することにより、アプリケーション内にカスタム検証ロジックを記述しなくても、許容できるユーザー入力を指定できます。  詳細については、<xref:System.Windows.Forms.MaskedTextBox> クラスの「解説」を参照してください。  
  
## \[マスク\] プロパティの手動設定  
 \[マスク\] プロパティがサポートする文字に精通している場合は、手動で入力できます。  \[マスク\] プロパティがサポートする文字の概要については、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A> プロパティの「解説」を参照してください。  
  
#### \[マスク\] プロパティを手動で設定するには  
  
1.  **デザイン** ビューで、<xref:System.Windows.Forms.MaskedTextBox> を選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A> プロパティを見つけます。  
  
3.  目的のマスクを入力します。  たとえば、「`###`」と入力します。  
  
## \[定型入力\] ダイアログ ボックスの使用  
 \[定型入力\] ダイアログ ボックスには、定義済みの定型入力がいくつか用意されています。  定義済みのマスクを変更することも、独自のマスクを手動で入力することもできます。  
  
#### \[定型入力\] ダイアログ ボックスを開くには  
  
1.  **デザイン** ビューで、<xref:System.Windows.Forms.MaskedTextBox> を選択します。  
  
    1.  スマート タグをクリックして、**\[MaskedTextBox タスク\]** パネルを開きます。  
  
    2.  **\[マスクの設定\]** をクリックします。  
  
     または  
  
    1.  **\[プロパティ\]** ウィンドウで <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> プロパティを選択します。  
  
    2.  プロパティの値列の省略記号ボタンをクリックします。  
  
     **\[定型入力\]** ダイアログ ボックスが表示されます。  
  
#### \[定型入力\] ダイアログ ボックスを使用するには  
  
1.  \(省略可能\) 一覧の定義済みのマスクのいずれかを選択します。  
  
2.  \(省略可能\) **\[マスク\]** ボックスで定義済みマスクを編集します。  
  
3.  \(省略可能\) **\[マスク\]** ボックスに新しいマスクを入力します。  つまり、定義済みのマスクのいずれかを使用する必要はありません。  
  
    > [!NOTE]
    >  プレビュー ボックスに、<xref:System.Windows.Forms.MaskedTextBox> に表示される文字 \(ユーザーが確認する文字\) が表示されます。  これらの文字は、ユーザーがデータを正確に入力するためのガイドの役割をします。  
  
4.  **\[ValidatingType を使用する\]** チェック ボックスをオンにするかオフにします。  **\[ValidatingType を使用する\]** チェック ボックスは、ユーザーによる入力データを、データ型を使用して検証するかどうかを指定します。  詳細については、<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> プロパティのトピックを参照してください。  
  
5.  **\[OK\]** をクリックします。  
  
     **\[プロパティ\]** ウィンドウの **\[マスク\]** プロパティにマスクが入力されます。  
  
## 参照  
 [チュートリアル : MaskedTextBox コントロールの使用](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)