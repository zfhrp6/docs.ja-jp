---
title: "Out (Generic Modifier) (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.VarianceOut"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Out keyword [Visual Basic]"
  - "covariance, Out keyword [Visual Basic]"
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Out (Generic Modifier) (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ジェネリック型パラメーターの `Out` キーワードは、型が共変であることを指定します。  
  
## 解説  
 共変性は、ジェネリック パラメーターによって指定された型よりも強い派生型を使用できるようにする機能です。  これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。  
  
 詳細については、「[共変性と反変性](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 規則  
 `Out` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。  
  
 ジェネリック インターフェイスでは、次の条件を満たす場合に型パラメーターを共変と宣言できます。  
  
-   型パラメーターがインターフェイス メソッドの戻り値の型としてのみ使用されてメソッド引数の型として使用されない。  
  
    > [!NOTE]
    >  この規則には例外が 1 つあります。  共変のインターフェイスで反変の汎用デリゲートをメソッド パラメーターとして使用する場合は、共変の型をこのデリゲートのジェネリック型パラメーターとして使用できます。  共変および反変の汎用デリゲートの詳細については、「[デリゲートの分散](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)」および「[Func および Action 汎用デリゲートでの分散の使用](../Topic/Using%20Variance%20for%20Func%20and%20Action%20Generic%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
-   型パラメーターがインターフェイス メソッドのジェネリック制約として使用されない。  
  
 汎用デリゲートでは、メソッドの戻り値の型としてのみ使用されてメソッド引数の型として使用されない型パラメーターを共変と宣言できます。  
  
 共変性および反変性は参照型ではサポートされますが、値型ではサポートされません。  
  
 Visual Basic では、デリゲート型を指定せずに共変のインターフェイスのイベントを宣言することはできません。  また、共変のインターフェイスに入れ子になったクラス、列挙、または構造体を含めることはできませんが、これらに入れ子になったインターフェイスを含めることはできます。  
  
## \[動作\]  
 共変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、型パラメーターによって指定された型よりも強い派生型を返すことができます。  たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IEnumerable%601> では T 型が共変なので、特別な変換メソッドを使用しなくても `IEnumerabe(Of String)` 型のオブジェクトを `IEnumerable(Of Object)` 型のオブジェクトに割り当てることができます。  
  
 共変のデリゲートには、型は同じだがより強い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。  
  
## 使用例  
 共変のジェネリック インターフェイスを宣言、拡張、および実装する方法を次の例に示します。  また、共変のインターフェイスを実装するクラスの暗黙の型変換を使用する方法も示します。  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## 使用例  
 共変の汎用デリゲートを宣言、インスタンス化、および起動する方法を次の例に示します。  また、デリゲート型に暗黙の型変換を使用する方法も示します。  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## 参照  
 [ジェネリック インターフェイスの分散](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)