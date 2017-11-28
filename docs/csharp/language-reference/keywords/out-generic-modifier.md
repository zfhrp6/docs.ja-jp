---
title: "out (ジェネリック修飾子) (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5c63fe2229d4b7190397d3ba98fa150c84a12fb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="out-generic-modifier-c-reference"></a>out (ジェネリック修飾子) (C# リファレンス)
ジェネリック型パラメーターの `out` キーワードは、型パラメーターが共変であることを指定します。 `out` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。  
  
 共変性は、ジェネリック パラメーターによって指定された型よりも強い派生型を使用できるようにする機能です。 これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。 共変性および反変性は参照型ではサポートされますが、値の型ではサポートされません。  
  
 共変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、型パラメーターによって指定された型よりも強い派生型を返すことができます。 たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IEnumerable%601> では T 型が共変なので、特別な変換メソッドを使用しなくても `IEnumerabe(Of String)` 型のオブジェクトを `IEnumerable(Of Object)` 型のオブジェクトに割り当てることができます。  
  
 共変のデリゲートには、型は同じでありながらより強い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。  
  
 詳細については、「[共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、共変のジェネリック インターフェイスを宣言、拡張、および実装する方法を示します。 また、共変のインターフェイスを実装するクラスの暗黙的な変換を使用する方法も示します。  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 ジェネリック インターフェイスでは、次の条件を満たす場合に型パラメーターを共変として宣言できます。  
  
-   型パラメーターがインターフェイス メソッドの戻り値の型としてのみ使用され、メソッド引数の型として使用されない。  
  
    > [!NOTE]
    >  この規則には例外が 1 つあります。 共変のインターフェイスで反変の汎用デリゲートをメソッド パラメーターとして使用する場合は、共変の型をこのデリゲートのジェネリック型パラメーターとして使用できます。 共変および反変の汎用デリゲートの詳細については、「[デリゲートの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)」および「[Func および Action 汎用デリゲートでの分散の使用](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)」を参照してください。  
  
-   型パラメーターがインターフェイス メソッドのジェネリック制約として使用されない。  
  
## <a name="example"></a>例  
 次の例では、共変の汎用デリゲートを宣言、インスタンス化、および呼び出す方法を示します。 また、デリゲート型を暗黙的に変換する方法も示します。  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 汎用デリゲートでは、メソッドの戻り値の型としてのみ使用され、メソッド引数には使用されない型を共変として宣言できます。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ジェネリック インターフェイスの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)
