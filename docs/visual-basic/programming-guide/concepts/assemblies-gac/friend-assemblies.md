---
title: "フレンド アセンブリ (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 23c9167bf6a632b53202bdc56aebb2248065e967
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="f78ca-102">フレンド アセンブリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f78ca-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="f78ca-103">A*フレンド アセンブリ*別のアセンブリにアクセスできるアセンブリは、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)型およびメンバーです。</span><span class="sxs-lookup"><span data-stu-id="f78ca-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="f78ca-104">フレンド アセンブリとしてアセンブリを指定する場合は、不要になった型とメンバーをパブリックにするためには、他のアセンブリがアクセスできるマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f78ca-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="f78ca-105">これは、次のシナリオで特に便利です。</span><span class="sxs-lookup"><span data-stu-id="f78ca-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="f78ca-106">単体テストでの中にテスト コードで実行時に別のアセンブリ権限が必要ですとマークされているテスト対象のアセンブリ内のメンバーへのアクセス`Friend`します。</span><span class="sxs-lookup"><span data-stu-id="f78ca-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="f78ca-107">クラス ライブラリを開発しており、ライブラリへの追加は、別のアセンブリに含まれるとマークされている既存のアセンブリのメンバーにアクセスする必要`Friend`します。</span><span class="sxs-lookup"><span data-stu-id="f78ca-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f78ca-108">コメント</span><span class="sxs-lookup"><span data-stu-id="f78ca-108">Remarks</span></span>  
 <span data-ttu-id="f78ca-109">使用することができます、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性を特定のアセンブリの&1; つまたは複数のフレンド アセンブリを指定します</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="f78ca-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="f78ca-110">次の例では、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>アセンブリ A 内の属性し、アセンブリを指定`AssemblyB`フレンド アセンブリとして</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="f78ca-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="f78ca-111">これにより、アセンブリ`AssemblyB`すべての型およびメンバーとしてマークされているアセンブリへのアクセス`Friend`します。</span><span class="sxs-lookup"><span data-stu-id="f78ca-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f78ca-112">アセンブリをコンパイルする場合 (アセンブリ`AssemblyB`) は内部型または別のアセンブリの内部メンバーにアクセスする (アセンブリ*A*) を使用して出力ファイル (.exe または .dll) の名前を明示的に指定する必要があります、 **/out**コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="f78ca-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="f78ca-113">コンパイラがバインド先の外部参照時に構築しているアセンブリの名前をまだ生成していないために必要です。</span><span class="sxs-lookup"><span data-stu-id="f78ca-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="f78ca-114">詳細については、次を参照してください。 [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)します。</span><span class="sxs-lookup"><span data-stu-id="f78ca-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
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
  
 <span data-ttu-id="f78ca-115">友人がアクセスできるように明示的に指定するアセンブリだけ`Friend`型およびメンバーです。</span><span class="sxs-lookup"><span data-stu-id="f78ca-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="f78ca-116">たとえば、アセンブリ B がアセンブリ A と C のアセンブリの参照アセンブリ B のフレンドである場合は、C がアクセスできないに`Friend`A の種類</span><span class="sxs-lookup"><span data-stu-id="f78ca-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="f78ca-117">コンパイラは渡されたフレンド アセンブリ名のいくつかの基本的な検証、実行、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="f78ca-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="f78ca-118">場合アセンブリ*A*宣言*B*フレンド アセンブリとして、検証規則は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="f78ca-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="f78ca-119">場合アセンブリ*A*という名前のアセンブリに厳密な*B*厳密な名前もします。</span><span class="sxs-lookup"><span data-stu-id="f78ca-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="f78ca-120">フレンド アセンブリ名、属性に渡される必要があります、アセンブリ名とアセンブリの署名に使用される厳密な名前キーの公開キーで構成されている*B*します。</span><span class="sxs-lookup"><span data-stu-id="f78ca-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="f78ca-121">渡されるフレンド アセンブリ名、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性がアセンブリの厳密な名前にすることはできません*B*: アセンブリのバージョン、カルチャ、アーキテクチャ、または公開キー トークンは含まれません</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="f78ca-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="f78ca-122">場合アセンブリ*A*強力ではありませんという名前のフレンド アセンブリ名がアセンブリ名だけで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f78ca-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="f78ca-123">詳細については、次を参照してください。[方法: 作成の署名のないフレンド アセンブリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)します。</span><span class="sxs-lookup"><span data-stu-id="f78ca-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="f78ca-124">場合アセンブリ*B*厳密な名前が、アセンブリの厳密な名前キーを指定する必要があります*B*プロジェクトの設定またはコマンドラインを使用して`/keyfile`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="f78ca-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="f78ca-125">詳細については、次を参照してください。[方法: 署名されたフレンド アセンブリを作成する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)します。</span><span class="sxs-lookup"><span data-stu-id="f78ca-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="f78ca-126"><xref:System.Security.Permissions.StrongNameIdentityPermission>クラスは、次の相違点の種類を共有する機能も提供します</xref:System.Security.Permissions.StrongNameIdentityPermission>。</span><span class="sxs-lookup"><span data-stu-id="f78ca-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="f78ca-127"><xref:System.Security.Permissions.StrongNameIdentityPermission>フレンド アセンブリがアセンブリ全体に適用中に、個々 の型に適用されます。</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="f78ca-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="f78ca-128">何百ものアセンブリ内の型がある場合*A*アセンブリを共有する*B*、追加する必要が<xref:System.Security.Permissions.StrongNameIdentityPermission>そのすべてを</xref:System.Security.Permissions.StrongNameIdentityPermission>。</span><span class="sxs-lookup"><span data-stu-id="f78ca-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="f78ca-129">フレンド アセンブリを使用する場合のみ、フレンド関係を&1; 回宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f78ca-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="f78ca-130">使用する場合<xref:System.Security.Permissions.StrongNameIdentityPermission>、共有する型がパブリックとして宣言する必要がある</xref:System.Security.Permissions.StrongNameIdentityPermission>。</span><span class="sxs-lookup"><span data-stu-id="f78ca-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="f78ca-131">として共有する型が宣言されたフレンド アセンブリを使用する場合`Friend`します。</span><span class="sxs-lookup"><span data-stu-id="f78ca-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="f78ca-132">詳細については、アセンブリにアクセスする方法について`Friend`型とモジュール ファイル (.netmodule 拡張子の付いたファイル) からメソッドを参照してください。 [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)です。</span><span class="sxs-lookup"><span data-stu-id="f78ca-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78ca-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="f78ca-133">See Also</span></span>  
 <span data-ttu-id="f78ca-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="f78ca-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
 <span data-ttu-id="f78ca-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="f78ca-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></span></span>   
<span data-ttu-id="f78ca-136"> [方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="f78ca-136"> [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
<span data-ttu-id="f78ca-137"> [方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="f78ca-137"> [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span></span>  
<span data-ttu-id="f78ca-138"> [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="f78ca-138"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="f78ca-139"> [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="f78ca-139"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)</span></span>
