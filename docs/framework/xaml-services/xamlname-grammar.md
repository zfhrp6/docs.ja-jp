---
title: XamlName の文法
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 32fd7b7b952ebbc853e41c0a8276d1ab487e619f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="xamlname-grammar"></a>XamlName の文法
XamlName の文法では、便宜上、ここで再度は、XAML 言語仕様 [MS-XAML] で定義されている特定の文法がします。  
  
## <a name="from-the-xaml-specification"></a>XAML の仕様  
 [MS-XAML] の仕様では、型とプロパティに使用される有効なシンボリック識別子のセットを識別する XamlName の文法を定義します。  
  
 文字列は次の文法に従う必要があります XamlName 型の値。  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Unicode 文字データベースで定義されている次の一般的なカテゴリ値を想定しています  
  
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
  
 XAML が、2 番目の文法、プロパティに使用される DottedXamlName を定義し、イベントの参照を修飾およびものメンバーをアタッチします。 詳細については、次を参照してください。<xref:System.Windows.DependencyProperty>と[XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)です。  
  
 文字列は次の文法に従う必要があります DottedXamlName 型の値。  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>コメント  
 は、完全な仕様を参照してください。 [ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)です。
