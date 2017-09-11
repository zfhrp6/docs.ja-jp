---
title: "namespace (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
dev_langs:
- CSharp
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2cef3949d9a41db36406db059218f7a204172ea
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="namespace-c-reference"></a><span data-ttu-id="62f8a-102">namespace (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="62f8a-102">namespace (C# Reference)</span></span>
<span data-ttu-id="62f8a-103">`namespace` キーワードは、関連する一連のオブジェクトを含む範囲を宣言するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="62f8a-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="62f8a-104">名前空間を利用し、コード要素を整理したり、グローバルに一意の型を作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="62f8a-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 <span data-ttu-id="62f8a-105">[!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="62f8a-105">[!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62f8a-106">コメント</span><span class="sxs-lookup"><span data-stu-id="62f8a-106">Remarks</span></span>  
 <span data-ttu-id="62f8a-107">名前空間内では、以下の型を 1 つ以上宣言できます。</span><span class="sxs-lookup"><span data-stu-id="62f8a-107">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="62f8a-108">別の名前空間</span><span class="sxs-lookup"><span data-stu-id="62f8a-108">another namespace</span></span>  
  
-   [<span data-ttu-id="62f8a-109">class</span><span class="sxs-lookup"><span data-stu-id="62f8a-109">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="62f8a-110">interface</span><span class="sxs-lookup"><span data-stu-id="62f8a-110">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="62f8a-111">struct</span><span class="sxs-lookup"><span data-stu-id="62f8a-111">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="62f8a-112">enum</span><span class="sxs-lookup"><span data-stu-id="62f8a-112">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="62f8a-113">delegate</span><span class="sxs-lookup"><span data-stu-id="62f8a-113">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="62f8a-114">C# ソース ファイル内に名前空間を明示的に宣言しているかどうかに関係なく、コンパイラは既定の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="62f8a-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="62f8a-115">この無名の名前空間はグローバル名前空間とも呼ばれますが、すべてのファイルに存在します。</span><span class="sxs-lookup"><span data-stu-id="62f8a-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="62f8a-116">グローバル名前空間内にある識別子は、名前付き名前空間で利用できます。</span><span class="sxs-lookup"><span data-stu-id="62f8a-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="62f8a-117">名前空間には暗黙的にパブリック アクセスが設定されます。この属性は変更できません。</span><span class="sxs-lookup"><span data-stu-id="62f8a-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="62f8a-118">名前空間内の要素に割り当てることができるアクセス修飾子については、「[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62f8a-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="62f8a-119">名前空間は、2 つ以上の宣言で定義できます。</span><span class="sxs-lookup"><span data-stu-id="62f8a-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="62f8a-120">たとえば、次の例では、`MyCompany` 名前空間の一部として 2 つのクラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="62f8a-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 <span data-ttu-id="62f8a-121">[!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="62f8a-121">[!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="62f8a-122">例</span><span class="sxs-lookup"><span data-stu-id="62f8a-122">Example</span></span>  
 <span data-ttu-id="62f8a-123">入れ子になった名前空間で静的なメソッドを呼び出す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="62f8a-123">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 <span data-ttu-id="62f8a-124">[!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="62f8a-124">[!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="62f8a-125">参照項目</span><span class="sxs-lookup"><span data-stu-id="62f8a-125">For More Information</span></span>  
 <span data-ttu-id="62f8a-126">名前空間の使用方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="62f8a-126">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="62f8a-127">名前空間</span><span class="sxs-lookup"><span data-stu-id="62f8a-127">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="62f8a-128">名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="62f8a-128">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="62f8a-129">方法: グローバル名前空間エイリアスを使用する</span><span class="sxs-lookup"><span data-stu-id="62f8a-129">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="62f8a-130">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="62f8a-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62f8a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="62f8a-131">See Also</span></span>  
 <span data-ttu-id="62f8a-132">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="62f8a-132">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="62f8a-133">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="62f8a-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="62f8a-134">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="62f8a-134">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="62f8a-135">[名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="62f8a-135">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 [<span data-ttu-id="62f8a-136">using</span><span class="sxs-lookup"><span data-stu-id="62f8a-136">using</span></span>](../../../csharp/language-reference/keywords/using.md)

