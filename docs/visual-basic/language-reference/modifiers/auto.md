---
title: Auto (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a><span data-ttu-id="92684-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92684-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="92684-103">Visual Basic で宣言されている外部プロシージャの外部名に基づいて、.NET Framework の規則に従って文字列をマーシャ リングする必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="92684-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="92684-104">プロジェクト外で定義されたプロシージャを呼び出すときに、Visual Basic コンパイラにはプロシージャを正しく呼び出すために必要な情報へのアクセスはありません。</span><span class="sxs-lookup"><span data-stu-id="92684-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="92684-105">この情報には、プロシージャが配置されている、それを識別する方法、その呼び出しシーケンスおよび戻り値の型が含まれます。 および使用する文字列の文字セットします。</span><span class="sxs-lookup"><span data-stu-id="92684-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="92684-106">[Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)外部プロシージャへの参照を作成し、この必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="92684-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="92684-107">`charsetmodifier`の一部、`Declare`ステートメントが外部プロシージャの呼び出し中に文字列をマーシャ リングするための文字セットの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="92684-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="92684-108">Visual Basic が外部プロシージャ名を外部ファイルを検索する方法にも影響します。</span><span class="sxs-lookup"><span data-stu-id="92684-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="92684-109">`Auto`修飾子は、Visual Basic が、.NET Framework の規則に従って文字列をマーシャ リングし、おり、場合、ランタイム プラットフォームの設定の基本文字を決定する必要があります最初の検索する場合、外部プロシージャ名を変更する必要がありますを指定します。失敗します。</span><span class="sxs-lookup"><span data-stu-id="92684-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="92684-110">詳細についてを参照してください「の文字セット」 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="92684-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="92684-111">文字セットに修飾子が指定されていない場合`Ansi`既定値です。</span><span class="sxs-lookup"><span data-stu-id="92684-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92684-112">コメント</span><span class="sxs-lookup"><span data-stu-id="92684-112">Remarks</span></span>  
 <span data-ttu-id="92684-113">`Auto`修飾子は、このコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="92684-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="92684-114">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="92684-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="92684-115">スマート デバイスの開発者向け注意事項</span><span class="sxs-lookup"><span data-stu-id="92684-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="92684-116">このキーワードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="92684-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92684-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="92684-117">See Also</span></span>  
 [<span data-ttu-id="92684-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="92684-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="92684-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="92684-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="92684-120">キーワード</span><span class="sxs-lookup"><span data-stu-id="92684-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
