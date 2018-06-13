---
title: namespace (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 343cce85dd235532fbe3fc90af0a785f48518db7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276020"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="4c906-102">namespace (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4c906-102">namespace (C# Reference)</span></span>
<span data-ttu-id="4c906-103">`namespace` キーワードは、関連する一連のオブジェクトを含む範囲を宣言するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c906-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="4c906-104">名前空間を利用し、コード要素を整理したり、グローバルに一意の型を作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="4c906-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="4c906-105">コメント</span><span class="sxs-lookup"><span data-stu-id="4c906-105">Remarks</span></span>  
 <span data-ttu-id="4c906-106">名前空間内では、以下の型を 1 つ以上宣言できます。</span><span class="sxs-lookup"><span data-stu-id="4c906-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="4c906-107">別の名前空間</span><span class="sxs-lookup"><span data-stu-id="4c906-107">another namespace</span></span>  
  
-   [<span data-ttu-id="4c906-108">class</span><span class="sxs-lookup"><span data-stu-id="4c906-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="4c906-109">interface</span><span class="sxs-lookup"><span data-stu-id="4c906-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="4c906-110">struct</span><span class="sxs-lookup"><span data-stu-id="4c906-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="4c906-111">enum</span><span class="sxs-lookup"><span data-stu-id="4c906-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="4c906-112">delegate</span><span class="sxs-lookup"><span data-stu-id="4c906-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="4c906-113">C# ソース ファイル内に名前空間を明示的に宣言しているかどうかに関係なく、コンパイラは既定の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="4c906-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="4c906-114">この無名の名前空間はグローバル名前空間とも呼ばれますが、すべてのファイルに存在します。</span><span class="sxs-lookup"><span data-stu-id="4c906-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="4c906-115">グローバル名前空間内にある識別子は、名前付き名前空間で利用できます。</span><span class="sxs-lookup"><span data-stu-id="4c906-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="4c906-116">名前空間には暗黙的にパブリック アクセスが設定されます。この属性は変更できません。</span><span class="sxs-lookup"><span data-stu-id="4c906-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="4c906-117">名前空間内の要素に割り当てることができるアクセス修飾子については、「[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c906-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="4c906-118">名前空間は、2 つ以上の宣言で定義できます。</span><span class="sxs-lookup"><span data-stu-id="4c906-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="4c906-119">たとえば、次の例では、`MyCompany` 名前空間の一部として 2 つのクラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="4c906-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="4c906-120">例</span><span class="sxs-lookup"><span data-stu-id="4c906-120">Example</span></span>  
 <span data-ttu-id="4c906-121">入れ子になった名前空間で静的なメソッドを呼び出す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c906-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="4c906-122">参照項目</span><span class="sxs-lookup"><span data-stu-id="4c906-122">For More Information</span></span>  
 <span data-ttu-id="4c906-123">名前空間の使用方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c906-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="4c906-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="4c906-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="4c906-125">名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="4c906-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="4c906-126">方法: グローバル名前空間エイリアスを使用する</span><span class="sxs-lookup"><span data-stu-id="4c906-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="4c906-127">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4c906-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4c906-128">参照</span><span class="sxs-lookup"><span data-stu-id="4c906-128">See Also</span></span>  
 [<span data-ttu-id="4c906-129">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="4c906-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4c906-130">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4c906-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4c906-131">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="4c906-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4c906-132">名前空間キーワード</span><span class="sxs-lookup"><span data-stu-id="4c906-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="4c906-133">using</span><span class="sxs-lookup"><span data-stu-id="4c906-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
