---
title: "リフレクション (C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
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
ms.openlocfilehash: ab40ab2258703670576084eccf7fd7e1b113d08d
ms.lasthandoff: 03/13/2017

---
# <a name="reflection-c"></a>リフレクション (C#)
リフレクションは、アセンブリ、モジュール、および型を記述する (<xref:System.Type> 型の) オブジェクトを提供します。 リフレクションを使用すると、動的に型のインスタンスを作成したり、作成したインスタンスを既存のオブジェクトにバインドしたり、さらに既存のオブジェクトから型を取得してそのオブジェクトのメソッドを呼び出したり、フィールドやプロパティにアクセスしたりできます。 コードで属性を使用している場合は、リフレクションを使用してそれらにアクセスできます。 詳細については、「[属性](https://msdn.microsoft.com/library/5x6cd29c)」を参照してください。  
  
 次の例は、`GetType` メソッドを使用して変数の型を取得する簡単なリフレクションを示しています。このメソッドは、`Object` 基底クラスからすべての型に継承される静的メソッドです。  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 出力は次のようになります。  
  
 `System.Int32`  
  
 次の例では、リフレクションを使用して、読み込まれたアセンブリの完全名を取得します。  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 出力は次のようになります。  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  C# の `protected` キーワードと `internal` キーワードは、IL では意味を持たないため、リフレクション API でも使用されません。 IL では、"*ファミリ*" および "*アセンブリ*" という用語がこれに相当します。 リフレクションを使用して `internal` メソッドを指定するには、<xref:System.Reflection.MethodBase.IsAssembly%2A> プロパティを使用します。 `protected internal` メソッドを指定するには、<xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A> を使用します。  
  
## <a name="reflection-overview"></a>リフレクションの概要  
 リフレクションは、次の場合に役立ちます。  
  
-   プログラムのメタデータ内の属性にアクセスする必要がある。 詳細については、「[属性に格納されている情報の取得](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)」を参照してください。  
  
-   アセンブリの型をチェックし、インスタンス化する。  
  
-   実行時に新しい型を作成する。 <xref:System.Reflection.Emit> でクラスを使用します。  
  
-   遅延バインディングを実行するために、実行時に作成された型でメソッドにアクセスする。 「[型の動的な読み込みおよび使用](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc)」を参照してください。  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
-   [リフレクション](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [型情報の表示](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [リフレクションとジェネリック型](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <xref:System.Reflection.Emit>  
  
-   [属性に格納されている情報の取得](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [共通言語ランタイムのアセンブリ](https://msdn.microsoft.com/library/k3677y81)
