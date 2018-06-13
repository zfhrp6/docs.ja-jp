---
title: 型の値&#39;type1&#39;に変換できない&#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602763"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>型の値&#39;type1&#39;に変換できない&#39;type2&#39;
型 'type1' の値は、'type2' へ変換できません。 最初の要素の文字列値を取得する、'Value' プロパティを使用することができます '\<parentElement >' です。  
  
 XML リテラルを特定の型を暗黙的にキャストしようとしました。 XML リテラルは、指定した型に暗黙的にキャストできません。  
  
 **エラー ID:** BC31194  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   XML リテラルの `Value` プロパティを使用して、その値を `String`として参照します。 `CType` 関数、別の型変換関数、または <xref:System.Convert> クラスを使用して、指定した型として値をキャストします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Convert>  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
