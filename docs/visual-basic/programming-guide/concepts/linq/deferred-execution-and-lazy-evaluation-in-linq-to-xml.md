---
title: "遅延実行とレイジー評価 linq to XML (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3b7318eb9853d633d152b93fafcf9570ccd03835
ms.lasthandoff: 03/13/2017


---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>遅延実行とレイジー評価 linq to XML (Visual Basic)
クエリと軸の操作は、多くの場合、遅延実行を使用するように実装されています。 このトピックでは、遅延実行の要件と利点、および実装に関する注意点について説明します。  
  
## <a name="deferred-execution"></a>遅延実行  
 遅延実行は、式の評価がまで遅延されることを意味の*実現*値が実際に必要です。 大きなデータ コレクションの操作が必要な場合、特に連結されたクエリや操作が含まれているプログラムでは、遅延実行によってパフォーマンスが大幅に向上することがあります。 最も効果的なケースでは、遅延実行を使用することによって、ソース コレクションの繰り返し処理を&1; 度行うだけで済むようになります。  
  
 LINQ テクノロジでは、広く利用されて遅延実行の中核となるメンバーで<xref:System.Linq?displayProperty=fullName>クラスと、さまざまな LINQ 名前空間、 <xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</xref:System.Xml.Linq.Extensions?displayProperty=fullName>などの拡張メソッドで</xref:System.Linq?displayProperty=fullName>  
  
## <a name="eager-vs-lazy-evaluation"></a>集中評価とレイジー評価  
 遅延実行を実装するメソッドを記述するときは、レイジー評価と集中評価のどちらを使用してメソッドを実装するかについても決定する必要があります。  
  
-   *レイジー評価*、反復子を呼び出すたびに、ソース コレクションの&1; つの要素を処理します。 これが、一般的な反復子の実装方法です。  
  
-   *集中評価*、コレクション全体が処理中に、反復子の最初の呼び出しになります。 ソース コレクションの一時的なコピーが必要になる場合もあります。 たとえば、<xref:System.Linq.Enumerable.OrderBy%2A>メソッドは、最初の要素を返す前に、コレクション全体を並べ替えるには</xref:System.Linq.Enumerable.OrderBy%2A>。  
  
 通常は、レイジー評価を使用するとパフォーマンスが向上します。コレクション評価時のオーバーヘッド処理が均等に分散され、一時データの使用が最小限に抑えられるためです。 もちろん、操作によっては、中間結果を具体化するより他に方法がない場合もあります。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルの次のトピックでは、遅延実行について説明します。  
  
-   [遅延実行の例 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: 遅延実行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)   
 [概念と用語 (関数型変換) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)   
 [集計操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
