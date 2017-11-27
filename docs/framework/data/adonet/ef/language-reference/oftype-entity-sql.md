---
title: OFTYPE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd2660eb5fddd0c75b44d0796edce37c83865e81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
クエリ式を使用して、指定された型のオブジェクトのコレクションを返します。  
  
## <a name="syntax"></a>構文  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 オブジェクトのコレクションを返す任意の有効なクエリ式。  
  
 `test_type`  
 `expression` から返される各オブジェクトを判定するための型。 型は名前空間で修飾する必要があります。  
  
## <a name="return-value"></a>戻り値  
 `test_type`型であるか、 `test_type`の基本データ型または派生型であるオブジェクトのコレクション。 ONLY を指定した場合、 `test_type` のインスタンスまたは空のコレクションのみ返されます。  
  
## <a name="remarks"></a>コメント  
 `OFTYPE` 式は、コレクションの各要素の型を判定するための式です。  `OFTYPE` 式では、指定された型の新しいコレクションが生成されます。生成されたコレクションには、指定された型と同じか、そのサブタイプの要素だけが格納されます。  
  
 `OFTYPE` 式は、次のクエリ式の省略形です。  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Manager が Employee のサブタイプである場合、次の式からは、従業員 (employee) のコレクションのうち、マネージャー (manager) のコレクションだけが返されます。  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 型フィルターを使用してコレクションをアップ キャストすることもできます。  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 すべての企業幹部はマネージャーであるので、結果のコレクションには元の企業幹部がすべて含まれたままですが、コレクションはマネージャーのコレクションとして型指定されています。  
  
 次の表は、いくつかのパターンにおける `OFTYPE` 演算子の動作を示しています。 すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。  
  
|パターン|動作|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Collection(EntityType)|  
|OFTYPE(Collection(ComplexType), ComplexType)|スロー|  
|OFTYPE(Collection(RowType), RowType)|スロー|  
  
## <a name="example"></a>例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、OFTYPE 演算子を使用して、Course オブジェクトのコレクションから OnsiteCourse オブジェクトのコレクションを取得して返します。 このクエリは、 [School モデル](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac)に基づいています。  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
