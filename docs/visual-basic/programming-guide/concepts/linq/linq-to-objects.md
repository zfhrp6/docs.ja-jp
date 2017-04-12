---
title: "LINQ to Objects (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d2bc048fea9affd4998430783d20b978317f3897
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
「LINQ オブジェクト」とは、LINQ の使用をいずれかと照会<xref:System.Collections.IEnumerable>または<xref:System.Collections.Generic.IEnumerable%601>コレクション、中間の LINQ プロバイダーやなどの API を使用せず、直接[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)または[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable> 。 LINQ を使用するには任意の列挙可能なコレクションなどのクエリに<xref:System.Collections.Generic.List%601>、 <xref:System.Array>、または<xref:System.Collections.Generic.Dictionary%602>.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Array> </xref:System.Collections.Generic.List%601> コレクションがユーザー定義か .NET Framework API によって返される可能性があります。  
  
 基本的な意味では、LINQ to Objects は、コレクションへの新しいアプローチを表します。 従来の方法では、複雑な `For Each` ループを記述して、コレクションからデータを取得する方法を指定する必要がありました。 LINQ のアプローチでは、説明を取得する表す宣言コードを記述します。  
  
 LINQ クエリがさらに、従来の経由での&3; つの主な利点を提供`For Each`ループします。  
  
1.  簡潔で読みやすい (特に複数の条件をフィルター処理する場合)。  
  
2.  強力なフィルター処理、並べ替え、およびグループ化機能を最小限のアプリケーション コードで実現できる。  
  
3.  ほとんど、またはまったく変更せずに、他のデータ ソースに移植できる。  
  
 一般より複雑なデータに対して実行する操作、LINQ を使用して、従来の反復処理の手法ではなく、実現が利点も増えます。  
  
 このセクションの目的は、いくつかの選択の例で、LINQ アプローチを示すためにです。 ただし、すべてを網羅したものではありません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 LINQ を使用して、文字列および文字列のコレクションの照会し、変換する方法について説明します。 これらの基本原則を具体的に示すトピックへのリンクも含まれます。  
  
 [LINQ とリフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 LINQ がリフレクションを使用する方法を示すサンプルへのリンク。  
  
 [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 LINQ を使用して、ファイル システムと対話する方法について説明します。 これらの概念を具体的に示すトピックへのリンクも含まれます。  
  
 [方法: クエリ、LINQ で ArrayList を (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 C# の ArrayList を照会する方法を示します。  
  
 [方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 LINQ クエリを使用する拡張メソッドを追加することでメソッドのセットを拡張する方法について説明します<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。  
  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 LINQ を説明し、クエリを実行するコードの例を紹介するトピックへのリンクを示します。
