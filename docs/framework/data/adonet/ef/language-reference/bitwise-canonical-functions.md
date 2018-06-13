---
title: ビット単位の正規関数
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: df3b81a47b8e1202884a5c38f55c7061279b245f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761195"
---
# <a name="bitwise-canonical-functions"></a>ビット単位の正規関数
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] にはビット単位の正規関数があります。  
  
## <a name="remarks"></a>コメント  
 次の表に、ビット単位の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数を示します。 これらの関数が返す`Null`場合`Null`入力を提供します。 戻り値の型は、引数の型と同じです。 複数の引数を関数が受け取る場合、それらの引数は同じ型にする必要があります。 異なる型でビット単位の演算を実行するには、明示的に同じ型にキャストする必要があります。  
  
|関数|説明|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|`value1` と `value2` のビット単位の論理積を `value1` と `value2` の型で返します。<br /><br /> **引数**<br /><br /> A `Byte`、 `Int16`、 `Int32`、および`Int64`です。<br /><br /> **例**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|`value` のビット単位の否定を返します。<br /><br /> **引数**<br /><br /> A `Byte`、 `Int16`、 `Int32`、および`Int64`です。<br /><br /> **例**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|`value1` と `value2` のビット単位の論理和を `value1` と `value2` の型で返します。<br /><br /> **引数**<br /><br /> A `Byte`、 `Int16`、`Int32`と`Int64`です。<br /><br /> **例**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|`value1` と `value2` のビット単位の排他的論理和を `value1` と `value2` の型で返します。<br /><br /> **引数**<br /><br /> A `Byte`、 `Int16`、`Int32`と`Int64`です。<br /><br /> **例**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>関連項目  
 [正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
