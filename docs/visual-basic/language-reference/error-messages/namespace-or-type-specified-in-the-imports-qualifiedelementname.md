---
title: "Namespace またはインポート &#39; で指定された型&lt;qualifiedelementname&gt;&#39; しません &#39; t がすべてのパブリック メンバーを含めるか、または見つかりません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords: BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 49cd9fa5d5182b2cf2d7fc4623bc8e9aa02bf85e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="cc4f1-102">Namespace またはインポート &#39; で指定された型&lt;qualifiedelementname&gt;&#39; しません &#39; t がすべてのパブリック メンバーを含めるか、または見つかりません</span><span class="sxs-lookup"><span data-stu-id="cc4f1-102">Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="cc4f1-103">インポートで指定された Namespace または型\<qualifiedelementname >'、パブリック メンバーが含まれていないか、または見つかりません。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="cc4f1-104">確認してください、名前空間または型が定義されている少なくとも 1 つのパブリック メンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="cc4f1-105">エイリアス名には他のエイリアスが含まれていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="cc4f1-106">`Imports`見つからない、またはいずれかを一切定義しませんをコンテナー要素を指定してステートメント`Public`メンバー。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="cc4f1-107">A*要素を含む*名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="cc4f1-108">コンテナー要素には、変数、プロシージャ、または他のコンテナー要素などのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="cc4f1-109">インポートの目的は、それらを修飾することがなく、名前空間または型メンバーにアクセスするようにコードを許可します。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="cc4f1-110">プロジェクトは、名前空間または型への参照を追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="cc4f1-111">詳細については、「を含む要素をインポートする」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="cc4f1-112">コンパイラに指定されたコンテナーの要素が見つからない場合、それを使用する参照を解決できません。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="cc4f1-113">かどうか、要素が見つかったが、要素はいずれかを公開しません`Public`メンバー、その参照はありませんが、成功することができます。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="cc4f1-114">どちらの場合は意味が要素をインポートします。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="cc4f1-115">コンテナー要素をインポートしてインポート エイリアスを割り当てる場合、使用できないことそのインポート エイリアスを別の要素をインポートすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="cc4f1-116">次のコードには、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-116">The following code generates a compiler error.</span></span>  
  
 <span data-ttu-id="cc4f1-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span><span class="sxs-lookup"><span data-stu-id="cc4f1-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span></span>  
  
 <span data-ttu-id="cc4f1-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span><span class="sxs-lookup"><span data-stu-id="cc4f1-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span></span>  
  
 <span data-ttu-id="cc4f1-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span><span class="sxs-lookup"><span data-stu-id="cc4f1-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span></span>  
  
 <span data-ttu-id="cc4f1-120">**エラー ID:** BC40056</span><span class="sxs-lookup"><span data-stu-id="cc4f1-120">**Error ID:** BC40056</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc4f1-121">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="cc4f1-121">To correct this error</span></span>  
  
1.  <span data-ttu-id="cc4f1-122">コンテナー要素に、プロジェクトからアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-122">Verify that the containing element is accessible from your project.</span></span>  
  
2.  <span data-ttu-id="cc4f1-123">親要素の仕様に別のインポートからのインポート エイリアスが含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-123">Verify that the specification of the containing element does not include any import alias from another import.</span></span>  
  
3.  <span data-ttu-id="cc4f1-124">コンテナーの要素が少なくとも 1 つを公開することを確認`Public`メンバー。</span><span class="sxs-lookup"><span data-stu-id="cc4f1-124">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4f1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc4f1-125">See Also</span></span>  
 [<span data-ttu-id="cc4f1-126">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="cc4f1-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="cc4f1-127">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="cc4f1-127">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="cc4f1-128">Public</span><span class="sxs-lookup"><span data-stu-id="cc4f1-128">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="cc4f1-129">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="cc4f1-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="cc4f1-130">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="cc4f1-130">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
