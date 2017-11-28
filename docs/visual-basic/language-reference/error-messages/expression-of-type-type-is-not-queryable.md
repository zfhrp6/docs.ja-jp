---
title: "型の式&lt;型&gt;はクエリ不可能"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords: BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>型の式&lt;型&gt;はクエリ不可能
型の式\<型 > はクエリ不可能です。 LINQ プロバイダーに対してアセンブリ参照や名前空間インポートが不足していないを確認してください。  
  
 クエリ可能型が定義されている、 <xref:System.Linq>、 <xref:System.Data.Linq>、および<xref:System.Xml.Linq>名前空間。 1 つ以上の LINQ クエリを実行するこれらの名前空間をインポートする必要があります。  
  
 <xref:System.Linq>名前空間を有効にするオブジェクトに対してクエリをコレクションや配列などに LINQ を使用しています。  
  
 <xref:System.Data.Linq>名前空間では、LINQ を使用して SQL Server データベースと ADO.NET データセットのクエリを実行することができます。  
  
 <xref:System.Xml.Linq>名前空間を使用すると XML のクエリに LINQ を使用して、Visual Basic で XML 機能を使用するとします。  
  
 **エラー ID:** BC36593  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  追加、`Import`のステートメント、 <xref:System.Linq>、 <xref:System.Data.Linq>、または<xref:System.Xml.Linq>をコード ファイルの名前空間。 使用して、プロジェクトの名前空間をインポートすることも、**参照**、プロジェクト デザイナーのページ (**My Project**)。  
  
2.  クエリのソースはクエリ可能型として指定した型を確認してください。 実装する型は、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
