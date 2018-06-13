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
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="88035-102">参照できません&#39;&lt;名前&gt;&#39;値に型指定されたフィールドのメンバーになっているため&#39;&lt;名前&gt;&#39;クラスの&#39; &lt;classname&gt; &#39;を持つ&#39;'system.marshalbyrefobject'&#39;基底クラスとして</span><span class="sxs-lookup"><span data-stu-id="88035-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="88035-103">`System.MarshalByRefObject`クラスには、アプリケーション ドメインの境界を越えてオブジェクトへのリモート アクセスをサポートするアプリケーションができるようにします。</span><span class="sxs-lookup"><span data-stu-id="88035-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="88035-104">型を継承する必要があります、`MarshalByRejectObject`クラスの種類をアプリケーション ドメインの境界を越えて使用するとします。</span><span class="sxs-lookup"><span data-stu-id="88035-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="88035-105">オブジェクトのメンバーが作成されたアプリケーション ドメインの外部で使用可能ではないために、オブジェクトの状態はコピーされません必要があります。</span><span class="sxs-lookup"><span data-stu-id="88035-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="88035-106">**エラー ID:** BC30310</span><span class="sxs-lookup"><span data-stu-id="88035-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88035-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="88035-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="88035-108">参照されているメンバーは、有効かどうかを確認への参照を確認してください。</span><span class="sxs-lookup"><span data-stu-id="88035-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="88035-109">持つメンバーを明示的に修飾、`Me`キーワード。</span><span class="sxs-lookup"><span data-stu-id="88035-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88035-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="88035-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="88035-111">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="88035-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
