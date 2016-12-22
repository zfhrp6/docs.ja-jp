---
title: "internal (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "internal_CSharpKeyword"
  - "internal"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "internal キーワード [C#]"
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# internal (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`internal` のキーワードは、型および型メンバーのための [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) です。  internal 型またはメンバーは、この例に示すように同じアセンブリのファイル内でのみアクセスできます。  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 `protected internal` アクセス修飾子を持つ型やメンバーは、現在のアセンブリ、または包含クラスから派生した型からアクセスできます。  
  
 `internal` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」および「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 アセンブリの詳細については、「[アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 内部アクセスは、コンポーネントのグループがアプリケーション コードの残りの部分には公開されないプライベートな手法で協調動作できるので、一般的にはコンポーネント ベースの開発に使用されます。  たとえば、グラフィカル ユーザー インターフェイスを構築するためのフレームワークでは、内部アクセスでメンバーを使用して協調動作する `Control` クラスと `Form` クラスを提供できます。  これらのメンバーは内部メンバーなので、フレームワークを使用するコードに対しては公開されません。  
  
 内部アクセスのメンバーまたは型を、メンバーまたは型が定義されているアセンブリの外側で参照するとエラーになります。  
  
## 使用例  
 この例には、`Assembly1.cs` および `Assembly1`\_`a.cs` という 2 つのファイルがあります。  1 つ目のファイルには、内部基本クラス `BaseClass` があります。  2 つ目のファイルでは、`BaseClass` のインスタンス化が試行されますがエラーになります。  
  
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
  
## 使用例  
 この例では、例 1 で使用したのと同じファイルを使用します。ただし、`BaseClass` のアクセシビリティ レベルを `public` に変更します。  また、`IntM` メンバーのアクセシビリティ レベルを `internal` に変更します。  この場合、クラスをインスタンス化できますが、internal メンバーにはアクセスできません。  
  
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
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)