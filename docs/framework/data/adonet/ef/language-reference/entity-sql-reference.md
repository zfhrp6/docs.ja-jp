---
title: Entity SQL リファレンス
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: ac05ec8a8732da383a4e33e84c669aa29660a0da
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="entity-sql-reference"></a>Entity SQL リファレンス
このセクションには、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 参照に関するトピックがあります。 このトピックでは、カテゴリ別に [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子をグループ化し、その概要を説明します。  
  
## <a name="arithmetic-operators"></a>算術演算子  
 算術演算子は、数値データ型が 1 つ以上含まれる 2 つの式の間で、数学的な操作を実行します。 次の表は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の算術演算子の一覧です。  
  
|演算子|使用|  
|--------------|---------|  
|[+ (加算)](../../../../../../docs/framework/data/adonet/ef/language-reference/add.md)|加算。|  
|「/(除算)」|除算。|  
|[% (剰余)](../../../../../../docs/framework/data/adonet/ef/language-reference/modulo-entity-sql.md)|除算の剰余|  
|[* (乗算)](../../../../../../docs/framework/data/adonet/ef/language-reference/multiply-entity-sql.md)|乗算。|  
|[- (負符号)](../../../../../../docs/framework/data/adonet/ef/language-reference/negative-entity-sql.md)|否定|  
|[- (減算)](../../../../../../docs/framework/data/adonet/ef/language-reference/subtract-entity-sql.md)|減算。|  
  
## <a name="canonical-functions"></a>正規関数  
 正規関数とは、すべてのデータ プロバイダーがサポートし、あらゆるクエリ テクノロジで使用できる関数です。 次の表に正規関数を示します。  
  
|関数|型|  
|--------------|----------|  
|[集計 Entity SQL 正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|集計 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数について説明します。|  
|[数値演算正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|数学 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数について説明します。|  
|[文字列正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|文字列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数について説明します。|  
|[日付と時刻の正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|日付および時刻の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数について説明します。|  
|[ビット単位の正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|ビット単位の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数について説明します。|  
|[その他の正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)|ビット単位、日付/時刻、文字列、数学、または集計に分類されない関数について説明します。|  
  
## <a name="comparison-operators"></a>比較演算子  
 比較演算子は、`Byte`、`Int16`、`Int32`、`Int64`、`Double`、`Single`、`Decimal`、`String`、`DateTime`、`Date`、`Time`、`DateTimeOffset` のデータ型に対して定義されます。 比較演算子が適用される前に、オペランドに対して暗黙の型の昇格が行われます。 比較演算子は常にブール値を取得します。 1 つ以上のオペランドが `null` である場合、結果は `null` になります。  
  
 等価演算子および非等価演算子は、`Boolean` 型など、ID を持つオブジェクト型に対して定義されます。 ID を含む非プリミティブ オブジェクトは、同じ ID を共有している場合に等価と見なされます。 次の表は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の比較演算子の一覧です。  
  
|演算子|説明|  
|--------------|-----------------|  
|[= (等しい)](../../../../../../docs/framework/data/adonet/ef/language-reference/equals-entity-sql.md)|2 つの式の等価性を比較します。|  
|[> (より大きい)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値よりも大きいかどうかを判別します。|  
|[>= (以上)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-or-equal-to-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値以上であるかどうかを判別します。|  
|[IS &#91;NOT&#93; NULL](../../../../../../docs/framework/data/adonet/ef/language-reference/isnull-entity-sql.md)|クエリ式が NULL かどうかを調べます。|  
|[< (より小さい)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値よりも小さいかどうかを判別します。|  
|[<= (以下)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-or-equal-to-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値以下であるかどうかを判別します。|  
|[&AMP;#91;いない&AMP;#93;BETWEEN](../../../../../../docs/framework/data/adonet/ef/language-reference/between-entity-sql.md)|式の結果が指定の範囲内の値になるかどうかを判断します。|  
|[!= (等しくない)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-equal-to-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値と等しくないかどうかを判別します。|  
|[&AMP;#91;いない&AMP;#93;など](../../../../../../docs/framework/data/adonet/ef/language-reference/like-entity-sql.md)|指定された文字列が指定されたパターンと一致するかどうかを判断します。|  
  
## <a name="logical-and-case-expression-operators"></a>論理演算子と CASE 式演算子  
 論理演算子は、条件の真偽をテストします。 CASE 式は、一連のブール式を評価して結果を判定します。 次の表に論理演算子と CASE 式演算子を示します。  
  
|演算子|説明|  
|--------------|-----------------|  
|[& & (論理 AND)](../../../../../../docs/framework/data/adonet/ef/language-reference/and-entity-sql.md)|論理 AND。|  
|[!(論理 NOT)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-entity-sql.md)|論理 NOT。|  
|[&#124;&#124;(論理 OR)](../../../../../../docs/framework/data/adonet/ef/language-reference/or-entity-sql.md)|論理 OR。|  
|[CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)|一連のブール式を評価して結果を決定します。|  
|[THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)|結果、[とき](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998)句を true に評価された場合。|  
  
## <a name="query-operators"></a>クエリ演算子  
 クエリ演算子は、エンティティ データを返すクエリ式を定義するために使用されます。 次の表にクエリ演算子を示します。  
  
|演算子|使用|  
|--------------|---------|  
|[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)|使用されているコレクションを示す[選択](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)ステートメントです。|  
|[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)|クエリによって返されるをオブジェクト グループを指定します ([選択](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) を配置する式は、します。|  
|[GroupPartition](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)|引数値のコレクションを返します。この値は、集計の関係先であるグループ パーティションから投影されたものです。|  
|[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)|グループまたは集計の検索条件を指定します。|  
|[LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)|使用される、 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)句物理ページングを実行します。|  
|[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)|返されたオブジェクトで使用されている並べ替え順序を指定します、[選択](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)ステートメントです。|  
|[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)|クエリによって返される投影の要素を指定します。|  
|[SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)|使用される、 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)句物理ページングを実行します。|  
|[TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)|クエリ結果の先頭から指定した行セットだけを返すよう指定します。|  
|[WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)|クエリによって返されるデータを条件に基づいてフィルター処理します。|  
  
## <a name="reference-operators"></a>リファレンス演算子  
 リファレンスは、特定のエンティティ セットにある特定のエンティティへの論理ポインター (外部キー) です。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 構築、分解、および参照を使用して移動するには、次の演算子をサポートしています。  
  
|演算子|使用|  
|--------------|---------|  
|[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)|エンティティ セット内のエンティティへの参照を作成します。|  
|[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)|参照値を逆参照し、その逆参照の結果を生成します。|  
|[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)|参照またはエンティティ式のキーを抽出します。|  
|[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)|リレーションシップ内のエンティティ型間を移動するために使用します。|  
|[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)|エンティティ インスタンスへの参照を返します。|  
  
## <a name="set-operators"></a>集合演算子  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は各種の強力な集合演算機能を備えています。 これには、set 演算子 UNION、INTERSECT、EXCEPT などの TRANSACT-SQL 演算子に似ていますが含まれます、および EXISTS です。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、重複排除 (SET)、メンバーシップのテスト (IN)、および結合 (JOIN) の演算子もサポートされています。 次の表に [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子を示します。  
  
|演算子|使用|  
|--------------|---------|  
|[ANYELEMENT](../../../../../../docs/framework/data/adonet/ef/language-reference/anyelement-entity-sql.md)|複数値のコレクションから要素を抽出します。|  
|[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)|EXCEPT オペランドの左辺のクエリ式から返される結果のうち、右辺のクエリ式でも返される結果を除いた、重複しない値のコレクションを返します。|  
|[&AMP;#91;いない&AMP;#93;EXISTS](../../../../../../docs/framework/data/adonet/ef/language-reference/exists-entity-sql.md)|コレクションが空かどうかを調べます。|  
|[FLATTEN](../../../../../../docs/framework/data/adonet/ef/language-reference/flatten-entity-sql.md)|コレクションのコレクションをフラット化して単一のコレクションに変換します。|  
|[&#91;NOT&#93; IN](../../../../../../docs/framework/data/adonet/ef/language-reference/in-entity-sql.md)|コレクション内に一致する値があるかどうかを調べます。|  
|[INTERSECT](../../../../../../docs/framework/data/adonet/ef/language-reference/intersect-entity-sql.md)|INTERSECT オペランドの左右両方のクエリ式によって返される個別の値のコレクションを返します。|  
|[OVERLAPS](../../../../../../docs/framework/data/adonet/ef/language-reference/overlaps-entity-sql.md)|2 つのコレクションに共通の要素が存在するかどうかを調べます。|  
|[SET](../../../../../../docs/framework/data/adonet/ef/language-reference/set-entity-sql.md)|重複する要素をすべて除外した新しいコレクションを生成することによって、オブジェクトのコレクションを 1 つの集合に変換するために使用されます。|  
|[UNION](../../../../../../docs/framework/data/adonet/ef/language-reference/union-entity-sql.md)|複数のクエリの結果を 1 つのコレクションに結合します。|  
  
## <a name="type-operators"></a>型演算子  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 式 (値) を作成、照会、および操作の種類を許可する操作を提供します。 次の表に型の操作に使用される演算子を示します。  
  
|演算子|使用|  
|--------------|---------|  
|[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)|あるデータ型の式を別のデータ型に変換します。|  
|[COLLECTION](../../../../../../docs/framework/data/adonet/ef/language-reference/collection-entity-sql.md)|使用される、[関数](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)宣言エンティティ型または複合型のコレクションを操作します。|  
|[&AMP;#91;いない&AMP;#93;の](../../../../../../docs/framework/data/adonet/ef/language-reference/isof-entity-sql.md)|式の型が指定の型であるか、またはそのサブタイプであるかを判断します。|  
|[OFTYPE](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)|クエリ式を使用して、指定された型のオブジェクトのコレクションを返します。|  
|[名前付きの型コンストラクター](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)|エンティティ型または複合型のインスタンスの作成に使用されます。|  
|[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)|値のリストからマルチセットのインスタンスを作成します。|  
|[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)|1 つまたは複数の値から構造的に型付けされた匿名レコードを構築します。|  
|[TREAT](../../../../../../docs/framework/data/adonet/ef/language-reference/treat-entity-sql.md)|特定の基本データ型のオブジェクトを指定の派生型のオブジェクトとして処理します。|  
  
## <a name="other-operators"></a>その他の演算子  
 次の表の[!INCLUDE[esql](../../../../../../includes/esql-md.md)]演算子。  
  
|演算子|使用|  
|--------------|---------|  
|[+ (文字列連結)](../../../../../../docs/framework/data/adonet/ef/language-reference/string-concatenation-entity-sql.md)|[!INCLUDE[esql](../../../../../../includes/esql-md.md)] で文字列を連結するために使用されます。|  
|[。(メンバー アクセス)](../../../../../../docs/framework/data/adonet/ef/language-reference/member-access-entity-sql.md)|構造型概念モデル型のインスタンスのプロパティ値またはフィールド値にアクセスするために使用されます。|  
|[-- (コメント)](../../../../../../docs/framework/data/adonet/ef/language-reference/comment-entity-sql.md)|[!INCLUDE[esql](../../../../../../includes/esql-md.md)] コメントを含めます。|  
|[FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)|Entity SQL クエリで実行できるインライン関数を定義します。|  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL 言語](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
