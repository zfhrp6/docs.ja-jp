---
title: using ディレクティブ (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="33e8b-102">using ディレクティブ (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="33e8b-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="33e8b-103">`using` ディレクティブは、次の 3 つの用途で使用します。</span><span class="sxs-lookup"><span data-stu-id="33e8b-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="33e8b-104">名前空間で型の使用を許可する場合。これにより、その名前空間内では型を修飾せずに使用できます。</span><span class="sxs-lookup"><span data-stu-id="33e8b-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="33e8b-105">アクセスを型名で修飾することなく、型の静的メンバーへのアクセスを許可する場合。</span><span class="sxs-lookup"><span data-stu-id="33e8b-105">To allow you to access static members of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="33e8b-106">詳細については、「[using static ディレクティブ](using-static.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33e8b-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="33e8b-107">名前空間または型のエイリアスを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="33e8b-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="33e8b-108">これは "*using エイリアス ディレクティブ*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="33e8b-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="33e8b-109">`using` キーワードは、*using ステートメント*の作成にも使用します。ファイルやフォントなどの <xref:System.IDisposable> オブジェクトを正しく処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="33e8b-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="33e8b-110">詳しくは、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33e8b-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="33e8b-111">using static 型</span><span class="sxs-lookup"><span data-stu-id="33e8b-111">Using Static Type</span></span>  
 <span data-ttu-id="33e8b-112">アクセスを型名で修飾することなく型の静的メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="33e8b-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="33e8b-113">コメント</span><span class="sxs-lookup"><span data-stu-id="33e8b-113">Remarks</span></span>  
 <span data-ttu-id="33e8b-114">`using` ディレクティブのスコープは、このディレクティブが存在するファイルに限定されます。</span><span class="sxs-lookup"><span data-stu-id="33e8b-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>  
  
 <span data-ttu-id="33e8b-115">`using` エイリアスを作成すると、名前空間または型への識別子を修飾しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="33e8b-115">Create a `using` alias to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="33e8b-116">using エイリアス ディレクティブの右側は、その前にある using ディレクティブに関係なく、必ず完全修飾型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="33e8b-116">The right side of a using alias directive must always be a fully-qualified type regardless of the using directives that come before it.</span></span>  
  
 <span data-ttu-id="33e8b-117">`using` ディレクティブを作成すると、名前空間内の型を、名前空間を指定することなく使用できます。</span><span class="sxs-lookup"><span data-stu-id="33e8b-117">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="33e8b-118">`using` ディレクティブでは、指定した名前空間に入れ子になった別の名前空間へのアクセスは許可されません。</span><span class="sxs-lookup"><span data-stu-id="33e8b-118">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="33e8b-119">名前空間は、ユーザー定義とシステム定義の 2 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="33e8b-119">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="33e8b-120">ユーザー定義の名前空間は、コードで定義された名前空間です。</span><span class="sxs-lookup"><span data-stu-id="33e8b-120">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="33e8b-121">システム定義の名前空間の一覧については、[.NET Framework クラス ライブラリの概要](../../../standard/class-library-overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="33e8b-121">For a list of the system-defined namespaces, see [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span></span>  
  
 <span data-ttu-id="33e8b-122">他のアセンブリのメソッドを参照する方法の例については、[コマンド ラインでアセンブリを作成し、使用する](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)方法に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33e8b-122">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="33e8b-123">例 1</span><span class="sxs-lookup"><span data-stu-id="33e8b-123">Example 1</span></span>  
  
 <span data-ttu-id="33e8b-124">次の例は、名前空間の `using` エイリアスを定義して使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="33e8b-124">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="33e8b-125">using エイリアス ディレクティブの右側には、オープン ジェネリック型を配置できません。</span><span class="sxs-lookup"><span data-stu-id="33e8b-125">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="33e8b-126">たとえば、List\<T> の using エイリアスを作成することはできませんが、List\<int> の using エイリアスは作成できます。</span><span class="sxs-lookup"><span data-stu-id="33e8b-126">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="33e8b-127">例 2</span><span class="sxs-lookup"><span data-stu-id="33e8b-127">Example 2</span></span>  
  
 <span data-ttu-id="33e8b-128">次の例は、クラスの `using` ディレクティブと `using` エイリアスを定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="33e8b-128">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="33e8b-129">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="33e8b-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33e8b-130">参照</span><span class="sxs-lookup"><span data-stu-id="33e8b-130">See Also</span></span>  
 [<span data-ttu-id="33e8b-131">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="33e8b-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="33e8b-132">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="33e8b-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="33e8b-133">名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="33e8b-133">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [<span data-ttu-id="33e8b-134">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="33e8b-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="33e8b-135">名前空間キーワード</span><span class="sxs-lookup"><span data-stu-id="33e8b-135">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="33e8b-136">名前空間</span><span class="sxs-lookup"><span data-stu-id="33e8b-136">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="33e8b-137">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="33e8b-137">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
