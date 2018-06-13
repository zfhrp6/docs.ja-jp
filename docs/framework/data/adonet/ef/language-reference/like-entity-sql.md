---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f2d06b364c577b581bb64af0436c133ca830bb2b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763041"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
指定された文字列 `String` が指定されたパターンと一致するかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>引数  
 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]に評価される式、`String`です。  
  
 `pattern`  
 指定された `String` に一致するパターン。  
  
 `escape`  
 エスケープ文字。  
  
 NOT  
 LIKE の結果を否定することを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true` がパターンに一致する場合は `string`、一致しない場合は `false`。  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 演算子を使用する式は、フィルター条件として等価性を使用する式と同じように評価されます。 ただし、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 演算子を使用する式は、リテラルとワイルドカード文字の両方を含めることができます。  
  
 次の表では、パターン `string` の構文について説明します。  
  
|ワイルドカード文字|説明|例|  
|------------------------|-----------------|-------------|  
|%|0 個またはそれ以上の文字で構成される任意の `string` です。|`title like '%computer%'` 単語のすべてのタイトルを検索`"computer"`タイトルに任意の場所。|  
|_ (アンダースコア)|任意の 1 文字です。|`firstname like '_ean'` 検索で終了するすべての 4 文字目名前`"ean`、"Dean や Sean などです。|  
|[ ]|指定した範囲 ([a-f]) またはセット ([abcdef]) にある任意の 1 文字です。|`lastname like '[C-P]arsen'` 姓が検索"arsen"で終わる C ~ P、Carsen や Larsen などの任意の 1 文字で始まります。|  
|[^]|指定した範囲 ([^a-f]) またはセット ([^abcdef]) にない任意の 1 文字です。|`lastname like 'de[^l]%'` "de"で始まり、"l"で、次の文字を含めないでくださいすべての姓を検索します。|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の LIKE 演算子および ESCAPE 句は、`System.DateTime` または `System.Guid` 値には適用できません。  
  
 LIKE では、ASCII パターン マッチと Unicode パターン マッチがサポートされています。 すべてのパラメーターが ASCII 文字の場合は、ASCII パターン マッチが行われます。 1 つまたは複数の引数が Unicode の場合は、すべての引数が Unicode に変換され、Unicode パターン マッチが行われます。 LIKE で Unicode を使用する場合、後続する空白は意味を持ちます。しかし、Unicode 以外のデータの場合、後続する空白は意味を持ちません。 パターン文字列構文[!INCLUDE[esql](../../../../../../includes/esql-md.md)]のと同じ[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]です。  
  
 パターンは、標準の文字とワイルドカード文字を含むことができます。 パターン マッチ時に、標準の文字は `string` に指定された文字と正確に一致する必要があります。 しかし、ワイルドカード文字は文字列の任意の部分と一致することができます。 ワイルドカード文字を使用する場合、LIKE 演算子は = や != などの文字列比較演算子よりも柔軟です。  
  
> [!NOTE]
>  特定のプロバイダーを対象とする場合は、プロバイダー固有の拡張機能を使用できます。 ただし、たとえばコンストラクターの扱いは、プロバイダーによって異なる場合があります。 SqlServer では、[first-last] および [^first-last] のパターンがサポートされています。前者は先頭と末尾の間の 1 文字が完全に一致し、後者は先頭と末尾の間以外の 1 文字が完全に一致します。  
  
### <a name="escape"></a>エスケープ特殊文字  
 前のセクションの表で説明しているように、ESCAPE 句を使用することで、1 文字以上の特殊なワイルドカード文字を含む文字列を検索できます。 たとえば、複数のドキュメントのタイトルにリテラル "100%" が含まれており、そのドキュメントすべてを検索するとします。 使用してエスケープする必要があります、パーセント (%) 文字は、ワイルドカード文字であるため、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE 句検索を正常に実行します。 このフィルターの例は次のとおりです。  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 この検索式では、感嘆符文字 (!) の直後のパーセント ワイルドカード文字 (%) は、ワイルドカード文字としてではなく、リテラルとして処理されます。 以外のエスケープ文字として任意の文字を使用することができます、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]ワイルドカード文字および角かっこ (`[ ]`) 文字です。 前の例では、感嘆符 (!) 文字はエスケープ文字です。  
  
## <a name="example"></a>例  
 次の 2 つ[!INCLUDE[esql](../../../../../../includes/esql-md.md)]クエリで使用、LIKE および ESCAPE 演算子、特定の文字の文字列かどうかを決定を指定したパターンに一致します。 最初のクエリを検索、`Name`文字で始まる`Down_`です。 アンダースコア (`_`) はワイルドカード文字であるため、このクエリは ESCAPE オプションを使用します。 ESCAPE オプションを指定せず、クエリはいずれかを検索`Name`という単語で始まる値`Down`後にアンダー スコア文字以外の 1 文字です。 クエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。  
  
2.  次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
