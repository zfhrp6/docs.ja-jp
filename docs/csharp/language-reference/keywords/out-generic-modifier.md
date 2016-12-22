---
title: "out (ジェネリック修飾子) (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "共変性, out キーワード [C#]"
  - "out キーワード [C#]"
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# out (ジェネリック修飾子) (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ジェネリック型パラメーターの `out` キーワードは、型パラメーターが共変であることを指定します。  `out` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。  
  
 共変性は、ジェネリック パラメーターによって指定された型よりも強い派生型を使用できるようにする機能です。  これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。  共変性および反変性は参照型ではサポートされますが、値型ではサポートされません。  
  
 共変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、型パラメーターによって指定された型よりも強い派生型を返すことができます。  たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IEnumerable%601> では T 型が共変なので、特別な変換メソッドを使用しなくても `IEnumerabe(Of String)` 型のオブジェクトを `IEnumerable(Of Object)` 型のオブジェクトに割り当てることができます。  
  
 共変のデリゲートには、型は同じだがより強い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。  
  
 詳細については、「[共変性と反変性](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 使用例  
 共変のジェネリック インターフェイスを宣言、拡張、および実装する方法を次の例に示します。  また、共変のインターフェイスを実装するクラスの暗黙の型変換を使用する方法も示します。  
  
 [!code-cs[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 ジェネリック インターフェイスでは、次の条件を満たす場合に型パラメーターを共変と宣言できます。  
  
-   型パラメーターがインターフェイス メソッドの戻り値の型としてのみ使用されてメソッド引数の型として使用されない。  
  
    > [!NOTE]
    >  この規則には例外が 1 つあります。  共変のインターフェイスで反変の汎用デリゲートをメソッド パラメーターとして使用する場合は、共変の型をこのデリゲートのジェネリック型パラメーターとして使用できます。  共変および反変の汎用デリゲートの詳細については、「[デリゲートの分散](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)」および「[Func および Action 汎用デリゲートでの分散の使用](../Topic/Using%20Variance%20for%20Func%20and%20Action%20Generic%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
-   型パラメーターがインターフェイス メソッドのジェネリック制約として使用されない。  
  
## 使用例  
 共変の汎用デリゲートを宣言、インスタンス化、および起動する方法を次の例に示します。  また、デリゲート型を暗黙的に変換する方法も示します。  
  
 [!code-cs[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 汎用デリゲートでは、メソッドの戻り値の型としてのみ使用されてメソッド引数の型として使用されない型を共変と宣言できます。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [ジェネリック インターフェイスの分散](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [in](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)