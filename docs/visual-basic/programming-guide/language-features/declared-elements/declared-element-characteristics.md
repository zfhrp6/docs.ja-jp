---
title: 宣言された要素の特性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 26c9ec247a0b848d46df063bc7b85ceec30d81c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650895"
---
# <a name="declared-element-characteristics-visual-basic"></a>宣言された要素の特性 (Visual Basic)
A*特性*宣言された要素のコードとの対話方法に影響する要素の特定の側面がします。 宣言された各要素には、関連付けられている次の特性の 1 つ以上があります。  
  
-   *データ型*— 要素が保持できる値、およびそれらの値を格納するしくみです。 詳細については、次を参照してください。[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)です。  
  
-   *有効期間*— 要素が使用可能である実行時間の期間。 詳細については、次を参照してください。 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)です。  
  
-   *スコープ*: その名前を修飾せず、要素を参照するすべてのコードのセット。 詳細については、次を参照してください。[する方法: 変数のスコープを制御](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)です。  
  
-   *アクセス レベル*— できるようにするコードのアクセス許可の要素を使用します。 詳細については、次を参照してください。[する方法: 変数の可用性を制御](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)です。  
  
## <a name="characteristics-of-the-elements"></a>要素の特性  
 次の表は、宣言された要素と 1 つずつに適用される特性を示します。  
  
|要素|データの種類|有効期間|スコープ<sup>1</sup>|アクセス レベル|  
|-------------|---------------|--------------|------------------------|------------------|  
|変数|[はい]|はい|はい|[はい]|  
|定数|[はい]|いいえ|はい|[はい]|  
|列挙|[はい]|いいえ|はい|[はい]|  
|構造体|×|Ｘ|はい|[はい]|  
|プロパティ|[はい]|はい|はい|[はい]|  
|メソッド|×|はい|はい|[はい]|  
|プロシージャ (`Sub`または`Function`)|×|はい|はい|[はい]|  
|プロシージャ パラメーター|[はい]|はい|はい|×|  
|関数の戻り値|[はい]|はい|はい|×|  
|演算子|[はい]|いいえ|はい|[はい]|  
|Interface|×|Ｘ|はい|[はい]|  
|クラス|×|Ｘ|はい|[はい]|  
|event|×|Ｘ|はい|[はい]|  
|Delegate|×|Ｘ|はい|[はい]|  
  
 <sup>1</sup>スコープとも呼ば*可視性*です。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
