---
title: "ImeMode プロパティによるアジア言語の文字表示 | Microsoft Docs"
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
  - "アジアの言語"
  - "アジアの言語, 表示 (ImeMode で)"
  - "中国語の文字, 表示 (ImeMode で)"
  - "グローバリゼーション [Windows フォーム], 文字セット"
  - "IME モード"
  - "IMEMode プロパティ"
  - "Input Method Editor (IME), モード"
  - "国際対応のアプリケーション [Windows フォーム], 文字表示"
  - "各種言語の文字"
  - "日本語の文字, 表示 (ImeMode で)"
  - "韓国語文字"
  - "ローカリゼーション [Windows フォーム], 文字セット"
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# ImeMode プロパティによるアジア言語の文字表示
<xref:System.Windows.Forms.Control.ImeMode%2A> プロパティは、IME \(Input Method Editor\) のモードを強制的に指定する場合に、フォームおよびコントロールで使用します。  IME は、中国語、日本語、および韓国語の言語を記述するときに不可欠なコンポーネントです。これらの言語には、通常のキーボードではエンコードできないほど多くの文字が含まれているからです。  たとえば、特定のテキスト ボックスに入力できる文字を ASCII 文字だけにする必要があるとします。  この場合、<xref:System.Windows.Forms.Control.ImeMode%2A> プロパティを <xref:System.Windows.Forms.ImeMode> に設定することにより、特定のテキスト ボックスでは、ユーザーが ASCII 以外の文字を入力できないように設定できます。  <xref:System.Windows.Forms.Control.ImeMode%2A> プロパティの既定の値は、<xref:System.Windows.Forms.ImeMode> です。したがって、プロパティをフォームに設定すると、このフォーム上のすべてのコントロールでこの設定が継承されます。  詳細については、「[ImeMode プロパティ](frlrfSystemWindowsFormsControlClassImeModeTopic)」および「[ImeMode 列挙](frlrfSystemWindowsFormsImeModeClassTopic)」を参照してください。  
  
## 参照  
 [Windows フォームのグローバル化](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)