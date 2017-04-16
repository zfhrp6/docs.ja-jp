---
title: "Label コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "Label"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "イメージ [Windows フォーム], 表示 (ラベルに)"
  - "Label コントロール [Windows フォーム], Label コントロールの概要"
  - "ラベル"
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Label コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.Label> コントロールを使用すると、ユーザーが編集できないテキストまたはイメージを表示できます。  Label コントロールでは、フォーム上のオブジェクトを識別します。このコントロールを使用して、特定のコントロールをクリックしたときの動作を記述したり、アプリケーションの実行時イベントやプロセスに応じた情報を表示したりできます。  たとえば、ラベルを使用して、テキスト ボックス、リスト ボックス、コンボ ボックスなどの説明テキストを追加します。  また、実行時にイベントに応じて表示されるテキストを変更するコードも記述できます。  たとえば、アプリケーションで変更を処理するのに数分かかる場合は、ラベルに処理状況のメッセージを表示します。  
  
## Label コントロールの操作  
 <xref:System.Windows.Forms.Label> コントロールはフォーカスを受け取ることができないため、このコントロールを使用して他のコントロールのアクセス キーを作成できます。  ユーザーは、**Alt** キーを押しながらアクセス キーを押すことによって、コントロールを選択した場合と同様の操作ができます。  詳細については、「[Windows フォーム コントロールのアクセス キーの作成](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)」と「[方法 : Windows フォームの Label コントロールでアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)」を参照してください。  
  
 ラベルに表示されるキャプションは、<xref:System.Windows.Forms.Label.Text%2A> プロパティに含まれています。  <xref:System.Windows.Forms.Label.TextAlign%2A> プロパティを使用すると、ラベル内のテキストの配置を設定できます。  詳細については、「[方法 : Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.Label>   
 [方法 : Windows フォーム Label コントロールのサイズを内容に合わせて変更する](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)   
 [方法 : Windows フォームの Label コントロールでアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)