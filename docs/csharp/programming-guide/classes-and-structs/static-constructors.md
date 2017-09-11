---
title: "静的コンストラクター (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
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
ms.openlocfilehash: 73df76c61f393bf5fe09af66935acfbac4b5663f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="5ebf3-102">静的コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5ebf3-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="5ebf3-103">静的コンストラクターは、任意の [static](../../../csharp/language-reference/keywords/static.md) データを初期化するため、または 1 回だけ実行する必要がある特定のアクションを実行するために使います。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="5ebf3-104">最初のインスタンスが作成され前、または静的メンバーが参照される前に、自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 <span data-ttu-id="5ebf3-105">[!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5ebf3-105">[!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]</span></span>  
  
 <span data-ttu-id="5ebf3-106">静的コンストラクターには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-106">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="5ebf3-107">静的コンストラクターはアクセス修飾子を取らず、パラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-107">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="5ebf3-108">静的コンストラクターは、最初のインスタンスが作成され前、または静的メンバーが参照される前に、[クラス](../../../csharp/language-reference/keywords/class.md)を初期化するために自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-108">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="5ebf3-109">静的コンストラクターを直接呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-109">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="5ebf3-110">ユーザーは、プログラムで静的コンストラクターが実行されるタイミングを制御できません。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-110">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="5ebf3-111">静的コンストラクターの一般的な用途は、クラスがログ ファイルを使っていて、このファイルにエントリを書き込むためにコンストラクターが使われる場合です。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-111">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="5ebf3-112">コンストラクターが `LoadLibrary` メソッドを呼び出すことができる場合は、アンマネージ コードのラッパー クラスを作成するときにも静的コンストラクターが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-112">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="5ebf3-113">静的コンストラクターが例外をスローした場合、ランタイムがその静的コンストラクターを再度呼び出すことはなく、その型は、プログラムが実行しているアプリケーション ドメインの有効期間中、初期化されないままになります。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-113">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ebf3-114">例</span><span class="sxs-lookup"><span data-stu-id="5ebf3-114">Example</span></span>  
 <span data-ttu-id="5ebf3-115">この例では、`Bus` クラスに静的コンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-115">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="5ebf3-116">`Bus` の最初のインスタンスが作成されるとき (`bus1`)、静的コンストラクターが呼び出されてクラスが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-116">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="5ebf3-117">サンプルの出力では、`Bus` のインスタンスが 2 つでも静的コンストラクターは 1 回だけ実行されること、およびインスタンス コンストラクターの実行前に静的コンストラクターが実行されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="5ebf3-117">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 <span data-ttu-id="5ebf3-118">[!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5ebf3-118">[!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebf3-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ebf3-119">See Also</span></span>  
 <span data-ttu-id="5ebf3-120">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ebf3-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5ebf3-121">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ebf3-121">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="5ebf3-122">[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="5ebf3-122">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="5ebf3-123">[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="5ebf3-123">[Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span></span>  
 [<span data-ttu-id="5ebf3-124">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="5ebf3-124">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

