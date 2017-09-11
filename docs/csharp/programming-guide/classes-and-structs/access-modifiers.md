---
title: "アクセス修飾子 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: 32
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
ms.openlocfilehash: 38b259b4d85d54467cd15cd49e5987f6198e8d99
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="e82e1-102">アクセス修飾子 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e82e1-102">Access Modifiers (C# Programming Guide)</span></span>
<span data-ttu-id="e82e1-103">すべての型とそのメンバーには、アクセシビリティ レベルがあります。同じアセンブリ (または他のアセンブリ) にある他のコードからそれらの型やそのメンバーを利用できるかどうかは、アクセシビリティ レベルによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-103">All types and type members have an accessibility level, which controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="e82e1-104">型またはメンバーにはその宣言時に、以下のアクセス修飾子を使ってアクセシビリティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-104">You can use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>  
  
 [<span data-ttu-id="e82e1-105">public</span><span class="sxs-lookup"><span data-stu-id="e82e1-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 <span data-ttu-id="e82e1-106">この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-106">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>  
  
 [<span data-ttu-id="e82e1-107">private</span><span class="sxs-lookup"><span data-stu-id="e82e1-107">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 <span data-ttu-id="e82e1-108">この型またはメンバーには、同じクラス内または同じ構造体内のコードからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-108">The type or member can be accessed only by code in the same class or struct.</span></span>  
  
 [<span data-ttu-id="e82e1-109">protected</span><span class="sxs-lookup"><span data-stu-id="e82e1-109">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 <span data-ttu-id="e82e1-110">この型またはメンバーには、同じクラス内または同じ構造体内のコードか、そのクラスから派生したクラス内のコードからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-110">The type or member can be accessed only by code in the same class or struct, or in a class that is derived from that class.</span></span>  
  
 [<span data-ttu-id="e82e1-111">internal</span><span class="sxs-lookup"><span data-stu-id="e82e1-111">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="e82e1-112">この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-112">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>  
  
 `protected internal`  
 <span data-ttu-id="e82e1-113">この型またはメンバーには、それが宣言されているアセンブリ内の任意のコードからアクセスできるほか、別のアセンブリの派生クラス内からアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-113">The type or member can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly.</span></span> <span data-ttu-id="e82e1-114">別のアセンブリからのアクセスは、当該の protected internal 要素が宣言されているクラスから派生したクラス宣言内で行い、かつ、その派生クラス型のインスタンスを介して行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e82e1-114">Access from another assembly must take place within a class declaration that derives from the class in which the protected internal element is declared, and it must take place through an instance of the derived class type.</span></span>  
  
 <span data-ttu-id="e82e1-115">次の例は、型とメンバーにアクセス修飾子を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e82e1-115">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>  
  
 <span data-ttu-id="e82e1-116">[!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e82e1-116">[!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]</span></span>  
  
 <span data-ttu-id="e82e1-117">コンテキストに関係なくすべての型またはすべてのメンバーにどのようなアクセス修飾子でも使用できるというわけではありません。型のメンバーのアクセシビリティが、それを含んでいる型のアクセシビリティによって制約を受ける場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e82e1-117">Not all access modifiers can be used by all types or members in all contexts, and in some cases the accessibility of a type member is constrained by the accessibility of its containing type.</span></span> <span data-ttu-id="e82e1-118">以降のセクションでは、アクセシビリティについてさらに詳しく取り上げます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-118">The following sections provide more details about accessibility.</span></span>  
  
## <a name="class-and-struct-accessibility"></a><span data-ttu-id="e82e1-119">クラスと構造体のアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="e82e1-119">Class and Struct Accessibility</span></span>  
 <span data-ttu-id="e82e1-120">名前空間に直接宣言されている (つまり、他のクラスや構造体の入れ子にされていない) クラスと構造体には、public または internal を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-120">Classes and structs that are declared directly within a namespace (in other words, that are not nested within other classes or structs) can be either public or internal.</span></span> <span data-ttu-id="e82e1-121">アクセス修飾子が指定されなかった場合は、既定で internal が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-121">Internal is the default if no access modifier is specified.</span></span>  
  
 <span data-ttu-id="e82e1-122">構造体のメンバー (入れ子にされているクラスや構造体も含む) は public、internal、private のいずれかとして宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-122">Struct members, including nested classes and structs, can be declared as public, internal, or private.</span></span> <span data-ttu-id="e82e1-123">クラスのメンバー (入れ子にされているクラスや構造体も含む) は public、protected internal、protected、internal、private のいずれかとして宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-123">Class members, including nested classes and structs, can be public, protected internal, protected, internal, or private.</span></span> <span data-ttu-id="e82e1-124">クラスのメンバーと構造体のメンバー (入れ子にされているクラスや構造体も含む) には、既定で private のアクセス レベルが指定されます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-124">The access level for class members and struct members, including nested classes and structs, is private by default.</span></span> <span data-ttu-id="e82e1-125">入れ子にされた型のうち、private が指定されているものには、それを含んでいる型の外部からはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-125">Private nested types are not accessible from outside the containing type.</span></span>  
  
 <span data-ttu-id="e82e1-126">派生クラスに、その基本型を超えるアクセシビリティを割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-126">Derived classes cannot have greater accessibility than their base types.</span></span> <span data-ttu-id="e82e1-127">つまり、internal クラス `A` から派生したクラス `B` を public にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-127">In other words, you cannot have a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="e82e1-128">仮にそれが許容されるならば、`A` が public になると考えられます。`A` のすべての protected メンバーと internal メンバーに派生クラスからアクセスできることになるからです。</span><span class="sxs-lookup"><span data-stu-id="e82e1-128">If this were allowed, it would have the effect of making `A` public, because all protected or internal members of `A` are accessible from the derived class.</span></span>  
  
 <span data-ttu-id="e82e1-129">InternalsVisibleToAttribute を使うと、internal 型へのアクセスを他の特定のアセンブリに許可することができます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-129">You can enable specific other assemblies to access your internal types by using the InternalsVisibleToAttribute.</span></span> <span data-ttu-id="e82e1-130">詳細については、[Friend アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e82e1-130">For more information, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="e82e1-131">クラスと構造体のメンバーのアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="e82e1-131">Class and Struct Member Accessibility</span></span>  
 <span data-ttu-id="e82e1-132">クラスのメンバー (入れ子にされているクラスや構造体も含む) は、5 種類あるアクセス修飾子をどれでも使って宣言できます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-132">Class members (including nested classes and structs) can be declared with any of the five types of access.</span></span> <span data-ttu-id="e82e1-133">構造体のメンバーを protected として宣言することはできません。構造体は継承をサポートしていないためです。</span><span class="sxs-lookup"><span data-stu-id="e82e1-133">Struct members cannot be declared as protected because structs do not support inheritance.</span></span>  
  
 <span data-ttu-id="e82e1-134">通常、メンバーのアクセシビリティが、それを含んでいる型のアクセシビリティを超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-134">Normally, the accessibility of a member is not greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="e82e1-135">ただし、internal クラスの public メンバーには、そのアセンブリの外部からアクセスできる場合もあります。そのメンバーがインターフェイスのメソッドを実装している場合や public な基本クラスに定義されている仮想メソッドをオーバーライドしている場合がそれに該当します。</span><span class="sxs-lookup"><span data-stu-id="e82e1-135">However, a public member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>  
  
 <span data-ttu-id="e82e1-136">フィールド、プロパティ、イベントのいずれかに該当するメンバーの型には、メンバー自体と同じかそれ以上のアクセシビリティが必要です。</span><span class="sxs-lookup"><span data-stu-id="e82e1-136">The type of any member that is a field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="e82e1-137">同様に、メソッド、インデクサー、デリゲートのいずれかに該当するメンバーの戻り値の型とパラメーターの型には、メンバー自体と同じかそれ以上のアクセシビリティが必要です。</span><span class="sxs-lookup"><span data-stu-id="e82e1-137">Similarly, the return type and the parameter types of any member that is a method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="e82e1-138">たとえば、クラス `C` を返すメソッド `M` を public にするためには、`C` も public である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e82e1-138">For example, you cannot have a public method `M` that returns a class `C` unless `C` is also public.</span></span> <span data-ttu-id="e82e1-139">同様に、`A` が private として宣言されている場合、`A` 型のプロパティを protected にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-139">Likewise, you cannot have a protected property of type `A` if `A` is declared as private.</span></span>  
  
 <span data-ttu-id="e82e1-140">ユーザー定義の演算子は、必ず public として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e82e1-140">User-defined operators must always be declared as public.</span></span> <span data-ttu-id="e82e1-141">詳細については、「[operator (C# Reference) (operator (C# リファレンス))](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e82e1-141">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
 <span data-ttu-id="e82e1-142">アクセシビリティ修飾子をファイナライザーに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-142">Finalizers cannot have accessibility modifiers.</span></span>  
  
 <span data-ttu-id="e82e1-143">クラスまたは構造体のメンバーにアクセス レベルを設定するには、該当するキーワードをメンバーの宣言に追加します。その例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e82e1-143">To set the access level for a class or struct member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="e82e1-144">[!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e82e1-144">[!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e82e1-145">protected internal のアクセシビリティ レベルは、"protected AND internal" ではなく "protected OR internal" という意味になります。</span><span class="sxs-lookup"><span data-stu-id="e82e1-145">The protected internal accessibility level means protected OR internal, not protected AND internal.</span></span> <span data-ttu-id="e82e1-146">つまり、protected internal のメンバーには、同じアセンブリ内の任意のクラス (派生クラスも含む) からアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-146">In other words, a protected internal member can be accessed from any class in the same assembly, including derived classes.</span></span> <span data-ttu-id="e82e1-147">同じアセンブリ内の派生クラスのみにアクセシビリティを限定するには、クラス自体は internal として宣言し、そのメンバーを protected として宣言します。</span><span class="sxs-lookup"><span data-stu-id="e82e1-147">To limit accessibility to only derived classes in the same assembly, declare the class itself internal, and declare its members as protected.</span></span>  
  
## <a name="other-types"></a><span data-ttu-id="e82e1-148">その他の型</span><span class="sxs-lookup"><span data-stu-id="e82e1-148">Other Types</span></span>  
 <span data-ttu-id="e82e1-149">名前空間内に直接宣言されたインターフェイスは、public または internal として宣言できます。クラスや構造体と同様、インターフェイスの既定のアクセス レベルは internal になります。</span><span class="sxs-lookup"><span data-stu-id="e82e1-149">Interfaces declared directly within a namespace can be declared as public or internal and, just like classes and structs, interfaces default to internal access.</span></span> <span data-ttu-id="e82e1-150">インターフェイスのメンバーは常に public です。他の型がクラスや構造体にアクセスできるようにすることがインターフェイスの目的であるためです。</span><span class="sxs-lookup"><span data-stu-id="e82e1-150">Interface members are always public because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="e82e1-151">インターフェイスのメンバーにアクセス修飾子を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-151">No access modifiers can be applied to interface members.</span></span>  
  
 <span data-ttu-id="e82e1-152">列挙型のメンバーは常に public となり、アクセス修飾子を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e82e1-152">Enumeration members are always public, and no access modifiers can be applied.</span></span>  
  
 <span data-ttu-id="e82e1-153">デリゲートの振る舞いは、クラスおよび構造体と似ています。</span><span class="sxs-lookup"><span data-stu-id="e82e1-153">Delegates behave like classes and structs.</span></span> <span data-ttu-id="e82e1-154">既定では、名前空間内に直接宣言されているときには internal アクセスが、入れ子にされているときは private アクセスが適用されます。</span><span class="sxs-lookup"><span data-stu-id="e82e1-154">By default, they have internal access when declared directly within a namespace, and private access when nested.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e82e1-155">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="e82e1-155">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e82e1-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="e82e1-156">See Also</span></span>  
 <span data-ttu-id="e82e1-157">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-157">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e82e1-158">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-158">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="e82e1-159">[インターフェイス](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-159">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 <span data-ttu-id="e82e1-160">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-160">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="e82e1-161">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-161">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="e82e1-162">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-162">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="e82e1-163">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-163">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 <span data-ttu-id="e82e1-164">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-164">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="e82e1-165">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="e82e1-165">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 [<span data-ttu-id="e82e1-166">interface</span><span class="sxs-lookup"><span data-stu-id="e82e1-166">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)

