---
title: "方法: 署名のないフレンド アセンブリ (Visual Basic) を作成する |Microsoft ドキュメント"
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
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
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
ms.openlocfilehash: ceddb35c306f72c8927deda326d9fcca6c75d786
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。
この例では、フレンド アセンブリを署名されていないアセンブリを使用する方法を示します。  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>アセンブリおよびフレンド アセンブリを作成するには  
  
1.  コマンド プロンプトを開きます。  
  
2.  という名前の Visual Basic ファイルの作成`friend_signed_A.`次のコードを格納しています。 コードを使用して、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>フレンド アセンブリとして friend_signed_B を宣言する属性</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' Vbc /target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  コンパイルし、次のコマンドを使用して friend_signed_A に署名します。  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  という名前の Visual Basic ファイルの作成`friend_unsigned_B`次のコードを格納しています。 Friend_unsigned_B のコードにアクセスできる friend_unsigned_A 指定フレンド アセンブリとして friend_unsigned_B しているので`Friend`型およびメンバー friend_unsigned_A からです。  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  次のコマンドを使用して friend_signed_B をコンパイルします。  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     コンパイラによって生成されるアセンブリの名前に渡されるフレンド アセンブリ名に一致する必要があります、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。 使用してアセンブリを明示的に設定することができます、`/out`コンパイラ オプション。  
  
6.  Friend_signed_B.exe ファイルを実行します。  
  
     2 つの文字列を出力します。"Class1.Test"と"Class2.Test"です。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性と<xref:System.Security.Permissions.StrongNameIdentityPermission>クラス</xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>の類似点があります。 その主な違いは<xref:System.Security.Permissions.StrongNameIdentityPermission>一方、コードの特定のセクションを実行するセキュリティのアクセス許可を要求できます、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性の表示を制御する`Friend`型およびメンバー</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission> 。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [フレンド アセンブリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [ガイドのプログラミング概念](../../../../visual-basic/programming-guide/concepts/index.md)
