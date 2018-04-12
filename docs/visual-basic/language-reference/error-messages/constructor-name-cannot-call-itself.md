---
title: コンス トラクター &#39;&lt;名前&gt;&#39; 自体を呼び出すことはできません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2361d6f4d710e17a4f4e29ac03bfde523191fa83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>コンス トラクター &#39;&lt;名前&gt;&#39; 自体を呼び出すことはできません
A`Sub New`クラスまたは構造体でプロシージャを呼び出します。  
  
 クラスのインスタンスを初期化するコンス トラクターの目的は、またはそのが最初に構造を作成します。 異なるパラメーター リストを持っている、それらはすべて、クラスまたは構造体によって複数のコンス トラクター、することができます。 それ自体に加え、その機能を実行する別のコンス トラクターを呼び出し、コンス トラクターを許可します。 コンス トラクターをそれ自体を呼び出すの意味がなく、実際に結果は無限再帰の許可されている場合。  
  
 **エラー ID:** BC30298  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  呼び出されるコンス トラクターのパラメーター リストを確認してください。 呼び出すコンス トラクターの場合と異なる場合があります。  
  
2.  別のコンス トラクターを呼び出す予定がない場合は、削除、`Sub New`完全呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクトの有効期間 : オブジェクトの作成と破棄](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
