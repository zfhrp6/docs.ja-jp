---
title: 参照できません &#39;です。&lt;名前&gt;&#39;以外の値に型指定されたフィールド &#39; のメンバーになっているため&lt;名前&gt;&#39; クラス &#39; の&lt;classname&gt;&#39; を持つ &#39;'System.marshalbyrefobject' &#39;基底クラスとして
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="b396f-102">参照できません &#39;です。&lt;名前&gt;&#39;以外の値に型指定されたフィールド &#39; のメンバーになっているため&lt;名前&gt;&#39; クラス &#39; の&lt;classname&gt;&#39; を持つ &#39;'System.marshalbyrefobject' &#39;基底クラスとして</span><span class="sxs-lookup"><span data-stu-id="b396f-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="b396f-103">`System.MarshalByRefObject`クラスには、アプリケーション ドメインの境界を越えてオブジェクトへのリモート アクセスをサポートするアプリケーションができるようにします。</span><span class="sxs-lookup"><span data-stu-id="b396f-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="b396f-104">型を継承する必要があります、`MarshalByRejectObject`クラスの種類をアプリケーション ドメインの境界を越えて使用するとします。</span><span class="sxs-lookup"><span data-stu-id="b396f-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="b396f-105">オブジェクトのメンバーが作成されたアプリケーション ドメインの外部で使用可能ではないために、オブジェクトの状態はコピーされません必要があります。</span><span class="sxs-lookup"><span data-stu-id="b396f-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="b396f-106">**エラー ID:** BC30310</span><span class="sxs-lookup"><span data-stu-id="b396f-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b396f-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b396f-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="b396f-108">参照されているメンバーは、有効かどうかを確認への参照を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b396f-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="b396f-109">持つメンバーを明示的に修飾、`Me`キーワード。</span><span class="sxs-lookup"><span data-stu-id="b396f-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b396f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b396f-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="b396f-111">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="b396f-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
