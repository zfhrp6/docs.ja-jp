---
title: "プライベート コンストラクター (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: 19
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
ms.openlocfilehash: 1ccd3db5f95e3a237bb37d9e09c34f415fcfd752
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="3f6bf-102">プライベート コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3f6bf-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="3f6bf-103">プライベート コンストラクターは、特別なインスタンス コンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="3f6bf-104">通常は、静的メンバーだけを含むクラスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="3f6bf-105">クラスに 1 つ以上のプライベート コンストラクターがあり、パブリック コンストラクターがない場合、他のクラス (入れ子になったクラスを除く) は、このクラスのインスタンスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="3f6bf-106">例:</span><span class="sxs-lookup"><span data-stu-id="3f6bf-106">For example:</span></span>  
  
 <span data-ttu-id="3f6bf-107">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3f6bf-107">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]</span></span>  
  
 <span data-ttu-id="3f6bf-108">空のコンストラクターを宣言すると、既定コンストラクターの自動生成は行われません。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-108">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="3f6bf-109">コンストラクターにアクセス修飾子を指定しない場合でも、コンストラクターは既定でプライベートになります。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-109">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="3f6bf-110">しかし、通常は、[プライベート](../../../csharp/language-reference/keywords/private.md)修飾子を明示的に使用して、クラスをインスタンス化できないことを明確に示します。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-110">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="3f6bf-111">プライベート コンストラクターは、<xref:System.Math> クラスなどのインスタンス フィールドやメソッドが存在しない場合や、クラスのインスタンスを取得するためにメソッドが呼び出される場合に、クラスのインスタンスが作成されないようにするために使用します。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-111">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="3f6bf-112">クラス内のすべてのメソッドが静的な場合は、クラス全体を静的にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-112">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="3f6bf-113">詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-113">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f6bf-114">例</span><span class="sxs-lookup"><span data-stu-id="3f6bf-114">Example</span></span>  
 <span data-ttu-id="3f6bf-115">次に示すのは、プライベート コンストラクターを使用するクラスの例です。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-115">The following is an example of a class using a private constructor.</span></span>  
  
 <span data-ttu-id="3f6bf-116">[!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="3f6bf-116">[!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]</span></span>  
  
 <span data-ttu-id="3f6bf-117">この例で、次のステートメントをコメント解除すると、保護レベルのためにコンストラクターにアクセスできなくなり、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3f6bf-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 <span data-ttu-id="3f6bf-118">[!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="3f6bf-118">[!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f6bf-119">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="3f6bf-119">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f6bf-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f6bf-120">See Also</span></span>  
 <span data-ttu-id="3f6bf-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f6bf-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3f6bf-122">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f6bf-122">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="3f6bf-123">[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="3f6bf-123">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="3f6bf-124">[ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="3f6bf-124">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 <span data-ttu-id="3f6bf-125">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="3f6bf-125">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 [<span data-ttu-id="3f6bf-126">public</span><span class="sxs-lookup"><span data-stu-id="3f6bf-126">public</span></span>](../../../csharp/language-reference/keywords/public.md)

