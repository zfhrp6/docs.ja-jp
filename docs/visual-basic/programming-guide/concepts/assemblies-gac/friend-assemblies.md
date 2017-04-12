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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c6e01ae91b9d5d875bb618993cd9eda82db59399
ms.lasthandoff: 03/13/2017

---
# <a name="friend-assemblies-visual-basic"></a>フレンド アセンブリ (Visual Basic)
A*フレンド アセンブリ*別のアセンブリにアクセスできるアセンブリは、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)型およびメンバーです。 フレンド アセンブリとしてアセンブリを指定する場合は、不要になった型とメンバーをパブリックにするためには、他のアセンブリがアクセスできるマークする必要があります。 これは、次のシナリオで特に便利です。  
  
-   単体テストでの中にテスト コードで実行時に別のアセンブリ権限が必要ですとマークされているテスト対象のアセンブリ内のメンバーへのアクセス`Friend`します。  
  
-   クラス ライブラリを開発しており、ライブラリへの追加は、別のアセンブリに含まれるとマークされている既存のアセンブリのメンバーにアクセスする必要`Friend`します。  
  
## <a name="remarks"></a>コメント  
 使用することができます、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性を特定のアセンブリの&1; つまたは複数のフレンド アセンブリを指定します</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。 次の例では、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>アセンブリ A 内の属性し、アセンブリを指定`AssemblyB`フレンド アセンブリとして</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。 これにより、アセンブリ`AssemblyB`すべての型およびメンバーとしてマークされているアセンブリへのアクセス`Friend`します。  
  
> [!NOTE]
>  アセンブリをコンパイルする場合 (アセンブリ`AssemblyB`) は内部型または別のアセンブリの内部メンバーにアクセスする (アセンブリ*A*) を使用して出力ファイル (.exe または .dll) の名前を明示的に指定する必要があります、 **/out**コンパイラ オプション。 コンパイラがバインド先の外部参照時に構築しているアセンブリの名前をまだ生成していないために必要です。 詳細については、次を参照してください。 [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)します。  
  
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
  
 友人がアクセスできるように明示的に指定するアセンブリだけ`Friend`型およびメンバーです。 たとえば、アセンブリ B がアセンブリ A と C のアセンブリの参照アセンブリ B のフレンドである場合は、C がアクセスできないに`Friend`A の種類  
  
 コンパイラは渡されたフレンド アセンブリ名のいくつかの基本的な検証、実行、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。 場合アセンブリ*A*宣言*B*フレンド アセンブリとして、検証規則は、次のようにします。  
  
-   場合アセンブリ*A*という名前のアセンブリに厳密な*B*厳密な名前もします。 フレンド アセンブリ名、属性に渡される必要があります、アセンブリ名とアセンブリの署名に使用される厳密な名前キーの公開キーで構成されている*B*します。  
  
     渡されるフレンド アセンブリ名、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性がアセンブリの厳密な名前にすることはできません*B*: アセンブリのバージョン、カルチャ、アーキテクチャ、または公開キー トークンは含まれません</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>。  
  
-   場合アセンブリ*A*強力ではありませんという名前のフレンド アセンブリ名がアセンブリ名だけで構成する必要があります。 詳細については、次を参照してください。[方法: 作成の署名のないフレンド アセンブリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)します。  
  
-   場合アセンブリ*B*厳密な名前が、アセンブリの厳密な名前キーを指定する必要があります*B*プロジェクトの設定またはコマンドラインを使用して`/keyfile`コンパイラ オプション。 詳細については、次を参照してください。[方法: 署名されたフレンド アセンブリを作成する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)します。  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>クラスは、次の相違点の種類を共有する機能も提供します</xref:System.Security.Permissions.StrongNameIdentityPermission>。  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission>フレンド アセンブリがアセンブリ全体に適用中に、個々 の型に適用されます。</xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
-   何百ものアセンブリ内の型がある場合*A*アセンブリを共有する*B*、追加する必要が<xref:System.Security.Permissions.StrongNameIdentityPermission>そのすべてを</xref:System.Security.Permissions.StrongNameIdentityPermission>。 フレンド アセンブリを使用する場合のみ、フレンド関係を&1; 回宣言する必要があります。  
  
-   使用する場合<xref:System.Security.Permissions.StrongNameIdentityPermission>、共有する型がパブリックとして宣言する必要がある</xref:System.Security.Permissions.StrongNameIdentityPermission>。 として共有する型が宣言されたフレンド アセンブリを使用する場合`Friend`します。  
  
 詳細については、アセンブリにアクセスする方法について`Friend`型とモジュール ファイル (.netmodule 拡張子の付いたファイル) からメソッドを参照してください。 [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 <xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Security.Permissions.StrongNameIdentityPermission>   
 [方法: 署名のないフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [方法: 署名されたフレンド アセンブリ (Visual Basic) を作成します。](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)
