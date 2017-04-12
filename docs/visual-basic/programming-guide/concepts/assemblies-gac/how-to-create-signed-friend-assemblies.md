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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1a69f7e833800ec7417bc35fad763f1001b3e7f9
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。
この例では、フレンド アセンブリを厳密な名前を持つアセンブリを使用する方法を示します。 両方のアセンブリは厳密な名前する必要があります。 この例では両方のアセンブリは、同じキーを使用して、2 つのアセンブリの異なるキーを使用できます。  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>署名されたアセンブリおよびフレンド アセンブリを作成するには  
  
1.  コマンド プロンプトを開きます。  
  
2.  厳密名ツールを使用して、次の一連のコマンドを使用して、キー ファイルを生成し、その公開キーを表示します。 詳細については、「[Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)」を参照してください。  
  
    1.  この例の厳密な名前のキーを生成し、FriendAssemblies.snk ファイルに保存します。  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  FriendAssemblies.snk から公開キーを抽出し、FriendAssemblies.publickey に配置します。  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  FriendAssemblies.publickey ファイルに格納されている公開キーが表示されます。  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  という名前の Visual Basic ファイルの作成`friend_signed_A`次のコードを格納しています。 コードを使用して、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>フレンド アセンブリとして friend_signed_B を宣言する属性</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。  
  
     厳密名ツールは、実行するたびに新しい公開キーを生成します。 そのため、次の例で示すように、生成した公開キーで、次のコードに公開キーを置き換える必要があります。  
  
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
  
4.  コンパイルし、次のコマンドを使用して friend_signed_A に署名します。  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  という名前の Visual Basic ファイルの作成`friend_signed_B`し、次のコードが含まれています。 Friend_signed_B のコードにアクセスできる friend_signed_A 指定フレンド アセンブリとして friend_signed_B しているので`Friend`型およびメンバー friend_signed_A からです。 ファイルには、次のコードが含まれています。  
  
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
  
6.  コンパイルし、次のコマンドを使用して friend_signed_B に署名します。  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     コンパイラによって生成されたアセンブリの名前に渡されるフレンド アセンブリ名に一致する必要があります、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。 使用してアセンブリを明示的に設定することができます、`/out`コンパイラ オプション。 詳細については、次を参照してください。 [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)します。  
  
7.  Friend_signed_B.exe ファイルを実行します。  
  
     文字列"Class1.Test"を出力します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性と<xref:System.Security.Permissions.StrongNameIdentityPermission>クラス</xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>の類似点があります。 その主な違いは<xref:System.Security.Permissions.StrongNameIdentityPermission>一方、コードの特定のセクションを実行するセキュリティのアクセス許可を要求できます、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性の表示を制御する`Friend`型およびメンバー</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission> 。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [フレンド アセンブリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)   
 [作成して、アセンブリの厳密な名前を使用します。](https://msdn.microsoft.com/library/xwb8f617)   
 [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)
