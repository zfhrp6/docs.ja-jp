---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 4f34f7f4ada3f8d61c9d855eab1b8b073a3d5ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599204"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
プロパティの記述が読み取らないことを指定します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="rules"></a>ルール  
 **宣言コンテキスト。** `WriteOnly` は、モジュール レベルでのみ使用できます。 つまりの宣言コンテキスト、`WriteOnly`プロパティは、クラス、構造体、またはモジュールにある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。  
  
 としてプロパティを宣言する`WriteOnly`が変数ではありません。  
  
## <a name="when-to-use-writeonly"></a>WriteOnly を使用する場合  
 コンシューマー コード値を設定するができないことができる場合があります。 たとえば、ソーシャル登録番号やパスワードなどの機密データを設定していないすべてのコンポーネントによるアクセスから保護する必要があります。 このような場合は、使用することができます、`WriteOnly`プロパティ値を設定します。  
  
> [!IMPORTANT]
>  定義して使用するときに、`WriteOnly`プロパティ、次の追加の保護手段を検討してください。  
  
-   **上書きします。** 場合は、プロパティ、クラスのメンバーである、許可が既定に[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、宣言しないと`Overridable`または`MustOverride`です。 これは派生クラスがオーバーライドによって不要なアクセスを作成することを防ぎます。  
  
-   **アクセス レベル。** 1 つまたは複数の変数で、プロパティの機密データを保持する場合は、宣言[プライベート](../../../visual-basic/language-reference/modifiers/private.md)できるように、その他のコードはアクセスできません。  
  
-   **暗号化します。** プレーン テキストではなく、暗号化された形式では、すべての機密データを格納します。 何らかの理由で、悪意のあるコードそのメモリ領域にアクセスできる場合より少なく、データを使用します。 暗号化も機密データをシリアル化する必要がある場合に役立ちます。  
  
-   **リセットしています。** クラス、構造体、またはプロパティを定義するモジュールが終了するときに既定値またはその他の意味のない値に機微なデータをリセットします。 これにより、一般的なアクセスにそのメモリ領域が解放されるとき、保護を強化できます。  
  
-   **永続化します。** これを回避する場合、たとえば、ディスク上の任意の機密データは保持されません。 クリップボードには、機密データは書き込みませんも、します。  
  
 `WriteOnly`修飾子は、このコンテキストで使用できます。  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)
