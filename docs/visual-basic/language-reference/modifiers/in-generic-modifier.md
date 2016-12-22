---
title: "In (Generic Modifier) (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.VarianceIn"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "contravariance, In keyword [Visual Basic]"
  - "In keyword [Visual Basic]"
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# In (Generic Modifier) (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ジェネリック型パラメーターの `In` キーワードは、型パラメーターが反変であることを指定します。  
  
## 解説  
 反変性は、ジェネリック パラメーターによって指定された型よりも弱い派生型を使用できるようにする機能です。  これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。  
  
 詳細については、「[共変性と反変性](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 規則  
 `In` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。  
  
 型パラメーターは、メソッド引数の型としてのみ使用されてメソッドの戻り値の型として使用されない場合に、ジェネリック インターフェイスまたは汎用デリゲートで反変であることを宣言できます。  `ByRef` パラメーターは、共変または反変にすることはできません。  
  
 共変性および反変性は参照型でサポートされ、値の型ではサポートされません。  
  
 Visual Basic では、デリゲート型を指定せずに、反変インターフェイスのイベントを宣言することはできません。  また、反変インターフェイスに入れ子になったクラス、列挙、または構造体を含めることはできませんが、これらに入れ子になったインターフェイスを含めることはできます。  
  
## \[動作\]  
 反変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、インターフェイスの型パラメーターによって指定された型よりも弱い派生型の引数を受け取ることができます。  たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IComparer%601> インターフェイスでは T 型が反変なので、`Person` が `Employee` を継承する場合、特別な変換メソッドを使用しなくても `IComparer(Of Person)` 型のオブジェクトを `IComparer(Of Employee)` 型のオブジェクトに割り当てることができます。  
  
 反変のデリゲートには、型は同じだがより弱い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。  
  
## 使用例  
 反変のジェネリック インターフェイスを宣言、拡張、および実装する方法を次の例に示します。  また、このインターフェイスを実装するクラスの暗黙の型変換を使用する方法も示します。  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## 使用例  
 反変の汎用デリゲートを宣言、インスタンス化、および起動する方法を次の例に示します。  また、デリゲート型を暗黙的に変換する方法も示します。  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## 参照  
 [ジェネリック インターフェイスの分散](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)