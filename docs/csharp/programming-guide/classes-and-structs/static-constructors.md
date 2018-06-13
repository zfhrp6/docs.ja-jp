---
title: 静的コンストラクター (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 52c52f68bc3612807b810047044aedbd2c457cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315712"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="e0547-102">静的コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e0547-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="e0547-103">静的コンストラクターは、任意の [static](../../../csharp/language-reference/keywords/static.md) データを初期化するため、または 1 回だけ実行する必要がある特定のアクションを実行するために使います。</span><span class="sxs-lookup"><span data-stu-id="e0547-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="e0547-104">最初のインスタンスが作成され前、または静的メンバーが参照される前に、自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e0547-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="e0547-105">静的コンストラクターには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="e0547-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="e0547-106">静的コンストラクターはアクセス修飾子を取らず、パラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="e0547-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="e0547-107">静的コンストラクターは、最初のインスタンスが作成され前、または静的メンバーが参照される前に、[クラス](../../../csharp/language-reference/keywords/class.md)を初期化するために自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e0547-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="e0547-108">静的コンストラクターを直接呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e0547-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="e0547-109">ユーザーは、プログラムで静的コンストラクターが実行されるタイミングを制御できません。</span><span class="sxs-lookup"><span data-stu-id="e0547-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="e0547-110">静的コンストラクターの一般的な用途は、クラスがログ ファイルを使っていて、このファイルにエントリを書き込むためにコンストラクターが使われる場合です。</span><span class="sxs-lookup"><span data-stu-id="e0547-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="e0547-111">コンストラクターが `LoadLibrary` メソッドを呼び出すことができる場合は、アンマネージ コードのラッパー クラスを作成するときにも静的コンストラクターが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="e0547-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="e0547-112">静的コンストラクターが例外をスローした場合、ランタイムがその静的コンストラクターを再度呼び出すことはなく、その型は、プログラムが実行しているアプリケーション ドメインの有効期間中、初期化されないままになります。</span><span class="sxs-lookup"><span data-stu-id="e0547-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0547-113">例</span><span class="sxs-lookup"><span data-stu-id="e0547-113">Example</span></span>  
 <span data-ttu-id="e0547-114">この例では、`Bus` クラスに静的コンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="e0547-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="e0547-115">`Bus` の最初のインスタンスが作成されるとき (`bus1`)、静的コンストラクターが呼び出されてクラスが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="e0547-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="e0547-116">サンプルの出力では、`Bus` のインスタンスが 2 つでも静的コンストラクターは 1 回だけ実行されること、およびインスタンス コンストラクターの実行前に静的コンストラクターが実行されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e0547-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e0547-117">参照</span><span class="sxs-lookup"><span data-stu-id="e0547-117">See Also</span></span>  
 [<span data-ttu-id="e0547-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e0547-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e0547-119">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="e0547-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="e0547-120">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="e0547-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="e0547-121">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="e0547-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="e0547-122">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="e0547-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
