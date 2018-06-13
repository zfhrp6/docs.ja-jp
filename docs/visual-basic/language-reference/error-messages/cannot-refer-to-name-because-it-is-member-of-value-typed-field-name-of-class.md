---
title: 参照できません&#39;&lt;名前&gt;&#39;値に型指定されたフィールドのメンバーになっているため&#39;&lt;名前&gt;&#39;クラスの&#39; &lt;classname&gt; &#39;を持つ&#39;'system.marshalbyrefobject'&#39;基底クラスとして
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586348"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>参照できません&#39;&lt;名前&gt;&#39;値に型指定されたフィールドのメンバーになっているため&#39;&lt;名前&gt;&#39;クラスの&#39; &lt;classname&gt; &#39;を持つ&#39;'system.marshalbyrefobject'&#39;基底クラスとして
`System.MarshalByRefObject`クラスには、アプリケーション ドメインの境界を越えてオブジェクトへのリモート アクセスをサポートするアプリケーションができるようにします。 型を継承する必要があります、`MarshalByRejectObject`クラスの種類をアプリケーション ドメインの境界を越えて使用するとします。 オブジェクトのメンバーが作成されたアプリケーション ドメインの外部で使用可能ではないために、オブジェクトの状態はコピーされません必要があります。  
  
 **エラー ID:** BC30310  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  参照されているメンバーは、有効かどうかを確認への参照を確認してください。  
  
2.  持つメンバーを明示的に修飾、`Me`キーワード。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.MarshalByRefObject>  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
