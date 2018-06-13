---
title: フレンド アセンブリ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
ms.openlocfilehash: 91bc33f33c4fc34c6e0f3ae197ecd2b876161de3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644382"
---
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="99234-102">フレンド アセンブリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99234-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="99234-103">A*フレンド アセンブリ*別のアセンブリにアクセスできるアセンブリ[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)型およびメンバー。</span><span class="sxs-lookup"><span data-stu-id="99234-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="99234-104">フレンド アセンブリとして指定した場合、public として宣言されていないその型とメンバーに、他のアセンブリからアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="99234-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="99234-105">この方法は、特に次の状況で利便性を発揮します。</span><span class="sxs-lookup"><span data-stu-id="99234-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="99234-106">単体テスト、時にテスト コードで実行されるときに別のアセンブリが必要ですとマークされているテスト対象のアセンブリ内のメンバーへのアクセス`Friend`です。</span><span class="sxs-lookup"><span data-stu-id="99234-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="99234-107">クラス ライブラリを開発していると、ライブラリへの追加は個別のアセンブリに含まれるとマークされている既存のアセンブリのメンバーにアクセスする必要`Friend`です。</span><span class="sxs-lookup"><span data-stu-id="99234-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99234-108">コメント</span><span class="sxs-lookup"><span data-stu-id="99234-108">Remarks</span></span>  
 <span data-ttu-id="99234-109"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を利用し、特定のアセンブリの 1 つまたは複数のフレンド アセンブリを特定できます。</span><span class="sxs-lookup"><span data-stu-id="99234-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="99234-110">次の例では、アセンブリ A で <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を利用し、アセンブリ `AssemblyB` をフレンド アセンブリとして指定しています。</span><span class="sxs-lookup"><span data-stu-id="99234-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="99234-111">これでアセンブリ `AssemblyB` は、アセンブリ A の中で `Friend` として宣言されているすべての型とメンバーにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="99234-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99234-112">別のアセンブリ (アセンブリ *A*) の内部型または内部メンバーにアクセスするアセンブリ (アセンブリ `AssemblyB`) をコンパイルする際は、**/out** コンパイラ オプションを使用して、出力ファイル (.exe または .dll) の名前を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99234-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="99234-113">この指定は必ず行ってください。コンパイラが外部参照にバインドする時点ではまだ、ビルド中のアセンブリの名前が生成されていないためです。</span><span class="sxs-lookup"><span data-stu-id="99234-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="99234-114">詳細については、次を参照してください。 [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)です。</span><span class="sxs-lookup"><span data-stu-id="99234-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports System  
<Assembly: InternalsVisibleTo("AssemblyB")>   
  
' Friend class.  
Friend Class FriendClass  
    Public Sub Test()  
        Console.WriteLine("Sample Class")  
    End Sub  
End Class  
  
' Public class with a Friend method.  
Public Class ClassWithFriendMethod  
    Friend Sub Test()  
        Console.WriteLine("Sample Method")  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="99234-115">`Friend` な型とメンバーにアクセスできるのは、明示的にフレンドとして指定されたアセンブリだけです。</span><span class="sxs-lookup"><span data-stu-id="99234-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="99234-116">たとえば、アセンブリ B がアセンブリ A のフレンドで、アセンブリ C がアセンブリ B を参照している場合、A の `Friend` 型に C からアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="99234-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="99234-117">コンパイラは、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡されるフレンド アセンブリ名の基本検証を実行します。</span><span class="sxs-lookup"><span data-stu-id="99234-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="99234-118">アセンブリ *A* が *B* をフレンド アセンブリとして宣言する場合、検証規則は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="99234-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="99234-119">アセンブリ *A* に厳密な名前が付けられている場合、アセンブリ *B* にも厳密な名前が付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="99234-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="99234-120">属性に渡されるフレンド アセンブリ名は、アセンブリ名と、アセンブリ *B* の署名に使用される厳密名キーの公開キーで構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="99234-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="99234-121"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡すフレンド アセンブリ名として、アセンブリ *B* の厳密な名前を指定することはできません。アセンブリのバージョン、カルチャ、アーキテクチャ、公開キー トークンは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="99234-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="99234-122">アセンブリ *A* が厳密名でない場合、フレンド アセンブリの名前は、アセンブリ名のみで構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="99234-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="99234-123">詳細については、次を参照してください。[する方法: 作成の署名のないフレンド アセンブリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)です。</span><span class="sxs-lookup"><span data-stu-id="99234-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="99234-124">アセンブリ *B* に厳密な名前が付けられている場合、プロジェクトの設定またはコマンド ラインの `/keyfile` コンパイラ オプションを使用してアセンブリ *B* の厳密名キーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99234-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="99234-125">詳細については、次を参照してください。[する方法: 署名されたフレンド アセンブリを作成する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)です。</span><span class="sxs-lookup"><span data-stu-id="99234-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="99234-126"><xref:System.Security.Permissions.StrongNameIdentityPermission> クラスも型を共有する機能を提供しますが、次のような違いがあります。</span><span class="sxs-lookup"><span data-stu-id="99234-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="99234-127">フレンド アセンブリはアセンブリ全体に適用されますが、<xref:System.Security.Permissions.StrongNameIdentityPermission> は個々の型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="99234-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="99234-128">アセンブリ *B* との間で共有したい型がアセンブリ *A* に数百個存在する場合、そのすべてに対して <xref:System.Security.Permissions.StrongNameIdentityPermission> を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99234-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="99234-129">フレンド アセンブリを使用した場合、フレンド関係を 1 回宣言するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="99234-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="99234-130"><xref:System.Security.Permissions.StrongNameIdentityPermission> を使用する場合、共有する型をパブリックとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99234-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="99234-131">フレンド アセンブリを使用する場合、共有する型は `Friend` として宣言されます。</span><span class="sxs-lookup"><span data-stu-id="99234-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="99234-132">アセンブリにアクセスする方法については`Friend`型とモジュール ファイル (.netmodule 拡張子を持つファイル) からメソッドを参照してください。 [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)です。</span><span class="sxs-lookup"><span data-stu-id="99234-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99234-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="99234-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [<span data-ttu-id="99234-134">方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="99234-134">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="99234-135">方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="99234-135">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="99234-136">アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99234-136">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="99234-137">プログラミングの概念</span><span class="sxs-lookup"><span data-stu-id="99234-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
