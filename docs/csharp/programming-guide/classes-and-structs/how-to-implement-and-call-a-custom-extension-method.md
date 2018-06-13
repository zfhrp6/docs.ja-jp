---
title: '方法 : カスタム拡張メソッドを実装して呼び出す (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 62dbbbfb7a63c8fb73661fe7d66e73d0eca73107
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340308"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="24b98-102">方法 : カスタム拡張メソッドを実装して呼び出す (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="24b98-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="24b98-103">このトピックでは、あらゆる .NET 型を対象に独自の拡張メソッドを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="24b98-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="24b98-104">クライアント コードで拡張メソッドを使用するには、拡張メソッドが格納されている DLL への参照を追加し、拡張メソッドが定義されている名前空間を指定する [using](../../../csharp/language-reference/keywords/using-directive.md) ディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="24b98-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../../csharp/language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="24b98-105">拡張メソッドを定義して呼び出すには</span><span class="sxs-lookup"><span data-stu-id="24b98-105">To define and call the extension method</span></span>  
  
1.  <span data-ttu-id="24b98-106">拡張メソッドを格納するための静的[クラス](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)を定義します。</span><span class="sxs-lookup"><span data-stu-id="24b98-106">Define a static [class](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="24b98-107">このクラスは、クライアント コードから参照できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="24b98-107">The class must be visible to client code.</span></span> <span data-ttu-id="24b98-108">アクセシビリティの規則の詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24b98-108">For more information about accessibility rules, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
2.  <span data-ttu-id="24b98-109">拡張メソッドを静的メソッドとして実装します。メソッドの可視性は、包含クラスと同レベル以上を指定します。</span><span class="sxs-lookup"><span data-stu-id="24b98-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3.  <span data-ttu-id="24b98-110">メソッドの最初のパラメーターでは、メソッドが操作する型を指定します。型名の前には [this](../../../csharp/language-reference/keywords/this.md) 修飾子を付加します。</span><span class="sxs-lookup"><span data-stu-id="24b98-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span>  
  
4.  <span data-ttu-id="24b98-111">呼び出し元のコードで、`using` ディレクティブを追加して、拡張メソッドのクラスを含む[名前空間](../../../csharp/language-reference/keywords/namespace.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="24b98-111">In the calling code, add a `using` directive to specify the [namespace](../../../csharp/language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5.  <span data-ttu-id="24b98-112">型のインスタンス メソッドと同じようにメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="24b98-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="24b98-113">呼び出し元のコードでは最初のパラメーターを指定しません。これは演算子を適用する型を表すものであり、コンパイラはオブジェクトの型を既に認識しているためです。</span><span class="sxs-lookup"><span data-stu-id="24b98-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="24b98-114">指定する必要があるのは、2 番目から `n` 番目のパラメーターの引数だけです。</span><span class="sxs-lookup"><span data-stu-id="24b98-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24b98-115">例</span><span class="sxs-lookup"><span data-stu-id="24b98-115">Example</span></span>  
 <span data-ttu-id="24b98-116">次の例では、`CustomExtensions.StringExtension` クラスの `WordCount` という名前の拡張メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="24b98-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="24b98-117">このメソッドは、最初のメソッド パラメーターとして指定された <xref:System.String> クラスを操作します。</span><span class="sxs-lookup"><span data-stu-id="24b98-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="24b98-118">`CustomExtensions` 名前空間は、アプリケーション名前空間にインポートされ、メソッドは `Main` メソッド内で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="24b98-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24b98-119">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="24b98-119">Compiling the Code</span></span>  
 <span data-ttu-id="24b98-120">このコードを実行するには、Visual Studio で作成した Visual C# コンソール アプリケーション プロジェクトに、そのコードをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="24b98-120">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="24b98-121">既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のバージョン 3.5 を対象としており、System.Core.dll への参照と System.Linq の `using` ディレクティブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="24b98-121">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="24b98-122">これらの要件のうち 1 つまたは複数を満たしていないプロジェクトの場合は、手動で追加することができます。</span><span class="sxs-lookup"><span data-stu-id="24b98-122">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="24b98-123">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="24b98-123">.NET Framework Security</span></span>  
 <span data-ttu-id="24b98-124">拡張メソッドには、固有のセキュリティ上の脆弱性はありません。</span><span class="sxs-lookup"><span data-stu-id="24b98-124">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="24b98-125">名前の衝突の解決では、型自体で定義されているインスタンス メソッドまたは静的メソッドが常に優先されるため、型の既存のメソッドを偽装するために拡張メソッドが使用されることはありません。</span><span class="sxs-lookup"><span data-stu-id="24b98-125">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="24b98-126">拡張メソッドは、拡張されたクラスのプライベート データにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="24b98-126">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b98-127">参照</span><span class="sxs-lookup"><span data-stu-id="24b98-127">See Also</span></span>  
 [<span data-ttu-id="24b98-128">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="24b98-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="24b98-129">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="24b98-129">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [<span data-ttu-id="24b98-130">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="24b98-130">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="24b98-131">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="24b98-131">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="24b98-132">protected</span><span class="sxs-lookup"><span data-stu-id="24b98-132">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="24b98-133">internal</span><span class="sxs-lookup"><span data-stu-id="24b98-133">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 [<span data-ttu-id="24b98-134">public</span><span class="sxs-lookup"><span data-stu-id="24b98-134">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="24b98-135">this</span><span class="sxs-lookup"><span data-stu-id="24b98-135">this</span></span>](../../../csharp/language-reference/keywords/this.md)  
 [<span data-ttu-id="24b98-136">namespace</span><span class="sxs-lookup"><span data-stu-id="24b98-136">namespace</span></span>](../../../csharp/language-reference/keywords/namespace.md)
