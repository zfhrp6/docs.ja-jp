---
title: "方法: クエリ (LINQ) (Visual Basic) の文字列内の文字を |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dabd63e52707f3078c6cdc41db8c4f0e7dfbf70e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>方法: クエリ (LINQ) (Visual Basic) の文字列内の文字
<xref:System.String>クラスに実装するジェネリック<xref:System.Collections.Generic.IEnumerable%601>インターフェイス、任意の文字列は、一連の文字としてクエリを実行できます</xref:System.Collections.Generic.IEnumerable%601></xref:System.String>。 ただし、LINQ の一般的な用途ではありません。 照合操作の複雑なパターンでは、<xref:System.Text.RegularExpressions.Regex>クラス</xref:System.Text.RegularExpressions.Regex>を使用してください。  
  
## <a name="example"></a>例  
 次の例では、含まれている数字の数を判断するための文字列をクエリします。 クエリが「再利用される」を初めて実行された後に注意してください。 これは、機能は、クエリ自体で実際の結果が格納されていないので可能です。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [方法: LINQ クエリは、正規表現 (Visual Basic) とを組み合わせる](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
