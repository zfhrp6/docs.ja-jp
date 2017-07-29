---
title: "リフレクション (C#)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fa0aee4a0580ea28e3f0c70528dabaaf6f635f71
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

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
  
-   プログラムのメタデータ内の属性にアクセスする必要がある。 詳細については、「[属性に格納されている情報の取得](../../../standard/attributes/retrieving-information-stored-in-attributes.md)」を参照してください。  
  
-   アセンブリの型をチェックし、インスタンス化する。  
  
-   実行時に新しい型を作成する。 <xref:System.Reflection.Emit> でクラスを使います。  
  
-   遅延バインディングを実行するために、実行時に作成された型でメソッドにアクセスする。 「[型の動的な読み込みおよび使用](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)」を参照してください。  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
-   [リフレクション](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [型情報の表示](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [リフレクションとジェネリック型](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [属性に格納されている情報の取得](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [共通言語ランタイムのアセンブリ](https://msdn.microsoft.com/library/k3677y81)

