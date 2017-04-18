---
title: "型の式&lt;型&gt;クエリ不可能です。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
dev_langs:
- VB
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 1e7e1e2652cf730ef6d14b0579d8a3ee3de67fbb
ms.lasthandoff: 03/13/2017

---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>型の式&lt;型&gt;クエリ不可能です
型の式\<型 > クエリ不可能です。 LINQ プロバイダーに対してアセンブリ参照や名前空間インポートを不足していないことを確認します。  
  
 クエリ可能型が定義されている、 <xref:System.Linq>、 <xref:System.Data.Linq>、および<xref:System.Xml.Linq>名前空間</xref:System.Xml.Linq></xref:System.Data.Linq></xref:System.Linq>。 1 つ以上の LINQ クエリを実行するこれらの名前空間をインポートする必要があります。  
  
 <xref:System.Linq>名前空間は、コレクションと配列などのクエリ オブジェクトを LINQ を使用しています</xref:System.Linq>。  
  
 <xref:System.Data.Linq>名前空間では、LINQ を使用して、ADO.NET データセットと SQL Server データベースを照会することができます</xref:System.Data.Linq>。  
  
 <xref:System.Xml.Linq>名前空間を使用すると XML のクエリに LINQ を使用して、Visual Basic で XML 機能を使用します</xref:System.Xml.Linq>。  
  
 **エラー ID:** BC36593  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  追加、`Import`のステートメント、 <xref:System.Linq>、 <xref:System.Data.Linq>、または<xref:System.Xml.Linq>をコード ファイルの名前空間</xref:System.Xml.Linq></xref:System.Data.Linq></xref:System.Linq>。 使用して、プロジェクトの名前空間をインポートすることも、**参照**プロジェクト デザイナーのページ (**My Project**)。  
  
2.  クエリのソースがクエリ可能型として指定した型を確認します。 つまり<xref:System.Collections.Generic.IEnumerable%601>、または<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>を実装する型  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 <xref:System.Data.Linq></xref:System.Data.Linq>   
 <xref:System.Xml.Linq>   
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)
