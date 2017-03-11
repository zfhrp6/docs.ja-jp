---
title: "in (ジェネリック修飾子) (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "反変性, in キーワード [C#]"
  - "in キーワード [C#]"
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# in (ジェネリック修飾子) (C# リファレンス)
ジェネリック型パラメーターの `in` キーワードは、型パラメーターが反変であることを指定します。  `in` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。  
  
 反変性は、ジェネリック パラメーターによって指定された型よりも弱い派生型を使用できるようにする機能です。  これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。  ジェネリック型パラメーターの共変性および反変性は参照型ではサポートされますが、値型ではサポートされません。  
  
 ジェネリック インターフェイスまたは汎用デリゲートでは、メソッド引数の型としてのみ使用され、メソッドの戻り値の型としては使用されない型を反変と宣言できます。  `Ref` パラメーターと `out` パラメーターにバリアントを指定することはできません。  
  
 反変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、インターフェイスの型パラメーターによって指定された型よりも弱い派生型の引数を受け取ることができます。  たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IComparer%601> インターフェイスでは T 型が反変なので、`Employee` が `Person` を継承する場合、特別な変換メソッドを使用しなくても `IComparer(Of Person)` 型のオブジェクトを `IComparer(Of Employee)` 型のオブジェクトに割り当てることができます。  
  
 反変のデリゲートには、型は同じだがより弱い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。  
  
 詳細については、「[共変性と反変性](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 使用例  
 反変のジェネリック インターフェイスを宣言、拡張、および実装する方法を次の例に示します。  また、このインターフェイスを実装するクラスの暗黙の型変換を使用する方法も示します。  
  
 [!code-cs[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/csharp/in-generic-modifier_1.cs)]  
  
## 使用例  
 反変の汎用デリゲートを宣言、インスタンス化、および起動する方法を次の例に示します。  また、デリゲート型を暗黙的に変換する方法も示します。  
  
 [!code-cs[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/csharp/in-generic-modifier_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [out](../../../csharp/language-reference/keywords/out-generic-modifier.md)   
 [共変性と反変性](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)