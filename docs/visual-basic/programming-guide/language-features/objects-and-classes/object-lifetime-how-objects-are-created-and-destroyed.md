---
title: "オブジェクトの有効期間: オブジェクトの作成と破棄 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Constructor
dev_langs:
- VB
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime, objects
- Sub New constructor, object lifetime
- Finalize method, object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method, object lifetime
- Class_Initialize
- object creation, object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection, Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
caps.latest.revision: 22
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
ms.openlocfilehash: 993d31f8e06b177a2a565635c2ed81c6948e2b78
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a><span data-ttu-id="da887-102">オブジェクトの有効期間: オブジェクトの作成と破棄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da887-102">Object Lifetime: How Objects Are Created and Destroyed (Visual Basic)</span></span>
<span data-ttu-id="da887-103">クラスのインスタンス (オブジェクト) を作成するには、`New` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="da887-103">An instance of a class, an object, is created by using the `New` keyword.</span></span> <span data-ttu-id="da887-104">新しいオブジェクトを使用する前に、多くの場合、そのオブジェクトに対して初期化タスクを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da887-104">Initialization tasks often must be performed on new objects before they are used.</span></span> <span data-ttu-id="da887-105">一般的な初期化タスクとして、ファイルを開く、データベースに接続する、レジストリ キーの値を読み取る、などがあります。</span><span class="sxs-lookup"><span data-stu-id="da887-105">Common initialization tasks include opening files, connecting to databases, and reading values of registry keys.</span></span> <span data-ttu-id="da887-106">Visual Basic と呼ばれるプロシージャを使用して新しいオブジェクトの初期化を制御する*コンス トラクター* (初期化を制御できる特殊なメソッド)。</span><span class="sxs-lookup"><span data-stu-id="da887-106">Visual Basic controls the initialization of new objects using procedures called *constructors* (special methods that allow control over initialization).</span></span>  
  
 <span data-ttu-id="da887-107">スコープを離れたオブジェクトは、共通言語ランタイム (CLR) によって解放されます。</span><span class="sxs-lookup"><span data-stu-id="da887-107">After an object leaves scope, it is released by the common language runtime (CLR).</span></span> <span data-ttu-id="da887-108">Visual Basic と呼ばれるプロシージャを使用しているシステム リソースの解放を制御する*デストラクター*します。</span><span class="sxs-lookup"><span data-stu-id="da887-108">Visual Basic controls the release of system resources using procedures called *destructors*.</span></span> <span data-ttu-id="da887-109">コンストラクターとデストラクターは共に、堅牢で予測可能なクラス ライブラリの作成をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="da887-109">Together, constructors and destructors support the creation of robust and predictable class libraries.</span></span>  
  
## <a name="using-constructors-and-destructors"></a><span data-ttu-id="da887-110">コンストラクターとデストラクターの使用</span><span class="sxs-lookup"><span data-stu-id="da887-110">Using Constructors and Destructors</span></span>  
 <span data-ttu-id="da887-111">コンストラクターとデストラクターは、オブジェクトの作成および破棄を制御します。</span><span class="sxs-lookup"><span data-stu-id="da887-111">Constructors and destructors control the creation and destruction of objects.</span></span> <span data-ttu-id="da887-112">Visual Basic の `Sub New` と `Sub Finalize` の各プロシージャが、オブジェクトを初期化および破棄します。これらは、`Class_Initialize` 6.0 とそれ以前のバージョンで使用される `Class_Terminate` と [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の各メソッドに置き換わるものです。</span><span class="sxs-lookup"><span data-stu-id="da887-112">The `Sub New` and `Sub Finalize` procedures in Visual Basic initialize and destroy objects; they replace the `Class_Initialize` and `Class_Terminate` methods used in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 and earlier versions.</span></span>  
  
### <a name="sub-new"></a><span data-ttu-id="da887-113">Sub New</span><span class="sxs-lookup"><span data-stu-id="da887-113">Sub New</span></span>  
 <span data-ttu-id="da887-114">`Sub New` コンストラクターは、クラスの作成時に&1; 回だけ実行できます。</span><span class="sxs-lookup"><span data-stu-id="da887-114">The `Sub New` constructor can run only once when a class is created.</span></span> <span data-ttu-id="da887-115">同じクラスまたは派生クラスから別のコンストラクターの最初のコード行以外の任意の場所で、明示的に呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="da887-115">It cannot be called explicitly anywhere other than in the first line of code of another constructor from either the same class or from a derived class.</span></span> <span data-ttu-id="da887-116">また、`Sub New` メソッド内のコードは常に、クラス内の他のすべてのコードより先に実行されます。</span><span class="sxs-lookup"><span data-stu-id="da887-116">Furthermore, the code in the `Sub New` method always runs before any other code in a class.</span></span> [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]<span data-ttu-id="da887-117">以降のバージョンが暗黙的に作成し、`Sub New`コンス トラクターに明示的に定義していない場合、実行時に、`Sub New`クラスのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="da887-117"> and later versions implicitly create a `Sub New` constructor at run time if you do not explicitly define a `Sub New` procedure for a class.</span></span>  
  
 <span data-ttu-id="da887-118">クラスのコンストラクターを作成するには、クラス定義の任意の場所に `Sub New` という名前のプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="da887-118">To create a constructor for a class, create a procedure named `Sub New` anywhere in the class definition.</span></span> <span data-ttu-id="da887-119">パラメーター化されたコンストラクターを作成するには、次のコードに示すように、他のプロシージャの引数を指定する場合と同じく、`Sub New` に引数の名前とデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="da887-119">To create a parameterized constructor, specify the names and data types of arguments to `Sub New` just as you would specify arguments for any other procedure, as in the following code:</span></span>  
  
 <span data-ttu-id="da887-120">[!code-vb[VbVbalrOOP #&42;](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="da887-120">[!code-vb[VbVbalrOOP#42](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_1.vb)]</span></span>  
  
 <span data-ttu-id="da887-121">コンストラクターは、次のコードに示すように、頻繁にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="da887-121">Constructors are frequently overloaded, as in the following code:</span></span>  
  
 <span data-ttu-id="da887-122">[!code-vb[VbVbalrOOP&116; 位](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="da887-122">[!code-vb[VbVbalrOOP#116](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_2.vb)]</span></span>  
  
 <span data-ttu-id="da887-123">別のクラスから派生したクラスを定義するときは、基本クラスにパラメーターを受け取らないアクセス可能なコンストラクターがある場合を除き、コンストラクターの&1; 行目で基本クラスのコンストラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="da887-123">When you define a class derived from another class, the first line of a constructor must be a call to the constructor of the base class, unless the base class has an accessible constructor that takes no parameters.</span></span> <span data-ttu-id="da887-124">たとえば、上記のコンストラクターを含む基本クラスの呼び出しは、`MyBase.New(s)` になります。</span><span class="sxs-lookup"><span data-stu-id="da887-124">A call to the base class that contains the above constructor, for example, would be `MyBase.New(s)`.</span></span> <span data-ttu-id="da887-125">それ以外の場合、`MyBase.New` はオプションであり、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ランタイムによって暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="da887-125">Otherwise, `MyBase.New` is optional, and the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime calls it implicitly.</span></span>  
  
 <span data-ttu-id="da887-126">親オブジェクトのコンストラクターを呼び出すコードを記述した後、追加の初期化コードを `Sub New` プロシージャに追加できます。</span><span class="sxs-lookup"><span data-stu-id="da887-126">After you write the code to call the parent object's constructor, you can add any additional initialization code to the `Sub New` procedure.</span></span> <span data-ttu-id="da887-127">`Sub New`は、パラメーター化されたコンストラクターとして呼び出されたときには、引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="da887-127">`Sub New` can accept arguments when called as a parameterized constructor.</span></span> <span data-ttu-id="da887-128">このようなパラメーターは、コンストラクターを呼び出すプロシージャ (たとえば、`Dim AnObject As New ThisClass(X)`) から渡されます。</span><span class="sxs-lookup"><span data-stu-id="da887-128">These parameters are passed from the procedure calling the constructor, for example, `Dim AnObject As New ThisClass(X)`.</span></span>  
  
### <a name="sub-finalize"></a><span data-ttu-id="da887-129">Sub Finalize</span><span class="sxs-lookup"><span data-stu-id="da887-129">Sub Finalize</span></span>  
 <span data-ttu-id="da887-130">オブジェクトを解放する前に、CLR は `Finalize` プロシージャを定義するオブジェクトの `Sub Finalize` メソッドを自動的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="da887-130">Before releasing objects, the CLR automatically calls the `Finalize` method for objects that define a `Sub Finalize` procedure.</span></span> <span data-ttu-id="da887-131">`Finalize` メソッドには、ファイルを閉じて状態情報を保存するコードなど、オブジェクトを破棄する直前に実行する必要があるコードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="da887-131">The `Finalize` method can contain code that needs to execute just before an object is destroyed, such as code for closing files and saving state information.</span></span> <span data-ttu-id="da887-132">`Sub Finalize` の実行には若干のパフォーマンス低下が伴うため、オブジェクトを明示的に解放する必要がある場合にのみ、`Sub Finalize` メソッドを定義してください。</span><span class="sxs-lookup"><span data-stu-id="da887-132">There is a slight performance penalty for executing `Sub Finalize`, so you should define a `Sub Finalize` method only when you need to release objects explicitly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da887-133">CLR のガベージ コレクターは、(ことはできません) 破棄しませんの*オブジェクトのアンマネージ*、オペレーティング システムが CLR 環境の外部で直接実行するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="da887-133">The garbage collector in the CLR does not (and cannot) dispose of *unmanaged objects*, objects that the operating system executes directly, outside the CLR environment.</span></span> <span data-ttu-id="da887-134">これは、管理されていないオブジェクトごとに異なる方法で破棄する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="da887-134">This is because different unmanaged objects must be disposed of in different ways.</span></span> <span data-ttu-id="da887-135">その情報は、管理されていないオブジェクトに直接には関連付けられません。オブジェクトのドキュメントに記載する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da887-135">That information is not directly associated with the unmanaged object; it must be found in the documentation for the object.</span></span> <span data-ttu-id="da887-136">管理されていないオブジェクトを使用するクラスでは、`Finalize` メソッド内でそのオブジェクトを破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da887-136">A class that uses unmanaged objects must dispose of them in its `Finalize` method.</span></span>  
  
 <span data-ttu-id="da887-137">`Finalize` デストラクターは、所属先のクラスまたは派生クラスからのみ呼び出し可能な保護されたメソッドです。</span><span class="sxs-lookup"><span data-stu-id="da887-137">The `Finalize` destructor is a protected method that can be called only from the class it belongs to, or from derived classes.</span></span> <span data-ttu-id="da887-138">`Finalize` はオブジェクトが破棄されるときに自動的に呼び出されるため、派生クラスの `Finalize` 実装の外部から `Finalize` を明示的に呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="da887-138">The system calls `Finalize` automatically when an object is destroyed, so you should not explicitly call `Finalize` from outside of a derived class's `Finalize` implementation.</span></span>  
  
 <span data-ttu-id="da887-139">オブジェクトが nothing に設定されるとすぐに実行される `Class_Terminate` と異なり、通常、オブジェクトがスコープを失ってから Visual Basic が `Finalize` デストラクターを呼び出すまでに遅延が発生します。</span><span class="sxs-lookup"><span data-stu-id="da887-139">Unlike `Class_Terminate`, which executes as soon as an object is set to nothing, there is usually a delay between when an object loses scope and when Visual Basic calls the `Finalize` destructor.</span></span> [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]<span data-ttu-id="da887-140">以降のバージョンでは、2 つ目の一種のデストラクター、および<xref:System.IDisposable.Dispose%2A>、すぐにリソースを解放するには、いつでも明示的に呼び出すを</xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-140"> and later versions allow for a second kind of destructor, <xref:System.IDisposable.Dispose%2A>, which can be explicitly called at any time to immediately release resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da887-141">`Finalize` デストラクターからは例外をスローしません。これは、その例外をアプリケーションで処理できないために、アプリケーションが異常終了する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="da887-141">A `Finalize` destructor should not throw exceptions, because they cannot be handled by the application and can cause the application to terminate.</span></span>  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a><span data-ttu-id="da887-142">クラス階層での New メソッドおよび Finalize メソッドの動作</span><span class="sxs-lookup"><span data-stu-id="da887-142">How New and Finalize Methods Work in a Class Hierarchy</span></span>  
 <span data-ttu-id="da887-143">クラスのインスタンスが作成されると、そのオブジェクト内に `New` という名前のプロシージャが存在する場合、共通言語ランタイム (CLR) はそのプロシージャを実行しようとします。</span><span class="sxs-lookup"><span data-stu-id="da887-143">Whenever an instance of a class is created, the common language runtime (CLR) attempts to execute a procedure named `New`, if it exists in that object.</span></span> <span data-ttu-id="da887-144">`New` は、オブジェクトの他のコードを実行する前に新しいオブジェクトを初期化するために使用される、`constructor`と呼ばれる種類のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="da887-144">`New` is a type of procedure called a `constructor` that is used to initialize new objects before any other code in an object executes.</span></span> <span data-ttu-id="da887-145">`New` コンストラクターを使用すると、ファイルを開く、データベースに接続する、変数を初期化するなど、オブジェクトを使用する前に実行する必要があるタスクを管理できます。</span><span class="sxs-lookup"><span data-stu-id="da887-145">A `New` constructor can be used to open files, connect to databases, initialize variables, and take care of any other tasks that need to be done before an object can be used.</span></span>  
  
 <span data-ttu-id="da887-146">派生クラスのインスタンスが作成されると、まず基本クラスの `Sub New` コンストラクターが実行され、続いて派生クラスのコンストラクターが実行されます。</span><span class="sxs-lookup"><span data-stu-id="da887-146">When an instance of a derived class is created, the `Sub New` constructor of the base class executes first, followed by constructors in derived classes.</span></span> <span data-ttu-id="da887-147">このように動作するのは、`Sub New` コンストラクターの最初のコード行では、`MyBase.New()` 構文を使用して、クラス階層の自身のすぐ上位にあるクラスのコンストラクターを呼び出すためです。</span><span class="sxs-lookup"><span data-stu-id="da887-147">This happens because the first line of code in a `Sub New` constructor uses the syntax `MyBase.New()`to call the constructor of the class immediately above itself in the class hierarchy.</span></span> <span data-ttu-id="da887-148">`Sub New` コンストラクターはその後、基本クラスのコンストラクターに到達するまで、クラス階層のクラスごとに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="da887-148">The `Sub New` constructor is then called for each class in the class hierarchy until the constructor for the base class is reached.</span></span> <span data-ttu-id="da887-149">その時点で、基本クラスのコンストラクター内のコードが実行され、続いてすべての派生クラスの各コンストラクター内のコードが実行され、最後にほとんどの派生クラス内のコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="da887-149">At that point, the code in the constructor for the base class executes, followed by the code in each constructor in all derived classes and the code in the most derived classes is executed last.</span></span>  
  
 <span data-ttu-id="da887-150">![コンス トラクターと継承](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")</span><span class="sxs-lookup"><span data-stu-id="da887-150">![Constructors and Inheritance](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")</span></span>  
  
 <span data-ttu-id="da887-151">CLR が呼び出すオブジェクトを不要になったとき、<xref:System.Object.Finalize%2A>のメモリを解放する前にそのオブジェクトのメソッドです</xref:System.Object.Finalize%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-151">When an object is no longer needed, the CLR calls the <xref:System.Object.Finalize%2A> method for that object before freeing its memory.</span></span> <span data-ttu-id="da887-152"><xref:System.Object.Finalize%2A>メソッドが呼び出される、`destructor`ファイルおよびデータベース、およびその他のオブジェクトを解放する前に行う必要があるタスクへの接続を閉じて状態情報の保存などのクリーンアップ タスクが実行されるためです</xref:System.Object.Finalize%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-152">The <xref:System.Object.Finalize%2A> method is called a `destructor` because it performs cleanup tasks, such as saving state information, closing files and connections to databases, and other tasks that must be done before releasing the object.</span></span>  
  
 <span data-ttu-id="da887-153">![コンス トラクター Inheritance2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")</span><span class="sxs-lookup"><span data-stu-id="da887-153">![Constructors Inheritance2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")</span></span>  
  
## <a name="idisposable-interface"></a><span data-ttu-id="da887-154">IDisposable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da887-154">IDisposable Interface</span></span>  
 <span data-ttu-id="da887-155">クラスのインスタンスは、多くの場合、Windows ハンドルやデータベース接続など、CLR では管理されないリソースを制御します。</span><span class="sxs-lookup"><span data-stu-id="da887-155">Class instances often control resources not managed by the CLR, such as Windows handles and database connections.</span></span> <span data-ttu-id="da887-156">これらのリソースは、オブジェクトがガベージ コレクターによって破棄されるときに解放されるように、クラスの `Finalize` メソッドで破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da887-156">These resources must be disposed of in the `Finalize` method of the class, so that they will be released when the object is destroyed by the garbage collector.</span></span> <span data-ttu-id="da887-157">ただし、ガベージ コレクターは、CLR でより多くの空きメモリが必要な場合にのみ、オブジェクトを破棄します。</span><span class="sxs-lookup"><span data-stu-id="da887-157">However, the garbage collector destroys objects only when the CLR requires more free memory.</span></span> <span data-ttu-id="da887-158">つまり、オブジェクトがスコープ外になるまで、リソースが解放されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="da887-158">This means that the resources may not be released until long after the object goes out of scope.</span></span>  
  
 <span data-ttu-id="da887-159">ガベージ コレクションを補足するために、クラスが実装している場合、システム リソースを積極的に管理するためのメカニズムを提供できます、<xref:System.IDisposable>インターフェイス</xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="da887-159">To supplement garbage collection, your classes can provide a mechanism to actively manage system resources if they implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="da887-160"><xref:System.IDisposable>1 つのメソッドを持つ<xref:System.IDisposable.Dispose%2A>、どのクライアントがオブジェクトを使用して終了するときに呼び出す必要があります</xref:System.IDisposable.Dispose%2A>。</xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="da887-160"><xref:System.IDisposable> has one method, <xref:System.IDisposable.Dispose%2A>, which clients should call when they finish using an object.</span></span> <span data-ttu-id="da887-161">使用することができます、<xref:System.IDisposable.Dispose%2A>をすぐにリソースを解放し、ファイルを閉じるなどのタスクを実行してデータベース接続</xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-161">You can use the <xref:System.IDisposable.Dispose%2A> method to immediately release resources and perform tasks such as closing files and database connections.</span></span> <span data-ttu-id="da887-162">異なり、`Finalize`デストラクター、<xref:System.IDisposable.Dispose%2A>メソッドは自動的に呼び出されません</xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-162">Unlike the `Finalize` destructor, the <xref:System.IDisposable.Dispose%2A> method is not called automatically.</span></span> <span data-ttu-id="da887-163">クラスのクライアントを明示的に呼び出す必要があります<xref:System.IDisposable.Dispose%2A>をすぐにリソースを解放する場合します</xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-163">Clients of a class must explicitly call <xref:System.IDisposable.Dispose%2A> when you want to immediately release resources.</span></span>  
  
### <a name="implementing-idisposable"></a><span data-ttu-id="da887-164">IDisposable の実装</span><span class="sxs-lookup"><span data-stu-id="da887-164">Implementing IDisposable</span></span>  
 <span data-ttu-id="da887-165">実装するクラス、<xref:System.IDisposable>インターフェイスは、次のコード セクションを含める必要があります:</xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="da887-165">A class that implements the <xref:System.IDisposable> interface should include these sections of code:</span></span>  
  
-   <span data-ttu-id="da887-166">オブジェクトが破棄されているかどうかを追跡するためのフィールド。</span><span class="sxs-lookup"><span data-stu-id="da887-166">A field for keeping track of whether the object has been disposed:</span></span>  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
-   <span data-ttu-id="da887-167">オーバー ロード、<xref:System.IDisposable.Dispose%2A>クラスのリソースを解放する</xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-167">An overload of the <xref:System.IDisposable.Dispose%2A> that frees the class's resources.</span></span> <span data-ttu-id="da887-168">このメソッドによって呼び出される、<xref:System.IDisposable.Dispose%2A>と`Finalize`基本クラスのメソッド:</xref:System.IDisposable.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="da887-168">This method should be called by the <xref:System.IDisposable.Dispose%2A> and `Finalize` methods of the base class:</span></span>  
  
    ```  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposed Then  
            If disposing Then  
                ' Insert code to free managed resources.  
            End If  
            ' Insert code to free unmanaged resources.  
        End If  
        Me.disposed = True  
    End Sub  
    ```  
  
-   <span data-ttu-id="da887-169">実装<xref:System.IDisposable.Dispose%2A>次のコードのみを含む:</xref:System.IDisposable.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="da887-169">An implementation of <xref:System.IDisposable.Dispose%2A> that contains only the following code:</span></span>  
  
    ```  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
    ```  
  
-   <span data-ttu-id="da887-170">次のコードのみを含む `Finalize` メソッドのオーバーライド。</span><span class="sxs-lookup"><span data-stu-id="da887-170">An override of the `Finalize` method that contains only the following code:</span></span>  
  
    ```  
    Protected Overrides Sub Finalize()  
        Dispose(False)  
        MyBase.Finalize()  
    End Sub  
    ```  
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a><span data-ttu-id="da887-171">IDisposable を実装するクラスからの派生</span><span class="sxs-lookup"><span data-stu-id="da887-171">Deriving from a Class that Implements IDisposable</span></span>  
 <span data-ttu-id="da887-172">実装する基本クラスから派生したクラス、<xref:System.IDisposable>インターフェイスは破棄する必要があるその他のリソースを使用しない限り、基本メソッドをオーバーライドする必要はありません</xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="da887-172">A class that derives from a base class that implements the <xref:System.IDisposable> interface does not need to override any of the base methods unless it uses additional resources that need to be disposed.</span></span> <span data-ttu-id="da887-173">その場合、派生クラスでは、派生クラスのリソースを破棄するように基本クラスの `Dispose(disposing)` メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="da887-173">In that situation, the derived class should override the base class's `Dispose(disposing)` method to dispose of the derived class's resources.</span></span> <span data-ttu-id="da887-174">このオーバーライドでは、基本クラスの `Dispose(disposing)` メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="da887-174">This override must call the base class's `Dispose(disposing)` method.</span></span>  
  
```  
Protected Overrides Sub Dispose(ByVal disposing As Boolean)  
    If Not Me.disposed Then  
        If disposing Then  
            ' Insert code to free managed resources.  
        End If  
        ' Insert code to free unmanaged resources.  
    End If  
    MyBase.Dispose(disposing)  
End Sub  
```  
  
 <span data-ttu-id="da887-175">派生クラスには、基本クラスのオーバーライドできません<xref:System.IDisposable.Dispose%2A>と`Finalize`メソッド</xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-175">A derived class should not override the base class's <xref:System.IDisposable.Dispose%2A> and `Finalize` methods.</span></span> <span data-ttu-id="da887-176">これらのメソッドが派生クラスのインスタンスから呼び出されると、基本クラスでのこれらのメソッドの実装によって、派生クラスでの `Dispose(disposing)` メソッドのオーバーライドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="da887-176">When those methods are called from an instance of the derived class, the base class's implementation of those methods call the derived class's override of the `Dispose(disposing)` method.</span></span>  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a><span data-ttu-id="da887-177">ガベージ コレクションと Finalize デストラクター</span><span class="sxs-lookup"><span data-stu-id="da887-177">Garbage Collection and the Finalize Destructor</span></span>  
 <span data-ttu-id="da887-178">[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]を使用して、*参照トレース ガベージ コレクション*システムを定期的に未使用のリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="da887-178">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] uses the *reference-tracing garbage collection* system to periodically release unused resources.</span></span> <span data-ttu-id="da887-179">Visual Basic 6.0 とそれ以前のバージョンの使用と呼ばれるさまざまなシステム*参照カウント*リソースを管理します。</span><span class="sxs-lookup"><span data-stu-id="da887-179">Visual Basic 6.0 and earlier versions used a different system called *reference counting* to manage resources.</span></span> <span data-ttu-id="da887-180">どちらのシステムも同じ機能を自動的に実行しますが、いくつかの重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="da887-180">Although both systems perform the same function automatically, there are a few important differences.</span></span>  
  
 <span data-ttu-id="da887-181">CLR は、不要と判断したオブジェクトを定期的に破棄します。</span><span class="sxs-lookup"><span data-stu-id="da887-181">The CLR periodically destroys objects when the system determines that such objects are no longer needed.</span></span> <span data-ttu-id="da887-182">オブジェクトは、システム リソースが不足したときには迅速に解放され、それ以外の場合には解放の頻度が低くなります。</span><span class="sxs-lookup"><span data-stu-id="da887-182">Objects are released more quickly when system resources are in short supply, and less frequently otherwise.</span></span> <span data-ttu-id="da887-183">オブジェクトがスコープを失ってから CLR が解放するまでに遅延が発生します。つまり、Visual Basic 6.0 とそれ以前のバージョンのオブジェクトとは異なり、オブジェクトがいつ破棄されるかを正確に特定することはできません。</span><span class="sxs-lookup"><span data-stu-id="da887-183">The delay between when an object loses scope and when the CLR releases it means that, unlike with objects in Visual Basic 6.0 and earlier versions, you cannot determine exactly when the object will be destroyed.</span></span> <span data-ttu-id="da887-184">このような場合、オブジェクトがあると言わ*不明確な有効期間*します。</span><span class="sxs-lookup"><span data-stu-id="da887-184">In such a situation, objects are said to have *non-deterministic lifetime*.</span></span> <span data-ttu-id="da887-185">ほとんどの場合、有効期間が不明確でもアプリケーションの作成方法は変わりません。ただし、オブジェクトがスコープを失ってもすぐには `Finalize` デストラクターが実行されない可能性があることに留意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da887-185">In most cases, non-deterministic lifetime does not change how you write applications, as long as you remember that the `Finalize` destructor may not immediately execute when an object loses scope.</span></span>  
  
 <span data-ttu-id="da887-186">ガベージ コレクション システム間の相違点にはこの他、`Nothing` を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="da887-186">Another difference between the garbage-collection systems involves the use of `Nothing`.</span></span> <span data-ttu-id="da887-187">Visual Basic 6.0 とそれ以前のバージョンの参照カウントを利用するために、プログラマはオブジェクト変数に `Nothing` を割り当てて、オブジェクト変数が保持する参照を解放することがありました。</span><span class="sxs-lookup"><span data-stu-id="da887-187">To take advantage of reference counting in Visual Basic 6.0 and earlier versions, programmers sometimes assigned `Nothing` to object variables to release the references those variables held.</span></span> <span data-ttu-id="da887-188">変数がオブジェクトへの最後の参照を保持していた場合、オブジェクトのリソースは直ちに解放されました。</span><span class="sxs-lookup"><span data-stu-id="da887-188">If the variable held the last reference to the object, the object's resources were released immediately.</span></span> <span data-ttu-id="da887-189">Visual Basic のそれ以降のバージョンでも、このプロシージャが有益な場合がありますが、実行しても、参照したオブジェクトによってリソースが直ちに解放されることはありません。</span><span class="sxs-lookup"><span data-stu-id="da887-189">In later versions of Visual Basic, while there may be cases in which this procedure is still valuable, performing it never causes the referenced object to release its resources immediately.</span></span> <span data-ttu-id="da887-190">リソースを直ちに解放するには、オブジェクトの<xref:System.IDisposable.Dispose%2A>メソッドを使用可能な場合です</xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="da887-190">To release resources immediately, use the object's <xref:System.IDisposable.Dispose%2A> method, if available.</span></span> <span data-ttu-id="da887-191">変数を `Nothing` に設定する必要があるのは、ガベージ コレクターが孤立したオブジェクトを検出するのに要する時間よりも、変数の有効期間が長い場合のみです。</span><span class="sxs-lookup"><span data-stu-id="da887-191">The only time you should set a variable to `Nothing` is when its lifetime is long relative to the time the garbage collector takes to detect orphaned objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da887-192">関連項目</span><span class="sxs-lookup"><span data-stu-id="da887-192">See Also</span></span>  
 <span data-ttu-id="da887-193"><xref:System.IDisposable.Dispose%2A></xref:System.IDisposable.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="da887-193"><xref:System.IDisposable.Dispose%2A></span></span>   
<span data-ttu-id="da887-194"> [コンポーネントの初期化と終了](http://msdn.microsoft.com/library/58444076-a9d2-4c91-b3f6-0e180dc0695d) </span><span class="sxs-lookup"><span data-stu-id="da887-194"> [Initialization and Termination of Components](http://msdn.microsoft.com/library/58444076-a9d2-4c91-b3f6-0e180dc0695d) </span></span>  
<span data-ttu-id="da887-195"> [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="da887-195"> [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
<span data-ttu-id="da887-196"> [アンマネージ リソースをクリーンアップします。](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) </span><span class="sxs-lookup"><span data-stu-id="da887-196"> [Cleaning Up Unmanaged Resources](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) </span></span>  
<span data-ttu-id="da887-197"> [Nothing](../../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="da887-197"> [Nothing](../../../../visual-basic/language-reference/nothing.md)</span></span>
