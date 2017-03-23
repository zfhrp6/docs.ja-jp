---
title: "遅延バインディングの解決実行時エラーが発生する可能性があります。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
dev_langs:
- VB
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ac885b0de2c4f44d4323487fc55cde9b23defa4
ms.lasthandoff: 03/13/2017

---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>遅延バインドの解決です。ランタイム エラーが発生する可能性があります。
として宣言された変数にオブジェクトが割り当てられている、 [Object データ型](../../../visual-basic/language-reference/data-types/object-data-type.md)します。  
  
 として変数を宣言すると`Object`、コンパイラを実行する必要があります*遅延バインディング*、これにより実行時に余分な処理が発生します。 また、アプリケーションで実行時エラーが発生する可能性があります。 割り当てる場合など、<xref:System.Windows.Forms.Form>に、`Object`変数にアクセスしようと、<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>プロパティには、ランタイムは、スロー、<xref:System.MemberAccessException>ため、<xref:System.Windows.Forms.Form>クラスを公開しません、`NameTable`プロパティ</xref:System.Windows.Forms.Form></xref:System.MemberAccessException></xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName></xref:System.Windows.Forms.Form>。  
  
 特定の種類を指定して変数を宣言する場合、コンパイラを実行できます*事前バインディング*コンパイル時にします。 これは、結果、パフォーマンスの向上、制御されたアクセスを特定の型のメンバーと、コードの読みやすさをします。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC42017  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   可能であれば、特定の種類を指定して変数を宣言します。  
  
## <a name="see-also"></a>関連項目  
 [事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)   
 [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
