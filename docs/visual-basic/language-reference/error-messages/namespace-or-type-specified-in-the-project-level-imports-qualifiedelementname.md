---
title: "プロジェクト レベルのインポートで指定された Namespace または型&lt;qualifiedelementname&gt;&quot; すべてのパブリック メンバーが含まれていないか、見つけることはできません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
dev_langs:
- VB
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 301e2bd419f0b4723ff76c2bdd2187c4c412e174
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="0358a-102">プロジェクト レベルのインポートで指定された Namespace または型&lt;qualifiedelementname&gt;' すべてのパブリック メンバーが含まれていないか、見つけることはできません</span><span class="sxs-lookup"><span data-stu-id="0358a-102">Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="0358a-103">プロジェクト レベルのインポートで指定された Namespace または型\<qualifiedelementname >' すべてのパブリック メンバーが含まれていないか、見つけることはできません。</span><span class="sxs-lookup"><span data-stu-id="0358a-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="0358a-104">名前空間または型が定義され、少なくとも&1; つのパブリック メンバーを含むことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0358a-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="0358a-105">エイリアス名には、他のエイリアスにはが含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0358a-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="0358a-106">見つからない、またはいずれかが定義されていませんのあるコンテナーの要素を指定して、プロジェクトのインポート プロパティ`Public`メンバーです。</span><span class="sxs-lookup"><span data-stu-id="0358a-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="0358a-107">A*要素を含む*名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="0358a-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="0358a-108">コンテナー要素には、変数、プロシージャ、または他のコンテナー要素などのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0358a-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="0358a-109">インポートの目的は、修飾しなくても、コードを名前空間または型のメンバーへのアクセスを許可するようにです。</span><span class="sxs-lookup"><span data-stu-id="0358a-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="0358a-110">プロジェクトは、名前空間または型への参照を追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="0358a-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="0358a-111">詳細については、「を含む要素のインポート」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。</span><span class="sxs-lookup"><span data-stu-id="0358a-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="0358a-112">コンパイラでは、指定されたコンテナー要素を見つけられない場合、それを使用して参照を解決できません。</span><span class="sxs-lookup"><span data-stu-id="0358a-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="0358a-113">要素はいずれかを公開しませんが、要素が見つかった`Public`メンバー、参照が成功することができます。</span><span class="sxs-lookup"><span data-stu-id="0358a-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="0358a-114">いずれの場合は、要素をインポートしても意味です。</span><span class="sxs-lookup"><span data-stu-id="0358a-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="0358a-115">使用する、**プロジェクト デザイナー**をインポートする要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="0358a-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="0358a-116">使用して、**インポートされた名前空間**のセクションで、**参照**ページです。</span><span class="sxs-lookup"><span data-stu-id="0358a-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="0358a-117">表示する、**プロジェクト デザイナー**をダブルクリックして、 **My Project**アイコン**ソリューション エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="0358a-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="0358a-118">**エラー ID:** BC40057</span><span class="sxs-lookup"><span data-stu-id="0358a-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0358a-119">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0358a-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="0358a-120">開いている、**プロジェクト デザイナー**に切り替えると、**参照**ページです。</span><span class="sxs-lookup"><span data-stu-id="0358a-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="0358a-121">**インポートされた名前空間**セクションで、コンテナーの要素が、プロジェクトからアクセス可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0358a-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="0358a-122">コンテナーの要素が少なくとも&1; つを公開することを確認`Public`メンバーです。</span><span class="sxs-lookup"><span data-stu-id="0358a-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0358a-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0358a-123">See Also</span></span>  
 <span data-ttu-id="0358a-124">[[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="0358a-124">[References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="0358a-125"> [NIB 方法: プロジェクトのプロパティと構成設定の変更](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="0358a-125"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="0358a-126"> [パブリック](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="0358a-126"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="0358a-127"> [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="0358a-127"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="0358a-128"> [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="0358a-128"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
