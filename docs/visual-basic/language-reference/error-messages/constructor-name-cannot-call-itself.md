---
title: コンス トラクター &#39;&lt;名前&gt;&#39;自体を呼び出すことはできません
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 069de813a0426230e19cddf14c3b83d40a602a41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588997"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>コンス トラクター &#39;&lt;名前&gt;&#39;自体を呼び出すことはできません
A`Sub New`クラスまたは構造体でプロシージャを呼び出します。  
  
 クラスのインスタンスを初期化するコンス トラクターの目的は、またはそのが最初に構造を作成します。 異なるパラメーター リストを持っている、それらはすべて、クラスまたは構造体によって複数のコンス トラクター、することができます。 それ自体に加え、その機能を実行する別のコンス トラクターを呼び出し、コンス トラクターを許可します。 コンス トラクターをそれ自体を呼び出すの意味がなく、実際に結果は無限再帰の許可されている場合。  
  
 **エラー ID:** BC30298  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  呼び出されるコンス トラクターのパラメーター リストを確認してください。 呼び出すコンス トラクターの場合と異なる場合があります。  
  
2.  別のコンス トラクターを呼び出す予定がない場合は、削除、`Sub New`完全呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクトの有効期間 : オブジェクトの作成と破棄](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
