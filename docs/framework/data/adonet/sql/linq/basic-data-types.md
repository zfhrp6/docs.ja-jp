---
title: "基本データ型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1c0452e03e9c6471a35cd8612c1f36bbabe002d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="basic-data-types"></a>基本データ型
LINQ to SQL クエリは、Microsoft SQL Server で実行される前に Transact-SQL に変換されるため、 LINQ to SQL は、SQL Server が基本データ型に対してサポートするのと同じ組み込み機能の多くをサポートします。  
  
## <a name="casting"></a>キャスト  
 SQL Server 内に同様の有効な変換が存在する場合は、変換元の CLR 型から変換先の CLR 型への暗黙的または明示的なキャストが有効になります。 CLR のキャストの詳細については、次を参照してください。 [CType 関数](~/docs/visual-basic/language-reference/functions/ctype-function.md)([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) および[として](~/docs/csharp/language-reference/keywords/as.md)です。 変換後、CLR 式に対して実行される操作の動作は、変換先の型に通常割り当てられる他の CLR 式の動作と一致するように、キャストによって変更されます。 継承の割り当てのコンテキストにおいてもキャストは変換可能です。 より厳密なエンティティ サブタイプにオブジェクトを変換して、そのサブタイプに固有のデータへのアクセスを可能にすることができます。  
  
## <a name="equality-operators"></a>等値演算子  
 LINQ to SQL は、LINQ to SQL クエリ内の基本データ型で次の等値演算子をサポートします。  
  
-   等値演算子および非等値演算子 : 等値演算子および非等値演算子は、数値型、<xref:System.Boolean> 型、<xref:System.DateTime> 型、および <xref:System.TimeSpan> 型についてサポートされます。 詳細については[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]演算子`=`と`<>`を参照してください[比較演算子](~/docs/visual-basic/language-reference/operators/comparison-operators.md)です。 C# の比較演算子の詳細については`==`と`!=`を参照してください[演算子 = =](~/docs/csharp/language-reference/operators/equality-comparison-operator.md)と[! = 演算子](~/docs/csharp/language-reference/operators/not-equal-operator.md)、それぞれ  
  
-   Is 演算子 : `IS` 演算子には、継承の割り当ての使用時にサポートされる変換があります。 これは、オブジェクトが特定の種類のエンティティであるかどうかを検査する場合に、判別列を直接調べる代わりとして使用でき、判別列のチェックに変換されます。 Visual Basic および C# の場合は、演算子の詳細については、次を参照してください。 [Is 演算子](~/docs/visual-basic/language-reference/operators/is-operator.md)と[は](~/docs/csharp/language-reference/keywords/is.md)します。  
  
## <a name="see-also"></a>関連項目  
 [SQL CLR の型マッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [データ型および関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
