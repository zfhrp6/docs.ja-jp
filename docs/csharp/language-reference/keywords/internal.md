---
title: internal (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3b115022ed2b38dfcfbbfad3c5fc00e0203b255
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="internal-c-reference"></a>internal (C# リファレンス)
`internal` キーワードは、型と型のメンバーを示す[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)です。 
  
 > このページで対象`internal`アクセスします。 `internal`キーワードはまたの一部、 [ `protected internal` ](./protected-internal.md)アクセス修飾子。
  
internal 型またはメンバーは、次の例のように、同じアセンブリ内のファイルでのみアクセスできます。  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 `internal` とその他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」と「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 アセンブリの詳細については、「[アセンブリとグローバル アセンブリ キャッシュ](../../../csharp/programming-guide/concepts/assemblies-gac/index.md)」を参照してください。  
  
 一般的に、内部アクセスはコンポーネント ベースの開発で使用されます。これは、コンポーネントのグループを、アプリケーション コードの他の部分に公開することなくプライベートに連携させることができるためです。 たとえば、グラフィカル ユーザー インターフェイスを構築するためのフレームワークでは、内部アクセスによってメンバーを使用することで連携する `Control` クラスと `Form` クラスを提供できます。 これらは内部のメンバーなので、フレームワークを使用しているコードには公開されません。  
  
 型またはメンバーが定義されているアセンブリの外側で、型またはメンバーを内部アクセスで参照するとエラーになります。  
  
## <a name="example"></a>例  
 この例には、2 つのファイル (`Assembly1.cs` と `Assembly1_a.cs`) が含まれています。 最初のファイルには、内部の基底クラス `BaseClass` が含まれています。 2 番目のファイルでは、`BaseClass` のインスタンス化を試行するとエラーが発生します。  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>例  
 この例では、例 1 で使用したのと同じファイルを使用し、`BaseClass` のアクセシビリティ レベルを `public` に変更します。 また、メンバー `IntM` のアクセシビリティ レベルを `internal` に変更します。 この場合、クラスのインスタンス化は可能ですが、内部メンバーへのアクセスはできません。  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)
