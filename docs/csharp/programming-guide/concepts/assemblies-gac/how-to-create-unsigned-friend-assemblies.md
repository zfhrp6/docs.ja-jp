---
title: "方法: 署名のないフレンド アセンブリを作成する (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c7d2924f0a619c234871232e155bb6f23e43aee4
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>方法: 署名のないフレンド アセンブリを作成する (C#)
この例では、署名のないアセンブリと共にフレンド アセンブリを使用する方法を示します。  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>署名のないアセンブリとフレンド アセンブリを作成するには  
  
1.  コマンド プロンプトを開きます。  
  
2.  次のコードを含む、`friend_signed_A.` という名前の C# ファイルを作成します。 このコードは、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性を使用して、friend_signed_B をフレンド アセンブリとして宣言します。  
  
    ```csharp  
    // friend_unsigned_A.cs  
    // Compile with:   
    // csc /target:library friend_unsigned_A.cs  
    using System.Runtime.CompilerServices;  
    using System;  
  
    [assembly: InternalsVisibleTo("friend_unsigned_B")]  
  
    // Type is internal by default.  
    class Class1  
    {  
        public void Test()  
        {  
            Console.WriteLine("Class1.Test");  
        }  
    }  
  
    // Public type with internal member.  
    public class Class2  
    {  
        internal void Test()  
        {  
            Console.WriteLine("Class2.Test");  
        }  
    }  
    ```  
  
3.  次のコマンドを使用して friend_signed_A をコンパイルして署名します。  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  次のコードを含む、`friend_unsigned_B` という名前の C# ファイルを作成します。 friend_unsigned_A が friend_unsigned_B をフレンド アセンブリとして指定しているため、friend_unsigned_B 内のコードは、friend_unsigned_A の `internal` 型とメンバーにアクセスできます。  
  
    ```csharp  
    // friend_unsigned_B.cs  
    // Compile with:   
    // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            // Access an internal type.  
            Class1 inst1 = new Class1();  
            inst1.Test();  
  
            Class2 inst2 = new Class2();  
            // Access an internal member of a public type.  
            inst2.Test();  
  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
5.  次のコマンドを使用して friend_signed_B をコンパイルします。  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     コンパイラによって生成されたアセンブリの名前は、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性に渡されたフレンド アセンブリ名と一致している必要があります。 `/out` コンパイラ オプションを使用して、出力アセンブリ (.exe または .dll) の名前を明示的に指定する必要があります。 詳しくは、「[/out (C# コンパイラ オプション)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md)」をご覧ください。  
  
6.  friend_signed_B.exe ファイルを実行します。  
  
     プログラムによって 2 つの文字列 "Class1.Test" と "Class2.Test" が出力されます。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性と <xref:System.Security.Permissions.StrongNameIdentityPermission> クラスには、類似点がいくつかあります。 主な違いは、<xref:System.Security.Permissions.StrongNameIdentityPermission> はセキュリティ アクセス許可を要求することで特定のコード セクションを実行しますが、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性は `internal` 型とメンバーの参照可能範囲を制御します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [アセンブリとグローバル アセンブリ キャッシュ (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [フレンド アセンブリ (C++)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [方法: 署名されたフレンド アセンブリを作成する (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)
