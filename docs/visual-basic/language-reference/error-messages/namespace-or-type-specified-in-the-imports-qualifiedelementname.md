---
title: インポートで指定された Namespace または型&#39; &lt;qualifiedelementname&gt; &#39;しません&#39;t がすべてのパブリック メンバーを含めるか、または見つかりません
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8be0df5cbe4b8d4a640c9b6c2e126b3828254fd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595106"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>インポートで指定された Namespace または型&#39; &lt;qualifiedelementname&gt; &#39;しません&#39;t がすべてのパブリック メンバーを含めるか、または見つかりません
インポートで指定された Namespace または型\<qualifiedelementname >'、パブリック メンバーが含まれていないか、または見つかりません。 確認してください、名前空間または型が定義されている少なくとも 1 つのパブリック メンバーが含まれています。 エイリアス名には他のエイリアスが含まれていないことを確認してください。  
  
 `Imports`見つからない、またはいずれかを一切定義しませんをコンテナー要素を指定してステートメント`Public`メンバー。  
  
 A*要素を含む*名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。 コンテナー要素には、変数、プロシージャ、または他のコンテナー要素などのメンバーが含まれています。  
  
 インポートの目的は、それらを修飾することがなく、名前空間または型メンバーにアクセスするようにコードを許可します。 プロジェクトは、名前空間または型への参照を追加する必要もあります。 詳細については、「を含む要素をインポートする」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)です。  
  
 コンパイラに指定されたコンテナーの要素が見つからない場合、それを使用する参照を解決できません。 かどうか、要素が見つかったが、要素はいずれかを公開しません`Public`メンバー、その参照はありませんが、成功することができます。 どちらの場合は意味が要素をインポートします。  
  
 コンテナー要素をインポートしてインポート エイリアスを割り当てる場合、使用できないことそのインポート エイリアスを別の要素をインポートすることに注意してください。 次のコードには、コンパイラ エラーが発生します。  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **エラー ID:** BC40056  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  コンテナー要素に、プロジェクトからアクセスできることを確認します。  
  
2.  親要素の仕様に別のインポートからのインポート エイリアスが含まれていないことを確認します。  
  
3.  コンテナーの要素が少なくとも 1 つを公開することを確認`Public`メンバー。  
  
## <a name="see-also"></a>関連項目  
 [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
