---
title: "遅延バインドの解決です。ランタイム エラーが発生する可能性があります。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords: BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d01164914b484ef689654f048a8743f3c2eb669
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>遅延バインドの解決です。ランタイム エラーが発生する可能性があります。
オブジェクトは、宣言する変数に割り当てられた、[オブジェクト データ型](../../../visual-basic/language-reference/data-types/object-data-type.md)です。  
  
 として変数を宣言するときに`Object`、コンパイラを実行する必要があります*遅延バインディング*、これによって実行時に余分な処理が発生します。 また、アプリケーションで実行時エラーが発生する可能性があります。 割り当てる場合など、<xref:System.Windows.Forms.Form>を`Object`変数にアクセスしようと、<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType>プロパティ、ランタイムは、スロー、<xref:System.MemberAccessException>ため、<xref:System.Windows.Forms.Form>クラスを公開しません、`NameTable`プロパティです。  
  
 コンパイラが実行できる場合は、特定の種類を指定して変数を宣言すると、*事前バインディング*コンパイル時にします。 これは、結果、パフォーマンスを向上させる、特定の種類のメンバーと、コードの読みやすいようにへのアクセスを制御します。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC42017  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   可能であれば、特定の種類を指定して変数を宣言します。  
  
## <a name="see-also"></a>関連項目  
 [事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
