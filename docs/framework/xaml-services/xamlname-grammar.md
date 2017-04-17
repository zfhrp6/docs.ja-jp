---
title: "XamlName の文法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DottedXamlName の文法 [XAML サービス]"
  - "文法 [XAML サービス]、DottedXamlName"
  - "文法 [XAML サービス]、XamlName"
  - "XAML の名前 [XAML サービス]"
  - "XamlName の文法 [XAML サービス]"
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
caps.latest.revision: 13
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 13
---
# XamlName の文法
XamlName の文法は、XAML 言語仕様 \[MS\-XAML\] で定義された固有の文法であり、ここでは便宜上、再掲しています。  
  
## XAML 仕様  
 \[MS\-XAML\] 仕様では、型とプロパティに使用される正式なシンボル識別子のセットを識別するために、文法 XamlName が定義されています。  
  
 XamlName 型の文字列値は、次の文法に準拠している必要があります。  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
  
```  
  
 ここでは、Unicode 文字データベースで定義されている次の一般的なカテゴリ値を想定しています。  
  
```  
  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 XAML では、プロパティとイベントで修飾される参照、およびアタッチされたメンバーで使用される、第 2 の文法 DottedXamlName が定義されています。  詳細については、「<xref:System.Windows.DependencyProperty>」および「[XAML の概要 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照してください。  
  
 DottedXamlName 型の文字列値は、次の文法に準拠している必要があります。  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## 解説  
 詳細な仕様については、「[\[MS\-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。