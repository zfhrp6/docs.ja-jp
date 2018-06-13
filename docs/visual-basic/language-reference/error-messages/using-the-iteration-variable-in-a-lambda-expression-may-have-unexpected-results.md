---
title: ラムダ式内で繰り返し変数を使用すると、予期しない結果が発生する可能性があります。
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 7144a5fd4a197fddaf1ac4132df0ff70995ad067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594163"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>ラムダ式内で繰り返し変数を使用すると、予期しない結果が発生する可能性があります。
ラムダ式で繰り返し変数を使用する必要があります予期しない結果。 代わりに、ループ内でローカル変数を作成し、繰り返し変数の値を割り当てます。  
  
 ループの反復変数をループ内で宣言されているラムダ式で使用する場合、この警告が表示されます。 たとえば、次の例に表示される警告が発生します。  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 次の例では、発生する可能性が予期しない結果を示します。  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 `For`ループがループの反復変数の値を返します、ラムダ式の配列を作成`i`です。 ラムダ式を評価するときに、`For Each`ループされる予定である 0、1、2、3、および 4 が表示されるの連続する値を参照してください`i`で、`For`ループします。 代わりの最終的な値を表示する`i`5 回を表示します。  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 既定では、このメッセージは警告です。 警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC42324  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ローカル変数に繰り返し変数の値を代入し、ローカル変数をラムダ式で使用します。  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>関連項目  
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
