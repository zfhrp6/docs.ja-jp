---
title: プロジェクト レベル インポートで指定された Namespace または型&#39; &lt;qualifiedelementname&gt; &#39;しません&#39;t がすべてのパブリック メンバーを含めるか、または見つかりません
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: d6d0c931262d892ec3e65888a76f25218b23d868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="1ac72-102">プロジェクト レベル インポートで指定された Namespace または型&#39; &lt;qualifiedelementname&gt; &#39;しません&#39;t がすべてのパブリック メンバーを含めるか、または見つかりません</span><span class="sxs-lookup"><span data-stu-id="1ac72-102">Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="1ac72-103">プロジェクト レベル インポートで指定された Namespace または型\<qualifiedelementname >'、パブリック メンバーが含まれていないか、または見つかりません。</span><span class="sxs-lookup"><span data-stu-id="1ac72-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="1ac72-104">確認してください、名前空間または型が定義されている少なくとも 1 つのパブリック メンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ac72-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="1ac72-105">エイリアス名には他のエイリアスが含まれていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1ac72-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="1ac72-106">見つからない、またはいずれかを一切定義しませんをコンテナー要素を指定して、プロジェクトのインポート プロパティ`Public`メンバー。</span><span class="sxs-lookup"><span data-stu-id="1ac72-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="1ac72-107">A*要素を含む*名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1ac72-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="1ac72-108">コンテナー要素には、変数、プロシージャ、または他のコンテナー要素などのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ac72-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="1ac72-109">インポートの目的は、それらを修飾することがなく、名前空間または型メンバーにアクセスするようにコードを許可します。</span><span class="sxs-lookup"><span data-stu-id="1ac72-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="1ac72-110">プロジェクトは、名前空間または型への参照を追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="1ac72-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="1ac72-111">詳細については、「を含む要素をインポートする」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ac72-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="1ac72-112">コンパイラに指定されたコンテナーの要素が見つからない場合、それを使用する参照を解決できません。</span><span class="sxs-lookup"><span data-stu-id="1ac72-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="1ac72-113">かどうか、要素が見つかったが、要素はいずれかを公開しません`Public`メンバー、その参照はありませんが、成功することができます。</span><span class="sxs-lookup"><span data-stu-id="1ac72-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="1ac72-114">どちらの場合は意味が要素をインポートします。</span><span class="sxs-lookup"><span data-stu-id="1ac72-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="1ac72-115">使用する、**プロジェクト デザイナー**をインポートする要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="1ac72-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="1ac72-116">使用して、**インポートされた名前空間**のセクションで、**参照**ページ。</span><span class="sxs-lookup"><span data-stu-id="1ac72-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="1ac72-117">取得する、**プロジェクト デザイナー**をダブルクリックして、 **My Project**アイコン**ソリューション エクスプ ローラー**です。</span><span class="sxs-lookup"><span data-stu-id="1ac72-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="1ac72-118">**エラー ID:** BC40057</span><span class="sxs-lookup"><span data-stu-id="1ac72-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1ac72-119">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1ac72-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="1ac72-120">開く、**プロジェクト デザイナー**に切り替えると、**参照**ページ。</span><span class="sxs-lookup"><span data-stu-id="1ac72-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="1ac72-121">**インポートされた名前空間**セクションで、コンテナーの要素が、プロジェクトからアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1ac72-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="1ac72-122">コンテナーの要素が少なくとも 1 つを公開することを確認`Public`メンバー。</span><span class="sxs-lookup"><span data-stu-id="1ac72-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac72-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ac72-123">See Also</span></span>  
 <span data-ttu-id="1ac72-124">[[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="1ac72-124">[References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>  
 [<span data-ttu-id="1ac72-125">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="1ac72-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="1ac72-126">Public</span><span class="sxs-lookup"><span data-stu-id="1ac72-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="1ac72-127">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="1ac72-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="1ac72-128">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="1ac72-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
