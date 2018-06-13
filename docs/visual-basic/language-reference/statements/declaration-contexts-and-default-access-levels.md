---
title: 宣言コンテキストと既定のアクセス レベル (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: b30b1068fe662d5f0318a1712dc4690b79bd739d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605447"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>宣言コンテキストと既定のアクセス レベル (Visual Basic)
このトピックでは、どのデータ型内でどの Visual Basic の型を宣言することができ、どのようなこれらのアクセス レベルを既定値も指定しない場合について説明します。  
  
## <a name="declaration-context-levels"></a>宣言コンテキスト レベル  
 *宣言コンテキスト*プログラミング要素が宣言されているコードの領域。 これが呼び出される別のプログラミング要素は、多くの場合、*要素を含む*です。  
  
 宣言コンテキストのレベル次に示します。  
  
-   *Namespace レベル*: ソース ファイルまたは名前空間内にあるが、クラス、構造体、モジュール、またはインターフェイス  
  
-   *モジュール レベル*: クラス、構造体、モジュール、またはインターフェイス内にあるが、プロシージャまたはブロック  
  
-   *プロシージャ レベル*— プロシージャまたはブロック内 (など`If`または`For`)  
  
 次の表は、その宣言コンテキストに応じて、さまざまな宣言されたプログラミングの要素の既定のアクセス レベルを示します。  
  
|宣言された要素|Namespace レベル|モジュール レベル|プロシージャ レベル|  
|----------------------|---------------------|------------------|---------------------|  
|変数 ([Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md))|許可されていません|`Private` (`Public`で`Structure`で許可されていない、 `Interface`)|`Public`|  
|定数 ([Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md))|許可されていません|`Private` (`Public`で`Structure`で許可されていない、 `Interface`)|`Public`|  
|列挙 ([Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|許可されていません|  
|クラス ([Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|許可されていません|  
|構造体 ([ステートメントを構造体](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|許可されていません|  
|モジュール ([モジュール ステートメント](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|許可されていません|許可されていません|  
|インターフェイス ([Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|許可されていません|  
|プロシージャ ([関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)、 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md))|許可されていません|`Public`|許可されていません|  
|外部参照 ([Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md))|許可されていません|`Public` (では許可されません`Interface`)|許可されていません|  
|演算子 ([Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md))|許可されていません|`Public` (では許可されません`Interface`または`Module`)|許可されていません|  
|プロパティ ([Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md))|許可されていません|`Public`|許可されていません|  
|既定のプロパティ ([既定](../../../visual-basic/language-reference/modifiers/default.md))|許可されていません|`Public` (では許可されません`Module`)|許可されていません|  
|イベント ([Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md))|許可されていません|`Public`|許可されていません|  
|デリゲート ([Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|許可されていません|  
  
 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)
