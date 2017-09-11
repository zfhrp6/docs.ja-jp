---
title: "方法: 署名されたフレンド アセンブリ (Visual Basic) を作成する |Microsoft ドキュメント"
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
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a8a7df331c8cd93de45d902cb9b6c67460952c6d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a><span data-ttu-id="67929-102">方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="67929-102">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="67929-103">この例では、フレンド アセンブリを厳密な名前を持つアセンブリを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="67929-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="67929-104">両方のアセンブリは厳密な名前する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67929-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="67929-105">この例では両方のアセンブリは、同じキーを使用して、2 つのアセンブリの異なるキーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="67929-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="67929-106">署名されたアセンブリおよびフレンド アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="67929-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="67929-107">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="67929-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="67929-108">厳密名ツールを使用して、次の一連のコマンドを使用して、キー ファイルを生成し、その公開キーを表示します。</span><span class="sxs-lookup"><span data-stu-id="67929-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="67929-109">詳細については、「[Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67929-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="67929-110">この例の厳密な名前のキーを生成し、FriendAssemblies.snk ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="67929-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="67929-111">FriendAssemblies.snk から公開キーを抽出し、FriendAssemblies.publickey に配置します。</span><span class="sxs-lookup"><span data-stu-id="67929-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="67929-112">FriendAssemblies.publickey ファイルに格納されている公開キーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="67929-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="67929-113">という名前の Visual Basic ファイルの作成`friend_signed_A`次のコードを格納しています。</span><span class="sxs-lookup"><span data-stu-id="67929-113">Create a Visual Basic file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="67929-114">コードを使用して、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>フレンド アセンブリとして friend_signed_B を宣言する属性</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="67929-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="67929-115">厳密名ツールは、実行するたびに新しい公開キーを生成します。</span><span class="sxs-lookup"><span data-stu-id="67929-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="67929-116">そのため、次の例で示すように、生成した公開キーで、次のコードに公開キーを置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="67929-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  <span data-ttu-id="67929-117">コンパイルし、次のコマンドを使用して friend_signed_A に署名します。</span><span class="sxs-lookup"><span data-stu-id="67929-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  <span data-ttu-id="67929-118">という名前の Visual Basic ファイルの作成`friend_signed_B`し、次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="67929-118">Create a Visual Basic file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="67929-119">Friend_signed_B のコードにアクセスできる friend_signed_A 指定フレンド アセンブリとして friend_signed_B しているので`Friend`型およびメンバー friend_signed_A からです。</span><span class="sxs-lookup"><span data-stu-id="67929-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `Friend` types and members from friend_signed_A.</span></span> <span data-ttu-id="67929-120">ファイルには、次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="67929-120">The file contains the following code.</span></span>  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="67929-121">コンパイルし、次のコマンドを使用して friend_signed_B に署名します。</span><span class="sxs-lookup"><span data-stu-id="67929-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     <span data-ttu-id="67929-122">コンパイラによって生成されたアセンブリの名前に渡されるフレンド アセンブリ名に一致する必要があります、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="67929-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="67929-123">使用してアセンブリを明示的に設定することができます、`/out`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="67929-123">You can explicitly set the assembly by using the `/out` compiler option.</span></span> <span data-ttu-id="67929-124">詳細については、次を参照してください。 [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)します。</span><span class="sxs-lookup"><span data-stu-id="67929-124">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
7.  <span data-ttu-id="67929-125">Friend_signed_B.exe ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="67929-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="67929-126">文字列"Class1.Test"を出力します。</span><span class="sxs-lookup"><span data-stu-id="67929-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="67929-127">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="67929-127">.NET Framework Security</span></span>  
 <span data-ttu-id="67929-128"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性と<xref:System.Security.Permissions.StrongNameIdentityPermission>クラス</xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>の類似点があります。</span><span class="sxs-lookup"><span data-stu-id="67929-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="67929-129">その主な違いは<xref:System.Security.Permissions.StrongNameIdentityPermission>一方、コードの特定のセクションを実行するセキュリティのアクセス許可を要求できます、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性の表示を制御する`Friend`型およびメンバー</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="67929-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67929-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="67929-130">See Also</span></span>  
 <span data-ttu-id="67929-131"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="67929-131"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
<span data-ttu-id="67929-132"> [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="67929-132"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="67929-133"> [フレンド アセンブリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="67929-133"> [Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span></span>  
<span data-ttu-id="67929-134"> [方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="67929-134"> [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
<span data-ttu-id="67929-135"> [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="67929-135"> [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="67929-136"> [Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23) </span><span class="sxs-lookup"><span data-stu-id="67929-136"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span></span>  
<span data-ttu-id="67929-137"> [作成して、アセンブリの厳密な名前を使用します。](https://msdn.microsoft.com/library/xwb8f617) </span><span class="sxs-lookup"><span data-stu-id="67929-137"> [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) </span></span>  
<span data-ttu-id="67929-138"> [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="67929-138"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)</span></span>
