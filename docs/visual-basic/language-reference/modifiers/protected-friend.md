---
title: 保護されたフレンド (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306543"
---
# <a name="protected-friend-visual-basic"></a>保護されたフレンド (Visual Basic)

`Protected Friend`キーワードの組み合わせは、メンバー アクセス修飾子。 両方を設定する[フレンド](friend.md)アクセスおよび[Protected](protected.md)に独自のクラスおよび派生クラスからは、同じアセンブリに任意の場所からアクセスできるように、宣言された要素にアクセスします。 指定できます`Protected Friend`クラスのメンバーにのみ適用することはできません`Protected Friend`構造体のメンバーにため、構造体は継承できません。

> [!NOTE]
> Visual Studio で、の F1 ヘルプ`protected friend`いずれかのヘルプを提供[保護](protected.md)または[フレンド](friend.md)です。 IDE では、複合語ではなく、カーソルの下にある 1 つのトークンを取得します。

## <a name="rules"></a>ルール

- **宣言コンテキスト。** 使用することができます`Protected Friend`クラス レベルでのみです。 つまりの宣言コンテキスト、`Protected`要素がクラスである必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。 


## <a name="see-also"></a>関連項目

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[保護されたプライベート](./private-protected.md)   
[Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
